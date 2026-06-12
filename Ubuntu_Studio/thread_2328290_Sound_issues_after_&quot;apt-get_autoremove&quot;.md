---
title: "Sound issues after &quot;apt-get autoremove&quot;"
date: 2016-06-19
forum: Ubuntu Studio
---

### Post by Shubol on 2016-06-19
Hi everybody, I use ubuntu studio and I have few issues after I use  "apt-get autoremove"
1: I can see moving slider on panel but volume does not change. I can change volume only in "sound settings". 
2: Sound play in chrome, but don't play in video (I try VLC, Parole and SMPlayer) 
3: No sound in games

I thing the best way should be reinstall all sound drivers, but how I can do it?  And which ones? I was windows user long time and there are (in Linux) few alternative to everything, so I'm confused so far :D

Thanks all for every advice :-)

---

### Post by ajgreeny on 2016-06-19
You may be able to see what was removed (package names) by running command ```
grep -i " remove " /var/log/dpkg.log /var/log/dpkg.log.1
``` which lists all packages that have been removed listed by date/time so you may be able to figure out when you ran the autoremove command and then reinstall the packages listed at that time.

---

### Post by Shubol on 2016-06-19
It work, everything is OK now. Thank you very much for great advice  =d>

---

### Post by ajgreeny on 2016-06-20
Great. Please mark as SOLVED from the Thread Tools menu up-top. It is a great help to users searching the forum.

marked as SOLVED on behalf of Shubol.

---

