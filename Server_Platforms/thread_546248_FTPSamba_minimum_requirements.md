---
title: "FTP/Samba minimum requirements?"
date: 2007-09-08
forum: Server Platforms
---

### Post by FKi on 2007-09-08
I would like to know, how fast of a computer is really necessary for a linux server os doing ftp and samba? because i dont really want to overkill it.

---

### Post by p_quarles on 2007-09-08
It depends entirely upon how many people are using it. If it's just going to be a fileserver for two or three people, you can get away with very little processing power. More important would be the hard drive speed; and then just enough processing speed and memory to work with that drive. In that scenario, I would think that a Pentium 3 with 64 MB RAM would be adequate, and I know that people do run Linux home servers on machines that old.

---

### Post by FKi on 2007-09-08
yeah it'll be used for about 6-7 people, so i can probably find a local computer for about 30-40 bucks thatll run it i bet

---

### Post by netlogic on 2007-09-09
> **FKi said:**
> I would like to know, how fast of a computer is really necessary for a linux server os doing ftp and samba? because i dont really want to overkill it.

My home server is 233mhz overlocked to 266mhz with 96megs of ram. It is running vsftp, samba, dnsmasq, postifix, apache, and rtorrent at all same time, but I am running a  custom kernel.

---

### Post by FKi on 2007-09-09
wow tahts tons lower that what i was expecting

---

### Post by netlogic on 2007-09-09
Always yank out what you don't need.  You can even run it on a 486 if you re-compile to your need. NEVER use a window manager on the server. Always monitor processes and use renice, so all other processes work together very well. My CPU on the server is only 35% right now.

---

### Post by netlogic on 2007-09-09
If this is a small network for six people, consider getting Linksys' nslu2. You can install Debian on it. You can find this at ebay for under $60. [http://www.nslu2-linux.org/](http://www.nslu2-linux.org/)

---

