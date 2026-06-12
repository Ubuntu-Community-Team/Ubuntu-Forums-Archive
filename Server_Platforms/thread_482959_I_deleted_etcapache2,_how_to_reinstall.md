---
title: "I deleted /etc/apache2, how to reinstall?"
date: 2007-06-24
forum: Server Platforms
---

### Post by siDDis on 2007-06-24
Im trying to setup apache2 + php 5

However Apache refuse to start, I tried to do apt-get remove apache2 but it didn't remove the configuration files. So I decided to start from scratch and just typed rm -R /etc/apache2

But now when I run apt-get install apache2 it doesn't reinstall.

What should I do?

---

### Post by Ziox on 2007-06-24
what are the error messages if you are installing from terminal?

---

### Post by siDDis on 2007-06-24
I dont get any error messages, it just dont rebuild the /etc/apache2 folder with its content

---

### Post by Ziox on 2007-06-24
apache2 is installed by default, yet there is no such folder as /etc/apache2 on the my system.

---

### Post by Wardazo on 2007-06-24
> **Ziox said:**
> apache2 is installed by default, yet there is no such folder as /etc/apache2 on the my system.

I can't see how you can have apache2 without an /etc/apache2 directory after a standard apt-get install

siDDis, I'm not sure about how to solve your problem... it's odd that 

```
sudo apt-get install apache2
```

Doesn't install apache or produce some kind of error report. Perhaps you shoud try removing with the purge option

sudo apt-get remove --purge apache2

Then try reinstalling and checking localhost in your browser. If you get any error messages this time, please post back.

---

### Post by Ziox on 2007-06-24
my mistake.  I must've cd(ed) into the wrong directory.

---

### Post by symvolker on 2007-07-18
Hi, I'm having the same problem. apt-get remove --purge apache2; apt-get install apache2 doesn't solve the problem. /etc/apache2 remains empty and apache doesn't come up. Any ideas...?

---

### Post by ZiRo on 2007-11-08
I removed mine and can't get it back - remove/install doesnt seem to generate the /etc/apache2/

Help.

---

### Post by MJN on 2007-11-08
What does the output of **dpkg -l apache2** look like?

You could try **dpkg -r --force-remove-reinstreq apache2** to really remove everything (including hopefully the status of the config files supposedly being present) and then run a new install with **apt-get install apache2**.

Mathew

---

### Post by ruibernardo on 2007-11-08
The configuration files are in the apache2-common or **apache2.2-common** package, depending on which one is installed (apache2.2-common in Feisty and Gutsy). Purge it and install apache2 again.

From a bookmarked thread:> **pzazz said:**
> The config files are from the package apache2-common, not apache2, so ...

$ /etc/init.d/apache2 stop
$ apt-get --purge remove apache2-common apache2

Removes all the apache config files.

$ apt-get install apache2

Installs all the config files again.


---

### Post by MJN on 2007-11-09
Well done that man. The rest of us were barking up the wrong tree!
 
Mathew

---

### Post by geforce123 on 2007-11-10
Maybe that would work too:

dpkg-reconfigure apache2
dpkg-reconfigure apache2-common

---

