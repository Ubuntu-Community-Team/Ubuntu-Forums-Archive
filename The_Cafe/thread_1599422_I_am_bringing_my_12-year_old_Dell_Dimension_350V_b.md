---
title: "I am bringing my 12-year old Dell Dimension 350V back into service"
date: 2010-10-17
forum: The Cafe
---

### Post by Shining Arcanine on 2010-10-17
These were its original specifications:

Intel 350MHz Pentium II Deschutes processor
Intel 440BX chipset
Integrated ATI Technologies Inc 3D Rage Pro AGP 1X/2X 
Integrated Sound
64MB of 100Mhz SDRAM
40x NEC CD-RW
8.4GB Maxtor Hard Drive
No NIC
56Kbps Modem
Windows 98 (First Edition)

Over the years, I upgraded it and I recently decided to bring it back into service as a server on my home network. Here are its specifications after everything I have done to it over the years:

Intel 350MHz Pentium II Deschutes processor
Intel 440BX chipset
Integrated ATI Technologies Inc 3D Rage Pro AGP 1X/2X
Integrated Sound
384MB of 133Mhz SDRAM, underclocked to 100MHz
Samsung SM-352B 52X/24X/52X/16X Combo Drive
200GB Western Caviar Hard Drive, one of the last drives with the Western Digital Signature Whine
Promise Ultra133 TX2
Linksys Network Everywhere (NC100) 10/100 NIC
56Kbps Modem
Gentoo Linux ~x86

It was a pain getting it to work. Intel's Pentium II Deschutes processors had defects that required operating systems to load microcode into the processors so that they would behave predictably. Since I used to use Windows until about a year ago and Microsoft had the foresight to have Windows load the necessary microcode, I never had to deal with this, so I wasted a ton of time learning why the system was crashing with Linux and not Windows. I also never had a drive larger than 80GB in this system and upgraded the boot drive to 200GB as part of the upgrade process, so I ran into the 128GB drive size limit for the first time, which forced me to use the Promise Ultra133 TX2 for the boot drive. I also rediscovered the fact that one of the channels on the Promise Ultra133 TX2 does not work, which was a rather vexing issue.

Installing the OS was also somewhat troublesome. I ended up attaching the drive to my desktop, mounting it and cross compiling the entire the installation because compilation on the Pentium II was rather problematic. This let me workaround the microcode issue until I came across a little note on kernel-seeds.org that talked about microcode for older x86 processors. If it had not been for my decision to install Gentoo Linux, I probably would have never managed to get it to work. Before I thought of doing the installation through my desktop, I had tried installing FreeBSD instead of Gentoo Linux, but it had the same issues with microcode that my attempts at installing Gentoo initially had.

The system is running well again now, so I plan to configure it to do a few things for me:

[LIST]
[*]Replace my Linksys WRT54GS v2.1 as an OpenVPN server
[*]Be a private Gentoo Linux mirror
[*]Be a system on which I can run irssi inside screen
[*]Be a NAS device on my home network
[*]Function as a private software repository
[/LIST]

Has anyone else tried using Linux to bring old systems back into service? How old are your systems? What do you have them doing?

---

### Post by inobe on 2010-10-17
i have an old dell latitude lm, no optical device, no usb ports, just a floppy device, the nic card needs the lan adapter, the tft screen is good but of course it ghosts, maybe a 2 sec response time.

planning on a lightweight distro maybe slitaz.

i would like to find a better lcd screen, cd rom "may use text installer floppy" and lan adapter.

it has 32megs of ram.

once done hand it down to my youngest.

---

### Post by sandyd on 2010-10-17
> **Shining Arcanine said:**
> These were its original specifications:

Intel 350MHz Pentium II Deschutes processor
Intel 440BX chipset
Integrated ATI Technologies Inc 3D Rage Pro AGP 1X/2X 
Integrated Sound
64MB of 100Mhz SDRAM
40x NEC CD-RW
8.4GB Maxtor Hard Drive
No NIC
56Kbps Modem
Windows 98 (First Edition)

