---
title: "Server Setup Issue"
date: 2008-03-31
forum: Server Platforms
---

### Post by haryoh on 2008-03-31
Hi,

I want to setup a server at home to support some of my projects and have access to it publicly. I followed the tutorial on the ubuntu site, [https://help.ubuntu.com/community/BIND9ServerHowto](https://help.ubuntu.com/community/BIND9ServerHowto) but I didn't get where it says nameserver settings. I don't know if I should set up a new nameserver for my domain on my home server and add it to my godaddy domain nameserver. And when I dig it, it didn't resolve to the domain name or the host name, instead it resolved 127.0.0.1

Is there any way i can get a straight forward tutorial that says everything in details.

I use a Compaq AMD 32bit with only 2 133MB memory sticks which is running perfectly.

Please, help.

---

### Post by FakeOutdoorsman on 2008-03-31
I'm assuming you want a web server, not a name server, so you can forget BIND9:
[Installing Apache, mySQL, and PHP on Ubuntu]("https://wiki.ubuntu.com/ApacheMySQLPHP") [Ubuntu Wiki]

---

### Post by haryoh on 2008-03-31
yes.. sorry, just got back from lunch.,.. I'll read through it and let you know the progress.. thanks

---

### Post by haryoh on 2008-03-31
What I'm trying to do is create a server that can do both web and ftp. thanks.

---

### Post by egonzalez on 2008-03-31
Fella,

You can use the LAMP installation included in the Ubuntu Server CD for the Web Server and  then install the ProFTPD for the FTP server.

Cool guides you can find here:
[http://www.ubuntugeek.com/settingup-an-ftp-server-on-ubuntu-with-proftpd.html](http://www.ubuntugeek.com/settingup-an-ftp-server-on-ubuntu-with-proftpd.html)

[http://ubuntuforums.org/showthread.php?t=51611](http://ubuntuforums.org/showthread.php?t=51611)

---

### Post by haryoh on 2008-03-31
one more question: so by the time I finish the LAMP installation, I will be able to access my server from any where and my ftp?

---

