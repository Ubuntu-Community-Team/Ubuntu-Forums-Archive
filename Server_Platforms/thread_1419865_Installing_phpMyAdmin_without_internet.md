---
title: "Installing phpMyAdmin without internet"
date: 2010-03-02
forum: Server Platforms
---

### Post by TheOldStaff on 2010-03-02
I haven't used LINUX in many years and am new to Ubuntu. I brought up a 9.10 server and want to run phpMyAdmin. The machine is not connected to the internet and will only be used on a LAN network. I want to run phpMyAdmin, but I am not sure how to go about getting it installed without net access. Will any Debian package work, or do I need an Ubuntu specific package. Where would I get it? Burn it to CD-R and install from the CD drive?

---

### Post by stlsaint on 2010-03-02
Try going to the php website and downloading the package for linux. Copy to usb and copy over to server to install. I also suggest installing ssh for use with lan network for remote access to server.

---

### Post by webtechquery on 2010-03-02
Hi.

May be you could simply download the phpMyAdmin from the following website, and copy it on USB or CD, and then try installing it on your Ubuntu.

[http://packages.debian.org/lenny/all/phpmyadmin/download](http://packages.debian.org/lenny/all/phpmyadmin/download)

This could be a good way of not using internet on Ubuntu, and installing it from the debian (.deb) file from some other computer.

Thanx.

---

### Post by TheOldStaff on 2010-03-02
Thanks. I'll try a USB thumb tonight. If that doesn't work, I'll burn a CD.

---

### Post by TheOldStaff on 2010-03-02
Downloaded. Aptitude is new to me, so I'm not sure; sudo apt -get install phpmyadmin means "get from internet and install"?  Assuming I have the package in the CD drive, would it be sudo apt install phpmyadmin? Does apt work with a .deb, or do I need to sudo apt-get install gdebi?
 
I don't know enough about what I'm trying to do, yet. Read "Installing Software" on this site. Page 9 talks about using synaptic, but it seems to require a second LINUX machine that IS on-line...there's mention of a manual way...go to URLs in generated script...but how will synaptic know about phpmyadmin if ist's not on the machine? Does it have some sort of generic list? I will explore, tonight. 
 
Sorry for all the complete newbie questions. Things like this seem insurmountable at first, but I gotta start somewhere and try my best to understand...

---

