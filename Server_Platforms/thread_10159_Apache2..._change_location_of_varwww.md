---
title: "Apache2... change location of var/www"
date: 2005-01-05
forum: Server Platforms
---

### Post by flade on 2005-01-05
Hi,

I've got A2PM (apache2, php4, mysql) runing.

Now I installed another hdd 20Gb Fujitsu that I found  under my bed. I want to use this drive to store webpages and other stuff. 

How to tell apache2 that my web pages are stored for example in "/mnt/drive2/www". Where do I do that.  :oops: 

I tried apache2.conf as httpd.conf is no longer present with apache2.


Help.


-------------
++   Flade

---

### Post by wulf on 2005-01-05
You want */etc/apache2/sites-available/default* (assuming you want to adjust the default site for your server). Replace the "/var/www" with the path to your website. It can get a lot more complex than this but that's the easy way.

For peace of mind, it might not be a bad idea to backup the original file before you start making changes. After you're done I think you need to restart apache - *apache2 -k restart* (off the top of my head).

Wulf

---

### Post by flade on 2005-01-05
tnx wulf, that's what I was looking for...



regards,

Fladé

---

### Post by az on 2005-01-05
Anyone remember "snappy answers to stupid questions?"


"Now I installed another hdd 20Gb Fujitsu that I found under my bed"


1-  Bluetooth fairy?
or

2-  That happens to me every other day.  Is there anybody I can call who will come and fumigate?
or

3-  Who's boots been under your bed?








nevermind.

---

### Post by ctimko on 2008-06-30
I wish my bed gave me 20 Gb Harddrives at random. That would be awesome. (Maybe some 1 TB Drives woul be even cooler!)

---

### Post by sparkyjoe34 on 2008-06-30
> I wish my bed gave me 20 Gb Harddrives at random. That would be awesome. (Maybe some 1 TB Drives woul be even cooler!)  :lolflag:

---

