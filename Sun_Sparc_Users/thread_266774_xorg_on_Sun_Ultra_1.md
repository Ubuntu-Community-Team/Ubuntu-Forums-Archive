---
title: "xorg on Sun Ultra 1"
date: 2006-09-27
forum: Sun Sparc Users
---

### Post by claudiomet on 2006-09-27
Hi..!!!

I have installed successfully Ubuntu Dapper 6.06.1 in a Sun Ultra 1, but can't confgure xorg.

First: The autodetection of my videocard fails
Second: I don't now what video card I have... (how can I see what videocard I have whithout open the machine..?)
Third: Therefore, I don't now what driver is for my video card...
Four: The lspci doesn't work... (appears nothing)

How can I configure the xorg on this machine...? ....help please.

PD: I use Linux (RedHat, Debian, SuSE, Mandriva, etc) for long time on i386 ...but i really newbie on this architecture... :-(

---

### Post by netztier on 2006-09-28
> **claudiomet said:**
> 
How can I configure the xorg on this machine...? ....help please.


Try with the information from this [thread]("http://www.ubuntuforums.org/showthread.php?t=160754") (scroll down to see the later posts). There acutally *gasp* **is** a search function in these forums! ;)  

If your box has a Creator card which runs with the **sunffb** driver, it will work.

regards

Marc

---

