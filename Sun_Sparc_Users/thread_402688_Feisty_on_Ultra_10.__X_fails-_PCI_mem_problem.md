---
title: "Feisty on Ultra 10.  X fails- PCI mem problem"
date: 2007-04-06
forum: Sun Sparc Users
---

### Post by chris_andrew on 2007-04-06
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/103605](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/103605) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Hi, all.

I have just done an install of Feisty on an Ultra 10.

The install went fine.  I then decided to install a graphical desktop, so installed _Ubuntu-Desktop_.

This all went fine, as well.  Unfortunately, when starting X, I get an error message:

xf86MapPciMem: Could not mmap PCI memory (some long address) (inappropriate ioctl for device)

I have run dpkg-reconfigure xserver-xorg, but still get the same error, as I don't know what the memory address should be.  As I have the standard PCI video card, that comes with the Ultra 10, I am concerned that this is a problem that should be ironed-out, before full release of Feisty.

Your help appreciated.

Many thanks,

Chris.

---

### Post by jnempu on 2007-04-11
> **chris_andrew said:**
> **This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/103605](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/103605) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Hi, all.

I have just done an install of Feisty on an Ultra 10.

The install went fine.  I then decided to install a graphical desktop, so installed _Ubuntu-Desktop_.

This all went fine, as well.  Unfortunately, when starting X, I get an error message:

xf86MapPciMem: Could not mmap PCI memory (some long address) (inappropriate ioctl for device)

I have run dpkg-reconfigure xserver-xorg, but still get the same error, as I don't know what the memory address should be.  As I have the standard PCI video card, that comes with the Ultra 10, I am concerned that this is a problem that should be ironed-out, before full release of Feisty.

Your help appreciated.

Many thanks,

Chris.

I got the same error in my ultra10 and sun blade100 but i use dapper, is strange that in two flavor of ubuntu its get the same error

---

### Post by timothyjones on 2007-04-16
Hello - I am in exactly the same predicament with 7.04 and a Sparc Ultra 5.  Beautiful server-only install, followed by trying to add xserver-xorg/kde.

I tried toggling the FrameBuffer flag in xorg.conf, and also taking the default color depth from 24 down to 16 and then 8, to no avail.

I'll be watching this thread for any progress!

---

### Post by chris_andrew on 2007-04-16
Timothy,

Can you add your comments to the bug report (link posted).

Cheers,

Chris.

---

### Post by chris_andrew on 2007-04-16
Looks like you already posted the bug info.

Thanks for that.

Cheers,

Chris.

---

### Post by timothyjones on 2007-04-18
I found a workaround on another page/bug, and it worked for me!

The workaround was to **[SIZE="2"]install the xserver-xorg packages from Debian's testing repository[/SIZE]**.  From there, I got the typical  "can't find font: fixed", which I have fixed countless times over the years by re-installing xfonts-base and adding all the font directories to the FontPath directives in /etc/X11/xorg.conf.

I am now posting from this sparc64 platform, with KDE and FF inside!

After years of using Debian, this is my first experience with Ubuntu.  I keep hearing all these wonderful things, and I just had to try.  I am so glad I did!  Thanks!



tlj

---

### Post by netztier on 2007-04-19
> **timothyjones said:**
> I found a workaround on another page/bug, and it worked for me!

The workaround was to **[SIZE="2"]install the xserver-xorg packages from Debian's testing repository[/SIZE]**.  From there, I got the typical  "can't find font: fixed", which I have fixed countless times over the years by re-installing xfonts-base and adding all the font directories to the FontPath directives in /etc/X11/xorg.conf.



Which release of Ubuntu are you using there? 6.06 LTS, 6.10 or 7.04? From what I gathered last, the workaround with using Debian's x.org executable doesn't work for 7.04 anymore.

best regards

Marc

---

### Post by timothyjones on 2007-04-19
I am using the Sparc64 edition of 7.04 (beta) on a Sun Ultra 5 with 256M of RAM, an external 9.0G SCSI drive, and an internal IDE CD-ROM (there is an internal IDE disk also, but it seems to prevent booting at all, so I unplugged it - obviously the drive is bad).

I can't answer to what other people have experienced, especially since I am new to Linux-on-Sparc, and new to Ubuntu.  But my X server gave this error until I installed the X packages from debian/testing.  


tlj

---

### Post by keirnna on 2007-08-26
> **timothyjones said:**
> I am using the Sparc64 edition of 7.04 (beta) on a Sun Ultra 5 with 256M of RAM, an external 9.0G SCSI drive, and an internal IDE CD-ROM (there is an internal IDE disk also, but it seems to prevent booting at all, so I unplugged it - obviously the drive is bad).

I can't answer to what other people have experienced, especially since I am new to Linux-on-Sparc, and new to Ubuntu.  But my X server gave this error until I installed the X packages from debian/testing.  


tlj

Exactly which repo did you add? I have an ultra 10 with Ubuntu 7.10 on it, but I have the same problem. I can't find this "testing repo".

---

