---
title: "Trying to install php 5.4"
date: 2015-12-18
forum: Repositories &amp; Backports
---

### Post by Lars_Bruins_Slot on 2015-12-18
Hey,
I'm currently working on a school project which requires me to use PHP version 5.4. However i'm kinda new to ubuntu ( and to Linux in general). 
My problem is that when i use sudo apt-get install php5 it will automatically install the latest recommended version which is at the moment 5.6.X. I did browse google for quite a bit but i cant seem to figure out how to install php 5.4, 
i hope you guys can help me!.
-Lars

---

### Post by brian-mccumber on 2015-12-18
Maybe this will help - [http://tecadmin.net/install-php5-on-ubuntu/#](http://tecadmin.net/install-php5-on-ubuntu/#)

These guys have set up a ppa for older versions of php. PHP 5.4 is the first on the page. 

Being that php is mostly backwards compatible I don't see why you would have a problem using the newest version, unless they have specifically said to use that specific version for some reason. I have been using php through a few versions and everything that I wrote in the past on older versions still work on the newest versions.

Usually php runs on an Apache server, have you already set that up?

---

