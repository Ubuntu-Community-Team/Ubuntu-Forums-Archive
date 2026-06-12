---
title: "GDAM with ubuntu 8.04"
date: 2008-12-17
forum: Ubuntu Studio
---

### Post by kbkntk on 2008-12-17
has anybody here got GDAM ([http://gdam.ffem.org/]("http://gdam.ffem.org/")) running on ubuntu hardy heron? i have some libary problems while trying to install it and can´t fix the problem. maybe someone can re-compile it for ubuntu? that would be great:), cause i don´t know how to do it.
there is also an old thread about this: [http://ubuntuforums.org/showthread.php?t=55684](http://ubuntuforums.org/showthread.php?t=55684) , but it doesn´t really help me. :(
i also tried mixxx ([http://mixxx.org/]("http://mixxx.org/")) as an alternative.... it´s great, too. but i do have some latency problems there and i think GDAM might be better for experimental DJ-ing, which i want to do...

thanx for any help
martin



___________________________________________________________________________
ASUS EEEPC 701 4G w/ 2GB RAM and 16GB SD ROM
right now i'm using [ubuntu eee 8.04.1]("http://www.ubuntu-eee.com/") plus emifreq-applet for switching cpu to 900MHz.

---

### Post by albinootje on 2008-12-17
> **kbkntk said:**
> has anybody here got GDAM ([http://gdam.ffem.org/]("http://gdam.ffem.org/")) running on ubuntu hardy heron? i have some libary problems while trying to install it and can´t fix the problem. maybe someone can re-compile it for ubuntu? that would be great:), cause i don´t know how to do it.
there is also an old thread about this: [http://ubuntuforums.org/showthread.php?t=55684](http://ubuntuforums.org/showthread.php?t=55684) , but it doesn´t really help me. :(
i also tried mixxx ([http://mixxx.org/]("http://mixxx.org/")) as an alternative.... it´s great, too. but i do have some latency problems there and i think GDAM might be better for experimental DJ-ing, which i want to do...

Just looked at [http://gdam.ffem.org](http://gdam.ffem.org) and noticed that there are deb files, but.. 
The sentence "You should use at least "potato" (debian 2.2) or later for themes to work properly." rings a bell ;-)
Debian Potato is from before Debian Woody, which is before the current Debian Etch. In other words.. this is old stuff.

I downloaded one gdam deb package and files inside are from ... the year 2000.

I don't want to spoil the party, but if you really want to try this software you might end up running it with a really old Linux distribution on a dual-boot machine.

Another idea is to try a real-time kernel with mixxx.

GL!

---

### Post by kbkntk on 2008-12-17
thanks for the quick respond..... yes, GDAM is a little older. but the feature list is great. there is no software with the same complex editing features. i didn´t find any.
i didn´t know about the option with the realtime kernel. thanks for that hint. i try to check that out. i´m not sure, if i can use it, cause i´m running the kernel by [array.org]("http://array.org/ubuntu/") on an eeepc, which is an extra design for that machine. another kernel might lack of important features like LAN or soundcard driver etc.

---

### Post by Stochastic on 2008-12-18
It should be possible to install the RT kernel from the regular repos alongside the custom eee kernel and switch between them with GRUB.  You really do need the RT kernel to get good quality sound out of Ubuntu.

As for your library problems, can you post more details?  A great tool to use is apt-file.  If your compile error reads something like "cannot find file whassit.cpp" then just do ```
apt-file search whassit.cpp
``` and that will give a list of packages that contain whassit.cpp files.

---

### Post by kbkntk on 2008-12-18
thanks stochastic. :)     i think i´ll try the realtime kernel...... also good hint with the filesearch. this might be very usefull sometime.
but in this case the problem really is, that the missing libaries are too old. i think the names were libglade0 and libglib1.2. those have been replaced by other libaries in newer OS-distributions..... i already tried to install GDAM with different versions of ubuntu, xubuntu and even fedora9 (it doesn´t work with redhat, too). so it is like albinootje said. i would have to run an old debian linux, which i think is not that satisfying than the current ubuntu.

---

