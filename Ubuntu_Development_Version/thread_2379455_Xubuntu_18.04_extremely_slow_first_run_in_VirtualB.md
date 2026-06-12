---
title: "Xubuntu 18.04 extremely slow first run in VirtualBox"
date: 2017-12-05
forum: Ubuntu Development Version
---

### Post by &amp;KyT$0P# on 2017-12-05
I've been experimenting with Xubuntu 18.04 in VirtualBox (5.1.30).  The live media boots OK, loads the GUI OK, but it takes a surprisingly long time to load the Try/Install screen.  Since this is a disposable VM, I click Install.  That part goes fine.  Reboot, enter my password to log in the new system, and...wow is it slow to load.

At first, I thought this was just a glitch of some sort, that surely someone would notice and fix.  But now, one month later, with the 2017-12-04 Xubuntu ISO, this is still the case.

So I tried Ubuntu 18.04.  And it appears to load fine, no unexpected slowness.  Nor is there any slowness installing and using XFCE in Ubuntu 18.04.  Nor on subsequent runs of Xubuntu 18.04.

To give some sense of just how bad this slowness is, here are some approximate times.  Identical VM specs for both.

Xubuntu 16.04 new install: about 14 seconds between login and desktop loaded
Xubuntu 18.04 new install: about **1min,36sec** between login and desktop loaded

Has anyone else experienced this?

---

### Post by flocculant on 2017-12-05
Not in vbox - but I see similar in kvm/qemu, though there I see the same problem with the Ubuntu 18.04 iso's.

Did have similar issues during the last cycle using the same setup. Not sure what happened there - the issue just went away before I could dig a bit deeper.

I also have the daily lined up to boot from grub - see the same behaviour there.

Booted daily with a usb - slower than I expected, but not as slow as the others.

I'll try and grab some time to check the same with the Ubuntu daily - then I'll see if I can get the ubiquity guy at Canonical interested ... he's generally interested ;)

---

### Post by ajgreeny on 2017-12-05
I am not seeing that at all with my 18.04 64bit VM in that same version of VirtualBox so I wonder why you have such a problem.  I  also have Ubuntu and Lubuntu 18.04 running superbly as VMs at the moment.

What hardware and how much ram have you allocated to the VM and how much video memory?
I have 4GB ram allocated and the max 128MB video memory and though I have not timed it my VM is up and running in about an estimated 10 seconds.

Do you have the correct guest additions installed or do you not bother to add them?
Do you have 3D graphics enabled in the VM?  If so, try disabling that as it really is not needed and may be causing this.

My final comment is that I am finding this unreleased dev version of my favourite *ubuntu version almost faultless so far, unlike you.

---

### Post by &amp;KyT$0P# on 2017-12-05
Thanks flocculant and ajgreeny for the replies!

> **ajgreeny said:**
> What hardware and how much ram have you allocated to the VM and how much video memory?
Physical hardware is a MacBook Pro 9,1 (see my signature).  The VMs all have identical specs: 4 GB RAM, default amount of video memory (16MB), 1 CPU core, and 58 GB hard drive (only the one virtual SATA controller for both hard drive and CD drive).

> Do you have the correct guest additions installed or do you not bother to add them?
The problem happens only when booting the ISO and on first login to the installed system.  Which is all before I would have the chance to install Guest Additions.  Subsequent runs are normal speed whether Guest Additions are installed or not (just timed one at about 11 seconds).

> Do you have 3D graphics enabled in the VM?
Nope, no 3D acceleration.

---

### Post by slickymaster on 2017-12-07
Not getting that also, in VMware with 4 GB Ram and with 3D Graphics enabled. That's with 2017-12-05 image.

---

### Post by VMC on 2017-12-07
> **halogen2 said:**
> I've been experimenting with Xubuntu 18.04 in VirtualBox (5.1.30).  The live media boots OK, loads the GUI OK, but it takes a surprisingly long time to load the Try/Install screen.  Since this is a disposable VM, I click Install.  That part goes fine.  Reboot, enter my password to log in the new system, and...wow is it slow to load.

At first, I thought this was just a glitch of some sort, that surely someone would notice and fix.  But now, one month later, with the 2017-12-04 Xubuntu ISO, this is still the case.

So I tried Ubuntu 18.04.  And it appears to load fine, no unexpected slowness.  Nor is there any slowness installing and using XFCE in Ubuntu 18.04.  Nor on subsequent runs of Xubuntu 18.04.

To give some sense of just how bad this slowness is, here are some approximate times.  Identical VM specs for both.

