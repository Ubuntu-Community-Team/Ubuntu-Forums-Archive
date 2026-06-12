---
title: "Dynamic DNS"
date: 2010-01-09
forum: Server Platforms
---

### Post by bluedrakonis on 2010-01-09
I am running an ubuntu 9.1 server, can someone recommend or tell me how to get it to host a website using a dynamic dsl connection?

---

### Post by SlugSlug on 2010-01-09
google dyndns, you'd want to reg there and put the settings in your router,

and then look into apache

---

### Post by Anatashinu on 2010-01-09
Do you mean how to host a website? Then you would do: ```
sudo tasksel install lamp
``` (Linux Apache MySQL PHP) and put your website files in /var/www

Or do you mean how to get a domain name for your website? Assuming you don't want to pay for one, go to [DynDNS.com]("http://www.dyndns.com") and set up an account. Then, you could do: ```
sudo apt-get install ddclient
``` and configure it to automatically update your account so that your hostname will always point to your computer, even when your IP changes.

Hope this helps! -Anatashinu

---

### Post by bluedrakonis on 2010-01-09
i have apache installed, and have a domain name, what ineed i s a program to automatically update my zoneedit account where i have a dynamic ip from my service provider

---

### Post by ian dobson on 2010-01-09
Hi,

Have a look here:- [http://www.zoneedit.com/doc/dynamic.html](http://www.zoneedit.com/doc/dynamic.html)

Regards
Ian Dobson

---

### Post by bluedrakonis on 2010-01-09
that helped some but how would i set one of them up to do what im trying to get it to do

---

### Post by noway2 on 2010-01-09
Do some reading on the Dyndsn site (note, the service is free).  I have been using them for about 9 months without a problem.  Basically, your domain registration will be such that it points to their DNS servers which in turn will direct the query to your server.  You then either configure your router, if it supports it or use their software client to inform them when your IP address changes.

---

