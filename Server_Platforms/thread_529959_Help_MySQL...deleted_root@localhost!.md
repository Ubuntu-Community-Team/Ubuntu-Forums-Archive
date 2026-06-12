---
title: "Help MySQL...deleted root@localhost!"
date: 2007-08-19
forum: Server Platforms
---

### Post by HiVoltRock on 2007-08-19
I'm new to Ubuntu (user about a month and a half), along with mySQL. I installed mySQL alng with myphpadmin to get my MythTV setup working with a Hauppauge PVR 150, and I logged into myphpadmin under root with no password, and when I want to change the password I accidentally deleted user 'root'@'localhost'

I have no idea how to fix this, and I've been searching the web for hours on end...can somebody help me?

---

### Post by HiVoltRock on 2007-08-19
Update:

I tried 'apt-get remove --purge' for mysql-server and phpmyadmin, and still get error 1045

---

### Post by southernman on 2007-08-19
Before you can uninstall it, you'll need to stop it I think.

sudo /etc/init.d/mysqld stop
or
sudo /etc/init.d/mysql stop

[http://www.google.com/search?q=error+1045&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a]("http://www.google.com/search?q=error+1045&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a")

---

### Post by HiVoltRock on 2007-08-20
I just tried both of those commands and it's telling me "No such file or directory"

---