Xubuntu 16.04 new install: about 14 seconds between login and desktop loaded
Xubuntu 18.04 new install: about **1min,36sec** between login and desktop loaded

Has anyone else experienced this?

I get the exact same result using ISO live media hardware boot. If I access a virtual terminal, I see the red timing and it keeps counting down. It takes a minute or so to fully boot. Not sure what its looking for. Now I know someone else has the same issue, but I will check ubiquity logs.

---

### Post by Chanath on 2017-12-08
> **VMC said:**
> I get the exact same result using ISO live media hardware boot. If I access a virtual terminal, I see the red timing and it keeps counting down. It takes a minute or so to fully boot. Not sure what its looking for. Now I know someone else has the same issue, but I will check ubiquity logs.

If you are booting in live mode, ubiquity has nothing to do with the lateness to boot. The booting process is trying to mount something, and cannot do that. It is a grub problem. If you are trying to install, and there is some lateness, then it is an ubiquity problem.

---

### Post by VMC on 2017-12-08
The op stated:> "[COLOR=#000000]I've been experimenting with Xubuntu 18.04 in VirtualBox (5.1.30). The live media boots OK, loads the GUI OK, but it takes a surprisingly long time to load the **Try/Install screen**. Since this is a disposable VM, I click Install. That part goes fine. Reboot, enter my password to log in the new system, and...wow is it slow to load."[/COLOR]
[COLOR=#000000]It is not a grub problem.  "Try/Install" comes way after grub. 

Booting from USB flash, grub is not involved.


[/COLOR]

---

### Post by Chanath on 2017-12-08
The problem is with VirtualBox, ***not*** with Xubuntu 18.04. 
I just installed it in an MBR and a UEFI laptop. No problems encountered.

---

### Post by flocculant on 2018-04-11
> **halogen2 said:**
> I've been experimenting with Xubuntu 18.04 in VirtualBox (5.1.30).  The live media boots OK, loads the GUI OK, but it takes a surprisingly long time to load the Try/Install screen.  Since this is a disposable VM, I click Install.  That part goes fine.  Reboot, enter my password to log in the new system, and...wow is it slow to load.

At first, I thought this was just a glitch of some sort, that surely someone would notice and fix.  But now, one month later, with the 2017-12-04 Xubuntu ISO, this is still the case.

So I tried Ubuntu 18.04.  And it appears to load fine, no unexpected slowness.  Nor is there any slowness installing and using XFCE in Ubuntu 18.04.  Nor on subsequent runs of Xubuntu 18.04.

To give some sense of just how bad this slowness is, here are some approximate times.  Identical VM specs for both.

Xubuntu 16.04 new install: about 14 seconds between login and desktop loaded
Xubuntu 18.04 new install: about **1min,36sec** between login and desktop loaded

Has anyone else experienced this?

Do you still see this?

I believe this was the fontconfig issue recently fixed.

---

### Post by VMC on 2018-04-11
[**[COLOR=#000000]flocculant[/COLOR]**]("https://ubuntuforums.org/member.php?u=1990108"), Do you have any more info on that fontconfig fix?  Was there a bug reported.

---

### Post by &amp;KyT$0P# on 2018-04-11
> **flocculant said:**
> Do you still see this?
The Xubuntu 18.04 20180411 ISO does not have this problem.

Thanks! :D

> **VMC said:**
>  any more info on that fontconfig fix?  Was there a bug reported.
Maybe [this]("https://bugs.launchpad.net/ubuntu/+source/fontconfig/+bug/1749546")?

---

### Post by flocculant on 2018-04-12
> **VMC said:**
> [**[COLOR=#000000]flocculant[/COLOR]**]("https://ubuntuforums.org/member.php?u=1990108"), Do you have any more info on that fontconfig fix?  Was there a bug reported.

> **halogen2 said:**
> The Xubuntu 18.04 20180411 ISO does not have this problem.

Thanks! :D


Maybe [this]("https://bugs.launchpad.net/ubuntu/+source/fontconfig/+bug/1749546")?

That's the one - sorry - interwebs died for a day here - and I got some rest :)

---

### Post by connectionistsystems on 2018-05-05
I'm experiencing the problem. It is extremely slow, not just during boot.  I updated from 17.10 to 18.04. 

This is not through a VM. I have Ubuntu installed directly on hard-drive and no other OS on the SSD.

This is I7 processor with 16GB Ram.

---

### Post by wildmanne39 on 2018-05-05
Thread closed since 18.04 is no longer in development, please start your own thread in the appropriate sub-forum, if unsure New to Ubuntu is fine for new users and welcome to the forum!

---

