---
title: "Need advice about a Linux distro for a very old laptop."
date: 2006-10-27
forum: The Cafe
---

### Post by Robert.Zapata on 2006-10-27
Hello there..!!

Hope everyone is doing great...!!!

Just a quick question. I have a very old laptop computer sitting in the garage and was wondering what will be the best distro to install or just put the machine in the trash can.

The machine is a COMPAQ LTE5400 (PENTIUM 150MHz)
RAM: 80 MB
HD:  2.0 GB
GRAPHIC RAM: 1 MB

I think there's no Linux GUI out there that will work on the machine but what about installing a text environment..??

Currently the machine is working with Windoze98SE

Thanks and have a nice day.!!:D

---

### Post by meng on 2006-10-27
What about Damn Small Linux? That might run on your notebook, WITH a GUI!

---

### Post by hkgonra on 2006-10-27
> **meng said:**
> What about Damn Small Linux? That might run on your notebook, WITH a GUI!

2nd vote for DSL.

---

### Post by lonce on 2006-10-27
Either damn small linux or damn small linux not.  Its the same as DSL, but uses a newer kernel and upgrades.

---

### Post by funkyade on 2006-10-27
Got an old Toshiba Laptop with Dual PCMCIA NICs acting as a firewall for my network (it's a 200Mhz P2).

I installed the [server variant of Ubuntu]("http://releases.ubuntu.com/6.10/ubuntu-6.10-server-i386.iso") and then did -

```
#> sudo aptitude install fluxbox fluxconf
```

then follow one of the many guides for setting up fluxbox how you want it, such as -

[https://help.ubuntu.com/community/Fluxbox](https://help.ubuntu.com/community/Fluxbox)

I would also take a look at -

[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

hth

---

### Post by Reshin on 2006-10-27
> **hkgonra said:**
> 2nd vote for DSL.

Good choice

---

### Post by Robert.Zapata on 2006-10-27
Rats...!!

The problem is that no CD or USB port...!!! Just Floppy Disk drive....](*,)

---

### Post by MedivhX on 2006-10-27
LOL!!! Try Minix!!! LOL but it doesn't have GUI!!! The oldest Linux!!! LOL!!!

---

### Post by meng on 2006-10-27
> **Robert.Zapata said:**
> Rats...!!
The problem is that no CD or USB port...!!! Just Floppy Disk drive....](*,)
Ah sorry, I would have advised differently had I known this. Debian Woody may still be available on floppy disk. Not sure how much processor it demands though.

---

### Post by funkyade on 2006-10-27
Do you have ethernet? Another computer available?

Try any of the following -

[https://help.ubuntu.com/community/Installation/Netboot](https://help.ubuntu.com/community/Installation/Netboot)

[https://help.ubuntu.com/community/Installation/WithFloppies](https://help.ubuntu.com/community/Installation/WithFloppies)

[https://help.ubuntu.com/community/SmartBootManagerHowto](https://help.ubuntu.com/community/SmartBootManagerHowto) (this will get the thing booted via a floppy at least!)

[https://wiki.ubuntu.com/EdubuntuViaNetBoot?action=show&redirect=InstallationViaNetBoot](https://wiki.ubuntu.com/EdubuntuViaNetBoot?action=show&redirect=InstallationViaNetBoot)

---

### Post by shining on 2006-10-27
> **MedivhX said:**
> LOL!!! Try Minix!!! LOL but it doesn't have GUI!!! The oldest Linux!!! LOL!!!

What's the matter with you?

---

### Post by funkyade on 2006-10-27
some more ideas -

[http://chris.silmor.de/hal91/](http://chris.silmor.de/hal91/) (HAL91)
[http://sunsite.auc.dk/mulinux/](http://sunsite.auc.dk/mulinux/) (muLinux)
[http://blueflops.sourceforge.net/](http://blueflops.sourceforge.net/)
[http://public.planetmirror.com/pub/floppix/](http://public.planetmirror.com/pub/floppix/)

can't guarantee any of these but worth exploring...

I am intrigued to see if you can get this going!

Good luck

---

