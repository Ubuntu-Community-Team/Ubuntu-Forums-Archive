---
title: "How much faster is Gentoo?"
date: 2006-01-09
forum: The Cafe
---

### Post by curuxz on 2006-01-09
So compared with Ubuntu how much faster is Gentoo, dont get me wrong I love ubuntu and use it as my only os but I want to play around with something else while not working, I installed gentoo a few years back on an old lappy and did not find it very good but would be willing to give it a try on my 3.2 64bit amd to see if there is a speed boost.

Worth the time installing?

---

### Post by Stormy Eyes on 2006-01-09
It depends entirely on what options you use when compiling. I used to use Gentoo before I switched to Ubuntu, and Ubuntu doesn't seem to be slower than Gentoo.

---

### Post by otake-tux on 2006-01-09
I used gentoo for a year.  I have been sing ubuntu for 2 months, I think.  I see no difference in speed.  

wait gentoo is faster than ubuntu booting up.  Especially if you're using the normal Ubuntu boot-up.  This can be modified with initng though.

the main difference between gentoo and ubuntu is not speed. Its package managment.  Gentoo always gets the latest faster than any other distro.  The downside is, nothing is done for you.

For example, recently I got pissed with ubuntu and decided to go back to gentoo.  Well I installed it off the live-cd, finished it in a day.  Then when I decided to check my battery (installed it on a laptop) no battery monitor.  It didnt include  battery support on the kernel.   I thought it would do that itself since I installed from CD and all other live-cd's seem to detect that its a laptop theyre running on and include the battery in kernel.  Gentoo failed to do this.  While the solution is simple (reconfigure the kernel and recompile) its just one example of troublesome things that you have to do.  It sucks having to go back after 10 hours of compiling and installing the operating system to recompile the kernel becuase of battery support.  Especially when Ubuntu does this kind of thing for you.

---

### Post by adi-beg on 2006-01-09
Hi.

It depends on what use you want with gentoo. It depends on your compile options. It depends on your internet connection. And so on...

I use gentoo at my home laptop. But here at internetcafe (which is free to use!), I'm administrator, and I prefer ubuntu. Takes less time to install and to customize to meet needs of users. In just a couple of days, I can install and customize more than ten computers when using ubuntu. If I used gentoo, I would need a couple of month (which I don't have).

If you have a lot of time to spend, it's worth it because of learning about linux. That's why I use gentoo at home.

Good luck!

---

### Post by GeneralZod on 2006-01-09
I noticed absolutely 0 speed increase and, for some reason (very probably something I did wrong :)) my gentoo install actually ended up being twice as large as any other install of Linux I've ever had (>7GB vs ~3.5GB).  

It's a very interesting distro, though, and nice if you want to get easy access to lots of up-to-date apps, all located in the same repository.

---

### Post by prizrak on 2006-01-09
Gentoo is not any faster than Ubuntu. In fact just about all Linux distros run at the same speed, they do use more or less the same kernel after all. The biggest speed difference that you will see in Linux distros will come from the GUI you use, fluxbox will be quick, GNOME/KDE will be pretty slow. If you run it CLI only it will flyyyyyy :)

---

### Post by Sheinar on 2006-01-09
Gentoo was a lot faster for me booting up, but that was because I only picked the options I needed to be loaded at boot. Ubuntu can be just as fast if you get rid of the options you don't need. When it comes to actually running apps, I didn't notice any difference in speed.

---

