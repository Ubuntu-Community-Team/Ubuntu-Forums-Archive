---
title: "mySQL and mySQL Workbench Help"
date: 2011-11-14
forum: Server Platforms
---

### Post by Clonus on 2011-11-14
Hi, everyone, long time Windows User but love Ubuntu, work keeps me in the Windows world.. however I'm not that biased.
 
Recently I have been looking to move into Ubuntu Server + mySQL since it seems to be able to handle so much more than I previously realized... not to mention easy on the wallet!
 
Setting up Ubuntu Server was pretty much click click install (VMWare)
 
Installing mySQL was just as easy.
 
I did use these instructions to install it
[https://help.ubuntu.com/11.04/serverguide/C/mysql.html](https://help.ubuntu.com/11.04/serverguide/C/mysql.html)
 
I also made sure the server was setup for Static IP and assigned that IP in the Binding setting within my.cfg
 
I've done a number of command lines to verify that "YES" mySQL is running but it seems I can't connect via mySQL Workbench via Windows Host machine (VMWare)
 
I eventually want to connect via ADO.net but figured I better attempt some administration first.
 
Can anyone give me some possible reasons why I can't connect to the mySQL Server?

---

### Post by volkswagner on 2011-11-14
You need to setup the user you want to connect with.  You want this user privileged from your workbench location (hostname or ip).

You need to grant the user permissions via MySql interface.

Depending if your user is setup already and how loose you want your permissions will determine how you edit the following:

```
grant all on *.* to username@clientHostNameorIP;

```

The above assumes uername exists and you want to give full permissions on all databases.

---

### Post by rubylaser on 2011-11-15
A few questions:

1. Can you connect locally with the mysql client on the server?
```
mysql -u root -p
```

2. Have you tried to comment out the bind-address line in my.cnf and restart the server to make sure that's not your problem?

3. Can you ping the server from your Windows box and get a reply?

4.  Is the Windows Firewall preventing the connection to the server on the MySQL port 3306?

Just a few ideas off the top of my head.

---

