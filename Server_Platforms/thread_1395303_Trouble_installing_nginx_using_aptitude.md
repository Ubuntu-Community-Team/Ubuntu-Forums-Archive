---
title: "Trouble installing nginx using aptitude"
date: 2010-01-31
forum: Server Platforms
---

### Post by jabamodern on 2010-01-31
Hello

I purchased a slice of vps thinking I will finally get around to learn Ubuntu. However, immediately, I got stuck trying to install nginx.

When I type in command
sudo aptitude install nginx

I get 
"No candidate version found for nginx"

My slice is on prgmr and it's Ubuntu 9.1

Thank you so much for your help

---

### Post by BkkBonanza on 2010-02-01
I run Nginx on Ubuntu but I installed from source. I don't know why you aren't getting it with aptitude but you may want to try apt-get instead. That worked when I tried it. There is also an Ubuntu PPA described on the Nginx install page that probably gets you more up to date versions.

[http://wiki.nginx.org/NginxInstall](http://wiki.nginx.org/NginxInstall)

I've generally used source because it always seems like I want some custom modules and the repo version is usually several versions behind. It really isn't hard to compile from source. 

PS. I think you mean version 9.10 of Ubuntu - there is no 9.1, and 1 != 10.

---

