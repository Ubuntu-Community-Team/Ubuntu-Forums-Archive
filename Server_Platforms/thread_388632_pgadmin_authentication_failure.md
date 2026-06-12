---
title: "pgadmin authentication failure"
date: 2007-03-19
forum: Server Platforms
---

### Post by cesera on 2007-03-19
I have just installed postgresql 8.2 on Edgy (64-bit), but I cannot work out how to use pgadmin. When I start it up and fill in the following:
 
Address: 127.0.0.1
Desciption: localhost
Service: [empty]
Port: 5432
Maintaince DB: postgres
User Name: postgres
 
I always get an authentication failure for user postgres, I have tried every password I can think of. Anyone any idea what the default password is?

---

### Post by franzag on 2007-07-01
ok, some late, but.. for anyone in the same problem.
this are the steps to set up a database and a user for that db, never use postgres as the main user for everyday work or for a public site!!!
1: go to a terminal and gain acces like postgres user:
```
[FONT="Courier New"]:~$ **sudo su postgres -**[/FONT]
```
2: now going to enter postgres client, there are linux commands to create databases and users, but I preffer to do all in the pgsql client, cuz when you go to other OS don' t get lost! :p
```
[FONT="Courier New"]:~$ **psql**
Bienvenido a psql 8.2.4, la terminal interactiva de PostgreSQL.

Digite:  \copyright para ver los términos de distribución
       \h para ayuda de comandos SQL
       \? para ayuda de comandos psql
       \g o or termine con punto y coma para ejecutar una consulta
       \q para salir

postgres=#[/FONT]
```
3: Change/set the postgres user password:
[FONT="Courier New"]**```
# ALTER USER postgres WITH ENCRYPTED PASSWORD 'yourhardtoguesspassword';
```**[/FONT]
don' t  forget the semicolon at the end of every sentence in the psql client.
4: Create the new database:
[FONT="Courier New"]**```
# CREATE DATABASE yourdatabase;
```**[/FONT]
5: Create the new user for the database:
[FONT="Courier New"]**```
#CREATE USER youruser WITH ENCRYPTED PASSWORD 'youruserpassword';
```**[/FONT]
6: Grant All privilegies to youruser in yourdatabase:
[FONT="Courier New"]**```
# GRANT ALL PRIVILEGES ON DATABASE yourdatabase TO youruser;
```**[/FONT]

from now on user youruser to manage yourdatabase, ans postgres user only to admin all the databases with pgadmin or other software or the psql client.

use the same process for every database, if need more refined user/roles/grant setup, check the [PostgreSQL doc]("http://www.postgresql.org/docs/8.2/interactive/user-manag.html").
:popcorn:

---

