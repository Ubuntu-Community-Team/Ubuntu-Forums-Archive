---
title: "OpenLDAP with MySQL for LTSP authentication"
date: 2011-04-26
forum: Server Platforms
---

### Post by PhillSlevin on 2011-04-26
Hi!

For my internship in Ethiopia  I need to set up an LTSP-environment. Because there are a lot of users that need to be authenticated I figured out that the best way to do this is with OpenLDAP. We have an excising MySQL-database which already contains the user information. Therefor I would like to set up the LDAP with SQL-backend. 

I tried the following guide without any result :(:
[http://www.docunext.com/archives/noofs/](http://www.docunext.com/archives/noofs/)

When I test the ODBC file with iodbctest it gives the following message:
> 1: SQLDriverConnect = [iODBC][Driver Manager]MySQL3: cannot open shared
        object file: No such file or directory (0)
            SQLSTATE=00000
2: SQLDriverConnect = [iODBC][Driver Manager]Specified driver could not
            be loaded (0) SQLSTATE=IM003
According to the guide this is because I don't have the necessary drivers for MySQL installed. However, when I check this these drivers are in place.

This is my odbc.ini file:
> ;
;  odbc.ini configuration for Connector/ODBC and Connector/ODBC 3.51 drivers
;

[ODBC Data Sources]
myodbc      = MyODBC 2.50 Driver DSN
myodbc3     = MyODBC 3.51 Driver DSN

[myodbc]
Driver       = MySQL
Description  = MySQL ODBC 2.50 Driver DSN
SERVER       = x.x.x.x
PORT         =
USER         = root
Password     = password
Database     = databasename
OPTION       = 3
SOCKET       =

[myodbc3]
Driver       = /usr/lib/odbc/libmyodbc.so
Setup        = /usr/lib/odbc/libodbcmyS.so
SERVER       = x.x.x.x
PORT         =
USER         = root
Password     = password
Database     = databasename
OPTION       = 3
SOCKET       =

[Default]
Driver       = /usr/local/lib/libmyodbc.so
Setup          = /usr/lib/odbc/libodbcmyS.so
Description  = Connector/ODBC 3.51 Driver DSN
SERVER       = x.x.x.x
PORT         =
USER         = root
Password     = password
Database     = databasename
OPTION       = 3
SOCKET       =
I hope that someone can give me a clue what I can try next. Im trying to find a solution for days now. :)

---

