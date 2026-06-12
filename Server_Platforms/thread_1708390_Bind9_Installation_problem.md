---
title: "Bind9 Installation problem"
date: 2011-03-16
forum: Server Platforms
---

### Post by sarmad54 on 2011-03-16
I am very new to UBUNTU server 10.10. I am currently using an Ubuntu 10.10 Desktop and I am intending to use it as a server by installing all the needed packages like bind9 and dnsutils. I am doing this for getting a new experience. First I installed bind9 and dnsutils and when I got a mix-up I removed these two by using the remove command from the Terminal. I also removed the content of bind directory. When I came to reinstall those two packages, it did not install and I was given the following error. I would be so grateful if you would be able to help me.

Setting up bind9 (1:9.7.1.dfsg.P2-2ubuntu0.2) ...
 * Starting domain name service... bind9                                 [fail] 
invoke-rc.d: initscript bind9, action "start" failed.
dpkg: error processing bind9 (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 bind9
E: Sub-process /usr/bin/dpkg returned an error code (1):confused:

---

### Post by cariboo on 2011-03-16
The thread you tagged onto the end of was 3 years old, and could contain outdated information. I started a new thread for you.

---

### Post by nosebreaker on 2011-03-16
Well I would just install the server version to be honest, rather than adding all the packages manually.  You'll probably encounter little problems here or there later that could be easily solved now by just installing the server version.

That error is just saying the service won't start, you can 'sudo apt-get remove named' and then 'sudo apt-get autoclean' and then see if it left any files behind in the bind/named directory.  If it did try removing them then installing bind again.

---

