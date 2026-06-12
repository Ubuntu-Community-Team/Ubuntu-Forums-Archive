---
title: "Stability nginx during apt-get upgrade"
date: 2016-01-12
forum: Server Platforms
---

### Post by Jan_W on 2016-01-12
Today I've a couple of websites in a shared hosting. I got myself a VPS (xen) 1GB ram, 1 core and 25GB SSD. 

I've plans to move those pages over here as soon as it is completely configured as a clean webserver.


Have relatively good experience with various distros 10 years back in time, yet I'm unable to decide which distro and layout I want. The main priority is stability and durability of future updates.


Right now I've got 2 options.


**1. Centos 7 with apache server (php, MariaDB).**


and..


**2. Ubuntu 4.14 with nginx (php-fpm, MariaDB)**


**Centos 7** image on the vps is probably screwed concerning permissions to nginx and php-fpm. Whatever I do and googling it refuses this setup to work. Therefore apache is apparently my only choice in Centos for now. 


**Ubuntu** is more easy to deal with. Here, everything seems fine. The only thing I think about is whether updates will destroy nginx and php-fpm (someone who has experience?) It still got 3 years of updates left.


The goal of this thread is a little input on what YOU would have chosen and why.


Thanks for any response.

---

### Post by QIII on 2016-01-12
I update both my web server and my development server frequently without issue.

They are both LEMP servers running Ubuntu Server 14.04.

Ubuntu Server because it's familiar and NGINX because it's light and robust.

---

