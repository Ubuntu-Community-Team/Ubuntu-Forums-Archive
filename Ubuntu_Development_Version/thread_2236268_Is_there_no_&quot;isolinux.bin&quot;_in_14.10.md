---
title: "Is there no &quot;isolinux.bin&quot; in 14.10?"
date: 2014-07-25
forum: Ubuntu Development Version
---

### Post by xmbwd on 2014-07-25
I am trying to use various programs (e.g., remastersys, relinux, etc.) to create an .iso of the 14.10 build plus my modifications.  These tools work fine on 14.04, but on 14.10, they fail -- with an error regarding isolinux.bin.

For remastersys, the error is:

```
genisoimage: Uh oh, I cant find the boot image     'isolinux.bin'
```

For relinux, the error is:

```
cp: cannot stat '/usr/lib/syslinux/isolinux.bin': No such file or directory
```

In 14.04, isolinux.bin can be found at: /usr/lib/syslinux/isolinux.bin.
In 14.10, at least the install I am using -- which seems to work perfectly otherwise, there is no isolinux.bin (in terminal "locate isolinux.bin" returns nothing).  And there is no folder "syslinux" in /usr/lib.

Am I working off of a flawed install of 14.10?  Or is isolinux.bin no longer used, and therefore these programs won't work on 14.10?

---

### Post by nerdopolis on 2014-08-05
Try installing the package isolinux
and modifying remastersys like this diff
[http://rebeccablackos.svn.sourceforge.net/viewvc/rebeccablackos/rebeccablacklinux_files/usr/import/usr/bin/remastersys?r1=2676&r2=2466](http://rebeccablackos.svn.sourceforge.net/viewvc/rebeccablackos/rebeccablacklinux_files/usr/import/usr/bin/remastersys?r1=2676&r2=2466)

I can't get it compatible with the Live USB creation tool yet...

EDIT: Not even the standard ISOs from Ubuntu work with the startup USB creator anymore

---

### Post by cariboo on 2014-08-06
If you already have a Linux distribution running on your system, use dd:

```
dd if=utopic-desktop-amd64.iso of=/dev/sdX bs=1M
```

where /dev/sdX = your USB device.

---

### Post by xmbwd on 2014-08-06
I haven't tried your suggestion yet.  But you should use [Multisystem]("http://sourceforge.net/projects/multisystem/") for the live USB stick.  It works great. And you can both create a persistent iso and install multiple isos on the same disk.  Great for creating a super-rescue disk.  Or just a backup of your system -- once you get Remastersys to work.

> **nerdopolis said:**
> Try installing the package isolinux
and modifying remastersys like this diff
[http://rebeccablackos.svn.sourceforge.net/viewvc/rebeccablackos/rebeccablacklinux_files/usr/import/usr/bin/remastersys?r1=2676&r2=2466](http://rebeccablackos.svn.sourceforge.net/viewvc/rebeccablackos/rebeccablacklinux_files/usr/import/usr/bin/remastersys?r1=2676&r2=2466)

I can't get it compatible with the Live USB creation tool yet...

EDIT: Not even the standard ISOs from Ubuntu work with the startup USB creator anymore

---

### Post by xmbwd on 2014-08-06
I am not sure what this will do other than create a USB stick with the stock Utopic on it.  I'm trying to get Remasytersys to work, so I can put a modified live version of Utopic on a bootable USB.  

> **cariboo907 said:**
> If you already have a Linux distribution running on your system, use dd:

```
dd if=utopic-desktop-amd64.iso of=/dev/sdX bs=1M
```

where /dev/sdX = your USB device.

---

### Post by grahammechanical on 2014-08-06
My Utopic Unicorn Software Centre has isolinux 3:6.03~pre18+dfsg-1 available for download. It is not installed by default. I also have /usr/lib/syslinux; /usr/lib/SYSLINUX; and /usr/lib/syslinux-legacy but without isolinux.bin because it is not installed.

It seems that isolinux is not installed as part of the syslinux package any more.

Regards.

---

### Post by nerdopolis on 2014-08-06
> **xmbwd said:**
> I haven't tried your suggestion yet.  But you should use [Multisystem]("http://sourceforge.net/projects/multisystem/") for the live USB stick.  It works great. And you can both create a persistent iso and install multiple isos on the same disk.  Great for creating a super-rescue disk.  Or just a backup of your system -- once you get Remastersys to work.

Wow, I might look into that, as I'm always using USB to test my Live CD on real hardware.
Anyway the issue that I get is that when I create my ISO as a bootable USB, it returns:
 ```
vesamenu.c32 isn't a valid COM32r file
```
However I tried with a vanilla Utopic ISO, and I get the same error as well, so that part is probably an upstream bug...

---

### Post by xmbwd on 2014-11-16
Well, I found a replacement for Remastersys that works great in 14.10.  It is called [Systemback]("http://sourceforge.net/projects/systemback/"), and it has the ability to create a live .iso, as well as other great features.  Just a great program.

---

### Post by cariboo on 2014-11-16
With that, thread closed.

---

