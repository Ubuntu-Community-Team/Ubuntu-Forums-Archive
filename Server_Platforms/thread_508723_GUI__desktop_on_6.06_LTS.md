---
title: "GUI / desktop on 6.06 LTS"
date: 2007-07-24
forum: Server Platforms
---

### Post by ratbastard on 2007-07-24
I looked I just can't seem to find the answer for how to get a desktop/ gui upand running on 6.06 -- I looked at a couple of threads that suggested install desktop-ubuntu via apt get. 

that method is not working 

any ideas

---

### Post by koenn on 2007-07-24
how far did you get and what exactly is not working ? 
and why is this in the server forum - did you start from a server install ?

---

### Post by ratbastard on 2007-07-24
I chose the INSTALL LAMP feature on the setup : 



I ran sudo update and upgrade I added other resp too.  


and here is what I am geting: 




lampman@lampserver:/etc/apt$ sudo apt-get install desktop-ubantu
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package desktop-ubantu
lampman@lampserver:/etc/apt$

---

### Post by Rui Pais on 2007-07-24
> **ratbastard said:**
> 
lampman@lampserver:/etc/apt$ sudo apt-get install desktop-ubantu
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package desktop-ubantu

sudo apt-get install **ubuntu-desktop**

or xubuntu-desktop if you want something lighter.

by the way, to avoid typos, write:
"sudo apt-get install ubu" and then press TAB key

---

### Post by koenn on 2007-07-24
that was easy  :)

---

### Post by ratbastard on 2007-07-24
too funny !

[http://ubuntuforums.org/showthread.php?t=193305](http://ubuntuforums.org/showthread.php?t=193305)


Take a look at the above post? 

my fault for being lazy !! 

lol

I am glad though because i wanted XFCE !@!!!!



thanks all

---

### Post by Rui Pais on 2007-07-25
> **ratbastard said:**
> too funny !

[http://ubuntuforums.org/showthread.php?t=193305](http://ubuntuforums.org/showthread.php?t=193305)


Take a look at the above post? 

my fault for being lazy !! 

lol

I am glad though because i wanted XFCE !@!!!!



thanks all

As i said before if you wanted, if you wanted, you could go with xubuntu-desktop.
You can have both installed so no problem to go for that now...
You can use aptitude instead of apt-get, that usually make it easy to uninstall later.

[Check here]("http://www.psychocats.net/ubuntu/purexfce") a suggestion on how to uninstall a metapackages *-desktop. 

If you want  to remove ubuntu-desktop to get xubuntu-desktop, maybe a better choice would be uninstall first and then do the sudo aptitude install xubuntu-desktop.

---

### Post by ratbastard on 2007-07-25
Wow even more good info :

I actually went with XFCE it installed with only one hitch , that being monitor h and v values but that was an easy fix .. 

thanks again !!!

---

