![Logo](./assets/images/logo.png)
# Vue fullstack template
![](https://travis-ci.org/erguotou520/vue-fullstack.svg?branch=master)

This project's goal is to help people create a **reactive, realtime and user friendly** backend system.

## Requirement
- `Mongodb` This project requires `mongodb` as the database. You can follow [it's tutorial](https://docs.mongodb.com/manual/administration/install-community/) to install it if you haven't installed it already. In consideration of the recent [mongodb attack event](https://www.bleepingcomputer.com/news/security/mongodb-apocalypse-is-here-as-ransom-attacks-hit-10-000-servers/), it's highly recommend to enable auth and disable public login for your mongodb.
- Basic `vue.js` skills

## About mock and i18n
If you chose to use mock server or not use i18n at project initialization, you need to take a look at this description, else you can skip this step.  
As `vue-cli` does't support to run a task after initialization, you need to run `npm run remove:i18n`(*This script doesn't change the page view which contains `change locale` in `client/src/components/Header.vue` and `client/src/view/auth/Login.vue`, you can remove that code manually.*) and `npm run remove:mock` manually.

## Usage
This is a project template for vue-cli. It is recommended to use npm 3+ for a more efficient dependency tree.
```shell
# cli version must be greater than 2.5.0
$ npm install -g vue-cli
$ vue init erguotou520/vue-fullstack my-project ## (important hint: don't use a dot in your project name, otherwise it will cause issues with mongodb)
$ cd my-project
$ npm install
# If you chose to use mock server, you need to run remove:mock to change the file structure, otherwise just skip this step
$ npm run remove:mock
# If you chose not to use vue-i18n, you need to run remove:i18n to replace the files with default locale text, otherwise just skip this step
$ npm run remove:i18n
# If you chose to use real backend server, run this script to start an express server
$ npm run server
# If you chose to use mock server, run this script to start a mock server
$ npm run mock
# Open another terminal and cd into my-project
# This runs a frontend dev server
$ npm run client
```

## What's Included
- `vue`
- `vue-router`
- `vuex`
- `vue-i18n`
- `vue-resource`
- `element-ui`
- `express`
- `mongoose`
- `socket.io`
- `mock server`

## Demo app
~~* Here is a [demo](https://vue-fullstack-demo.herokuapp.com) and the demo repo is [here](https://github.com/erguotou520/vue-fullstack-demo)~~  
~~* This is [another one](http://meals.erguotou.me)~~

Now the demo apps are generated by ci automatically and pushed to `vf-backend`|`vf-mock` branches.
- [Backend server demo](https://vf-backend.herokuapp.com)
- [Mock server demo](https://vf-mock.herokuapp.com/)

*Do not change the password please.*
```
username: admin
password: admin
```

## App structure
```
├─client               # frontend source folder
│  ├─build             # frontend dev scripts
│  ├─src               # frontend src
│  │  ├─assets
│  │  │  ├─css
│  │  │  ├─fonts
│  │  │  └─images
│  │  ├─components     # vue components
│  │  ├─http           # vue-resource configuration
│  │  ├─locale         # vue-i18n configuration
│  │  ├─router         # vue-router configuration
│  │  ├─socket         # socket.io configuration
│  │  ├─storage        # web storage api
│  │  ├─store          # vuex store
│  │  │  └─modules
│  │  └─view           # app pages
│  │     └─auth
│  └─static            # static folder
├─mock                 # mock server
│  ├─ajax              # ajax mock configs
│  ├─socket            # socket.io mock configs
└─server               # backend server folder
    ├─api              # backend api list
    │  ├─thing
    │  └─user
    ├─auth             # user auth logical
    │  └─local
    ├─components       # server components
    │  └─errors
    ├─config           # server configs, contains express socket.io, etc.
    └─views            # server served pages
```

## Configuration
Most of the configuration is concentrated in the `config.js` file and most of them have explicit comments. You need to take a look at it first.

Here are some important/frequently-used configurations:
- `frontend.port` port that frontend server listens at
- `backend.port` port that backend server listen at
- `backend.secrets.session` secret for session, important when you deploy your app, make sure it's complex enough
- `backend.mongo.uri` change this if your mongodb uri is not matched
- `backend.serverFrontend` whether to server the frontend code. If set to `true` the express server serves the frontend code. Otherwise you may need a http server like nginx to serve frontend code and there is a nginx configuration at `nginx.example.conf` (default true)

## Environment variables
When you deploy your app to you cloud server it's easy to configure youre app with `environment variables`. Following are supported:  
- `APP_port` or `PORT`: set to `backend.port`
- `APP_HOST` or `APP_IP` or `HOST` or `IP`: set to `backend.ip`
- `MONGODB_URI` or `MONGOHQ_URI`: set to `backend.mongo.uri`
- `SECRET`: set to `backend.secrets.session`

## Notice
The generated app is just a template to build your app system fast. Maybe it can't meet your needs, so you need to do some changes at this issue.

## License
Under [MIT license](./LICENSE)

## At the end
I am very glad to receive your suggestions and pull request.
