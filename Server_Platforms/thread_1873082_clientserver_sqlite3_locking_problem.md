---
title: "client/server sqlite3 locking problem"
date: 2011-10-31
forum: Server Platforms
---

### Post by jmsgz on 2011-10-31
Hi folks
 thanks in advance

 have a simple db in sqlite3 on an ubuntu server running nfs, ssh etc
 and on an unbuntu client running same 

 after sucessfully mounting the desired directory from the server on
 the client, i attempt to access the db data with sqlitebrowser on the 
 client. 

 i get a "db locked message" and cannot open files and access the data. 
 have reviewed man exports,chmods and chown, i suspect
 there might be a sqlite3 command line directive to unlock the 
 db on the server via ssh prior to remotely mounting?
 -or- could this be an exports file config fix?

 can one of you point me in the right direction
 or give example of possible commands

---

