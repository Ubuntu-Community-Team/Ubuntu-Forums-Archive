---
title: "eBox 404 not found"
date: 2010-05-13
forum: Server Platforms
---

### Post by AresArtemis1 on 2010-05-13
hi, professionals, I just installed eBox on the Ubuntu server 10.version, server reports is successfully finished installation, but I received warning message 
**Not Found**

 The requested URL /ebox was not found on this server.
  Apache/2.2.14 (Ubuntu) Server at 192.168.1.100 Port 80

when I tried to open ebox web based panel in firefox on my laptop.


my Apache web server is running well, see,

**It works!**

 This is the default web page for this server.
 The web server software is running but no content has been added, yet.


please help!!

many thanks:guitar::guitar::guitar::guitar:

---

### Post by Iowan on 2010-05-13
A quick trip to the **ebox** [website]("http://trac.ebox-platform.com/wiki/Document/Documentation/InstallationGuide") suggested > Once the installation process is done, you can access the web interface using a web browser (usually from another machine in the same network):

https://<ebox-ip-address>/


---

### Post by CharlesA on 2010-05-13
Try [https://ipaddressgoeshere:8080](https://ipaddressgoeshere:8080)

Either that, or stop apache and see if you can connect.

---

