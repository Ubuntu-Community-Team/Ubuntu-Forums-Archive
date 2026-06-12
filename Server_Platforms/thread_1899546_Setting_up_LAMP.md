---
title: "Setting up LAMP"
date: 2011-12-23
forum: Server Platforms
---

### Post by 0Virus on 2011-12-23
I have just spent the last hour or so reading many different articles on how to setup a LAMP enviroment. I want to setup a server for 1 forum based website. Previously I have been using Webmin on CentOS but this installs a lot of stuff I don't want and is taking up server resources which I need. I figure if I can setup the Apache, PHP and MySQL myself then I will save a lot of CPU and RAM usage, while making the server a little more secure.
 
Every article I have read give different commands. If my memory serves me correctly wasn't there three different ways to installing PHP??? Something like Standalone, Apache Mod, or something else?? Well eitherway I am totally lost now.
 
Can't I just use these commands.... ?
apt-get install apache2
apt-get install php5
apt-get install mysql-server
 
If I have missed anything, please let me know...
 
 
Security...
The server sits behind a hardware firewall which blocks all incoming connections except on port 80 and 22, however access to port 22 is IP specific. I also intend to run apt-get update once a week to keep the system up-to-date. Root access will be disabled.
 
Backup...
Because this is a forum based website most of the data will be held in MySQL which I will be backing up manually once a week. In addition to this a system snapshot will be automatically taken weekly.

---

### Post by collisionystm on 2011-12-23
I dont see why not. If you still need addition programs just install them.

---

### Post by Dangertux on 2011-12-23
Quick tip

```

sudo apt-get install lamp-server^

```

*the ^ should be there.

Also everything else looks fine :-)

Hope this helps.

---

### Post by 0Virus on 2011-12-25
I have installed Ubuntu 10.04 Minimal, which uses about 11 MB after updating with apt-get. However after installed apache2, the memory usage jumps to 555 MB. Apache 2.2 on Fedora uses 26 MB in total. What is wrong that is it using so much memory ?

---

### Post by johnno40 on 2011-12-26
Not answering your question, but in my early days I used: 
[http://www.apachefriends.org/en/index.html](http://www.apachefriends.org/en/index.html)

Perhaps it helps.

John.

---

