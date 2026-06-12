---
title: "Gentoo64, have your cake and eat it too"
date: 2005-07-18
forum: The Cafe
---

### Post by vandal43 on 2005-07-18
Ok, I've become a convert, Ubuntu while being a great distro just doesn't have the package support on amd64 - don't get me wrong it was fun to try though. I've thus switched to Gentoo64 and I am able to run a native 64 bit OS and still take advantage of all the software that's 32 bit only sans any ugly chroot stuff. For example, I give you [this link](http://sh.nu/mplayer/), which gives you all the tools necessary to get mplayer (32 bit) up and running with all the win32 codecs in Gentoo64. You can also have your flashplayer, just emerge the 32 bit binary package firefox-bin. It works just like normal, no nasty chroot, no separate package repos, just nice and streamlined. I've come to the conclusion that Gentoo is really the only distro at this point that makes a 64 bit distro viable. I encourage anyone here who is tired of missing out on great functionality, but still wants a 64 bit OS, to check it.

[Gentoo](http://www.gentoo.org)

---

### Post by Terracotta on 2005-07-18
Well if it installed as easy as kubuntu does I'd switch, but it doesn't, I've read the manual several times, and you can call me a morron, but until the install doesn't become easier (no need to go too graphical, but as easy a kubuntu's install I mean), a lot of people will stay binary based :-).

---

### Post by endy on 2005-07-18
On [this](http://www.gentoo.org/main/en/philosophy.xml) page it's noted that they are looking towards a binary solution.

> 
At around the time Gentoo was born, the thing that got in the way was the lack of an easy way to build packages from source, to a user's specifications. Currently, we've done that very well, but what we haven't done very well is support pre-built packages, even though Portage has supported building binary packages almost since its inception. So we are doing that now.

It's important that our tools support binary packages, because binary packages are widely used and widely in demand in the Linux community. If our tools don't support binary packages, then we can't claim that our tools are designed to allow a user to do anything he or she might want to do. If we purposely choose to exclude binary support, then we are attempting to interfere with how users might choose to approach particular problems, by instead imposing our own will or view of how they should approach a problem. And if we do not build binary packages, then we are not taking any steps to ensure that our tools actually work well with binary packages, nor are we taking steps to ensure that others can build binary packages, nor are we able to *demonstrate* that our tools work well with binary packages. Besides these philosophical reasons, there are many practical reasons to create binary packages.


When they get there I'll certainly have another go of gentoo. I've done it all before but lost interest building everything from source, althought the gentoo way is good it just seems like the long way round. But yes, their 64bit support was rather good, but only if you like everything else that comes with the package.

---

### Post by Jet2k5 on 2005-07-18
Yeah I hear that too,  But well think about it Ubuntu is still a new distro.  AMD64's haven't been around for the longest and neither has Ubuntu.  I suggest you stick to what ever you have now and check Ubuntu out in the future.  I don't know what is going to be in store for us in Breezy.  I do hope to god that Ubuntu developers get rid of the chroot system.  It's a heck of a lot easier.  They should just include 64 and 32 bit repos.  Allowing you to download 32-bit programs while running 64-bit program.  Like they should have firefox32 or firefox64.  If you want to use flash obviously you would do something like *sudo apt-get install mozilla-firefox32 flash32* ... and so on.  

I hope that is the future.

---

### Post by Jet2k5 on 2005-07-18
[QUOTE=Jet2k5]Yeah I hear that too,  But well think about it Ubuntu is still a new distro.  AMD64's haven't been around for the longest and neither has Ubuntu.  I suggest you stick to what ever you have now and check Ubuntu out in the future.  I don't know what is going to be in store for us in Breezy.  I do hope to god that Ubuntu developers get rid of the chroot system.  It's a heck of a lot easier.  They should just include 64 and 32 bit repos.  Allowing you to download 32-bit programs while running 64-bit program.  Like they should have firefox32 or firefox64.  If you want to use flash obviously you would do something like *sudo apt-get install mozilla-firefox32 flash32* ... and so on.  

I hope that is the future.[/QUOTE]


Really?  I didn't see anything about 64-bit support on their Developer Notes for July ... must be something different.

---

### Post by BWF89 on 2005-07-18
> Ubuntu while being a great distro just doesn't have the package support on amd64 - don't get me wrong it was fun to try though. I've thus switched to Gentoo64 and I am able to run a native 64 bit OS and still take advantage of all the software that's 32 bit only sans any ugly chroot stuff
Mabye I read your post wrong but I thought that 32bit apps were 100% compatible with a 64bit processor.

---

### Post by TravisNewman on 2005-07-18
depends on the operating system. You have to set up a chroot jail to run a 32 bit firefox to get flash, for example, in Ubuntu 64. You can't run the 32 bit stuff natively in Ubuntu 64 bit. BUT you CAN install the 32 bit version on a 64 bit processor. It's not just the processor compatibility you have to factor in, it's the OS compatibility.

---

### Post by WildTangent on 2005-07-19
i tried gentoo a couple times. i eventually got sick of the rediculously long install process, and having to compile all my apps. KDE took 9 hours to compile!  ](*,)  :-x 

-Wild

---

### Post by TravisNewman on 2005-07-19
OOo was about a day for me.

---

### Post by poofyhairguy on 2005-07-19
[QUOTE=vandal43]Ok, I've become a convert, Ubuntu while being a great distro just doesn't have the package support on amd64 - don't get me wrong it was fun to try though. I've thus switched to Gentoo64 and I am able to run a native 64 bit OS and still take advantage of all the software that's 32 bit only sans any ugly chroot stuff. For example, I give you [this link](http://sh.nu/mplayer/), which gives you all the tools necessary to get mplayer (32 bit) up and running with all the win32 codecs in Gentoo64. You can also have your flashplayer, just emerge the 32 bit binary package firefox-bin. It works just like normal, no nasty chroot, no separate package repos, just nice and streamlined. I've come to the conclusion that Gentoo is really the only distro at this point that makes a 64 bit distro viable. I encourage anyone here who is tired of missing out on great functionality, but still wants a 64 bit OS, to check it.
[/QUOTE]

Suse is like that as well.

Ubuntu needs (and will probably always need, it will just get easier) chroot because of the way debian works.

The 64 bit Ubuntu and the 32 bit Ubuntu are two different OSes. Just like Debian Sarge and Potato are different OSes. You CAN install potato debs in Sarge...but they might not work.  You probably COULD force 64 bit Ubuntu to use the 32 bit binary debs, but they you would run into compatibility problems and apt-get breakage. As great as apt-get is...its has to keep its platforms separate.

Gentoo gets around this by compiling everything. Software has to be binary compatible on you system because it was compiled on your system. If I had a 64 bit chip, I would use Gentoo with a Ubuntu chroot.

---

