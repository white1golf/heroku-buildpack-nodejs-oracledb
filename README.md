# heroku-buildpack-nodejs-oracledb

Automatically download and configure [oracle/node-oracledb](https://github.com/oracle/node-oracledb) and it's dependencies at Heroku build time.

## oracledb

Remove the dependency on `oracledb` from your `package.json`. [heroku-buildpack-nodejs-oracledb](https://github.com/MichaelBuhler/heroku-buildpack-nodejs-oracledb) will install it after th Oracle Instant Client libraries and environment variables have been set.

## heroku-buildpack-apt

The Oracle Instant Client libraries depend on other libraries which are not loaded into the Heroku slug by default. We will use Heroku's [heroku-buildpack-apt](https://github.com/heroku/heroku-buildpack-apt) to download these Debian packages when the slug is built.

Add heroku-buildpack-apt buildpack to your app:

    $ heroku buildpacks:add https://github.com/heroku/heroku-buildpack-apt.git -a APP_NAME

Add `Aptfile` to the root of your source code with these contents:

    libaio1
    libaio-dev

## heroku-buildpack-nodejs-oracledb

Add heroku-buildpack-nodejs-oracledb buildpack to your app:

    $ heroku buildpacks:add https://github.com/MichaelBuhler/heroku-buildpack-nodejs-oracledb.git -a APP_NAME