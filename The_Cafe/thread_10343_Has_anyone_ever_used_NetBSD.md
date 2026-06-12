---
title: "Has anyone ever used NetBSD?"
date: 2005-01-06
forum: The Cafe
---

### Post by BWF89 on 2005-01-06
I've been looking at into some BSD websites. Namely OpenBSD, FreeBSD, and NetBSD and it's pretty interesting. On NetBSD's website they have a full list of [every NetBSD package](ftp://ftp.netbsd.org/pub/NetBSD/packages/pkgsrc/README-all.html) ! AND IT'S ALL ON AN OFFICIAL SITE!

What are the main differences between Ubuntu and NetBSD? I think the deciding point on which OS I will install when I get a new partition or computer will be how you install programs. On Ubuntu when you download a program can you just click on an install file and have it install like Windows? How about on NetBSD...

Has anyone ever used a BSD distro? If so, what was your experince?

---

### Post by TravisNewman on 2005-01-06
BSD is what I would use if I had a box I wanted to make into a server. It's SOLID. I haven't used it in ages, so I don't know what kind of package management it has in general. I know that FreeBSD has some sort of package management where you basically have a database of makefiles and some other things so you just cd into the directory of the app you want to compile, execute a couple commands, and it compiles and installs it.

For a desktop system, I'd just stick to Linux.

---

### Post by jdong on 2005-01-06
Well, I've tried FreeBSD before on multiple occasions, but I still prefered Linux to it.

It was harder to configure -- not as user-friendly at the console as Linux is... But it's fast... unbelievably fast on old computers!

And yeah, ports (FreeBSD's source compilation tree that portage is based off) is wonderful. You cd into /usr/ports/directory, issue **make install**, and you're done. Issue **make uninstall** to remove.

---

### Post by BWF89 on 2005-01-06
[QUOTE=jdong]And yeah, ports (FreeBSD's source compilation tree that portage is based off) is wonderful. You cd into /usr/ports/directory, issue **make install**, and you're done. Issue **make uninstall** to remove.[/QUOTE]
For most of the programs all you have to do is put it into a directory and do a "make install-whateverfilename" command? THAT'S IT!

---

### Post by az on 2005-01-06
Just for kicks, if you want to play around with another unix, try the HURD.

There is a package called crosshurd that will install the hurd or bsd onto a partition for you.

Filename: pool/universe/c/crosshurd/crosshurd_1.6.3_all.deb

Description: Install a Debian system
 crosshurd uses apt and a bit of black magic to setup a functional
 Debian system. It supports the following target systems:
  - linux-gnu (GNU/Linux)
  - gnu (GNU)
  - kfreebsd-gnu (GNU/kFreeBSD)
  - knetbsd-gnu (GNU/kNetBSD)
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu

It depends on the way you see it.  Linux is just another unix kernel.  just like the bsd kernel.  GNU is the os (utilities and apps). GNU is another name for the HURD kernel (mach microkernel).

Anyway, look it up...

---

### Post by TravisNewman on 2005-01-06
BFW: Actually it's easier :) You don't even have to have the wahteverfilename. Just make install :) I'm not sure about dependency checking.

azz: sweet, I've been wanting to play with HURD.

---

### Post by kahping on 2005-01-06
i've been reading up on NetBSD myself. if i understood the site's explanations correctly, FreeBSD and OpenBSD got their package system from NetBSD. u just pkg_add <path_to_package_tgz> to install precompiled binaries and pkg_delete <path_to_package_tgz> to uninstall. 

if u want to compile from source, then just cd to /usr/pkgsrc/<package_name> IIRC, then make install to install; make deinstall to remove.

in both cases, dependancies are resolved automatically(just like .deb)

hope that helps

kahping

edit: corrections. btw, <path_to_package_tgz> can be a ftp URL or local path ;)

---

### Post by BWF89 on 2005-01-06
> u just pkg_add <package_name> to install precompiled binaries and pkg_delete <package_name> to uninstall. 
Sounds like BSD is allready ahead of most Linux distros  =P~

---

