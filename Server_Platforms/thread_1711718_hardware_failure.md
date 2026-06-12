---
title: "hardware failure?"
date: 2011-03-21
forum: Server Platforms
---

### Post by xdarkness2 on 2011-03-21
Hello im trying to setup a Ubuntu Server installation on (dont laugh) a thin client. Now for its purpose it is fully quallified to do the job. Have my 4gb flash drive and done a nice installation, the installation went slow bud steady and did the job. 

Now here's the problem. Whenever i have large I/O 's the system freezes. For example i write some large files or restart a daemon, then at random (not on every daemon restart or filewrite) it freezes, i had a kernel panic in there once too. When idle .. nothing wrong.. it will run forever.

Frist i thought it was a corrupt flash disk (the internal flash drive 64 mb) which i turned into a swapdisk. Turning it off it still (but more rarely) crashes.. Can it have something to do with memmory.. is the cpu too hot ?? your guess is as good as mine. Anyone have this problem? thanks in advance.

Thin client: t5520 from HP

---

### Post by Joe of loath on 2011-03-21
What CPU does it have, and how much memory?

---

### Post by xdarkness2 on 2011-03-22
all specifications [http://h18000.www1.hp.com/products/quickspecs/12265_div/12265_div.HTML]("http://h18000.www1.hp.com/products/quickspecs/12265_div/12265_div.HTML")

---

### Post by walt.smith1960 on 2011-03-22
Ubuntu on a machine with 128 Mb. RAM seems rather ......optimistic.

---

### Post by xdarkness2 on 2011-03-22
> **walt.smith1960 said:**
> Ubuntu on a machine with 128 Mb. RAM seems rather ......optimistic.

Not nessesarly, the minimum hardware requirement is 64mb, recommended 256, in ubuntu desktop edition (without gui). And for its purpose it well exceeds the memmory requirement. And if required i can always add a usb flash disk with swap RAM. Besides that, i dont get "out of memmory" errors. The problem is a crash or kernel panic on large i/o's ..
so back op topic ... the problem..........

I liked the answer about the cpu, maybe i need to add some kernel parameters or disable some... Maybe the videocard (which also takes a part of the memmory) is messing things up. I will look into this tonight...

Thanks for all your reply's so far :)

:popcorn:

---

### Post by Joe of loath on 2011-03-22
What does memtest86 say? Also, if you connect a monitor and run top, what happens to the resource usage before it crashes?

---

### Post by xdarkness2 on 2011-03-25
Well after a long search i found out that the CPU can not run 686 based systems. So i either have to find a way to disable 686 features in the kernel or build a custom kernel (586) any hint on kernel parameters to force some sort of 586 mode please do, dont know if there are... else it will prolly be custom build ..

Thanks for all the help, great!!!

Greetings from The Netherlands :)

---

### Post by Joe of loath on 2011-03-25
It might be simpler to just install Debian. On a CLI install you won't notice much difference, and it works with older processors IIRC.

---

### Post by iissmart on 2011-03-25
Use the Debian netinst: [http://www.debian.org/distrib/netinst](http://www.debian.org/distrib/netinst)

Verify with uname -a after it installs that it correctly autodetected & uses the i586 kernel (could be anything i386-i586).

I'm surprised it was able to boot an i686 kernel if it only supports up to i586...

---

### Post by xdarkness2 on 2011-03-26
Well it suppose to be a 686, bud they made some poor design decissions which break full compatibility with the 686, as far as i know..

im not the expert... just something picked up from ____ ?? where was it.. ow well .. 

I build my custom kernel (not difficult to build, at least not on a system that does not crash... this one for once was a tricky one) and i still have the same problems.

I will look into the debian install..

or maybe it is just a bad/broken cpu. :/

---

