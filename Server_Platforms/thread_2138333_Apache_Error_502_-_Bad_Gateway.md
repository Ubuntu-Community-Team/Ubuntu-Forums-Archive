---
title: "Apache Error 502 - Bad Gateway"
date: 2013-04-23
forum: Server Platforms
---

### Post by danooch13 on 2013-04-23
Hello,
 
Hopefully someone can help me with this.
 
My webserver has been offline for about 6 months since some construction in my house. 

I turned it back on the other day - all seemed fine - the website it was hosting was fine.
 
I did some updates (apt-get update and upgrade) - all still seemed fine.
 
The next day the website stopped working. 

Now what I am getting is sometimes the site loads sometimes it doesnt. On an iphone I get an error 502 bad gateway, on a computer I get the page cannot be displayed.
 
Any ideas what this could be?

---

### Post by beboylips on 2013-04-23
Could you post your *ifconfig *output, your *httpd.conf* (or apache2.conf), and your /etc/apache2/sites-enabled/* configs.

---

### Post by danooch13 on 2013-04-23
Thank you.

See attached for text files.

What do you think it is?  It is such a generic message.

---

### Post by danooch13 on 2013-04-23
Also - another point I didnt mention 

It works internally on the network.

---

### Post by danooch13 on 2013-04-23
I think its a hardware issue - although very much a coincidence.  I am noticing the server dropping my ssh connection and pings sometimes just do nothing or miss sequences


PING 10.50.1.1 (10.50.1.1) 56(84) bytes of data.
64 bytes from 10.50.1.1: icmp_seq=35 ttl=64 time=0.335 ms
64 bytes from 10.50.1.1: icmp_seq=36 ttl=64 time=0.361 ms
64 bytes from 10.50.1.1: icmp_seq=37 ttl=64 time=0.348 ms
64 bytes from 10.50.1.1: icmp_seq=38 ttl=64 time=0.353 ms
64 bytes from 10.50.1.1: icmp_seq=39 ttl=64 time=0.364 ms
64 bytes from 10.50.1.1: icmp_seq=40 ttl=64 time=0.326 ms
64 bytes from 10.50.1.1: icmp_seq=41 ttl=64 time=0.365 ms
64 bytes from 10.50.1.1: icmp_seq=42 ttl=64 time=0.368 ms
64 bytes from 10.50.1.1: icmp_seq=43 ttl=64 time=0.365 ms
64 bytes from 10.50.1.1: icmp_seq=44 ttl=64 time=0.344 ms
64 bytes from 10.50.1.1: icmp_seq=45 ttl=64 time=0.345 ms
64 bytes from 10.50.1.1: icmp_seq=46 ttl=64 time=0.338 ms
64 bytes from 10.50.1.1: icmp_seq=47 ttl=64 time=0.351 ms
64 bytes from 10.50.1.1: icmp_seq=48 ttl=64 time=0.339 ms
64 bytes from 10.50.1.1: icmp_seq=49 ttl=64 time=0.359 ms
64 bytes from 10.50.1.1: icmp_seq=84 ttl=64 time=0.343 ms
64 bytes from 10.50.1.1: icmp_seq=85 ttl=64 time=0.371 ms
64 bytes from 10.50.1.1: icmp_seq=86 ttl=64 time=0.360 ms
64 bytes from 10.50.1.1: icmp_seq=87 ttl=64 time=0.364 ms
64 bytes from 10.50.1.1: icmp_seq=88 ttl=64 time=0.382 ms
64 bytes from 10.50.1.1: icmp_seq=89 ttl=64 time=0.333 ms
64 bytes from 10.50.1.1: icmp_seq=90 ttl=64 time=0.379 ms
64 bytes from 10.50.1.1: icmp_seq=91 ttl=64 time=0.366 ms
^C

---

