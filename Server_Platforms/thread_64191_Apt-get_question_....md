---
title: "Apt-get question ..."
date: 2005-09-10
forum: Server Platforms
---

### Post by dbee on 2005-09-10
I don't have any gcc compiler on my server. I know that it isn't included in the desktop version either, although the desktop version has an apt-get facility which means that it's easy to install.

Unfortunately there seems to be no apt-get on the server edition. And I can't seem to access the ubuntu mirrors to claim individual packages... 

which means no complier, which means no checkinstall, which means no ./configure apache packages

... well I seem to have the apt-get man page .. but when I

sudo apt-get gcc

I get 

E: invalid operation gcc

Anybody have any suggestions ... ???

Thanks

---

### Post by Leif on 2005-09-10
try 

sudo apt-get install build-essentials

---

### Post by dbee on 2005-09-10
Thanks Leif,

My box says that it can't find build-essentials ...

I can get make though, and when I run the make on my configured apache files I get a weird error ...

Makefile:31: /home/aaron/downloads/http-2.0.50/build/rules.mk: No such file or directory

... I don't have a /home/aaron on my computer, so I don't know which file it's looking for ...

---

### Post by Leif on 2005-09-10
oops, my bad, that should be 

sudo apt-get install build-essential


as for /home/aaron, are you sure ? is your username aaron ? if so, then this is your home directory.

---

