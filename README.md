<a name="languages"></a>
# Labook

<a id="pt-readme"></a>
### Português | [English](#en-readme)
Estrutura de back-end do Projeto **Labook** do bootcamp da escola Labenu.
Trata-se de uma API com funcionalidades básicas de uma rede social.

<a name="pt-menu"></a>
- [Requisitos Básicos](#requisitos)
- [Primeiros Passos](#primeiros-passos)
- [Scripts Disponíveis](#pt-scripts)
- [Funcionalidades](#funcionalidades)
- [Bibliotecas e Frameworks](#bibliotecas)
- [Endpoints](#endpoints)

<a id="requisitos"></a>
## Requisitos Básicos:
* Git
* Node
* Typescript
* MySQL

<a id="primeiros-passos"></a>
## Primeiros Passos:
* Clone esse repositório no diretório de sua escolha com o comando `git clone <url>`.
* Abra o projeto na sua IDE favorita.
* Rode o comando `npm install` **ou** `npm i` para instalar as dependências do projeto.
* Crie um arquivo `.env` na pasta raíz do projeto com as suas informações:
```
# Database
DB_HOST = host do banco de dados
DB_USER = user do banco de dados
DB_PASSWORD = senha
DB_NAME = nome do banco de dados

# JasonWebToken
JWT_KEY = chave para gerar o jason web token
JWT_EXPIRES_IN = tempo de expiração do token

# Bcrypt
BCRYPT_COST = 12
```

<a id="pt-scripts"></a>
## Scripts Disponíveis:
* `npm run my-sql-setup` para criar as tabelas.
* `npm run start` para rodar a aplicação.
* `npm run dev` para iniciar a aplicação em modo de desenvolvimento com hot reload.

<a id="funcionalidades"></a>
## Funcionalidades:
* Cadastro
* Login
* Fazer uma postagem
* Ver feed com todos os posts
* Exibir detalhes de um post específico
* Fazer amizade
* Remover amizade

<a id="bibliotecas"></a>
## Bibliotecas e Frameworks:
* cors
* express
* knex
* mysql
* dotenv
* uuid
* jsonwebtoken
* bcryptjs

---

<a id="en-readme"></a>
### [Português](#pt-readme) | English
Back-end structure of the Labook Project developed at Labenu School bootcamp.
An API with basic features of a social media.

<a name="pt-menu"></a>
- [Minimum Requirements](#requirements)
- [Getting Started](#getting-started)
- [Available Scripts](#scripts)
- [Features](#features)
- [Libs and Frameworks](#libs)
- [Endpoints](#endpoints)

<a id="requirements"></a>
## Minimum Requirements:
* Git
* Node
* Typescript
* MySQL

<a id="getting-started"></a>
## Getting Started:
* Clone this repository in a directory of your choice running `git clone <url>` command.
* Open the project on your favorite IDE.
* Run the `npm install` command **or** `npm i` to install all the dependencies.
* On the root directory of the project, create a `.env` file with your environment variables:
```
# Database
DB_HOST = database host
DB_USER = database user name
DB_PASSWORD = user password
DB_NAME = database name

# JasonWebToken
JWT_KEY = key to generate jason web token
JWT_EXPIRES_IN = token expires at

# Bcrypt
BCRYPT_COST = 12
```

<a id="scripts"></a>
## Available Scripts:
* `npm run my-sql-setup` to create the necessary tables.
* `npm run start` to run the application.
* `npm run dev` to start the application in development mode, with hot reload.

<a id="features"></a>
## Features:
* Cadastro
* Login
* Create a post
* Get feed with all posts
* Display selected post details
* Add friend
* Remove friend

<a id="libs"></a>
## Libs and Frameworks:
* cors
* express
* knex
* mysql
* dotenv
* uuid
* jsonwebtoken
* bcryptjs

<a id="endpoints"></a>
## Endpoints
<a name="endpoints-menu"></a>
- [Signup](#signup)
- [Login](#login)
- [Create Post](#create-post)
- [Get Post By Id](#get-post-by-id)
- [Add Friend](#add-friend)
- [Remove Friend](#remove-friend)
- [Get Posts](#get-posts)

<a id="signup"></a>
### signup
   * Request:
      ```bash
      curl -i -X POST http://localhost:3003/users/signup -H "Content-Type: application/json" -d '{"name":"Alice","email":"alice@gmail.com","password":"pass123"}'
      ```
   * Response (success):
      ```bash
      HTTP/1.1 201 Created
      X-Powered-By: Express
      Access-Control-Allow-Origin: *
      Content-Type: application/json; charset=utf-8
      Content-Length: 220
      ETag: W/"dc-ec7r4rkKsMBe/V0SGyUkO6Vyto0"
      Date: Tue, 17 Nov 2020 14:33:15 GMT
      Connection: keep-alive

      {"message":"Success!", "token":"eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6Ijg5OGJjNDVlLTExZjEtNGEyMy04OTZhLTdmMmUyOWNmZTAxMiIsImlhdCI6MTYwNTYyMzU5NSwiZXhwIjoxNjA1NzA5OTk1fQ.pWxV2vtLnp0hKm0CXXnLpnDu6PEPkZM27A71oTTCYfE"}%   
      ```
<a id="login"></a>
### login
   * Request:
      ```bash
      curl -i -X POST http://localhost:3003/users/login -H "Content-Type: application/json" -d '{"email":"alice@gmail.com","password":"pass123"}'
      ```
   * Response (success):
      ```bash
      HTTP/1.1 200 OK
      X-Powered-By: Express
      Access-Control-Allow-Origin: *
      Content-Type: application/json; charset=utf-8
      Content-Length: 220
      ETag: W/"dc-IBDYVXSmDzdFsqHXhPCAutzNwn8"
      Date: Tue, 17 Nov 2020 14:39:23 GMT
      Connection: keep-alive

      {"message":"Success!","token":"eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6Ijg5OGJjNDVlLTExZjEtNGEyMy04OTZhLTdmMmUyOWNmZTAxMiIsImlhdCI6MTYwNTYyMzk2MywiZXhwIjoxNjA1NzEwMzYzfQ.9JvXRQpazI5k6GAnc1lFcVcTbZ_ElASnwyybU_tRU48"}%   
      ```
<a id="create-post"></a>      
### createPost
   * Request:
      ```bash
      curl -i -X POST http://localhost:3003/posts/create -H "Content-Type: application/json" -H "authorization:$token" -d '{"photo":"https://i.picsum.photos/id/238/200/200.jpg?hmac=O4Jc6lqHVfaKVzLf8bWssNTbWzQoaRUC0TDXod9xDdM","description":"My city is beautiful =D","type":"normal"}'
      ```
   * Response (success):
      ```bash
      HTTP/1.1 201 Created
      X-Powered-By: Express
      Access-Control-Allow-Origin: *
      Content-Type: application/json; charset=utf-8
      Content-Length: 22
      ETag: W/"16-ChcZhlw1slqtGuDwxLsUclql5gE"
      Date: Tue, 17 Nov 2020 14:47:15 GMT
      Connection: keep-alive

      {"message":"Success!"}%    
      ```
<a id="get-post-by-id"></a>      
### getPostById
   * Request:
      ```bash
      curl -i GET http://localhost:3003/posts/$id -H "Content-Type: application/json" -H "authorization:$token" 
      ```
   * Response (success):
      ```bash
      HTTP/1.1 200 OK
      X-Powered-By: Express
      Access-Control-Allow-Origin: *
      Content-Type: application/json; charset=utf-8
      Content-Length: 322
      ETag: W/"142-IYRwCODXZBltXE3MydHuIDB8M3w"
      Date: Tue, 17 Nov 2020 14:52:19 GMT
      Connection: keep-alive

      {"message":"Success!","post":{"id":"e4eb1531-d814-4742-b614-be2a36602548","photo":"https://i.picsum.photos/id/238/200/200.jpg?hmac=O4Jc6lqHVfaKVzLf8bWssNTbWzQoaRUC0TDXod9xDdM","description":"My city is beautiful =D","type":"normal","createdAt":"2020-11-17T17:47:15.000Z","authorId":"898bc45e-11f1-4a23-896a-7f2e29cfe012"}}% 
      ```
<a id="add-friend"></a>      
### addFriend
   * Request:
      ```bash
      curl -i PUT http://localhost:3003/users/friendship/$id -H "Content-Type: application/json" -H "authorization:$token" 
      ```
   * Response (success):
      ```bash
      HTTP/1.1 200 OK
      X-Powered-By: Express
      Access-Control-Allow-Origin: *
      Content-Type: application/json; charset=utf-8
      Content-Length: 38
      ETag: W/"26-FRG92jk/IDv4fDHb8n2wbljn+Xw"
      Date: Fri, 05 Feb 2021 20:07:12 GMT
      Connection: close

      {"message": "Friend added successfuly"} 
      ```    
<a id="remove-friend"></a>      
### removeFriend
   * Request:
      ```bash
      curl -i DELETE http://localhost:3003/users/friendship/$id -H "Content-Type: application/json" -H "authorization:$token" 
      ```
   * Response (success):
      ```bash
      HTTP/1.1 200 OK
      X-Powered-By: Express
      Access-Control-Allow-Origin: *
      Content-Type: application/json; charset=utf-8
      Content-Length: 40
      ETag: W/"28-p/Q+JvLS79xP5hajp1hbgqiqxTM"
      Date: Fri, 05 Feb 2021 20:10:39 GMT
      Connection: close

      {"message": "Friend removed successfuly"} 
      ```      

<a id="get-posts"></a>
### getPosts
   * Request:
      ```bash
      curl -i GET http://localhost:3003/posts/feed -H "Content-Type: application/json" -H "authorization:$token" 
      ```
   * Response (success):
      ```bash
      {"posts":[{"id":"25a2dc30-86f0-42f7-af90-1c323b95d7fc","photo":"Terceiro Post da Amiga da Aline","description":"Descrição do post dela","type":"event","createdAt":"2021-02-05T16:30:34.000Z","authorId":"77a5f772-cb00-4bf9-9d8a-7227cd88cbc8"},{"id":"12ab0792-e0c7-41ad-b810-f3a0d69406a6","photo":"Segundo Post da Amiga da Aline","description":"Descrição do post dela","type":"event","createdAt":"2021-02-05T16:30:21.000Z","authorId":"77a5f772-cb00-4bf9-9d8a-7227cd88cbc8"},{"id":"564f711e-0341-4c1a-a12b-9d5fd1044691","photo":"Post da Amiga da Aline","description":"Descrição do post dela","type":"normal","createdAt":"2021-02-05T16:29:56.000Z","authorId":"77a5f772-cb00-4bf9-9d8a-7227cd88cbc8"}]} 
      ```
