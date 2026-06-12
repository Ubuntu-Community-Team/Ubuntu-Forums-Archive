---
title: "Auditing file access"
date: 2011-06-06
forum: Server Platforms
---

### Post by Elwha on 2011-06-06
Hello all, 
 
Running Ubuntu Server 10.4 
 
I'm in need of some auditing to determine what is happening with some files on our local server. What is generally the best tool to load, and do you have any good links to a tutorial on how to install, setup and run?
 
I'm looking for what users have accessed a file. ... read, open, edit, delete, move, save... etc..

---

### Post by hawk2010 on 2011-06-07
Sure. But to answer this I have a question : 

What are the services used by the users to log into the server ?  For e.g. Samba, FTP , SSH  let us know. Depending on the service you can tweak the configuration files on each on to enable auditing. 

If you want a system level auditing. then i should recommend the built-in auditd , you can set the rules and it will log. But this is resource killing in terms of disk space.

---

### Post by amauk on 2011-06-07
The kernel spews out lots of info on altered filesystem state via the inotify interface

Install "inotify-tools", and see the manpage for "inotifywatch"
This provides a basic audit log over time of specified files / directories

If you need something more bespoke, the link below details building a client that interfaces with the inotify kernel interface
[http://www.ibm.com/developerworks/linux/library/l-ubuntu-inotify/index.html](http://www.ibm.com/developerworks/linux/library/l-ubuntu-inotify/index.html)

---

### Post by Elwha on 2011-06-07
> **hawk2010 said:**
> Sure. But to answer this I have a question : 
 
What are the services used by the users to log into the server ? For e.g. Samba, FTP , SSH let us know. Depending on the service you can tweak the configuration files on each on to enable auditing. 
 
If you want a system level auditing. then i should recommend the built-in auditd , you can set the rules and it will log. But this is resource killing in terms of disk space.
 
Samba shares.

---

### Post by Elwha on 2011-06-07
I have found the Samba logs, there are logs for each machine that connects but the detail is very low.  Just the connection information. 
 
[2011/04/15 10:54:30,  1] smbd/service.c:1063(make_connection_snum)
  backup-pc (10.0.0.146) connect to service scans initially as user jgarnerstone (uid=1001, gid=1016) (pid 27458)
 
I looked at the log levels 2/3 etc but it doesn't appear to give me the data I'm looking for.  Save, move, delete, etc..

---