Over the years, I upgraded it and I recently decided to bring it back into service as a server on my home network. Here are its specifications after everything I have done to it over the years:

Intel 350MHz Pentium II Deschutes processor
Intel 440BX chipset
Integrated ATI Technologies Inc 3D Rage Pro AGP 1X/2X
Integrated Sound
384MB of 133Mhz SDRAM, underclocked to 100MHz
Samsung SM-352B 52X/24X/52X/16X Combo Drive
200GB Western Caviar Hard Drive, one of the last drives with the Western Digital Signature Whine
Promise Ultra133 TX2
Linksys Network Everywhere (NC100) 10/100 NIC
56Kbps Modem
Gentoo Linux ~x86

It was a pain getting it to work. Intel's Pentium II Deschutes processors had defects that required operating systems to load microcode into the processors so that they would behave predictably. Since I used to use Windows until about a year ago and Microsoft had the foresight to have Windows load the necessary microcode, I never had to deal with this, so I wasted a ton of time learning why the system was crashing with Linux and not Windows. I also never had a drive larger than 80GB in this system and upgraded the boot drive to 200GB as part of the upgrade process, so I ran into the 128GB drive size limit for the first time, which forced me to use the Promise Ultra133 TX2 for the boot drive. I also rediscovered the fact that one of the channels on the Promise Ultra133 TX2 does not work, which was a rather vexing issue.

Installing the OS was also somewhat troublesome. I ended up attaching the drive to my desktop, mounting it and cross compiling the entire the installation because compilation on the Pentium II was rather problematic. This let me workaround the microcode issue until I came across a little note on kernel-seeds.org that talked about microcode for older x86 processors. If it had not been for my decision to install Gentoo Linux, I probably would have never managed to get it to work. Before I thought of doing the installation through my desktop, I had tried installing FreeBSD instead of Gentoo Linux, but it had the same issues with microcode that my attempts at installing Gentoo initially had.

The system is running well again now, so I plan to configure it to do a few things for me:

[LIST]
[*]Replace my Linksys WRT54GS v2.1 as an OpenVPN server
[*]Be a private Gentoo Linux mirror
[*]Be a system on which I can run irssi inside screen
[*]Be a NAS device on my home network
[*]Function as a private software repository
[/LIST]

Has anyone else tried using Linux to bring old systems back into service? How old are your systems? What do you have them doing?
I actually have a lot of old systems - I collect them, strip the parts, decide which computer I feel like sticking the parts in, and rebuild it.

The computers are the ones that are picked up off the curb. By stripping out defective hardware and old hardware (I actually strip out everything, as in including the CPU), I build new machines and give them out. I do research on which CPU works with which chipset, then decide which computer its going into (if its at least a PIII 700+MHz). The rest of the processors, I throw out. Its kind of a waste, beacuase all these people throw out properly working computers....

I even have rebuilt a mac G5 (quad core) that ran perfectly after I replaced the power supply and upgraded some RAM. It now happily resides in my room running snow leopard now (the guy at the storee looked at me like I was nuts when I asked for a OEM copy of Snow leopard :P).

---

### Post by Shining Arcanine on 2010-10-17
> **inobe said:**
> i have an old dell latitude lm, no optical device, no usb ports, just a floppy device, the nic card needs the lan adapter, the tft screen is good but of course it ghosts, maybe a 2 sec response time.

planning on a lightweight distro maybe slitaz.

i would like to find a better lcd screen, cd rom "may use text installer floppy" and lan adapter.

it has 32megs of ram.

once done hand it down to my youngest.

If I were you, I would install Gentoo Linux on it. While 32MB of RAM is low, a conventional Gentoo Linux installation should be able to scale down to it as long as you customize it correctly. A Gentoo Linux installation that uses uclibc as the system library would be even better, but that is more difficult to install.

