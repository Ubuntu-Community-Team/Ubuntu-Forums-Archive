---
title: "Dovecot mail stack delivery config file empty?"
date: 2015-11-24
forum: Server Platforms
---

### Post by jordan58 on 2015-11-24
Hi all, 

I'm a bit of a Ubuntu noob so just getting that out there before we go any further :p 

I'm in the process of setting up an email server (following an online guide) and I'm just going though the process of configuring postfix and dovecot, in the guide it mentions making some changes to the  /etc/dovecot/conf.d/01-mail-stack-delivery.conf file but when i open the file with nano its blank, is it supposed to be empty or have i done something wrong somewhere? I did install postfix and dovecot using the sudo mail-stack-delivery command so from what i understand it should contain some info of some sort. 

If anyone wants the link to the guide just say so and I'll post it in my next reply :)

---

### Post by sandyd on 2015-11-24
Hi,

Your thread has been moved to *Server Platforms*.

We will need to know what guide you are using, as well as the version of Ubuntu you are running.

---

### Post by jordan58 on 2015-11-25
> **sandyd said:**
> Hi,

Your thread has been moved to *Server Platforms*.

We will need to know what guide you are using, as well as the version of Ubuntu you are running.


Thanks sandyd, 

The guide I'm following is located here [http://arstechnica.com/information-technology/2014/03/taking-e-mail-back-part-2-arming-your-server-with-postfix-dovecot/4/](http://arstechnica.com/information-technology/2014/03/taking-e-mail-back-part-2-arming-your-server-with-postfix-dovecot/4/) its about a quarter way down the page is where I'm running into problems. 

I'm testing it out on Ubuntu 14.04.3 Desktop at the moment before i do move over to Ubuntu Server, perhaps that's where I'm going wrong :p?

---

### Post by sandyd on 2015-11-25
> **jordan58 said:**
> Thanks sandyd, 

The guide I'm following is located here [http://arstechnica.com/information-technology/2014/03/taking-e-mail-back-part-2-arming-your-server-with-postfix-dovecot/4/](http://arstechnica.com/information-technology/2014/03/taking-e-mail-back-part-2-arming-your-server-with-postfix-dovecot/4/) its about a quarter way down the page is where I'm running into problems. 

I'm testing it out on Ubuntu 14.04.3 Desktop at the moment before i do move over to Ubuntu Server, perhaps that's where I'm going wrong :p?

Guide is for Ubuntu 12.04 - you need a newer guide.
Try [https://www.exratione.com/2014/05/a-mailserver-on-ubuntu-1404-postfix-dovecot-mysql/](https://www.exratione.com/2014/05/a-mailserver-on-ubuntu-1404-postfix-dovecot-mysql/)

Seems to work - I did the guide a while back with several modifications.

---

### Post by jordan58 on 2015-11-26
> **sandyd said:**
> Guide is for Ubuntu 12.04 - you need a newer guide.
Try [https://www.exratione.com/2014/05/a-mailserver-on-ubuntu-1404-postfix-dovecot-mysql/](https://www.exratione.com/2014/05/a-mailserver-on-ubuntu-1404-postfix-dovecot-mysql/)

Seems to work - I did the guide a while back with several modifications.


Fantastic, I'll give that ago later or maybe over the weekend. Thanks for your help!

---

