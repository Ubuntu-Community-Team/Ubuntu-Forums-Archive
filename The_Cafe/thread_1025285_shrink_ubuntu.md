---
title: "shrink ubuntu?"
date: 2008-12-29
forum: The Cafe
---

### Post by kevin11951 on 2008-12-29
the ubuntu install on my dell mini 9 has only 168 kb left, with a deafult, and a few tweaks. ooo3, netbook remix, etc...

is there any thing huge, that i dont need on a netbook, that i can get rid of?

---

### Post by MaxIBoy on 2008-12-30
Remove the netbook remix GUI altogether, and go for something ligher, like wmii or awesomeWM. Wmii only takes up about 5 megs on your hard drive.

If openoffice has any extra unneeded language packs installed, get rid of those. Also, if there are any unneeded components (suppose you never use openoffice's formula editor,) you can get rid of those as well. 

Go to /boot and see if there are any old kernels you can get rid of.

By default, there are a bunch of drivers you won't need. (Example, two different printer daemons, one for HP printers, one for something else.) 

You can shave off a few hundred kb by compiling a custom kernel.

Use "sudo apt-get autoremove" every time you uninstall something.

---

### Post by doorknob60 on 2008-12-30
sudo apt-get clean

---

### Post by kevin11951 on 2008-12-30
> **MaxIBoy said:**
> Remove the netbook remix GUI altogether, and go for something ligher, like wmii or awesomeWM. Wmii only takes up about 5 megs on your hard drive.

If openoffice has any extra unneeded language packs installed, get rid of those. Also, if there are any unneeded components (suppose you never use openoffice's formula editor,) you can get rid of those as well. 

Go to /boot and see if there are any old kernels you can get rid of.

By default, there are a bunch of drivers you won't need. (Example, two different printer daemons, one for HP printers, one for something else.) 

You can shave off a few hundred kb by compiling a custom kernel.

Use "sudo apt-get autoremove" every time you uninstall something.

"sudo apt-get autoremove" freed up 700mb! (it was 3 kernels)

---

### Post by cnbiz850 on 2008-12-30
Ubuntu is realy huge in some sense.

A couple days ago, a friend asked me to load Linux on his old Pentium III 700MHz 256MB RAM Thinkpad.  He has been running XP on it and he now is sick about the unreliability of XP so wants some change.  As a matter of fact, XP run well on that machine besides the normal Windows problems.  I use Ubuntu and thought that Ubuntu shouldn't demand more resources than XP, so I installed  8.10 on it.  I had a couple breakings in the process, but finally, Ubuntu was loaded.  To my supprise, when I login to it, the memory went out easily when I just did s couple simple things like opening Firefox and a terminal window.  It is simply unusable!

---

### Post by init1 on 2008-12-30
> **cnbiz850 said:**
> Ubuntu is realy huge in some sense.

A couple days ago, a friend asked me to load Linux on his old Pentium III 700MHz 256MB RAM Thinkpad.  He has been running XP on it and he now is sick about the unreliability of XP so wants some change.  As a matter of fact, XP run well on that machine besides the normal Windows problems.  I use Ubuntu and thought that Ubuntu shouldn't demand more resources than XP, so I installed  8.10 on it.  I had a couple breakings in the process, but finally, Ubuntu was loaded.  To my supprise, when I login to it, the memory went out easily when I just did s couple simple things like opening Firefox and a terminal window.  It is simply unusable!
Ubuntu on 256MB? Not surprised it failed so quickly, actually. I used to have 512MB on my laptop, but I was swapping a LOT (sometimes as much as 300MB) so I had to upgrade. Firefox takes up around 200MB RAM after a few hours of use, I've seen it as high as 270MB. You should have more success with a lighter WM or a lighter distro.

---

### Post by MikeTheC on 2008-12-30
[font="Courier New"]$ sudo apt-get install new-computer[/font]

---

### Post by oldos2er on 2008-12-30
> **kevin11951 said:**
> is there any thing huge, that i dont need on a netbook, that i can get rid of?

 Install "localepurge".

---

### Post by MikeTheC on 2008-12-30
@ "Shrink Ubuntu"...

[YouTube: I'm Shrinking!](http://www.youtube.com/watch?v=O8RJH5KJPA4)

---

### Post by hessiess on 2008-12-30
> **cnbiz850 said:**
> Ubuntu is realy huge in some sense.

A couple days ago, a friend asked me to load Linux on his old Pentium III 700MHz 256MB RAM Thinkpad.  He has been running XP on it and he now is sick about the unreliability of XP so wants some change.  As a matter of fact, XP run well on that machine besides the normal Windows problems.  I use Ubuntu and thought that Ubuntu shouldn't demand more resources than XP, so I installed  8.10 on it.  I had a couple breakings in the process, but finally, Ubuntu was loaded.  To my supprise, when I login to it, the memory went out easily when I just did s couple simple things like opening Firefox and a terminal window.  It is simply unusable!

XP is like 8 years or so old, Ubuntu is at maximum 6 mounts out of date, so being newer it will obviously use more resources. Try using a lighter DE, like XFCE, DWM. Or a light distro sutch as DSL, puppy or Arch.

---

### Post by der_joachim on 2008-12-31
> **hessiess said:**
> (...) Or a light distro sutch as DSL, puppy or Arch.

+1

I love arch on my EEE900, even with Gnome + NBR.

---

### Post by bigbrovar on 2008-12-31
> **cnbiz850 said:**
> Ubuntu is realy huge in some sense.

A couple days ago, a friend asked me to load Linux on his old Pentium III 700MHz 256MB RAM Thinkpad.  He has been running XP on it and he now is sick about the unreliability of XP so wants some change.  As a matter of fact, XP run well on that machine besides the normal Windows problems.  I use Ubuntu and thought that Ubuntu shouldn't demand more resources than XP, so I installed  8.10 on it.  I had a couple breakings in the process, but finally, Ubuntu was loaded.  To my supprise, when I login to it, the memory went out easily when I just did s couple simple things like opening Firefox and a terminal window.  It is simply unusable!

you should have your self to blame then... when people say linux or ubuntu uses lesser resuoures then xp they dont usually mean the latest gnome complete with compiz. infact what pple mean is that ubuntu has various versions that can be used on a system with low hardware. like xubuntu which uses a xfce desktop environment. why would any one install gnome ubuntu on a P3 laptop with 256 mb and expect it to be on per with xp. it simply wont .. because ubuntu ships not just with the core OS but with other stuffs too like office suits, graphic ultilitie and many other software which dont ship with a default xp. not to talk of other stuffs under the hood which are meant to enhance auto detection. if you are going to use ubuntu on a low hardware then u can install xubuntu and load lxde desktop manager on it. i have tried it and its freaking awesome. beside u dont have to use firefox. u can use seamonkey. or midori which are all lite browsers that work fine. i tried cruchbang linux an ubuntu based distro that uses openbox as a DE and it was freaking fast. on a 256mb desktop htop showed that it uses just 88mb or ram on idle mode. i loaded lxde on it and it was even cooler. so please do your research before making blunders. and blaming linux for your loss

---

### Post by cnbiz850 on 2009-01-02
Blaming myself is easy to do, but I don't think it is easy for every new comer trying Ubuntu to blame themselves.  To them, both XP and Ubuntu are OS's running on PC's.  Xp runs well on both a lowly configured machine as well as a highly configured one.  Ubuntu is the most popular Linux distro, so it is expected to be at least the same if not better than XP.  IE has been highly bashed, but the result at the end is that it runs powerfully on both low and high -end machines.  Firefox has been highly hyped, but the end result is that it fails on low-end machines.  Some said that it easily takes up 200MB ram -- what is going on?

Doesn't everyone see this picture?  Many new triers would end up saying "Linux sucks".

---

### Post by gletob on 2009-01-02
> **cnbiz850 said:**
> Blaming myself is easy to do, but I don't think it is easy for every new comer trying Ubuntu to blame themselves.  To them, both XP and Ubuntu are OS's running on PC's.  Xp runs well on both a lowly configured machine as well as a highly configured one.  Ubuntu is the most popular Linux distro, so it is expected to be at least the same if not better than XP.  IE has been highly bashed, but the result at the end is that it runs powerfully on both low and high -end machines.  Firefox has been highly hyped, but the end result is that it fails on low-end machines.  Some said that it easily takes up 200MB ram -- what is going on?

Doesn't everyone see this picture?  Many new triers would end up saying "Linux sucks".

Have you seen IE 7 on an older machine?

---

### Post by gn2 on 2009-01-03
> **cnbiz850 said:**
> Ubuntu is realy huge in some sense.

A couple days ago, a friend asked me to load Linux on his old Pentium III 700MHz 256MB RAM Thinkpad.  He has been running XP on it and he now is sick about the unreliability of XP so wants some change.  As a matter of fact, XP run well on that machine besides the normal Windows problems.  I use Ubuntu and thought that Ubuntu shouldn't demand more resources than XP, so I installed  8.10 on it.  I had a couple breakings in the process, but finally, Ubuntu was loaded.  To my supprise, when I login to it, the memory went out easily when I just did s couple simple things like opening Firefox and a terminal window.  It is simply unusable!

Couple of points, on that hardware there's no way that a standard Ubuntu 8.10 will run well.
But with the right Linux distro correctly installed and configured, (e.g. Arch, Debian Xfce, OzOS, Elive, Zenwalk) it will fly.

Comparing Ubuntu 8.10 with Xp is not a good comparison, try comparing it with Vista and see how you get on installing that on your friend's machine.

---

