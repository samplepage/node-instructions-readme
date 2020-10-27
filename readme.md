# Node Instructions

## commands

- npm install
- npm init: essentially makes a node server; use npm init like git init to intiate a node folder
- npm install express
- npm i express
- touch .gitignore is a way to prevent accumulating packages
  echo "node_modules" >> .gitignore
- put node_modules and .env in the .gitignore file
- ls -a is way to check for hidden files, specifically the .gitignore file
- create your entry point file: touch index.js
- To import a module, use the word require

## setting up express file

npm init after mkdir
touch index.js to make the entry point file
install express by running npm i express
open in text editor
touch .gitignore
add node_modules to it by doing echo "node_modules" >> .gitignore
touch .enc and iclude environment variables
import express, which means doing "const express = require('express');" Below, create an instance of express app by "const app = express();"
create a home rout: app.get('/', (req, res)=>{
res.send('Hello, World');
});
set up to listen to port: app.listen(8000);
the index.js in its entirety should look like:
"//import the express module
const express = require('express');
//create an instance of an express app
const app = express();

//home route
app.get('/', (req, res)=>{
res.send('hello, world')
/_res.sendFile()//send a static html file
res.render()//send html templates
res.json()//what is used when we create APIs_/
})

app.listen(8000, ()=>{
console.log('you are listening to port 8000');
})"

then control c
then enter node index.js into the console and you'll see the message

## ejs

Each line when using js in template use <% %>; anything that is html you don’t have to wrap in the alligator tags; use <%= %> when you want to print to the page

npm i ejs

Layouts are like partials, except we inject main content into boilerplate with headers, footers, etc

npm i express-ejs-layouts will install

npm install axios
then require axios at top of index.js 'const axios = require('axios')

npm i dotenv
refer to files for middleware setup

## Sequelize

npm i pg sequelize
sequelize init must be run to initialize a sequelize project
go into config.json and remove top two lines from each three section (development, test, production), then change the "database name" to name of the app; for example, insert "userapp" so that it's userapp_development; and do for each three sections (userapp_development, userapp_test, userapp_production) with "userapp" combined with the name of the section
change dialect to "postgres"
"sequelize db:create userapp" to create the database
run \psql to make sure the database is there
"sequelize model:create --name user --attributes firstName:string",lastName:string,age:integer,email:string
open models and you'll see user.js
sequelize db:migrate will migrate into node app
run \c userapp_development and then \dt to double check the table is there
can now use what you set up in index.js
need to require your models in index.js by adding "const db = require('./models')" at the top
refer to "userapp" for CRUD actions in index.js
.create is same thing as "INSERT"
