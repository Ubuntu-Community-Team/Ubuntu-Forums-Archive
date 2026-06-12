---
title: "Name for Project?"
date: 2011-03-17
forum: The Cafe
---

### Post by kevin11951 on 2011-03-17
In an effort to learn Python, I want to write and release an application for Linux...

A recent issue I've had is running a Linux server on a laptop, and wanting it to shut down automatically in the even of a power disruption.

The code works (but I will clean it up before release), however I still need a name for it...

The project will watch for any power disruptions (/proc/acpi/battery/BAT0/state changes), and upon such an event happening it will wait one minute and check again, if the disruption is still occurring, it will shut down the laptop in question, and optionally alert the sys admin via email...

**What would I name this project...**

PS. While such an application may not be useful to anyone besides me, perhaps it will grow to become useful as time goes on.

edit: and yes, I already thought of "UselessApp.py"

---

### Post by Xantheil on 2011-03-17
How about STFU.py?
:P

Does what it says!

---

### Post by Joe of loath on 2011-03-17
serversave?

Something like that :p

---

### Post by YfoMp5QBh2 on 2011-03-17
so does it protect the laptop against power surges? how about **'server surge shield'**
 
catchy! :P

---

### Post by fuduntu on 2011-03-17
> **kevin11951 said:**
> In an effort to learn Python, I want to write and release an application for Linux...

A recent issue I've had is running a Linux server on a laptop, and wanting it to shut down automatically in the even of a power disruption.

The code works (but I will clean it up before release), however I still need a name for it...

The project will watch for any power disruptions (/proc/acpi/battery/BAT0/state changes), and upon such an event happening it will wait one minute and check again, if the disruption is still occurring, it will shut down the laptop in question, and optionally alert the sys admin via email...

**What would I name this project...**

PS. While such an application may not be useful to anyone besides me, perhaps it will grow to become useful as time goes on.

edit: and yes, I already thought of "UselessApp.py"

Drop a shell script in /etc/pm/power.d that counts the number of switches.  After #n, shutdown.  In /etc/rc.local, delete the counter.

---

### Post by kevin11951 on 2011-03-17
For the interested among you:

[http://serversave.sourceforge.net/](http://serversave.sourceforge.net/)

Also, if you are interested, I could use some help...

---

### Post by NightwishFan on 2011-03-17
That is awesome. I will check it out.

---

### Post by forrestcupp on 2011-03-17
So you went with serversave? You took the fun out of trying to think up names. ;)

---

### Post by kevin11951 on 2011-03-17
> **forrestcupp said:**
> So you went with serversave? You took the fun out of trying to think up names. ;)

Well, I can always change it ;)

---

