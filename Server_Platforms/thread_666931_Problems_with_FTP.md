---
title: "Problems with FTP"
date: 2008-01-13
forum: Server Platforms
---

### Post by Freesprt30 on 2008-01-13
HEy everyone,  

  I am new to Linux an new to servers.  I decided to build my own home server and to start a forum.  We have serveral family members in the service and I thought having a family forum would be great way to stay in contact.

  I go my Gusty server running using this guide [http://www.howtoforge.com/perfect_server_ubuntu7.10](http://www.howtoforge.com/perfect_server_ubuntu7.10)

 With 
# Web Server: Apache 2.2
# Database Server: MySQL 5.0
# Mail Server: Postfix
# DNS Server: BIND9
# FTP Server: proftpd
# ISP config

Everything seems to work and I  upload item to my web using ISPconfig.

  How ever I cann't FTP in any other way.  Not sure what I am doing wrong and I would like to be able to use Cute ftp or Front page.

  I read some post on configuring proftpd but I am confused.  Can I still ftp in with out using ISP config?

  I have more question about forums and mail but one step at a time :)

   IS this the best server config for hosting a forum and family site and music files etc...

---

### Post by freebeer on 2008-01-13
The thing about proftp I've found is that you need to log in in ACTIVE not passive mode.  I've got proftp up and that's what I had to do when I set it up.  I access it through a number of means, but they must be in active mode.  (There's probably a way of getting it to work properly in passive mode, but I've not run across the solution.)

---