### Post by Rogee on 2005-01-07
If you want to try out FreeBSD, download FreeSBIE.  It's a liveCD based off FreeBSD that can also be installed to the hard drive.  It's also desktop oriented, as it come with XFCE and a number of programs.  It's very impressive.
[http://www.freesbie.org](http://www.freesbie.org)

I use FreeBSD at work, but only in a command-line environment, as we use it on our servers.  I've never used NetBSD, but would like to.

---

### Post by jdodson on 2005-01-07
[QUOTE=BWF89]I've been looking at into some BSD websites. Namely OpenBSD, FreeBSD, and NetBSD and it's pretty interesting. On NetBSD's website they have a full list of [every NetBSD package](ftp://ftp.netbsd.org/pub/NetBSD/packages/pkgsrc/README-all.html) ! AND IT'S ALL ON AN OFFICIAL SITE!

What are the main differences between Ubuntu and NetBSD? I think the deciding point on which OS I will install when I get a new partition or computer will be how you install programs. On Ubuntu when you download a program can you just click on an install file and have it install like Windows? How about on NetBSD...

Has anyone ever used a BSD distro? If so, what was your experince?[/QUOTE]

netbsd used to claim(or it claimed when i checked last, which was a few years ago) that it had the most ports of an os.  i have a diehard friend who is into netbsd because he can "install a system off a floppy drive."  whereas that is super-cool-o-rama, i am phasing out the floppy so that really doesnt matter to me anymore, plus tons-o-gnu/linux distros do that anyway.  

it seems to me on the surface bsds are pretty similar to gnu/linux.  they both utilize GNU tools and other free projects, gnome, kde, mysql, postgres, etc.  they both are free as in beer and freedom.  the kernels are different, and there are arguments for why one is better than the other.  i have always wanted to hack around on bsd, but never really got around to it.  i think i might checkout freesbie, perhaps even download it today :mrgreen:

---

### Post by tiiim on 2005-01-07
[QUOTE=BWF89] On Ubuntu when you download a program can you just click on an install file and have it install like Windows? How about on NetBSD...

[/QUOTE]


Ubuntu file system is .deb and IMHO far superior to say RPM or whatever. I dont know much about BSD but Ubuntu is easy to install you also have apt on Ubuntu which gives you access to like almost every major prog every at a click.

---

### Post by Dylanby on 2005-01-07
Being a 'nix newbie I've also been looking at installing one of the BSD's onto a spare hard drive.
Just for fun. I have no plans to replace Ubuntu as my main OS. ;)

My impression of NetBSD is that it's a very elegant & sophisticated OS. One thing to keep in mind is that although very mature, NetBSD doesn't have the developer resources that the Linux community possesses.

From their web site:
> Some systems seem to have the philosophy of *"If it works, it's right"*. In that light NetBSD could be described as *"It doesn't work **unless** it's right"*. 
Applies to some Linux distros too. Solutions, not hacks. A small example would be Ubuntu & their bootsplash stance.

I downloaded a mini iso for NetBSD & tried to install it on a old junker I have lying around. The thing has a flaky cdrom & no Linux distro has ever been able to boot from cd. NetBSD had no problems. I ran into some trouble setting up X & eventually decided to leave it for now & go back to it when I have more time (to read up on it) or when I'm more experienced.

One thing a really like is the FreeBSD handbook. It'd be great to have a Ubuntu handbook.

Whether you like Linux or BSD my experience has been that the more I try the more I appreciate the world of 'free software' as a whole. It's great!

---

### Post by BWF89 on 2005-01-07
I posted a similar topic on Linuxtimes.net and one guy (a Linux expert) said that "NetBSD is not a desktop OS"...

---

### Post by jdodson on 2005-01-07
ok well i downloaded freesbie and i have to say it was pretty cool.  they have fluxbox and xfce as the desktops.  fluxbox(the one i tried) was setup with a few gdesklets and was very, very slick.  

firefox, thunderbird, xterm, xchat, gaim, gimp, xwindows.

it pretty much seemed like what i was used to in gnu/linux cept a few things are not in the gnu/linux places, init.d for one.  beyond that it was not that alien at all, i expected more differences.  

i am downloading freebsd now to hack around with when i have some spare time.

---

### Post by Dylanby on 2005-01-07
*BWF89 wrote:*
> I posted a similar topic on Linuxtimes.net and one guy (a Linux expert) said that "NetBSD is not a desktop OS"... 

"Desktop" is very subjective. It's definitely a workstation OS.
Fact is there **are** people using NetBSD as a desktop. It's just a matter of preference.

I've been using Linux for a short time. I'm used to Ubuntu. I "know" Ubuntu (well, a little). I'm part of a community that also likes & uses Ubuntu. But if I had a neighbour or cousin or friend who used BSD & introduced me to it & was willing to mentor me in it, then that's probably what I'd be using right now. With most if not all of the same apps.

---

### Post by Quest-Master on 2005-01-07
I'm getting really interested in FreeBSD, but I highly doubt it will manage to pull me away from Ubuntu. Will still give it a swing though.

Btw, while looking through some of the FreeBSIE screens, I noticed it used XFCE. :D
XFCE is extremely awesome. It runs really fast, is small, lightweight, and pretty much perfect and customizable as well. :D

