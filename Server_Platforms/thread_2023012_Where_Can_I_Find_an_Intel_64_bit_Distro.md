---
title: "Where Can I Find an Intel 64 bit Distro"
date: 2012-07-11
forum: Server Platforms
---

### Post by Bill Z on 2012-07-11
Where Can I Find an Intel 64 bit Distro

My goal is to build a virtual server with Ubuntu being the host OS running VMWare.  My machine has a Supermicro X6DHE-XB Mobo with 2 Intel Xion Dual CPUs and 4Gb RAM.  This should give me enough to run 2 virtual guests at any one time.

Some problems that I need suggestions with:

Is Ubuntu the better choice for my ultimate goal?

The only Ubuntu distros for 64 bit indicate AMD processors.  Will these work with an Intel Xion?  If not then what should I use?

When I try to load any ubuntu distro on this machine, it hangs at boot.  Doesn’t even give me the question to boot from CD.  Sometimes I get the following:

ISOLINUX 4.02 debian-20101016 ETCD copyright © 1994-2010 H.Peter Anvin et al

It goes no farther.  That is the most I get.  Even after letting it sit that way for an hour (just in case).

Please know that this machine will boot to a CD with DOS, XP distro or Win7 distro with no problems.  Also, the Ubuntu distros I tried to load on this machine works well on my laptop and a 64 bit AMD  box.

Please help me figure how to get this distro to boot.

---

### Post by QIII on 2012-07-11
AMD64 is the one you want.

The naming convention is historical.

Did you check the md5sum?

Burn the ISO slowly?

Are you using the same actual disk from previous installations?

Are you using the Alternate (non GUI) disk for the Server edition?

---

### Post by Bill Z on 2012-07-11
> **QIII said:**
> AMD64 is the one you want.

The naming convention is historical.

Did you check the md5sum?

Burn the ISO slowly?

Are you using the same actual disk from previous installations?

Are you using the Alternate (non GUI) disk for the Server edition?

I not only did both, burned a new distro and when that didn't work, tried a distro that has worked in the past.  Then I tried the new distro on a laptop and it worked there.  I then installed a new CD ROM drive in the target machine and tried it all again with no better luck.  

The mobo owner's guide mentioned something about 'Latency Timer' for Unix, Novel and other OSs.  I set it as directed with no better luck.

Don't want Windows on the machine but I thought I'd try and it loaded.  Great.  Not what I wanted.

I noticed in this forum where others have loaded Ubuntu on a Xion machine but the post were over a year old.  Should I try an older distro?


I feel like I keep going on rabbit trails.

---

### Post by oldfred on 2012-07-12
What did you use to write flash drive. It looks like you have the old bug from several versions ago.

syslinux errors help/enter works:
[https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/617779](https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/617779)
Delete ui in syslinux.cfg
[https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/608382](https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/608382)
in the directory from "isolinux.cfg" to "syslinux.cfg"
Try replacing the file vesamenu.c32 on the USB disk drive with that one "/usr/lib/syslinux/vesamenu.c32" of Ubuntu Maverick system or use UNetbootin than works fine.
[http://www.linuxquestions.org/questions/linux-mint-84/trying-to-boot-linux-mint-9-from-usb-flash-drive-vesamenu-c32-not-a-com32r-image-829397/](http://www.linuxquestions.org/questions/linux-mint-84/trying-to-boot-linux-mint-9-from-usb-flash-drive-vesamenu-c32-not-a-com32r-image-829397/)

---

### Post by Bill Z on 2012-07-12
The downloads of the ISOs were fresh 2 days ago from ubuntu.org/download.  The burn was at the slowest my software would support.  I even verified the new CD by trying it out on a laptop then running the verify.  All checked out.  However, just in case, I did it again with the same results.

---

### Post by SeijiSensei on 2012-07-12
Give the [USB stick approach]("https://help.ubuntu.com/community/Installation/FromUSBStick/") a try if you can control the order of the boot devices in the BIOS.

---

### Post by Bill Z on 2012-07-18
The BIOS doesn't allow booting to USB, just CD, floppy, HD and via NIC.  Old BIOS but current.
 
Again, the distros that I have for Ubuntu work in other machines.  I'm thinking it is something in the BIOS and not the distro.

---

### Post by LHammonds on 2012-07-18
See if an Ubuntu Server 10.04 LTS x64 CD-ROM will boot on that machine.
 
I read somewhere that 12.04 dropped support for some particular hardware (non-PAE capable?)
 
LHammonds

---

### Post by Bill Z on 2012-07-19
> **LHammonds said:**
> See if an Ubuntu Server 10.04 LTS x64 CD-ROM will boot on that machine.
 
I read somewhere that 12.04 dropped support for some particular hardware (non-PAE capable?)
 
LHammonds

LHammonds.  That worked.  I found an iso of 10.04.4 server amd64, burned a DVD and it booted up.  I'm installing it right now.  

Now I wondering if applying upgrades will stop it from working. 

Always something.

---

### Post by Wim Sturkenboom on 2012-07-20
First step after install would be an upgrade to 12.04 in my opinion. It's better to find out now if it will work than later when there's no longer support for 10.04.

If it does not work, you might (depending on your needs) be better off with a distro that really has long term support.

---

### Post by LHammonds on 2012-07-20
> **Bill Z said:**
> Now I wondering if applying upgrades will stop it from working. 
Don't wonder.  Test it out now before you are stuck and cannot afford to test it out.

If I recall correctly, if you have a working 10.04 and do an in-place distribution upgrade to 12.04, it will retain the necessary support to keep the hardware working...but I would not trust my memory especially when the subject was only vaguely understood.  Just try it and see.

The main point that I got from those articles/posts that I read is that if 12.04 won't install directly, you may have to use an alternative 12.04 dvd that included support for older hardware "or" install 10.04 and then do an in-place upgrade.

Be sure to let us know what you find out so that others reading this can learn from your experience.

LHammonds

---

### Post by Bill Z on 2012-07-21
As you requested, I ran everything I know how to for any and all upgrades.  I ran aptitude full-upgrade then aptitude safe-upgrade then do-release-upgrade. 

After all of that , I ran shutdown -P now

After rebooting it still shows Build 10.04

Shouldn't is say something like Build 11.10?

I'm in very new territory now.  What should I do not to ether see if it is, in fact a newer version or run something to get it there?

Let me know,  I don't mind being used.

---

### Post by LHammonds on 2012-07-22
The [do-release-upgrade]("https://help.ubuntu.com/community/PreciseUpgrades/#Network_Upgrade_for_Ubuntu_Servers_.28Recommended.29") should have taken you straight to 12.04.

Run these commands to know exactly what is on your system:

```
lsb_release -a
uname -a
```LHammonds

---

### Post by Bill Z on 2012-07-22
lsb_release -a

No LSB modules are available.
Distributor ID: Ubuntu
Description: Ubuntu 10.04.4 LTS
Release: 10.04
Codename: lucid

uname -a

Linux Ubuntu-Server 2.6.32-41-Server #91-Ubuntu SMP Wed Jun 13 11:58:56 UTC 20 X86_64 GNU/Linux

---

### Post by LHammonds on 2012-07-23
When you ran the do-release-upgrade, did it say "No new release found"?  If so, you will need to look a bit closer at the article I linked to in the prior post.

LHammonds

---

### Post by Bill Z on 2012-07-25
It worked!

Last night I put the -d switch on and it started. 

I only had time this morning to warm boot it but it comes up as 12.04.

Tonight I will do a cold boot.  I'll post the results.

Thanks for your help and encouragement.

---

