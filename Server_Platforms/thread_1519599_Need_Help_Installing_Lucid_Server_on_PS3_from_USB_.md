---
title: "Need Help Installing Lucid Server on PS3 from USB Drive"
date: 2010-06-28
forum: Server Platforms
---

### Post by Morgans on 2010-06-28
Hi there,

I need some help installing Lucid Server on my PS3 from a flash drive. The BD-ROM in my unit is totally shot, and I have some experience installing the Desktop version from flash drive. 

I can install the desktop by formating my flash drive as an ext3 system and then extracting the iso image to the flash drive. Using petitboot, it will see the kboot.conf of the flash drive, boot it up and within the hour it's done.

However, this does not work for either the PS3 server or alternate server iso's. I can get petitboot to load up the installer, however the installer looks for the ubuntu disc in the cd drive, and for obivious reasons, can't find it. 

I've tried copying the iso file over to the flash drive and experimented it some mount commands, but to no avail. Does anyone have any suggestions for tricking it into thinking the iso is the cd drive?

Thanks,

Morgans

---

### Post by arrrghhh on 2010-06-28
Unless you held your PS3 back, the newer firmwares don't allow the "Other OS" option any longer...

---

### Post by windependence on 2010-06-28
I'm kinda curious as to why you would want to do this?

-Tim

---

### Post by arrrghhh on 2010-06-28
> **windependence said:**
> I'm kinda curious as to why you would want to do this?

Well the non-server version of Ubuntu on a PS3 does have advantages... but I don't see the benefit of installing Ubuntu Server on a PS3 unless you just want it to crunch numbers for Folding@Home or something like that...

---

### Post by Morgans on 2010-06-28
What I want to achieve with this PS3 is to use it as my file server. When my roommate's PS3 BD drive died, he pretty much let me have it (as he didn't feel like waiting a couple of weeks to send it in for repair, he just bought a new one). I need a computer that I can use as a samba server, and neither my tablet or netbook are candidates for the position as they are more easily lost or stolen than something that stays at home all the time. 

My goal in installing the server version is to have a minimal install that does what I want it to do. Sure, I could install the desktop version and figure out how to use apt-get to remove unnecessary packages, but a) I don't have a list of differences in the packages between the two, b) I want minimal resources to be used from the first boot, and c) I cannot find any guides on how to switch to the server kernel on the PPC versions. I've seen guides on how to compile a custom kernel on the PS3, but I want something that'll be supported. On top of that, there's also the security concerns that many people express when using a desktop version as a server that I'd like to avoid.

I've also realized that due Sony's practices, I shouldn't update the firmware, and I have zero plans to do so. Normally, I'd complain about them taking away my hard earned money, but it wasn't my money that paid for it.

Morgans

---

### Post by arrrghhh on 2010-06-28
Well I don't think there's a server version that's designed for the PS3.  PuppyLinux had a special version for the PS3, as did Ubuntu- PS3buntu.com is the website I believe, but if he already updated the firmware past whatever version it broke in - 3.2 I think - then it's already too late.

If you're not past that firmware revision, you can certainly do it - I just don't know if anyone has done it with the server edition & a PS3.  I had a version of Xubuntu on my PS3 before Sony took that feature away...

---

### Post by windependence on 2010-06-28
Thanks for the explanation. Makes sense to me especially the minimal install. One gripe I have about most distros is that I cannot get a minimal install like I can with FreeBSD. Ubuntu server is the closest I can get to what I want with Linux so I understand you wanting to use it for this application.

-Tim

---

### Post by Morgans on 2010-06-28
I was able to find the server version for the PS3 here:
[http://cdimage.ubuntu.com/ports/releases/10.04/release/](http://cdimage.ubuntu.com/ports/releases/10.04/release/)

I've  tried googling around for instructions on how to install FreeBSD on the  PS3, however none of the links have anything useful. Add to the fact  that I don't think the kernel has PS3 support in it, and I wouldn't know  how to compile in support for the ps3da device, and it's not a viable  option. I've considered the Slackintosh port of Slackware, however it's  outdated, and I don't know how to do a mass recompile from the Slackware  source. I've tried googling for a PS3 version of Puppy Linux. Right  now, I can't seem to find a download link for the PPC version, but I'm  seen some evidence it does exists.

I've found a guide on how to  install Debian on the PS3 here: 
 [http://www.kernel.org/pub/linux/kernel/people/geoff/cell/ps3-howto/ps3-debian-install-howto.txt](http://www.kernel.org/pub/linux/kernel/people/geoff/cell/ps3-howto/ps3-debian-install-howto.txt)  

I'll see if I can jerry-rig it to the server install.

Morgans

---

