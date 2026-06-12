---
title: "HTTPS Apache Squirrelmail"
date: 2008-06-04
forum: Server Platforms
---

### Post by chrismyers on 2008-06-04
Hi All,

Does anyone know how I get my squirrelmail to work over HTTPS?

My current squirrelmail is working, but only over HTTP.

I believe I have to make a change to Apache, but so far all the things I have tried have failed.

Does anyone have a how-to (preferably specific to Ubuntu).

Many, many thanks in advance. :-)

---

### Post by quelx on 2008-06-04
[https://help.ubuntu.com/community/Squirrelmail#head-00337963abb6d420cde13e8dd711ea342e360a84](https://help.ubuntu.com/community/Squirrelmail#head-00337963abb6d420cde13e8dd711ea342e360a84)

---

### Post by chrismyers on 2008-06-05
Hi quelx,

Thanks for the response, but the how to you provide is for getting squirrelmail working.

I already have a working squirrelmail.

I need to get it working over a secure connection (HTTPS/SSL).

Assistance would still be appreciated.

---

### Post by quelx on 2008-06-05
> **chrismyers said:**
> 
I need to get it working over a secure connection (HTTPS/SSL).


You need to edit your **squirrelmail** config file in */etc/apache2/sites-avaliable/*

> 
Alternatively, if you wish to use a virtual server setup instead, you can. For setting up SSL, uncomment the last section from the configuration file. For more details on how to use apache, see the Apache page. 

---

