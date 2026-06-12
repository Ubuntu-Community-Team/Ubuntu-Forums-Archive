---
title: "Desktop linux performance issues"
date: 2005-10-05
forum: The Cafe
---

### Post by NoTiG on 2005-10-05
The desktop performance issues cause me concern... so I have taken a particular interest into the various areas where speed improvements might be changing for the better for the average desktop user:

[http://www.gnome.org/~lcolitti/gnome-startup/analysis/]("http://www.gnome.org/~lcolitti/gnome-startup/analysis/")

As part of the google summer of code project, one of the tasks set was to minimize or reduce gnomes start up time. After reading this article... it seems that perhaps the startup time for gnome itself can be reduced up to 50% with various "hacks" which may or may not become part of the tree by gnome 2.14

[http://initng.thinktux.net/index.php/Main_Page](http://initng.thinktux.net/index.php/Main_Page)

initng is a replacement of the systemv init which is the bootup process, and replaces it with a "parallel" boot to achieve faster booting times... much like the mac OS.  According to many user reports... boot times are halved or reduced down to as low as 15 seconds , depending on your hardware ! When it matures, it is expected to make it into Dapper drake , possibly. (YES!)


[http://www.drobe.co.uk/riscos/artifact1298.html](http://www.drobe.co.uk/riscos/artifact1298.html)
[http://www.coyotegulch.com/reviews/gcc4/](http://www.coyotegulch.com/reviews/gcc4/)

THese two articles are sort of contradictory... but hopefully as gcc matures, it will compile programs to be more efficient and run faster. 

[http://www.linuxformat.co.uk/modules.php?op=modload&name=News&file=article&sid=102](http://www.linuxformat.co.uk/modules.php?op=modload&name=News&file=article&sid=102)

I was kind of disappointed reading this article. One of the most popular apps is open office... and it is VERY slow to load, yet this guy proclaims that it is the kernel's fault. Things dont seem to be looking good for this program (correct me if im wrong)

[http://dri.freedesktop.org/~jonsmirl/graphics.html](http://dri.freedesktop.org/~jonsmirl/graphics.html)

> Using 3D for the desktop is not just about making more eye candy. A lot of the 3D generated eye candy may just be glitz but there are also valid reasons for using 3D. 3D is simply faster than 2D, no one is making their 2D functions faster, all of silicon engineering is going into 3D. You can do fast, arbitrary image processing for things like color space conversion, stretching/warping, etc. I’ve seen some extremely complex filtering done in real time with shader hardware that would take the main CPU several seconds a frame to do. Support for heterogeneous window depths (simultaneous 8, 16, 24-bit windows) with arbitrary colormaps. On-the-fly screen flipping/rotation for projectors, and whole-screen scaling for the visual impaired, etc. Resolution independence allows objects to be rendered at arbitrary resolution/size and down/up-sampled when shown on-screen. More interesting applications are described later in the windowing section.

A few more points to touch:
[http://live.gnome.org/MemoryReduction](http://live.gnome.org/MemoryReduction)

 GTK 2.8 and memory reduction . Right now infrastructure for advanced debugging has been integrated in gtk and glib 2.7.x. After 2.8 is released, reducing memory comsuption will be much easier.

The k7 kernel could end up replacing the deprecated 386 kernels resulting in speed increases. But how much of an improvement? and when?

Reiser 4 

The state of the reiser 4 file system is not clear to me. I am not sure if it is being merged with the mainline kernel... but supposedly it benchmarks as the fastest file system. ALl it needs is a repacker module (defragment) . I have heard some issues with the Latency of this file system so I am not sure if the claims hold true. There is also another possibile option... which is to enable dir_index in the ext3 file system which could result in speed improvements. Perhaps it will be enabled in the future ?

---

### Post by poofyhairguy on 2005-10-06
The biggest improvement is in XFCE's hands.

---

### Post by drizek on 2005-10-06
[QUOTE=poofyhairguy]The biggest improvement is in XFCE's hands.[/QUOTE]

im running SUPER right now and it boots to a full KDE desktop in 45 seconds. with initing, that number should be even lower. as for actual system performance, its very fast and snappy. OOo loads much faster tahn ubuntu, but still kinda slow(about 5-7 seconds, about equal to MS office 2k3). the gimp loads in just a few seconds, konsole and konqueror load up instantly, k3b doesnt need a splash screen anymore :cool: even yast is actually kinda fast now

---

### Post by laforge on 2005-10-06
in xfce4 everything loads in a few sec maybe 5 max.  I haven't tried any resource hoggers though, ie image programs.

---

### Post by arctic on 2006-03-13
I also experience a tremendous slowdown in Dappers OpenOffice package, even after tweaking the system. Other distros load it faster on the same hardware. I wonder what they did to the OOo package... It definitely seems to be an Ubuntu-related bug.

---

### Post by jc87 on 2006-03-13
Stop posting this stuff , that way i can no longer upgrade my machine with the excuse that is no longer fit to simple desktop uses:twisted:.

Do you really want to live in a world where in 10 years from now my P4 1700 , 512 DDR 400 , Ati radeon 9250 is still a useful machine? think off the children who no longer will have a pc capable of playing the latest Doom and Quake , and thoose poor companies like Amd and Intel!

You insensitive bastards , stop making speed improvements/memory leaks removal and concentrate in wasting all my machine power , and turning it obsolete as fast as you can.

P.S. This entire post is sarcasm , please don´t take it seriously , really is just a joke , stop saying i´m the new messias.

---

### Post by GoA on 2006-03-13
Actually, I would say that use more power. Why couldn't linux take power to draw graphics or use much memory or CPU speed? Let's compare it to windows vista which will use much power. Ok, it maybe isn't programmed so well as linux but still, why shoul your machine be idling all time long? 

I have quite normal "old" computer:

AMD Athlon Barton overclokked to 2.2 Ghz
1 Gb of DDR dual channel memory
Geforce 6800LE
200 gig harddisk space. 

Most of the time linux uses very little of this power and it's therefore useless. I say, use more! I would be happy to by new hardware to get all nice little things. :D Of course you need to take concern to low-end users but you should be able to use the whole power of your machine so that the new nice hardware is doing something else than idling. :) And folding at home isn't the answer here boys and girls.

---

### Post by Bandit on 2006-03-13
Wester Digital Raptor = Everything boots fast :D

---

### Post by Lord Illidan on 2006-03-13
[quote=GoA]Actually, I would say that use more power. Why couldn't linux take power to draw graphics or use much memory or CPU speed? Let's compare it to windows vista which will use much power. Ok, it maybe isn't programmed so well as linux but still, why shoul your machine be idling all time long? 

I have quite normal "old" computer:

AMD Athlon Barton overclokked to 2.2 Ghz
1 Gb of DDR dual channel memory
Geforce 6800LE
200 gig harddisk space. 

Most of the time linux uses very little of this power and it's therefore useless. I say, use more! I would be happy to by new hardware to get all nice little things. :D Of course you need to take concern to low-end users but you should be able to use the whole power of your machine so that the new nice hardware is doing something else than idling. :) And folding at home isn't the answer here boys and girls.[/quote]
Then, play hard core games, or try XGL/Compiz. Not everyone has the same spec as you do. IMHO, the OS should be as minimal as possible, the less power it takes, the better. Why overtax your processor on an OS, instead of apps or games?

---

### Post by GoA on 2006-03-13
[QUOTE=Lord Illidan]Then, play hard core games, or try XGL/Compiz. Not everyone has the same spec as you do. IMHO, the OS should be as minimal as possible, the less power it takes, the better. Why overtax your processor on an OS, instead of apps or games?[/QUOTE]

Games goes to windows side and XGL is running all the time. :) And this is pure taste issue, first in windows side I tuned windows to be as fast as possible but then I gaved my finger to the devil and started to care about eyecandy. :) But this is the reason why people should have a choice, XGL is on of them but I'm saying that with it's technology, it could do even more. 

But time will show, nobody nows for sure what the future will bring. However, I'm currently drooling over for the AMD's X2 or the future M2 socket processors with 2 gb of memory etc. However, with my current budget, not a chance. :D

---

### Post by mstlyevil on 2006-03-13
[QUOTE=GoA]Games goes to windows side and XGL is running all the time. :) And this is pure taste issue, first in windows side I tuned windows to be as fast as possible but then I gaved my finger to the devil and started to care about eyecandy. :) But this is the reason why people should have a choice, XGL is on of them but I'm saying that with it's technology, it could do even more. 

But time will show, nobody nows for sure what the future will bring. However, I'm currently drooling over for the AMD's X2 or the future M2 socket processors with 2 gb of memory etc. However, with my current budget, not a chance. :D[/QUOTE]

I love AMD but you should check this out for something else to drool over.

[URL="http://www.hardwarezone.com/articles/view.php?cid=1&id=1845"]
Sneak Peek - Conroe Puts the Fear into Athlon 64 FX-60[/URL]

---

### Post by GoA on 2006-03-13
Yes, allready have read about that. But still, I have my suspisions untill I see the results everywhere AND the price.

---

### Post by mstlyevil on 2006-03-13
[QUOTE=GoA]Yes, allready have read about that. But still, I have my suspisions untill I see the results everywhere AND the price.[/QUOTE]

Me too.

---

### Post by GoA on 2006-03-13
Because if it's beating FX-60 so much and FX-60 costs about 1000 euros, that won't be cheap. And Extreme Edition from that - Unbelievable pricy. :)

---

### Post by mstlyevil on 2006-03-13
They claimed it was the mid range Conroe CPU. I still want to wait and see what they actually do when they come out but this looks promising.

---

