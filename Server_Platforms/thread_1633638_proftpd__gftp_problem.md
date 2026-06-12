---
title: "proftpd / gftp problem?"
date: 2010-11-29
forum: Server Platforms
---

### Post by killboymota on 2010-11-29
hhey,

im trying to connect to my server via gftp but as soon as tries to connect it gets disconnected.

Trying xxx.xx.xxx.xx:21
Connected to xxx.xx.xxx.xx:21
Disconnecting from site xxx.xx.xxx.xx:21
Waiting 30 seconds until trying to connect again

With Filezilla the problem ends like this:

Status:	Connection established, waiting for welcome message...
Error:	Connection closed by server
Error:	Could not connect to server

i configured proftpd [using this thread]("http://ubuntuforums.org/showthread.php?t=79588"). of course i made all the changes to fit my server needs.

The most strange thing is that it worked 3 days ago!

Then i tried using the *console*:

**421 Service not available, remote server has closed connection**

Then i ran *nmap*:

Host is up (0.26s latency).
Not shown: 993 closed ports
PORT     STATE SERVICE
**21/tcp   open  ftp**
22/tcp   open  ssh
80/tcp   open  http
443/tcp  open  https
554/tcp  open  rtsp
1755/tcp open  wms
3306/tcp open  mysql


What i'm doing wrong?

---

