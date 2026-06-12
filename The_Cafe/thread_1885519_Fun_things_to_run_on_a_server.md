---
title: "Fun things to run on a server?"
date: 2011-11-23
forum: The Cafe
---

### Post by sandyd on 2011-11-23
New box just arrived at colocation, and its going to be serving most of my sites. Sadly, I have 4GB RAM on it. The nginx + php5-fpm + mysql setup only uses 300mb RAM, even at high load. :P

Ideas?

*no game servers

---

### Post by BlouBlou on 2011-11-23
Try an IRC server, about your webs or offtopic.

---

### Post by Dragonbite on 2011-11-23
Repository Mirror?
OwnCloud cloud file server?
Isn't there a music streaming server program out there (just can't think of the name)?
DejaDup backup destination?

---

### Post by nickleboyblue on 2011-11-23
Slightly off topic, but it is rather entertaining to make websites that look like th interface to Start Trek's computers in HTML5 and CSS3... you can even make the right areas clickable or "touchable" if you have a touch screen and makes for a good conversation piece.

Otherwise, there are tons of game servers out there, you'll just have to find them.  Plane Shift may be looking for a volunteer, as are many other projects.  Just look around...

---

### Post by BrokenKingpin on 2011-11-23
File server, with raid-5.

---

### Post by sandyd on 2011-11-23
> **Dragonbite said:**
> Repository Mirror?
OwnCloud cloud file server?
Isn't there a music streaming server program out there (just can't think of the name)?
DejaDup backup destination?

Hmm. I like the idea of OwnCloud, esp since it works with nginx.

---

### Post by Linuxratty on 2011-11-23
You said no game servers,but Linuxinternationals has pokerTH on our server and poker every Sat (Come join us!)
:popcorn:
Work with Meshnet. (See Reddit about that.)

---

### Post by Dragonbite on 2011-11-23
> **sandyd said:**
> Hmm. I like the idea of OwnCloud, esp since it works with nginx.

Now what could be interesting is to combine ownCloud and iFolder for a Dropbox-like synchronization and browser accessibility!

---

### Post by sandyd on 2011-11-23
> **Dragonbite said:**
> Now what could be interesting is to combine ownCloud and iFolder for a Dropbox-like synchronization and browser accessibility!

Aha!
You solved my integration problem. Wasn't so sure how I could have uploaded the files to there VIA webdav.

---

### Post by LowSky on 2011-11-23
start folding@home.

---

### Post by Old_Grey_Wolf on 2011-11-23
> **sandyd said:**
> New box just arrived at colocation, and its going to be serving most of my sites. Sadly, I have 4GB RAM on it. The nginx + php5-fpm + mysql setup only uses 300mb RAM, even at high load. :P

Ideas?

*no game servers

How many cores does it have, what speed are they, how much disk storage does it have, does the CPU have VT extensions?

I had fun playing with Infrastructure as a Service using virtualization; such as, Ubuntu Enterprise Cloud, Eucalyptus, CloudStack, etc. However, my servers had enough cores to run about 8 operating systems simultaneously. I had virtual servers for a web server (LAMP stack), an email server, a ftp server, and so on. I started playing with it at home; although, now I do it as part of my job.

---

### Post by sandyd on 2011-11-23
> **Old_Gray_Wolf said:**
> How many cores does it have, what speed are they, how much disk storage does it have, does the CPU have VT extensions?

I had fun playing with Infrastructure as a Service using virtualization; such as, Ubuntu Enterprise Cloud, Eucalyptus, CloudStack, etc. However, my servers had enough cores to run about 8 operating systems simultaneously. I had virtual servers for a web server (LAMP stack), an email server, a ftp server, and so one. I started playing with it at home; although, now I do it as part of my job.
Sadly, its one of my lower end servers because im using it as a gateway

Intel Xenon 2GHz X2, 100 GB Disk, No VT (well, the processor supports it, but damned HP Bios doesn't :( )

---

### Post by undecim on 2011-11-23
How about something like towel.blikenlights.nl (telnet to that address if you're a Star Wars fan)

A website over telnet would be kind of cool, actually.

---