### Post by curuxz on 2006-01-09
KK thanks all :) ill stick with just ubuntu me thinks :) may try making my old 700mhz laptop lighting quick, tho its an IBM I1300 and hence a bitch to install linux on :( would be greatfull if any speed junkies know any tips to make a laptop look cool and do 2d tasks rapidly on old hardware with only 128m ram

---

### Post by poofyhairguy on 2006-01-09
[QUOTE=curuxz]KK thanks all :) ill stick with just ubuntu me thinks :) may try making my old 700mhz laptop lighting quick, tho its an IBM I1300 and hence a bitch to install linux on :( would be greatfull if any speed junkies know any tips to make a laptop look cool and do 2d tasks rapidly on old hardware with only 128m ram[/QUOTE]


Honestly my first tip is to buy some RAM. No modern OS wants to run in that amount. Ubuntu would FLY if you were closer to 512. I mean it. You could not imagine the difference.

If you don't wanna, use XFCE. Really. I would have to with that much RAM. it would kill me to use Gnome.

---

### Post by prizrak on 2006-01-09
[QUOTE=curuxz]KK thanks all :) ill stick with just ubuntu me thinks :) may try making my old 700mhz laptop lighting quick, tho its an IBM I1300 and hence a bitch to install linux on :( would be greatfull if any speed junkies know any tips to make a laptop look cool and do 2d tasks rapidly on old hardware with only 128m ram[/QUOTE]
XFCE or Fluxbox for your GUI would make it snappier.

---

### Post by erikpiper on 2006-01-09
Do NOT use KDE or GNOME. Use XFCE or something even lighter.

Install correct kernel for optimum speed. Most noticable on old machines, only a tiny increase, but why not? In synaptic, linux-i686.. K7 for AMD.. Etc.

Read the howtos for tips

Have fun!

---

### Post by BSDFreak on 2006-01-09
The flags beyond -O2 don't really make any difference and can in some cases even make the system slower so the benefits of compiling your entire system are questionable at best. 

If you want to optimize anything then start with the distro of your choice, download the kernel sources (either via apt or the latest from kernel.org) and compile your own kernel, it's the one thing that does make a noticeable difference. (as Sheinar said, bootup speed can be reduced a lot by removing unneeded hardware/filesystem/software support and it's quite possible to tune the system by changing certain key values). Compiling your own kernel isn't very hard but it usually takes trial and error so keep your known working kernel in the grub menu until you are certain your new kernel works as it should. There is zero risk if you follow that advice.

If you want better overall system speed then install FreeBSD instead, the difference really is huge, even with a newer computer.

---

### Post by prizrak on 2006-01-09
[QUOTE=BSDFreak]The flags beyond -O2 don't really make any difference and can in some cases even make the system slower so the benefits of compiling your entire system are questionable at best. 

If you want to optimize anything then start with the distro of your choice, download the kernel sources (either via apt or the latest from kernel.org) and compile your own kernel, it's the one thing that does make a noticeable difference. (as Sheinar said, bootup speed can be reduced a lot by removing unneeded hardware/filesystem/software support and it's quite possible to tune the system by changing certain key values). Compiling your own kernel isn't very hard but it usually takes trial and error so keep your known working kernel in the grub menu until you are certain your new kernel works as it should. There is zero risk if you follow that advice.

If you want better overall system speed then install FreeBSD instead, the difference really is huge, even with a newer computer.[/QUOTE]
You and your BSD :)

---

### Post by Lovechild on 2006-01-09
It largely depends you can tweak Gentoo is quite significant ways to decrease boottime and such. As for pure application speed there's hardly any real difference, if you use Gentoo you probably will benefit more from the sheer number of easily installable applications in Portage than the speed increase.

That being said compiler and linker tricks can benefit vastly in some general cases, I for one, like being able to determine that applications be build with -Os in an effort to study the effects of cache misses and less IO required when loading. It seems promising as prior studies have shown.

The best part and possibly also the worst part about Gentoo is that there's no default application set - I don't much like OpenOffice e.g. I feel that AbiWord is superior as is GNUmeric for my needs at least. So I can have a setup what has only support for the hardware and software I want. This also means I miss out on some of the nice things in distros like Ubuntu, a predefined and polished desktop and a system that will work even if I switch hardware between boots (since I might have stripped that from the kernel).

---

