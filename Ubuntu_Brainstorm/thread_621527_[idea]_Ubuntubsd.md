---
title: "[idea] Ubuntubsd"
date: 2007-11-23
forum: Ubuntu Brainstorm
---

### Post by puccaso on 2007-11-23
i have to admit, freebsd is damned fast.
i have 1g memory, and gutsy uses about 300g idle
but freebsd uses 100m!!!! it is so tight and so secure.. 



how do we get all the ubuntu goodness ontop of bsd?


OK: EDIT.. I GOT DEBIAN/KFREEBSD installed in virtualbox. 

how would i go about seeing if ubuntu works on here as apposed to debian?? 

what packages would be best to test

im going to try the following

samba
avahi
pidgin
xorg
nautilus
firefox/epiphany
(they're the only things i really use)

---

### Post by smartboyathome on 2007-11-23
Recompile all the programs to run on BSD. There is no other way, as Ubuntu is compiled for the Linux kernel, while BSD is a separate kernel. Also, it could be the fact that Gutsy DOES use tracker and compiz (which takes up a lot of idle CPU),

---

### Post by puccaso on 2007-11-23
its not gutsy or compiz.. 
this is just base level stuff..

there is avaliable the kbsdsource or something,
its the kernel that gnu/bsd uses.. 

gnu/bsd (if i recall correctly)
is bascially a debian system built over the netbsd kernel..

if the debian guys have done it - 
we should try :) cos whatever debian does - ubuntu does better.

---

### Post by dips_xe on 2007-11-23
once you get all the "ubuntu-goodness" on bsd, it's idle is gonna be around 300.

---

### Post by puccaso on 2007-11-23
bare in mind, this idle is basicaly with desktopbsd - which uses freebsd annd kde..

for some reasons, the bsd guys listen to linus and dont like gnome ( so it seems ) 

and kde is just so ugly.. urgh

---

### Post by smartboyathome on 2007-11-24
> **puccaso said:**
> its not gutsy or compiz.. 
this is just base level stuff..

there is avaliable the kbsdsource or something,
its the kernel that gnu/bsd uses.. 

gnu/bsd (if i recall correctly)
is bascially a debian system built over the netbsd kernel..

if the debian guys have done it - 
we should try :) cos whatever debian does - ubuntu does better.

Yes, debian HAS done it, but you can't use normal Ubuntu distros with it since they are compiled for Linux's kernel and not BSD's. This leads to a lot less packages for BSD.

---

### Post by puccaso on 2007-11-24
i dont care about the amount of packages
i think the idea of having 16k+ packages is just a selling point
but i use pidgin, and firefox. nothing else is really important to be honest.

it has to work, not crash, not get stuck, not slow down..

---

### Post by smartboyathome on 2007-11-24
Ok, then. Compile the BSD kernel, compile a desktop environment on top of it, and then compile the programs you want. Right now, I don't think there is a better way.

---

### Post by mangar on 2007-11-25
bsd can run linux binary natively - both are posix-like systems, bsd supports elf)

---

### Post by tgoose on 2007-11-25
> **puccaso said:**
> i dont care about the amount of packages
i think the idea of having 16k+ packages is just a selling point
but i use pidgin, and firefox. nothing else is really important to be honest.

it has to work, not crash, not get stuck, not slow down..

Then why Ubuntu? You can run Pidgin and Firefox on a BSD anyway; since adding all the Ubuntu packages will only slow it down and you don't need the advantages that Ubuntu comes with, you can just use a BSD completely!

---

### Post by mellowd on 2007-11-25
When installing FreeBSD you can allow it to run linux binaries. Your milage may vary though.

---

### Post by puccaso on 2007-11-25
thats actually a good question
mmmmmmmm

why am i on ubuntu?

---

### Post by tjagoda on 2007-11-25
Perhaps because of the massive community and huge developer base?

---

### Post by loa on 2007-12-04
I think hardware support is better in Linux also.

What is using all those 300m is not the kernel, the kernel itself is quite small. If you count only the kernel code, it sits in at just 2015 kb (dmesg |grep Memory), but around 20m extra for other info. What takes up all that memory is the user-space applications, and those would be exactly the same if Ubuntu was to use the freebsd kernel. Perhaps you would save a few megs, but not much more.

Maybe the freebsd memory management is better, which would make the system perform better under memory pressure, but that won't in any way affect how much memory is consumed, just the managing of that consumed memory.

---

### Post by maybeway36 on 2007-12-04
I wish someone would make an easy-to-use package manager for BSD. I really miss APT when I use systems that aren't based on Debian or Mandriva.

---

### Post by zachtib on 2007-12-06
> **maybeway36 said:**
> I wish someone would make an easy-to-use package manager for BSD. I really miss APT when I use systems that aren't based on Debian or Mandriva.

have you used FreeBSD's ports?

I just installed FreeBSD for the first time yesterday, and I'm having no trouble at all installing software using ports.

---

### Post by puccaso on 2007-12-06
you see the reason i asked about ubuntubsd is because of the ubuntu philosophy.. 

linux is good, its secure and stable but ubuntu does it best.. 

now bsd, its better then linux and more secure and more stable - so ubuntu could make it go WOW..

---

### Post by maybeway36 on 2007-12-08
Ports are a nightmare in PC-BSD. I'll burn a netboot FreeBSD 7 image when it comes out - I think I can just install Xorg and KDE, right?

---

### Post by puccaso on 2007-12-09
yep
x11 and kde would be fine
although i use gnome - but it seems that the bsd guys prefere kde over gnome.

i have to admit - there are some compatability issues
i know how to deal with sources in linux but bsd is a tad confusing.. i wanted to try gentoo/bsd but its not getting any development done really
i may have to try out the debian/bsd hybrid to see how it works.. 

but whatever works in bsd - works better then it does in linux..

---

### Post by puccaso on 2007-12-09
and

we have a friggin ps3 ubuntu live cd for gods sake
why dont we have a ubuntu/bsd cd :@ grr

---

### Post by marsmissionaries on 2007-12-09
Here is the beauty of linux: Every linux distribution is essentially the same except they all have different packages installed (the kernels have different patches as well).

So basicly: compile a BSD kernel, and then compile all of the packages ubuntu has, and there you have it: the ubuntu package base on a bsd kernel.

---

### Post by maybeway36 on 2007-12-09
Easier to just get Debian GNU/kFreeBSD.

---

### Post by puccaso on 2007-12-09
could i get debian gnu/kfreebsd ontop of ubuntu somehow? in virtual box or - or maybe in a chroot?

---

### Post by maybeway36 on 2007-12-10
Possibly. Regular old FreeBSD has problems with VirtualBox (namely Xorg -configure causes a crash.)

---

### Post by puccaso on 2007-12-15
ok
so i got debian/kfreebsd working on virtualbox. although X -configure doesnt work dpkg-reconfigure xserver-xorg does work.. 

installed xdm to install all other xorg deps.

now im install prevu and i put the gutsy deb-source into source.list.. 

lets see how it goes.

---

### Post by puccaso on 2007-12-15
ok
prevu installs

but prevu-unit requires lsb_release binary to tell it what it is building against
and lsb_core required libc6 and some other nonsense..

does anyone know how (using gentoo's terminology) inject libc6 into the dpkg db?/

---

