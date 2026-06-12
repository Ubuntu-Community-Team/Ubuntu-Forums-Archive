---
title: "RAM Disk Firewall/DHCP/Wireless AP - Worth It?"
date: 2005-10-16
forum: Server Platforms
---

### Post by faulkner132 on 2005-10-16
Would it be worth it to take an old machine and have it boot directly off a USB flash drive and run in memory to perform the following (and possibly more):

DCHP (router and gateway)
Firewall
Wireless AP
NAT

I would want it to be completely on a gigabit network.  I know you can get gigabit wireless routers which do this for around $125, but they are limited to a single network and a single IP.

Any advantages/disadvantages to one over the other (beside the obvious - price)?  Anything else you would add?  How hard would it be to implement this?  It may not even be worth it.  I would appreciate any other thoughts beside my own...

---

### Post by cactus on 2005-10-17
Unless you have a gigabit pipe to upstream, it is a waste to shoot for all gigabit.
Sure. Put a nice gigabit switch behind your firewall/nat/router/wirelessAP, but not many people will need a real 'gigabit firewall/gateway/router'.

---

### Post by bluck on 2005-10-17
[QUOTE=cactus]Unless you have a gigabit pipe to upstream, it is a waste to shoot for all gigabit.
Sure. Put a nice gigabit switch behind your firewall/nat/router/wirelessAP, but not many people will need a real 'gigabit firewall/gateway/router'.[/QUOTE]

agreed, but is this really about need, or funsies? Sysadmins do love to show off their zippy fast network, quiescent as it may be.

---

### Post by faulkner132 on 2005-10-17
Definitely fun, but I would like to learn too...

Anyone have any idea how to create/update a Linux build which will boot off the USB flash drive?

---

### Post by LordHunter317 on 2005-10-17
To second the gigabit is silly idea: An old machine is likely to get nothing approaching GigE speeds anyway.

---

### Post by faulkner132 on 2005-10-17
Silly? Yes.

I just want if and how it can be done.

---

### Post by bluck on 2005-10-17
[QUOTE=faulkner132]Definitely fun, but I would like to learn too...

Anyone have any idea how to create/update a Linux build which will boot off the USB flash drive?[/QUOTE]

well, if its older hardware, you migh have trouble with that.  You need to check that your BIOS will support booting off of USB devices.

---

### Post by faulkner132 on 2005-10-17
I know it will boot off USB and support both 10/100 and gigabit cards.
I'm more concerned with loading/configuring a kernel to run in memory (512 should be fine).  I can update config files as needed on the flash drive to configure the firewall/router.

I am most curious about the OS part, I have the hardware part in order.

Thanks again for everyone's help.

---

### Post by casper_2095 on 2005-10-18
I've recently seen usb drives available with ubuntu pre-installed, which would save you some trouble.  There is a how-to floating around for debian to do it yourself.  I'm not so sure that ubuntu would be the ideal distro for this application.  My favourite was the "linux router project" ([http://sourceforge.net/projects/leaf](http://sourceforge.net/projects/leaf))  for quite a while.  I've heard good things about [http://www.m0n0.ch/](http://www.m0n0.ch/) (note the o's are zero's).  Hunt around for one of these hardened/dedicated distros, it will be easier/better/faster.
[http://www.flonix.com/article.php?id_article=102](http://www.flonix.com/article.php?id_article=102)
[http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)
[http://www.8ung.at/spblinux/](http://www.8ung.at/spblinux/)
so much to play with, so little time.

---

### Post by nystire on 2005-10-25
You may wish to look at this: [http://slax.linux-live.org/](http://slax.linux-live.org/)
Also, search for a program called MySlax. It may be Windows only (I've only ever used that version), but it allows you to customie the Slax CD image and to create a LiveCD or a bootable USB stick from your custom image.

---

### Post by Go-Linux on 2008-01-19
Yes, it is definitely worth it.

I have been running RAM-based firewalls for quite some time.  I currently  have OpenBSD firewalls which boot off a USB Flash Drive (or Compact Flash) and run in RAM.  Both i386 and WRAP are supported.  I am working (today) on a Linux (Debian) version.

The beauty of it is you don't need a hard drive and there are different methods of logging, local and remote.

Check out the "Do IT Yourself Flash Drive" link at [www.go-unix.com](www.go-unix.com) for details.
[www.go-linux.com](www.go-linux.com) is the same site and I will soon separate the OpenBSD version from the Linux version in different files.

As the other posts note, gigabit is unnecessary on the WAN side (unless you have a really hot Internet  link).

Good luck!

---

