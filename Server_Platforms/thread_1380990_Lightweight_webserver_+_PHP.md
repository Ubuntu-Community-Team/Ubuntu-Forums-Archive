---
title: "Lightweight webserver + PHP"
date: 2010-01-14
forum: Server Platforms
---

### Post by Nerd King on 2010-01-14
Just wondering if anyone could suggest a light webserver with which I can integrate PHP? I'm normally an apache guy but I need to squeeze something into a fairly small amount of memory and so I need to find every possible way of lowering the footprint here! Any suggestions?

---

### Post by i.r.id10t on 2010-01-14
One of the old 1.3 series of Apache?

---

### Post by memilanuk on 2010-01-14
nginx, hiawatha and lighthttpd are supposed to be fairly popular as far as small/lightweight httpd servers...

This [article]("http://en.wikipedia.org/wiki/Comparison_of_lightweight_web_servers") might help as well.

---

### Post by maddog39 on 2010-01-14
Lighttpd is probably easy enough, theres a lot of documentation available for it also. Heres a howtoforge article on setting up lighty on Ubuntu 9.10 with PHP 5 and MySQL.

[http://www.howtoforge.com/installing-lighttpd-with-php5-and-mysql-support-on-ubuntu-9.10](http://www.howtoforge.com/installing-lighttpd-with-php5-and-mysql-support-on-ubuntu-9.10)

---

### Post by Nerd King on 2010-01-14
Excellent thanks guys, I guess my google skills sucked this time. Will read up on the aforementioned and implement accordingly :)

---

### Post by Vegan on 2010-01-14
The standard LAMP stack is not very big, it will fit on any old junk disk > 4GB easily. It will also run fine on a USB stick too.

---

### Post by Nerd King on 2010-01-14
Yeah I know it's small, but I'm trying to do this on a box with very little RAM, apache's a bit hungry, hence looking at alternatives.

---

### Post by maddog39 on 2010-01-14
I got apache2 running on my VPS with 256MB of RAM and Ubuntu 9.04 and it eats memory like theres no tomorrow. In fact I generally have to reboot the server like every week because it crashes due to out of memory error.

---

### Post by Nerd King on 2010-01-14
> **maddog39 said:**
> I got apache2 running on my VPS with 256MB of RAM and Ubuntu 9.04 and it eats memory like theres no tomorrow. In fact I generally have to reboot the server like every week because it crashes due to out of memory error.
I'll be running on even less than that! Try 64MB!

---

### Post by maddog39 on 2010-01-15
Well thats exactly what I am saying, Apache 2 is a memory hog on that, it'll never run on the kind of hardware you're using.

---

### Post by Nerd King on 2010-01-15
> **maddog39 said:**
> Well thats exactly what I am saying, Apache 2 is a memory hog on that, it'll never run on the kind of hardware you're using.
Yeah I know. I did some tests, I did actually get it running on a 64MB box but speed wasn't exactly as I would like, so that's why I'm so grateful for everyone's suggestions.

---

### Post by theRemix on 2010-01-15
> **maddog39 said:**
> I got apache2 running on my VPS with 256MB of RAM and Ubuntu 9.04 and it eats memory like theres no tomorrow. In fact I generally have to reboot the server like every week because it crashes due to out of memory error.

i'm running the same. i tried out lighty, it just wouldn't do for what i need, or i don't know enough about it to replace apache yet. their community is very inactive.

---

### Post by Nerd King on 2010-01-15
Inactive community's a worry, but in this case my needs are probably simpler than yours. All I need it to do is basic web serving for 1 site, and linking up to PHP which presumably I can find a nice tutorial for somewhere on google.

---

### Post by Xipher on 2010-01-15
I've got lighttpd running some stuff myself. It's pretty easy to work with and I've have it setup to run an ubuntu mirror as well as Zabbix. Ubuntu includes the basic config to get php5 working as a fastcgi and that worked after enabling it and a restart of lighty.

---

