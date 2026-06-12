---
title: "OS suggestions for an ancient PC"
date: 2009-09-21
forum: The Cafe
---

### Post by the.dark.lord on 2009-09-21
I've an old Compaq sitting around with a whopping 64MB RAM, Pentium III, and a 20 GB HD. I currently make it ***slog*** along with great difficulty on XP(my cousin installed this on top of Win ME- and I just let it be). 

I'm thought of installing Xubuntu on this using the alternate installer. Think it'll run fine? Minimum reqs state that it needs at least 128 MB RAM.

Other suggestions? I need something user-friendly; nothing too advanced. :)

---

### Post by AllRadioisDead on 2009-09-21
This is relevant to my interests.

---

### Post by cmay on 2009-09-21
You could try damn small linux. puppy linux. or debian netinstaller . 

but I would have installed minix or freedos on these specs. If not window ME or windows 96. I do not know of experience any other more light choices but these. 

there is also a possible choice in tiny core if you dont mind setting up the system.

please post back what works for you.

---

### Post by stwschool on 2009-09-21
Slitaz probably offers best range of apps, ease of use, nicest interface etc for that kind of machine. It'll run on a toaster and you've got a nice easy installer to do most of the work. Or you could go Arch with Openbox window manager and general minimalism (awaits flaming).

---

### Post by doorknob60 on 2009-09-21
Puppy, maybe DSL (although it has old software), or if you wanted something more complete, Debian or Arch with minimal software (no DEs). Definitely not Xubuntu though, not enough RAM for that.

---

### Post by NormanFLinux on 2009-09-21
LXDE. Its very lightweight and compact. It should be good enough for a Pentium III.

---

### Post by -grubby on 2009-09-21
If it's just for messing around, or a (limited) amount of work, you can always try [Haiku](http://www.haiku-os.org/).

---

### Post by misfitpierce on 2009-09-21
Ubuntu but run LXDE or use Lubuntu or w/e its called where LXDE environment is default but still using Ubuntu code... LXDE is ultra light but more updated looking than openbox and stuff but nearly just as light and fast.

---

### Post by blackened on 2009-09-21
Slap a couple TBs worth of storage in it and install server edition with just a CLI. Quality learning experience.

---

### Post by lukeiamyourfather on 2009-09-21
Something not discussed so far is what you plan to do with the machine? Even if the machine is able to run an operating system smoothly a simple browser session like Gmail or Wikipedia would use more than 64MB of memory by itself and cause the system to thrash the swap.

Puppy Linux would probably not work as it requires at least 128MB when installed according to their internal Wiki. The only option I know of for sure that would work is DSL, but Gentoo or Debian could work with very minimal installations built up from scratch. If it were me I'd look for at least 256MB of memory to stick in the machine so it could do more than just boot without thrashing.

I know the question is related to what operating system to use, but you might want to consider upgrading the hardware or building a new machine. As little as $200 could get that system running Ubuntu 9.04 without issue. Cheers!

---

### Post by lespaul_rentals on 2009-09-21
[Wolvix Cub](http://www.wolvix.org).

---

### Post by DasEi on 2009-09-21
netinstaller - textmode,  don't choose any soft in first place, icewm - windowmanager, and 64 MB ram , SD I guess,  should be no problem to get to 128 MB at least, unless it's least a 400 MHZ PIII

can also make a decent router/firewall from it

---

### Post by NormanFLinux on 2009-09-21
The maximum amount of RAM on Pentium III's is 768MB. They can run Windows XP and they should be able to run XFCE or LXDE without choking.

---

### Post by kk0sse54 on 2009-09-21
Crux or TinyCore

Edit: scratch that, why do I never see the part about wanting something beginner friendly? As suggested before perhaps slitaz instead.

---

### Post by schauerlich on 2009-09-21
Any "full", modern linux distro will be slow on it. Try something like Puppy, DSL, or Slitaz. Or, if you want to experiment with *BSD, FreeBSD will install on a 486 or better with 24mb of RAM.

---

### Post by lespaul_rentals on 2009-09-21
The bottom line is, this should definitely be a command-line only PC.

---

### Post by kk0sse54 on 2009-09-21
> **EDavidBurg said:**
> Any "full", modern linux distro will be slow on it. Try something like Puppy, DSL, or Slitaz. Or, if you want to experiment with *BSD, FreeBSD will install on a 486 or better with 24mb of RAM.

For *BSD I'd go with NetBSD which has  an absolute minimum requirement of 4 MB RAM with a recommended minimum of 16 MB. Throw in dwm or tinywm and you get a nice little setup :). Another option would perhaps be Evoke which is a 50 MB slimmed down version of FreeBSD.

---

### Post by magmon on 2009-09-21
I vote you upgrade the ram. I have an old compaq running with 128 mb of ram and a 7 gig hard drive wth xubuntu.

---

### Post by NormanFLinux on 2009-09-21
Upgrading RAM will help. As the previous poster noted Xubuntu can be run on even very old systems with 128MB RAM and a 7GB HD. Though a bigger HD would solve much of the thrashing issue and leave room to install all needed applications.

---

### Post by HappinessNow on 2009-09-22
> **the.dark.lord said:**
> I've an old Compaq sitting around with a whopping 64MB RAM, Pentium III, and a 20 GB HD. I currently make it ***slog*** along with great difficulty on XP(my cousin installed this on top of Win ME- and I just let it be). 

I'm thought of installing Xubuntu on this using the alternate installer. Think it'll run fine? Minimum reqs state that it needs at least 128 MB RAM.

Other suggestions? I need something user-friendly; nothing too advanced. :)Definitely Puppy or Puppy derivative like MacPup Opera or MacPup Foxy.

---

### Post by jaxxstorm on 2009-09-22
I'm currently developing an Ubuntu based distribution using IceWM as its window manager, as well as a few other tweaks

The website is [http://www.sprilinux.com](http://www.sprilinux.com).

Unfortunately its a Live CD + installer only at the moment, however I'll be creating a build script very soon meaning that you can install it on any machine, even with less than 192mb. Give it a try

---

### Post by gn2 on 2009-09-22
Get more RAM in it and try Antix.

---

### Post by HappinessNow on 2009-09-22
> **&#20170 said:**
> Definitely Puppy or Puppy derivative like MacPup Opera or MacPup Foxy.

When size matters: 

MacPup Opera 176,700 KB

MacPup Foxy 37, 888 KB

---

### Post by bodyharvester on 2009-09-22
my ancient pc has half as much ram at 32MB and only a pentium II, consider yourself lucky :p i may try whatever you try
EDIT: also the HD is only 2GB, not your impressive 20GB

---

### Post by CJ Master on 2009-09-22
> **lespaul_rentals said:**
> The bottom line is, this should definitely be a command-line only PC.

I agree. Use links with framebuffer for graphical online viewing.

---

### Post by gjoellee on 2009-09-22
Slitaz or Puppy

---

### Post by Warpnow on 2009-09-22
You can do a command line install of Ubuntu and apt-get LXDE or ICEwm and it will work fine.

If you want something easier, Slitaz IS nice, as are DSL and Puppy.

The easiest solution is puppy. Most user friendly distribution I've ever used.

---

### Post by NormanFLinux on 2009-09-22
Agreed. A CLI install of Ubuntu and then one can add a lightweight GUI desktop environment/window manager post-installation. Either ICEWM, OpenBox, Fluxbox or LXDE will work fine.

---