### Post by donjuan on 2006-01-09
I just have to point you guys to some funny stuff that this thread reminded me of due to the misconception that the main point of Gentoo is speed:
[http://www.funroll-loops.org/](http://www.funroll-loops.org/)
[http://bugs.gentoo.org/show_bug.cgi?id=74072](http://bugs.gentoo.org/show_bug.cgi?id=74072)
[http://forums.gentoo.org/viewtopic-t-309752.html](http://forums.gentoo.org/viewtopic-t-309752.html)

---

### Post by poofyhairguy on 2006-01-09
[QUOTE=prizrak]You and your BSD :)[/QUOTE]

Thats what I was thinking. I'm so glad the forum has a BSD fan!

---

### Post by BSDFreak on 2006-01-09
[QUOTE=prizrak]You and your BSD :)[/QUOTE]

Hehe, well it fits well in this discussion especially since you can either install the binary packages or build your world, it's fairly easy to do too, make buildworld && make buildkernel && make installkernel and reboot, log in as single user, run mergemaster-p && make installworld && mergemaster, reboot again and you have rebuilt your entire world, doesn't take several days either, takes a couple of hours on a sempron 2300.

I would really like to push harder for OpenBSD but i'm afraid that anyone who tries OpenBSD as their first BSD will get scared away. ;)

---

### Post by prizrak on 2006-01-09
[QUOTE=BSDFreak]Hehe, well it fits well in this discussion especially since you can either install the binary packages or build your world, it's fairly easy to do too, make buildworld && make buildkernel && make installkernel and reboot, log in as single user, run mergemaster-p && make installworld && mergemaster, reboot again and you have rebuilt your entire world, doesn't take several days either, takes a couple of hours on a sempron 2300.

I would really like to push harder for OpenBSD but i'm afraid that anyone who tries OpenBSD as their first BSD will get scared away. ;)[/QUOTE]
Yes yes they will, I tried it as my first BSD the install was a breeze ^_^ and all the hardware got recognized but then I had no clue how to use despite Linux experience so no BSD for me :)

---

### Post by BSDFreak on 2006-01-09
[QUOTE=prizrak]Yes yes they will, I tried it as my first BSD the install was a breeze ^_^ and all the hardware got recognized but then I had no clue how to use despite Linux experience so no BSD for me :)[/QUOTE]

Yeah the learning curve is very steep if you want to be able to use it as anything else than a security box.

You are one of the very few who actually think that the installation of OpenBSD is a breeze though, i agree with you completely, it's straightforward and you don't really have to do much more than press enter to install it but somehow people find it hard anyway.

---

### Post by DigitalAxis on 2006-01-10
In my experience, any speed increase in Gentoo has been due to finer control over WHAT is running.  Gentoo might be faster, but it's probably not a noticeable difference; most other distros already include the most important optimizations too.

Gentoo is built to be tweaked and configured, and by that I don't mean Cflags.   (Too much playing around that way and you get immortalized on Funroll-loops, and sometimes yelled at by developers when you ask for help and reveal you're running things known to break systems. (Little known fact: Many Gentoo packages actually filter out some of the more outrageous optimizations so packages will compile).)

I sorta administrate a Pentium II 333Mhz system.  It runs XFCE4, OpenOffice, Gaim, Firefox and various sciency UNIX programs that are its reason for existing...  It's lightweight, and competitively fast compared to the Pentium 4 1.9 GHz systems next to it, that apparently run tons of spyware and big-brotherware.  (I'm not sure what's wrong with them since they seem to be just as fast as the Pentium III 500Mhz machines they replaced.)

---

### Post by BSDFreak on 2006-01-10
[QUOTE=DigitalAxis]In my experience, any speed increase in Gentoo has been due to finer control over WHAT is running.  [/QUOTE]

Please expand on this.

---

### Post by curuxz on 2006-01-11
Well im more than expereinced enough to give BSD a try, (having built several LFS and Gentoo systems before). But what are the advantages over ubuntu? is bsd faster, if so i take it your recommending openbsd?

---

### Post by tseliot on 2006-01-11
[QUOTE=curuxz]Well im more than expereinced enough to give BSD a try, (having built several LFS and Gentoo systems before). But what are the advantages over ubuntu? is bsd faster, if so i take it your recommending openbsd?[/QUOTE]
I've tried FreeBSD 6.0 and it's fast as hell.
AFAIK OpenBSD is slower than FreeBSD as it's more concerned with security. I've never tried OpenBSD so if what I'm saying is wrong, please correct me.

---

