# Petstore
TIBCO BusinessEvents demo using Open API and BE WebStudio.

# Setup swagger editor
Swagger editor is used to send test and demo requests to BE engines via HTTP.

Download and unzip https://github.com/swagger-api/swagger-editor/releases/tag/v4.12.2 

Start swagger editor:
```
cd swagger-editor-4.12.2
npm i --legacy-peer-deps
npm start
```
The editor is started at URL: http://localhost:3001

To send HTTP requests from the Swagger editor to BE engines, we need to start browser with cors disabled.

For Chrome, close all browsers then
```
open -a "Google Chrome" --args --disable-web-security --user-data-dir=/tmp/chrome
```

For Brave, close all browsers then
```
open -n -a /Applications/Brave\ Browser.app/Contents/MacOS/Brave\ Browser --args --user-data-dir="/tmp/brave_dev_sess_1" --disable-web-security
```

In the browser, open URL `http://localhost:3001`, and then open the api specification file [Petstore.yaml](./Deployments/Petstore.yaml), you can then send API requests to BE inference engines.

Note that the BE inference engine can be started by using [start.script](./Deployments/start.script).

## Setup TIBCO BE RMS
RMS manages rules and decision tables that can be edited via WebStudio.

Start RMS
```
cd $BE_HOME/rms/bin
./be-rms
```

If it failed to start due to conflicting port of `5000`, you may find and stop the conflicting process and then restart RMS.
```
lsof -i tcp:5000
```

Login WebStudio in a web browser at `http://localhost:8090/WebStudio`.
default user name `admin` and password `admin`.

To import the Petstore project and edit its decision tables via the WebStudio, you may have to add an autorization file in `$BE_HOME/rms/config/security/Petstore.ac`.
