---
title: "Do you use default Ubuntu Apache2 installation?"
date: 2006-02-13
forum: Server Platforms
---

### Post by mikeh883 on 2006-02-13
Hello, another linux newbie here....

I am swtiching from Fedora Core 4, where I had installed Apache web server, and Tomcat, for a pretty simple web site. It took a while to get everything connected and up and running but it works. I have a second server that I am installing Ubuntu on, and would like to eventually convert my FC4 server over.

So far I really like Ubuntu, but have noticed some differences between it's included Apache web server installation, and the one I downloaded and compiled  from Apache. After a while I uninstalled Ubuntu's Apache and downloaded and installed from the Apache site again. I ran into some problems with make, and make-install because my user didn't have permissions to create directories owned by root. Now I have startup problems because my user can not bind to the correct ports, unless I su into root. Anyway... I finally got it installed, but am starting to wonder if I should have kept with Ubuntu's installation, for capability, and future ease of upgrade.

If anyone has any opinions on advantages of creating a server by using Ubuntu to install the software (java, Apache, Tomcat, ANT...) or by manually doing it yourself, I would love to hear them.

---

### Post by Glut on 2006-02-14
It's all about package management. One of the great advantages is that maintanence is easy - A patch will be released and apt can install it automatically. It greatly reduces the amount of watching that you have to do for each package on each system. 
Also, you don't have the fun of compiling errors.

---