### Post by ssam on 2006-01-11
i had a quick play with gentoo on my mini itx computer. i used -Os as the C3 chips has a tiny cache
* boot is very fast. i did not install init-ng (unless it is installed by default). i think having a kernel with only what i need in it helped.
* software version were not as new as i expected. the repos contain several versions of each package, and they are marked stable or testing for each architecture. although there are some new packages, they are not marked stable. no gcc 4 (see below) [http://packages.gentoo.org/packages/?category=sys-devel;name=gcc](http://packages.gentoo.org/packages/?category=sys-devel;name=gcc) , you'd expect the gentoo people to be early adopters of gcc4, but i imagine its very hard to do the transision on a running system.
* it seemed like a very good system for experimenting with non standard set ups. i hope some of the ubuntu devs play with it occasionally.

i imagine with not too much work apt could be made to download the source debs and compile them with different options. you could do something like
apt-get build --flags="-O2" xine
that could keep tweakers happy. (does this already exist?)

---

### Post by curuxz on 2006-01-11
well i will try out freebsd on my pc see what happens, tho i realy dont wana leave the world of ubuntu since its nice here :)

---

### Post by BSDFreak on 2006-01-11
[quote=tseliot]I've tried FreeBSD 6.0 and it's fast as hell.
AFAIK OpenBSD is slower than FreeBSD as it's more concerned with security. I've never tried OpenBSD so if what I'm saying is wrong, please correct me.[/quote]

No, you are quite correct, OpenBSD's focus is security, it's a great OS for critical tasks, i'd even say it's the best OS for that.

FreeBSD is desktop oriented, it has great hardware support and it is built to be fast on the desktop and that it most definently is, it's still one of the safer OS's, definently better than Linux in that regard. 

The BSD's differ from most Linux's (the exception being Slackware) in file system hierarchy and init (Ubuntu using SysV based init and BSD and slackware using BSD based init) which is something you'll have to learn to work with, you'll have to edit the files directly. The way things are partitioned in BSD is like having one extended partition, or "BSD slice" and then separate labels within that partition, most common is /, /usr, /var, /home and of course, a swap partition. The partition MUST be a primary partition, you can't put it as a logical partition within an extended partition.

