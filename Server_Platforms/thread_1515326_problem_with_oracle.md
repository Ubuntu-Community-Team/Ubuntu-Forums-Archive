---
title: "problem with oracle"
date: 2010-06-22
forum: Server Platforms
---

### Post by dreamyouth_m90 on 2010-06-22
Hi there
 
I've installed oracle 10g express databse on my ubuntu server 6.06 after I configured the server I wanted to connect from oracle 6i developer installed on windows xp but I couldn't
Assume that the abuntu server and winxp are on the same LAN
can any hero help me .
 
Regards ,Hasan

---

### Post by clrg on 2010-06-22
Is the server running?
Does the server allow remote logins?
Do you have the necessary rights to connect to the database?
Have you tried not using Windows?

Also, 6.06 is not supported anymore.

---

### Post by koenn on 2010-06-22
You need to read the Oracle documentation.
IIRC, this dbms is  only accessible locally (ie not over a network) initially. You have to change that + create user accounts before you can use it remotely. 

What OS it runs on is irrelevant.

---

### Post by dapperdanny77 on 2010-06-22
you need the oracle listener running, which usually listens on port 1521 - so if lsof -i :1521 shows you the listener process this requirement is met. 

however - reading the oracle doc is highly recommended - usually it's not plug and play

---

### Post by dreamyouth_m90 on 2010-06-24
thanks for your replies
I ran the command lsof -i :1521 
it produces the following
COMMAND  PID   USER   FD   TYPE DEVICE SIZE NODE NAME
tnslsnr 3863 oracle   10u  IPv4   8789       TCP 192.168.10.1:1521 (LISTEN)
 
and the oracle service is running I tied to copy and paste the information of the connection from file
tnsnames.ora on ubuntu to the same named file on windows but still have the problem

---

### Post by koenn on 2010-06-24
as I said befere, iirc, Oracle Express by default has disabled remote SQL connections. Unless you've enabled them, you're not going to get very far. 

see here:
[http://www.debianhelp.co.uk/oracle.htm](http://www.debianhelp.co.uk/oracle.htm)
[http://users.telenet.be/mydotcom/library/databases/oracleprimer.htm](http://users.telenet.be/mydotcom/library/databases/oracleprimer.htm)
[http://www.oracle.com/technology/software/products/database/xe/files/install.102/b25144/toc.htm#BABIJBHJ](http://www.oracle.com/technology/software/products/database/xe/files/install.102/b25144/toc.htm#BABIJBHJ)
[http://www.oracle.com/pls/db10g/portal.portal_demo3?selected=1](http://www.oracle.com/pls/db10g/portal.portal_demo3?selected=1)

---

