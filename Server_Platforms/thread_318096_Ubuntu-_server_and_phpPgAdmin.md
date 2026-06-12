---
title: "Ubuntu- server and phpPgAdmin"
date: 2006-12-13
forum: Server Platforms
---

### Post by carl on 2006-12-13
I have now installed  phpPgAdmin  on a ubuntu-server6.10, but I am having some problems getting the phpPgAdmin to function.

I have set up an average user for postgreSQL

postgres@freja:~$ **createuser -P sqladmin**


And here after create a database for sqladmin

postgres@tux:~$ **createdb -O sqladmin -W biavls_data**


When I try to login using **postgres**
[http://freja.server.dk/phppgadmin/](http://freja.server.dk/phppgadmin/)

I can´t seem to login using 
**(Login disallowed for security reasons.) **
It is as it should be


But when I try using **sqladmin** with the pasword I createt
Nothing happens and after 2 min I get the following message
**Login failed**

My /etc/postgresql/8.1/main/pg_hba.conf looks like this

# Database administrative login by UNIX sockets
local   all         postgres                          ident sameuser

# TYPE  DATABASE    USER        CIDR-ADDRESS          METHOD

# "local" is for Unix domain socket connections only
local   all         all                               md5

# IPv4 local connections:
host    all         all         127.0.0.1/32          md5

# IPv6 local connections:
host    all         all         ::1/128               md5

# Allow any user from any host with IP address 10.0.0.2 - 10.0.0.3 to connect
# to database "biavls_data" as the same user name that ident reports for
# the connection (typically the Unix user name).
# 
# TYPE  DATABASE         USER        CIDR-ADDRESS         METHOD
host    biavls_data      sqladmin    10.0.0.2/3            md5

Why can´t I login as **sqladmin**

I have restarted PostgreSQL

**/etc/init.d/postgresql-8.1 restart**

I use 
Apache2 2.0.55
php 5.1.6
PostgreSQL 8.1.4-7
phpPgAdmin 4.0.1-2


Carl

---

### Post by fozzyuw on 2008-06-10
I'm having the same issue with 8.04.

I've installed PostgreSQL fine, I can access it via the CLI (though, creating/dropping databases outside of the psql CLI threw me off for a bit).

I also disabled the "extra security" config in phpPgAdmin that prevents you from logging in as postgresql.

I believe the problem comes from phpPgAdmin not having Ubuntu permissions (this would be Apache) to access PostgreSQL.  However, I cannot seem to find the answer for this.

I did not use "sudo apt-get install phppgadmin", I simply copied the phppgadmin files into a web folder of my choice.  I can access the web folder, but I get "login failed" when trying to login via postgresql (with extra security disabled).

Any ideas?

Cheers,
Fozzy

---