All in all, for FreeBSD [http://www.freebsd.org/doc/en_US.ISO8859-1/books/handbook/](http://www.freebsd.org/doc/en_US.ISO8859-1/books/handbook/) will tell you what you need to know to install and setup FreeBSD.

---

### Post by BSDFreak on 2006-01-11
> **ssam]i had a quick play with gentoo on my mini itx computer. i used -Os as the C3 chips has a tiny cache
* boot is very fast. i did not install init-ng (unless it is installed by default). i think having a kernel with only what i need in it helped.
* software version were not as new as i expected. the repos contain several versions of each package, and they are marked stable or testing for each architecture. although there are some new packages, they are not marked stable. no gcc 4 (see below) [URL="http://packages.gentoo.org/packages/?category=sys-devel said:**
> http://packages.gentoo.org/packages/?category=sys-devel;name=gcc[/URL] , you'd expect the gentoo people to be early adopters of gcc4, but i imagine its very hard to do the transision on a running system.
* it seemed like a very good system for experimenting with non standard set ups. i hope some of the ubuntu devs play with it occasionally.

i imagine with not too much work apt could be made to download the source debs and compile them with different options. you could do something like
apt-get build --flags="-O2" xine
that could keep tweakers happy. (does this already exist?)

That would compile xine with the same flag that it's compiled with in the deb. In every comparison i have seen comparing Debian and Gentoo the difference has either been none or negligable in either direction.

From the Ubuntu Faq:

> 
Do you provide **packages** **compiled** with processor-specific optimisations?  Where can I find them?
          [LIST]
[*] Optimised kernels can be obtained by installing the linux-686, linux-k7, etc. **packages**.  Search for "linux" with Synaptic, aptitude or apt-cache.
[*] An optimised C library is installed by default, in the libc6-i686 **packages**.
[*] Optimised cryptography routines for i586- and i686-class systems are included with the OpenSSL library and used automatically
[*] Ubuntu **packages** are generally built with nearly all generic compile-time optimisations which do not involve increasing code size (gcc -**O2**), except where the package maintainer deviates from this (for example, **packages** intended for debugging are often less optimised, as this eases debugging). Smaller code allows better utilisation of cache memory.
[*] Ubuntu **packages** for the i386 architecture are **compiled** using the i486 instruction set (-march=i486), with instruction choices based on the Pentium 4 processor (-mcpu=pentium4).  This combination provides benefits for modern processors without sacrificing compatibility with older and embedded devices.[/LIST]

---

### Post by DigitalAxis on 2006-01-16
@BSDfreak
  The control I refer to (at least as far as I've used it) is that you have to basically tell Gentoo what you want to install (the base system is minimal; they tell you how to customize the default USE flags during the install; even the core GNU utilities are replaceable) so you can install as little or as much software as you want.  I have no doubt that Debian (or even Ubuntu) will also let you do that if you really want to, but Gentoo's designed to be built from the bottom up.  Call it a flaw or a feature if you want.

The other feature is USE flags.  You can enable and disable optional support for features.  That slow machine has no soundcard, so I told it not to compile any programs with the optional alsa, oss or esd (where available) support; this reduces dependencies.  Similarly, GTK+ programs tend to have options to install for Gnome libraries or just normal GTK+; since that thing uses XFCE4 I can have it not add Gnome integration.  Again, I would be surprised if there weren't any Debian utilities to do something like that, but that isn't Debian's (or Ubuntu's) main focus.

Mostly it's the first reason cited though; you have control over the software you installed because Gentoo prides itself about being about choice.

These features, naturally, mean there's no such thing as a standard Gentoo install, which does add complexity to troubleshooting.  I suspect that has a lot to do with Gentoo's Q&A reputation.  I was luckier than some, less lucky than others in that regard.

@ssam
  InitNG's not standard, yet.

---

### Post by BSDFreak on 2006-01-17
[quote=DigitalAxis]@BSDfreak
  The control I refer to (at least as far as I've used it) is that you have to basically tell Gentoo what you want to install (the base system is minimal; they tell you how to customize the default USE flags during the install; even the core GNU utilities are replaceable) so you can install as little or as much software as you want.  I have no doubt that Debian (or even Ubuntu) will also let you do that if you really want to, but Gentoo's designed to be built from the bottom up.  Call it a flaw or a feature if you want.

The other feature is USE flags.  You can enable and disable optional support for features.  That slow machine has no soundcard, so I told it not to compile any programs with the optional alsa, oss or esd (where available) support; this reduces dependencies.  Similarly, GTK+ programs tend to have options to install for Gnome libraries or just normal GTK+; since that thing uses XFCE4 I can have it not add Gnome integration.  Again, I would be surprised if there weren't any Debian utilities to do something like that, but that isn't Debian's (or Ubuntu's) main focus.

Mostly it's the first reason cited though; you have control over the software you installed because Gentoo prides itself about being about choice.

These features, naturally, mean there's no such thing as a standard Gentoo install, which does add complexity to troubleshooting.  I suspect that has a lot to do with Gentoo's Q&A reputation.  I was luckier than some, less lucky than others in that regard.

@ssam
  InitNG's not standard, yet.[/quote]

Well, i wouldn't have asked you to expand on it if you didn't say "finer control over what is running". I still don't understand how you have better control over what is running with Gentoo, over what is installed, ok, but then again you have hundreds of distros where you do have that (most notable Slackware, Rock Linux and Arch Linux) but is there anything special in Gentoo that gives you finer control over what is *running*, in my experience the init files are about the same in all SysV init systems and just as easy (or hard, i HATE SysV init) to manipulate.

---

### Post by gamma on 2006-01-27
I literally just switched to Kubuntu this week after using Gentoo for the last 4 years. I had a highly optimized kernel with the bare minimum of things I needed. I also had a optimized set of USE flags and pretty decent CFLAGS. I ran reiser4 because it had the best performance to offer. I actually think KDE runs faster in Kubuntu than it did when I was using Gentoo. Also I don't have to wait a day for KDE to compile, and everything works from the start with Kubuntu.

Portage, Gentoo's package system, needs some optimization since more and more packages have been added since launch. Sync used to take about 5mb of space, but now has gotten up to 120MB of data. emerge -s and emerge --sync are very slow and unoptimized. They were great when I started using Gentoo and there weren't many packages, but now it's horrible.

---

### Post by TechSonic on 2006-01-27
This whole discussion makes me glad I went with Ubuntu.

Although, FreeBSD does interest me now more then ever.  I have some old worn down 500mhz computers stacked in parts in my cabnets.  I'll pull them down and fit me an old Drive on one and Tinker with FreeBSD and see how it works.  But even if it is faster or easy to use, I still do not believe I will switch my main computer over.  I'll continue using Ubuntu, reguardless of how easy another distro/unix os may be.

You don't learn anything from going stright the easy way.  Take things the in the way that you can learn and keep you're mind active.  I belive Linux instead of Windows for me is a good thing.  I keeps me guessing, it keeps me from wasting my brain.  I want to learn things the hard way, sort of speak.  Plus, on Linux/BSD/"Unix" in general are unlimited to their abilities.  Even things that have not been thought of, can be done.  The sky was the limit on Windows, but on Linux it is even further.  Not even Saturn (the planet) is the limit.)

