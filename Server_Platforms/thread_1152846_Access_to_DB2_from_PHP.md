---
title: "Access to DB2 from PHP"
date: 2009-05-08
forum: Server Platforms
---

### Post by AlbertoT on 2009-05-08
I've an Ubuntu server 8.04, Apache and PHP.
I need to access a remote DB2 database since PHP.
I'm trying to configure unixodbc but when I make a test with isql:

:~$ isql -v as400ODBC
[IM002][unixODBC][Driver Manager]Data source name not found, and no default driver specified
[ISQL]ERROR: Could not SQLConnect

It's clear that I've made a bad setup of ODBC 

How is the correct procedure of setup?

thanks

---

