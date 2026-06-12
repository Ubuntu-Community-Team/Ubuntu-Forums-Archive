---
title: "Ubuntu version statistics - July 2008"
date: 2008-07-01
forum: The Cafe
---

### Post by jingo811 on 2008-07-01
Nice to have links:
[http://en.wikipedia.org/wiki/Ubuntu_(Linux_distribution)#Releases](http://en.wikipedia.org/wiki/Ubuntu_(Linux_distribution)#Releases)

I focus the data for my statistics to the Ubuntu distro only not the other flavors of Ubuntu and to Desktop only.  There's too much chaos for Absolute Beginners as it is.

[IMG]http://i31.tinypic.com/9uyd6d.png[/IMG]

72 of 69 540 active members participated in the polls 2008-06.  That's around [ 72 / 69 540 ] => [SIZE="4"]0.13 %[/SIZE] of all active members.
The LIE isn't complete I need more data!!! =P~

[RIGHT][FONT="Arial Black"][SIZE="3"]Ubuntu version statistics - Overview[/SIZE][/FONT]
[clicky]("http://ubuntuforums.org/showthread.php?t=785805")
[/RIGHT]

---

### Post by jingo811 on 2008-07-03
bump 1.

approx 3 months left until Intrepid need more voters to be able to see the intersecting between 2 Ubuntu versions.

---

### Post by jingo811 on 2008-07-04
nudge 2

---

### Post by Chame_Wizard on 2008-07-04
Using Kububtu Gutsy Gibbon:guitar:

---

### Post by lisati on 2008-07-04
Still on Feisty.... it works well enough for what I've been doing lately (mostly visiting the forums, email, plus monitoring a Windows machine that lives in another part of the house....)

---

### Post by jingo811 on 2008-07-05
[CENTER][IMG]http://i27.tinypic.com/2n0r2v.gif[/IMG] [IMG]http://i26.tinypic.com/qoeedt.png[/IMG] Bump! [IMG]http://i26.tinypic.com/qoeedt.png[/IMG] Bump! [IMG]http://i28.tinypic.com/ztyhpf.png[/IMG] Pata! [IMG]http://i26.tinypic.com/qoeedt.png[/IMG] Bump! [IMG]http://i27.tinypic.com/2n0r2v.gif[/IMG][/CENTER]

---

### Post by spamzilla on 2008-07-05
+1 for Intrepid :D

---

### Post by jingo811 on 2008-07-06
bump: 6/31 - July 2008

Hey forum.Mods is it OK if I bump this and future monthly polls once everyday until the year 2010?

---

### Post by ssam on 2008-07-06
you could gather stats using [http://popcon.ubuntu.com/by_inst](http://popcon.ubuntu.com/by_inst) and counding kernel versions.

then you would be counting everyone who has enabled statistics in system->admin->software sources

---

### Post by jingo811 on 2008-07-06
That's a great idea!
Sorry for asking an obvious question but what is the package name for the kernel?

Is this a correct line to pull out numbers for my graph?
```
#rank name                            inst  vote   old recent no-files (maintainer)
...
...
4431  linux-source-2.6.22             9299     0     0     0  9299 (Unknown)   
...
...
```

Also could someone direct me to some good website that lists what kernel versions each Ubuntu "distro" uses.  With "distro" I mean Dapper, Feisty, Gutsy, Hardy, Intrepid, etc. etc.

Scratch the last question I think I know how to figure out which kernel versions belong to which "distro"
[http://en.wikipedia.org/wiki/Ubuntu_(Linux_distribution)#Releases](http://en.wikipedia.org/wiki/Ubuntu_(Linux_distribution)#Releases)

---

### Post by HansKisaragi on 2008-07-06
Hardy all the way *bump*

---

### Post by nick09 on 2008-07-06
Hardy here also, it has been sable ever since I installed it months ago.

---

### Post by smartboyathome on 2008-07-06
Hardy here, though it is such a mutant due to all the external repos that I might as well be running an intrepid-hardy ospring. ;)

---

### Post by jingo811 on 2008-07-06
> **ssam said:**
> you could gather stats using [http://popcon.ubuntu.com/by_inst](http://popcon.ubuntu.com/by_inst) and counding kernel versions.

then you would be counting everyone who has enabled statistics in system->admin->software sources

I grep'd out all the kernel lines from the website.  But which of these files should I use?  Should I filter out all the ODD looking lines or should I also count them in my graph :confused:

> danny@devito:$ **wc -l kernel-headers_2008_06_06.txt **
[COLOR="Red"]230[/COLOR] kernel-headers_2008_06_06.txt

> danny@devito:$ **wc -l kernel-headers_ODD_NAMES_2008_06_06.txt **
[COLOR="Red"]20[/COLOR] kernel-headers_ODD_NAMES_2008_06_06.txt

> danny@devito:$ **wc -l kernel-headers_USUAL_SUSPECTS_2008_06_06.txt **
[COLOR="Red"]210[/COLOR] kernel-headers_USUAL_SUSPECTS_2008_06_06.txt


For instance how should I interpret the lines in this file?
**kernel-headers_ODD_NAMES_2008_06_06.txt**
[PHP]11128 linux-kernel-headers            1137    21  1111     5     0 (Gnu Libc Maintainers)          
33553 linux-kernel-headers-arm-cross    25     0    24     0     1 (Unknown)                       
37727 pistachio-kernel-headers          13     1    12     0     0 (Unknown)                       
43308 linux-kernel-headers-powerpc-cross     6     0     6     0     0 (Unknown)                       
46811 linux-kernel-headers-mips-cross     4     0     3     0     1 (Unknown)                       
49762 linux-kernel-headers-mipsel-cross     3     0     2     0     1 (Unknown)                       
60698 cross-armv4l-kernel-headers        1     0     1     0     0 (Unknown)                       
60717 cross-iwmmxt-kernel-headers-i839     1     0     1     0     0 (Unknown)                       
60718 cross-iwmmxt-kernel-headers-mizi     1     0     1     0     0 (Unknown)                       
63337 genibo-kernel-headers              1     0     1     0     0 (Unknown)                       
75159 linux-kernel-headers-arm-dcvl      1     0     0     0     1 (Unknown)                       
75160 linux-kernel-headers-armeb-cross     1     0     1     0     0 (Unknown)                       
75161 linux-kernel-headers-i386-cross     1     0     1     0     0 (Unknown)                       
75162 linux-kernel-headers-m68k-cross     1     0     1     0     0 (Unknown)                       
75163 linux-kernel-headers-s390-cross     1     0     1     0     0 (Unknown)                       
75164 linux-kernel-headers-sh3-cross     1     0     1     0     0 (Unknown)                       
76602 mipsel-linux-kernel-headers        1     0     1     0     0 (Unknown)                       
76616 misdn-kernel-headers               1     0     1     0     0 (Unknown)                       
81159 rx-34-kernel-headers               1     0     1     0     0 (Unknown)                       
82332 stlinux23-sh4-kernel-headers       1     0     0     0     1 (Unknown)                [/PHP]

---

### Post by kevincarmony on 2008-07-06
Hardy, but eagerly awaiting Intrepid, several things in Hardy are not quite as good as they could be (GCC 4.3.1 is out, X Server 1.5 is in Fedora).

My main system runs Fedora 9.

My other systems run Ubuntu because its better with buggy proprietary hardware than Fedora is, but other than that, Fedora is very much "cooler".

---

### Post by cardinals_fan on 2008-07-06
I don't have Ubuntu installed on my main box, but Dapper Drake dual-boots with NetBSD on my secondary.

---

### Post by hellion0 on 2008-07-06
My three Linux machines are all running various flavors of 8.04.

---

### Post by Kernel Sanders on 2008-07-06
[IMG]http://img372.imageshack.us/img372/9522/lolzxu6.jpg[/IMG]

---

### Post by jingo811 on 2008-07-07
That would require Warty 4.10 history (Oct 2004) I only started taking temperature some weeks after Hardy 8.04 (LTS) got released (April 2008').  But even so the numbers aren't reliable enough.  That's why this has its origo set a few units to the right of the graph.  You need much more reliable data to set origo at x:y => 0:0
[IMG]http://i31.tinypic.com/9uyd6d.png[/IMG]

---

### Post by angry_johnnie on 2008-07-07
I use Hardy on my laptop, and Feisty/Mandriva on my desktop.  I'm really not sure which computer gets the most use, but I answered Hardy anyway.

---

### Post by Jeff Rage on 2008-07-07
Dapper - 6.06 8)

Is it time try a newer version yet?

---

