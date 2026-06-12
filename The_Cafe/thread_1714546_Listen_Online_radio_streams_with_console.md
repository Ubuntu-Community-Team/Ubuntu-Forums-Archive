---
title: "Listen Online radio streams with console"
date: 2011-03-25
forum: The Cafe
---

### Post by frenchn00b on 2011-03-25
Hi,

Perl and bash are available everyone, on all machines, for everyone, and it can run programs.

Shoutcast is a great database that can be accessed my theme of radio.

Has someone developed a program code either in perl or bash, that can run mplayer or cplay/splay or other, to play the radio stream ? 

Would be very appreciated by lot lot of users and coders

---

### Post by frrobert on 2011-03-25
You could use mplayer in slave mode.  More information can be found at [ftp://ftp2.mplayerhq.hu/MPlayer/DOCS/tech/slave.txt](ftp://ftp2.mplayerhq.hu/MPlayer/DOCS/tech/slave.txt)

---

### Post by frenchn00b on 2011-03-25
> **frrobert said:**
> You could use mplayer in slave mode.  More information can be found at [ftp://ftp2.mplayerhq.hu/MPlayer/DOCS/tech/slave.txt](ftp://ftp2.mplayerhq.hu/MPlayer/DOCS/tech/slave.txt)

well, I do not understand. But how to wget the list of streams with categories from shoutcast, adn play the one one wants?

---

### Post by frrobert on 2011-03-26
mplayer -slave -playlist url
will pull in and play url no need for wget

Example
mplayer -slave -playlist [http://yp.shoutcast.com/sbin/tunein-station.pls?id=1270282](http://yp.shoutcast.com/sbin/tunein-station.pls?id=1270282)

---

### Post by Ibidem on 2011-03-26
Err...mpg123 /mpg321 does all the work:
mpg123 <shoutcast stream URL>
and it starts playing.

---

### Post by honeybear on 2011-03-26
I would like to ask you, if there is a console way to retrieve a list of radio url's, this based on the radio type (eg. rock, talk, pop, ...)?

---

