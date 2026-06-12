---
title: "Which solution for running both Ubuntu &amp; XP?"
date: 2008-05-23
forum: Virtualisation
---

### Post by pikseli@work on 2008-05-23
I already have a dual boot. But it would be very inconvinient to boot into XP 10-20 times per day just to see if something shows in Internet Explorer like it does in Firefox. 

So when I am working on my portfolio or the framework it runs on, I am stuck on (horror!) Windows XP.

I'm in the process of finding more memory, and once I get more, I want to run either ubuntu as guest on XP, or XP as guest on ubuntu.

I prefer using ubuntu 100%, but am not certain that running XP on top of ubuntu is as easy as just running existing Ubuntu in Qemu on XP.

I value stability. My CPU does not support virtualization codes.

Also I am lazy and would like to keep hacking and confing to minimum.

Which virtualization solution would you suggest for me?

---

### Post by NightwishFan on 2008-05-23
Although I am unfamiliar with virtualization I would suggest running Xp as a guest, since Linux manages available resources better.
Edit: I wish I had enough ram to run a virtual vista that would be fun. :D

---

### Post by peitschie on 2008-05-23
It might also be worth looking at running IE under wine.  see [http://ubuntuforums.org/showthread.php?t=611676](http://ubuntuforums.org/showthread.php?t=611676) for some details.

---

### Post by pikseli@work on 2008-05-23
> **peitschie said:**
> It might also be worth looking at running IE under wine.  see [http://ubuntuforums.org/showthread.php?t=611676](http://ubuntuforums.org/showthread.php?t=611676) for some details.

Yeah, I also found Ie4Lin and it works great. But I also need other stuff on XP. Thanks for suggesting though.

Please, stay on topic :) Even if other solutions do exist for browser testing ;)

---

### Post by Devport on 2008-05-23
Personally I would run Windows threw Virtualbox with Ubuntu as host.

Another possibility to mention may be Colinux.

[http://colinux.org](http://colinux.org)

- Windows host
- Only possible with linux + Windows being x86-32bit
- Will take **a whole lot of work** to learn and setup
+ **Highest performace / most powerful** ( due to linux apps being run almost natively )

[[IMG]http://files.codepilot.net/CoLinux2-small.jpg[/IMG]](http://files.codepilot.net/CoLinux2.jpg)

You could make all apps look more integrated by using Clearlooks for gtk, Clearlooks for Windows ( [http://deviantart.com](http://deviantart.com) ) and use qgtkstyle for qt4 / kde4 -> that way you wouldn`t even be able to easily determine which apps belong to which OS / desktop.

---

### Post by dcstar on 2008-05-24
> **pikseli@work said:**
> 
........
I prefer using ubuntu 100%, but am not certain that running XP on top of ubuntu is as easy as just running existing Ubuntu in Qemu on XP.

I value stability. My CPU does not support virtualization codes.

Also I am lazy and would like to keep hacking and confing to minimum.

Which virtualization solution would you suggest for me?

VMWare has a free utility that will allow you to convert your existing Windows install into a VM so it works exactly as it does now.

I run XP as a VM inside VMWare server on Ubuntu.

---

