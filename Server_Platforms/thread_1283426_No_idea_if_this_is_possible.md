---
title: "No idea if this is possible"
date: 2009-10-05
forum: Server Platforms
---

### Post by Carlo1973 on 2009-10-05
Hey all. I have no idea if what I am attempting to do is even possible.

First let me start by saying I love Ubuntu. Secondly let me describe what I am trying to do.

I have an old computer I want to setup as a server. Initially I wanted to set it up as a Radius server to act as Enterprise WPA2 connection for my various wireless computers (some on windows, some on linux, a wii, a ps3, an xbox 360, etc) just to say "Yes I did it - no real reason to but I did it"

This idea has now expanded to me wanting to also use the box to host roaming profiles for my computers. Eventually I want to add an application server, ftp server, mail server, maybe have it setup like exchange but utilising linux ldap. The system I'm running it on is an old AMD Athlon XP 2.(something-or-other)Ghz cpu, with about 2gb of ram, 4 HDD's, and 1 DVD-RW. 

My hdd's are configure as such
drive 1
75gb = /
5gb = swap

drive 2
17gb = /var

drive 3 
13gb = /tmp

drive 4 (external usb)
160gb = /home

The problem is that I am using a Dlink wireless N Extreme router. My computers are all behind that and that's the way I want it to remain - not wanting to set it up as an access point.  

Is there a way for me to set this up, so that everything works with the router providing the NAT addressing? I have the server statically set to an IP address on the router. 

Hope I can get assistance with this. Thanks in advance

Carlo

---

### Post by whoop on 2009-11-07
Look at this tutorial. It's the most complete one I could ever find. Sadly it was written for 7.10 (although it works with 8.04 also):
[http://www.rrcomputerconsulting.com/view.php?article_id=3](http://www.rrcomputerconsulting.com/view.php?article_id=3)

We need up-to-date documentation on this topic, please **vote**:
[http://brainstorm.ubuntu.com/idea/22151/](http://brainstorm.ubuntu.com/idea/22151/)

---

