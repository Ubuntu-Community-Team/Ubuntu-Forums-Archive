---
title: "Cant Get SSL working on Server 8.04"
date: 2008-05-24
forum: Server Platforms
---

### Post by kustomjs on 2008-05-24
Hi Guys
I cant get my ssl to work and I cant even get my https working what do I need to do? here is my server info:

Server Host: XXXXXXconnection (XXX.XXX.X.X) Database Host: localhost (127.0.0.1)
Server OS: Linux 2.6.24-16-server Database: MySQL 5.0.51a-3ubuntu5
Server Date: 05/22/2008 21:21:16 Datebase Date: 05/22/2008 21:21:16
Server Up Time: 21:21:16 up 4:58, 1 user, load average: 0.00, 0.00, 0.00
HTTP Server: Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.1 with Suhosin-Patch mod_ssl/2.2.8 OpenSSL/0.9.8g
PHP Version: 5.2.4-2ubuntu5.1 (Zend: 2.2.0)

---

### Post by kustomjs on 2008-05-24
~~~bump~~~

---

### Post by kustomjs on 2008-05-24
I finally got to work I forgot to add it in my router settings note if your using any linksys wired/wireless router make you go to 
[http://192.168.1.1](http://192.168.1.1) to access your router then go to Applications
& Gaming then to Port Range Forwarding

enter this stuff
	
  Port Range 
Application	Start	End  Protocol IP Address    Enabled 
Server                           80           80         Both   192.168.1.X        Enable
SSL                              443        443         Both   192.168.1.X         Enable
FTP                              21            21         Both   192.168.1.X        Enable

---

