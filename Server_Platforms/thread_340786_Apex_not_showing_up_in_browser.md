---
title: "Apex not showing up in browser"
date: 2007-01-17
forum: Server Platforms
---

### Post by LinXway on 2007-01-17
I installed oracle-xe via apt-get...ran the config...install finished all is fine.

problem is I cant access ://myserver:8080/apex

acording to install it should work but its not...the oracle is working and I can access via sqlplus on the cmd line...so if any one knows why I cant access it on my local server please let me know...

---

### Post by LinXway on 2007-01-17
Ok I solved this delima...

You can also use SQL*Plus command line to enable access from remote clients. To use
SQL*Plus command line to change this setting, log into SQL*Plus as system, and run the
following command:

EXEC DBMS_XDB.SETLISTENERLOCALACCESS(FALSE);

after doing this I was able to log into myserver:8080/apex/

So if like me you have 2 or more pc's networked and 1 of them is a server ( mine is a lamp) and you want to access apex from another pc...use the above from the command line on the server.

---