---

### Post by mark on 2005-01-07
If I'm not mistaken, isn't Gentoo's Portage based on the BSD ports packaging sytem?

---

### Post by TravisNewman on 2005-01-08
[QUOTE=mark]If I'm not mistaken, isn't Gentoo's Portage based on the BSD ports packaging sytem?[/QUOTE]
 See jdong's first post in the thread.
...
Yes it is :)

---

### Post by kahping on 2005-01-08
i'm thinking of trying NetBSD someday; even dual boot it with ubuntu(if possible), but it seems like *BSD uses UFS/FFS and linux doesn't seem to have support for these filesystems. anybody knows otherwise? i've been googling but can't find anything that confirms whether linux supports UFS/FFS reliably. 

same goes vice versa; i can't seem to confirm whether NetBSD supports any linux filesystem other than ext2fs.

while i'd prefer 1 PC == 1 OS, unfortunately, i don't have the money or living space for more than 1 PC, so dual/multi boot seems my only option if i want to explore various open source OS solutions :(

kahping

---

### Post by BWF89 on 2005-01-08
Kahping: Ask your question [here](http://www.freebsdforums.org/forums/) ...

---

### Post by tiiim on 2005-01-08
[QUOTE=BWF89]Kahping: Ask your question [here](http://www.freebsdforums.org/forums/) ...[/QUOTE]
 so the big question is: what is the future of OSes? Linux or FreeBSD? 

A personal question: How user friendly is BSD compared to Linux and how similar are the file systems?

---

### Post by BWF89 on 2005-01-08
[QUOTE=tiiim]so the big question is: what is the future of OSes? Linux or FreeBSD? 

A personal question: How user friendly is BSD compared to Linux and how similar are the file systems?[/QUOTE]
The future of OS's is Linux...

I don't think BSD is as user friendly as Linux because it uses more commandline. I didn't know this when I posted the topic so I'll probably stick with Linux...

---

### Post by jdodson on 2005-01-08
[QUOTE=tiiim]so the big question is: what is the future of OSes? Linux or FreeBSD? 

A personal question: How user friendly is BSD compared to Linux and how similar are the file systems?[/QUOTE]

the future is whatever you use.  whatever is more supported by vendors?  well right now i would say gnu/linux, though nvidia and unreal tournament both support BSD.

---

### Post by deception on 2005-01-08
As jdong knows, I have tried FreeBSD in the past week. I, for some reason, liked to install X and Gnome / KDE myself. Configuring X with xorgconfig was my first experience with it too. 

I kept getting errors when compiling things like xine, and firefox had issues that I didn't have the time to work on. Ports was easy enough to use, and the handbook is fantastic. 

The stablility and speed of the system was overall excellent. 

I prefer Linux though, especially Ubuntu, and am now posting from Ubuntu after removing FreeBSD. I will someday go back to a BSD, whether that's FreeBSD or another variant I'm not sure. But when I set up a server, it will most probably be with a BSD. That's not to say it's not good for a workstation, on the contrary, but at this present time it just isn't what I'm looking for. 

Ubuntu is  ;-)

---

### Post by tiiim on 2005-01-08
[QUOTE=deception]As jdong knows, I have tried FreeBSD in the past week. I, for some reason, liked to install X and Gnome / KDE myself. Configuring X with xorgconfig was my first experience with it too. 

I kept getting errors when compiling things like xine, and firefox had issues that I didn't have the time to work on. Ports was easy enough to use, and the handbook is fantastic. 

The stablility and speed of the system was overall excellent. 

I prefer Linux though, especially Ubuntu, and am now posting from Ubuntu after removing FreeBSD. I will someday go back to a BSD, whether that's FreeBSD or another variant I'm not sure. But when I set up a server, it will most probably be with a BSD. That's not to say it's not good for a workstation, on the contrary, but at this present time it just isn't what I'm looking for. 

Ubuntu is  ;-)[/QUOTE]
 I was reading about BSD seems pretty good.

But then again maybe several years time the GNU/Hurd may cause a strong alternative... who knows....

---

### Post by jdong on 2005-01-08
With the recent local-root vulnerability (which I can't reproduce on Ubuntu, btw), I'm getting seriously worried about providing public services with Linux systems. I really want to make testing BSD distros on my priorities list.

That's it -- I'm rewriting my new year's resolution.

---

### Post by kahping on 2005-01-09
[QUOTE=BWF89]Kahping: Ask your question [here](http://www.freebsdforums.org/forums/) ...[/QUOTE]

thanks, BWF89. i think i'll browse the bsd forums first. :P

kahping

---

