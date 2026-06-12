---
title: "Ubuntu - Wine - ADO.NET"
date: 2010-10-19
forum: Wine
---

### Post by mayankgarg on 2010-10-19
Hello All,
In wine i am trying to do the following:
1. Install winetricks
2. sh winetricks fontfix
3. sh winetricks mdac28
4. sh winetricks jet40 (nothing to do with my app)
5. Install PostgreSQL 8.4 for Linux from enterprisedb.com
6. Install psqlodbc.msi into wine
7. sh winetricks dotnet20
I am using the latest ubuntu and wine versions. 
Now i have a simple dotnet 2.0 application which uses ado.net
I am trying to just pass the connection parameters using ado.net to connect
to any database in Postgres 8.4 (like server, port, database, username and password). I am using the PostgreSQL ANSI driver. 
When i connect through my application, i get the following message
 
ERROR [IM002][unixODBC][Driver Manager]Data source name not found, and no default driver specified.
 
I checked the ODBC drivers by running the ODBC utility odbcad32.exe in the system32 folder, by creating a DSN using the PostgreSQL ANSI driver and its working. 
The drivers have seemed to be installed properly else this would not have worked. 
I even tried using the PostgreSQL Unicode driver in my app but still does not connect. 
I dont understand why the error message has unixODBC. 
I have tested a VB6 application with the general way of connecting through a ADODB connection object with the same driver and connection parameters. This works but not the ado.net app. Dot net 2 is also installed properly else the application would not have opened.
 
If someone could please help me out on this. Would be great
 
Mayank :KS

---

