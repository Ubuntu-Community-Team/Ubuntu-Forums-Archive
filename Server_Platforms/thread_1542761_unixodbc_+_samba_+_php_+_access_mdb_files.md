---
title: "unixodbc + samba + php + access mdb files"
date: 2010-07-31
forum: Server Platforms
---

### Post by inittab on 2010-07-31
Hello, I'm attempting to access an access database via php with a unixodbc connection.

if I copy the mdb database over to the local filesystem I have no issues and can query the database fine. But if I try to access it over my samba mounted directory I get the following error:

Can't alloc filename
Unable to locate database /mnt/netops/20101.mdb


/mnt/netops was mounted with the following command:
mount -t cifs -o username=XXXXXXXXX,password=XXXXXXXX //10.2.1.XX/NetOps /mnt/netops

I can read files off of the share fine, and can copy the database off but it seems unixodbc cannot access the file.

root@laptop:~# file /mnt/netops/20101.mdb
/mnt/netops/20101.mdb: Microsoft Access Database


/etc/odbc.ini:
[NetOps]
Description = Netops Database
Driver = MDBToolsODBC
Database = /mnt/netops/20101.mdb
Servername = localhost
UserName =
Password =
port = 5432

I am using the mdbtools driver:
[MDBToolsODBC]
Description		= MDB Tools ODBC drivers
Driver		= /usr/lib/libmdbodbc.so.0
Driver64		= 
Setup		= 
Setup64		= 
UsageCount		= 1
CPTimeout		= 
CPReuse		= 




Any help is appreciated.

---