If you decide to install Gentoo Linux on it, do all compilation on another system like I did. Pull out the hard drive, use an adapter to attach it to a modern UNIX system, mount it and follow the Gentoo Handbook, making minor adjustments for the fact that it is not the system boot drive (e.g. install grub to hd1 instead of h0). Set your CFLAGS to use -Os, do not install any large software (e.g. KDE) and it should have a relatively low memory footprint. Make certain that your kernel is compiled with -Os as well. You should probably be able to install LXDE or XFCE on it and get decent performance from Firefox. Be sure to utilize Gentoo Linux's USE flags to strip out as many unneeded features as possible (e.g. firefox's "inter-process communication between tabs and plugins").

---

### Post by Shining Arcanine on 2010-10-17
> **sandyd said:**
> I actually have a lot of old systems - I collect them, strip the parts, decide which computer I feel like sticking the parts in, and rebuild it.

The computers are the ones that are picked up off the curb. By stripping out defective hardware and old hardware (I actually strip out everything, as in including the CPU), I build new machines and give them out. I do research on which CPU works with which chipset, then decide which computer its going into (if its at least a PIII 700+MHz). The rest of the processors, I throw out. Its kind of a waste, beacuase all these people throw out properly working computers....

I even have rebuilt a mac G5 (quad core) that ran perfectly after I replaced the power supply and upgraded some RAM. It now happily resides in my room running snow leopard now (the guy at the storee looked at me like I was nuts when I asked for a OEM copy of Snow leopard :P).

Why did you install Snow Leopard instead of Linux? Several major Linux distributions support your hardware:

[http://www.gentoo.org/](http://www.gentoo.org/)
[http://www.centos.org/](http://www.centos.org/)
[http://www.redhat.com/rhel/](http://www.redhat.com/rhel/)
[http://www.fedoraproject.org/](http://www.fedoraproject.org/)
[http://www.debian.org/](http://www.debian.org/)

If you prefer BSD operating systems, FreeBSD also supports your hardware:

[http://www.freebsd.org/](http://www.freebsd.org/)

---

### Post by inobe on 2010-10-17
> **Shining Arcanine said:**
> If I were you, I would install Gentoo Linux on it. While 32MB of RAM is low, a conventional Gentoo Linux installation should be able to scale down to it as long as you customize it correctly. A Gentoo Linux installation that uses uclibc as the system library would be even better, but that is more difficult to install.

If you decide to install Gentoo Linux on it, do all compilation on another system like I did. Pull out the hard drive, use an adapter to attach it to a modern UNIX system, mount it and follow the Gentoo Handbook, making minor adjustments for the fact that it is not the system boot drive (e.g. install grub to hd1 instead of h0). Set your CFLAGS to use -Os, do not install any large software (e.g. KDE) and it should have a relatively low memory footprint. Make certain that your kernel is compiled with -Os as well. You should probably be able to install LXDE or XFCE on it and get decent performance from Firefox. Be sure to utilize Gentoo Linux's USE flags to strip out as many unneeded features as possible (e.g. firefox's "inter-process communication between tabs and plugins").

that is a really great idea, but that brings up a thought about linux hardware detection, sometime ago i remember pulling a drive from a completely different computer onto another and all devices worked flawlessly, hmm

---

### Post by pwnst*r on 2010-10-17
> **Shining Arcanine said:**
> Why did you install Snow Leopard instead of Linux? Several major Linux distributions support your hardware:



Because he can?  He probably already runs *nix on another system, so what's the big deal?

---

### Post by sandyd on 2010-10-17
> **inobe said:**
> that is a really great idea, but that brings up a thought about linux hardware detection, sometime ago i remember pulling a drive from a completely different computer onto another and all devices worked flawlessly, hmm
which is the point of the gentoo kernel compiliation.
Naturally, it requires you to identify all your hardare.
In this case, you would compile the hardware drivers the computer that you were compiling it on as modules, and the drivers needed for the computer that you were compiling for as built in.

Its largely possible, my gentoo setup (which im typing from) loads everything built in except for bcmwl and virtualbox

---

### Post by sandyd on 2010-10-17
> **Shining Arcanine said:**
> Why did you install Snow Leopard instead of Linux? Several major Linux distributions support your hardware:

[http://www.gentoo.org/](http://www.gentoo.org/)
[http://www.centos.org/](http://www.centos.org/)
[http://www.redhat.com/rhel/](http://www.redhat.com/rhel/)
[http://www.fedoraproject.org/](http://www.fedoraproject.org/)
[http://www.debian.org/](http://www.debian.org/)

If you prefer BSD operating systems, FreeBSD also supports your hardware:

[http://www.freebsd.org/](http://www.freebsd.org/)
cause new good mac systems cost $1500< in my area, and its a shame to waste a powerful mac computer that can easily run leopard without hacking kexts

---

### Post by K.Mandla on 2010-10-17
> **Shining Arcanine said:**
> Has anyone else tried using Linux to bring old systems back into service? How old are your systems? What do you have them doing?
Yup.

[http://kmandla.wordpress.com/hardware](http://kmandla.wordpress.com/hardware)

Daily system is a 120Mhz Pentium running Crux Linux. I use a 133Mhz Pentium as a torrent slave and a 150Mhz Pentium (with one USB port! :P ) for experimentation purposes. (Insert fiendish laugh.)

The only reason I have so many of these is that no one will take them from me. Everyone thinks they're too old ... :???:

---

### Post by Shining Arcanine on 2010-10-17
> **pwnst*r said:**
> Because he can?  He probably already runs *nix on another system, so what's the big deal?

Mac OS X is a proprietary UNIX OS. The point is that you do not need to pay for UNIX.

---

### Post by Shining Arcanine on 2010-10-17
> **sandyd said:**
> which is the point of the gentoo kernel compiliation.
Naturally, it requires you to identify all your hardare.
In this case, you would compile the hardware drivers the computer that you were compiling it on as modules, and the drivers needed for the computer that you were compiling for as built in.

Its largely possible, my gentoo setup (which im typing from) loads everything built in except for bcmwl and virtualbox

I think you misunderstood what I was saying. I was not saying to do a Gentoo Linux installation on a hard drive from computer A in computer B as if you were installing it for computer B and then transplant the hard drive into computer A. I was saying to start computer A, use its existing operating system's tools to prepare the hard drive from computer B for a chroot environment, chroot into the hard drive on computer B, perform the installation for computer A and then move the hard drive to computer A.

I hope that makes sense. Your way works too, but there are subtle differences between the two methods. My method gives you an existing computing environment from which you can copy and paste stuff from the handbook and only requires that the kernel support computer B's hardware. Your method requires that you do everything without the assistance of an existing environment that can provide you with tools that make the installation easier (e.g. terminal window, web browser, working network connection, google, clip board). It also requires that the kernel support both computers' hardware.

---

### Post by Khakilang on 2010-10-18
Well the oldest computer I got right now as stated below. 

Pentium 4 1.5GHz, 512MB RAM
20GB Hard disk, DVD RW,
S3 Graphics card, Aztech wifi USB adapter
Built in network card.

I use it to test other Distro and currently I install PCLinuxOS and its run pretty well.

---

### Post by kio_http on 2010-10-18
> **sandyd said:**
> I actually have a lot of old systems - I collect them, strip the parts, decide which computer I feel like sticking the parts in, and rebuild it.

The computers are the ones that are picked up off the curb. By stripping out defective hardware and old hardware (I actually strip out everything, as in including the CPU), I build new machines and give them out. I do research on which CPU works with which chipset, then decide which computer its going into (if its at least a PIII 700+MHz). The rest of the processors, I throw out. Its kind of a waste, beacuase all these people throw out properly working computers....

I even have rebuilt a mac G5 (quad core) that ran perfectly after I replaced the power supply and upgraded some RAM. It now happily resides in my room running snow leopard now (the guy at the storee looked at me like I was nuts when I asked for a OEM copy of Snow leopard :P).

Snow Leopard is only for Intel Macs!!! It is impossible to run SL on a G5 powerpc.

---

### Post by Spice Weasel on 2010-10-18
> **Shining Arcanine said:**
> Mac OS X is a proprietary UNIX OS. The point is that you do not need to pay for UNIX.

OpenSolaris is free and is one of the only free Unixes. Linux, BSD (the most similar to Unix) and GNU are UNIX-like, not UNIX. I don't know how many times I will have to tell you this. The GNU in GNU/Linux stands for GNU's Not Unix! OpenDarwin and similar projects are all based on the same base system as Mac OSX, and those are free. Parts of the OSX system are open source and free, it's the GUI that isn't. It's a bit like running [CDE]("http://en.wikipedia.org/wiki/Common_Desktop_Environment") (a proprietary desktop environment) on top of Ubuntu Server.

> 
The Open Group, an industry standards consortium, owns the &#8220;Unix&#8221; trademark. Only systems fully compliant with and certified according to the Single UNIX Specification are qualified to use the trademark; others may be called "Unix system-like" or "Unix-like" (though the Open Group disapproves of this term). However, the term "Unix" is often used informally to denote any operating system that closely resembles the trademarked system.


---

### Post by Shining Arcanine on 2010-10-18
> **Spice Weasel said:**
> OpenSolaris is free and is one of the only free Unixes. Linux, BSD (the most similar to Unix) and GNU are UNIX-like, not UNIX. I don't know how many times I will have to tell you this. The GNU in GNU/Linux stands for GNU's Not Unix! OpenDarwin and similar projects are all based on the same base system as Mac OSX, and those are free. Parts of the OSX system are open source and free, it's the GUI that isn't. It's a bit like running [CDE]("http://en.wikipedia.org/wiki/Common_Desktop_Environment") (a proprietary desktop environment) on top of Ubuntu Server.

I was talking about FreeBSD. Is FreeBSD not UNIX?

---

### Post by Spice Weasel on 2010-10-18
> **Shining Arcanine said:**
> I was talking about FreeBSD. Is FreeBSD not UNIX?

According to Wikipedia, it is not a clone of UNIX, but works like UNIX, with UNIX-compliant internals and system APIs.

---

### Post by samalex on 2010-10-18
I love seeing old computers brought back to life like this.  If I only had more time to tinker :)  Honestly if I could get Linux even a basic Linux kernel installed on an 8088 I have an old Tandy laptop I'd love to breath some life back into, but alas it's just not doable with anything modern.

These old computers honestly work great as home servers or as Linux routers, but just note that many of these old boxes had huge power supplies (400 + Watts) which can eat-up some juice if ran 24/7.

---

### Post by Spice Weasel on 2010-10-18
> **samalex said:**
> I love seeing old computers brought back to life like this.  If I only had more time to tinker :)  Honestly if I could get Linux even a basic Linux kernel installed on an 8088 I have an old Tandy laptop I'd love to breath some life back into, but alas it's just not doable with anything modern.

These old computers honestly work great as home servers or as Linux routers, but just note that many of these old boxes had huge power supplies (400 + Watts) which can eat-up some juice if ran 24/7.

Would it be worth trying [this]("http://blueflops.sourceforge.net/")? It says that it requires x86, but I don't know if a 16 bit processor would work or not.

---

### Post by pwnst*r on 2010-10-18
> **Shining Arcanine said:**
> Mac OS X is a proprietary UNIX OS. The point is that you do not need to pay for UNIX.

Unix is NOT the same as OSX, lol.  Good try though.

---

