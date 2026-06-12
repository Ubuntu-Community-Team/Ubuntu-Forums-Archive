---
title: "Accessing FireBird Database on Oneiric from Windows"
date: 2011-10-15
forum: Server Platforms
---

### Post by tribalboy on 2011-10-15
Hi Guys,

  I have recently upgraded to Oneiric and have installed Firebird 2.5 SuperClassic on it. I have also got the FlameRobin GUI tool and added a database to it successfully. Now I want to access this database from  a 64 bit windows 7 running on VirtualBox on the same machine.

I am running win7 under bridged mode and can see shared folders on ubuntu when I login with the username/password combination. The firebird database is in one of the shared folders and I can see the file but when trying to connect to the database I get a file I/O error when trying to connect & open the database. 

I have also made sure that the logged in user has Read/Write access to the file but dunno what seems to be causing this.., any pointers or ideas would be appreciated

Many thanks

---

### Post by tribalboy on 2011-10-15
Managed to get it working finally. Seems that I was not passing in the right path.

servername:/var/lib/firebird/2.5/data/databasename.fdb

Also had to pass in the user id (sysdba) and password (masterkey)

---