I believe that in the future, Linux will make more things possible.  The improvement of our lives and evolution, depend on it.

Who knows, maybe the first computer to improve medical standards to help save more lives, will be done on a Linux operating system.

---

### Post by Gotterdammerung on 2006-09-26
At home, Ubuntu seems faster and smoother, but I have never learn so much about linux than when I turned to Gentoo.

Now I'm tired of spending too much time compiling my system. So I turned to Ubuntu.

BTW, glxgears runs very smoothly now with the very same hardware.

---

### Post by jharr on 2006-09-26
I'm pretty sure the performance advantages are somewhere along the lines of 1%. I've heard of people claiming 10%, but that's for a specific application.

Here's some food for thought though:
A guy told me (just today) that it took 10 days for him to compile openoffice. If that gives you a 10% CPU advantage, and you use openoffice for 5 hours a day, averaging 15% CPU load, you'll have to use it in that manner for about 667 days to reep the benefits of recompiling it.

If you're running 1000 homogeneous workstations (and lets face it, if you're running 1000 workstations, you're probably using windows. No offense to idealists), it might make sense to do it this way. You still have to ask yourself if it is worth the extra effort to maintain/update the packages that way. Compiling from source is a sure fire way to lead to uncovering bugs that no one else has. Binaries make more sense for most people because they've been tested widely.

</rant> ;)

---

### Post by interzoneuk on 2006-09-28
I have been using Gentoo for 6 about months and am now using it as my main desktop - instead of Suse.

I did use kubuntu for a while but to be honest it did seem slower in general than arklinux,suse,etc so i stopped using it, I did love the apt-get package management for simplicty but it is no better than smart on suse - Gentoo's portage is mind boggingly customisible.

After a few attempts of configuring gentoo I now have a really nice speedy desktop.

As a guide here is the Doom3 benchmark on my machine on 3 different O.S's
(machine = AthlonXP 3000 - nvidia geforce 4200 - timedemo-1 800x600 med detail)

(this is with the same nvidia driver version)

Kubuntu 6.06 : 28.2 fps
Suse 10.1 : 30.6 fps
Gentoo : 32.1 fps

Although 4 fps does't seem like much it is a bit noticable.

Also the speed of KDE in gentoo (after recompiling it to my system with hiddenvisibilty) is faster than all other OS's i have tried.

My 2 cents !

---

### Post by Gotterdammerung on 2006-09-29
> **BSDFreak said:**
> Well, i wouldn't have asked you to expand on it if you didn't say "finer control over what is running". I still don't understand how you have better control over what is running with Gentoo, over what is installed, ok, but then again you have hundreds of distros where you do have that (most notable Slackware, Rock Linux and Arch Linux) but is there anything special in Gentoo that gives you finer control over what is *running*, in my experience the init files are about the same in all SysV init systems and just as easy (or hard, i HATE SysV init) to manipulate.

I don't know BSD enough to compare, but Debian & Sons does not provide you an option to install a specific version of a package, or to install a package without its dependencies, for example. Gentoo lets you do it.

Gentoo is really about choice. You choose everything in your system, from bottom to top, since your kernel modules and the way you want to compile them (kernel CFLAGS), etc files, to the way each and every package should be compiled on your system, choosing even if you want part of the packages from unstable (masked or ~arch) and the rest from stable.

The way of Gentoo gives you a lot of knowledge on how your system behaves, since you get to know every part of it. Far too different from bin pack distros.

---

### Post by Reshin on 2006-09-29
also it has much better control of what version of specific application you want to install and much easier to revert to older versions.

---

### Post by ice60 on 2006-09-29
arch smokes everything. i have suse on a fast computer and arch on something many times slower, and arch, on the slow computer, is about 3 times faster then suse :shock: arch is optimised for i686 processors [img]http://forums.expectedmiracles.com/images/smilies/smokin.gif[/img]

---

