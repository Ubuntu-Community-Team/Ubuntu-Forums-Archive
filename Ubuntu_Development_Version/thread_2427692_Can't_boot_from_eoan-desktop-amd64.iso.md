---
title: "Can't boot from eoan-desktop-amd64.iso"
date: 2019-09-24
forum: Ubuntu Development Version
---

### Post by kagashe on 2019-09-24
I downloaded the iso from [http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)
and tried to boot from grub:
```
menuentry "Eoan Desktop iso" {
            set isofile="~/eoan-desktop-amd64.iso"
            loopback loop (hd0,X)$isofile
            linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile noprompt noeject
            initrd (loop)/casper/initrd
    }

```
but got this error
```
/scripts/casper-premount/20isoscan: line 59: try_mount: not found
```

There is a [Bug reported on launchpad]("https://bugs.launchpad.net/ubuntu-cdimage/+bug/1841455") by a user on 2019-08-26 in this regard.

But I thought I should report here since the Bug is not replied.

Kamalakar

---

### Post by guiverc on 2019-09-24
That bug has not been reported in eoan ISO testing  ([http://iso.qa.ubuntu.com/qatracker/reports/bugs/1841455](http://iso.qa.ubuntu.com/qatracker/reports/bugs/1841455)) which could provide a greater chance of being noticed. 

The bug also didn't have any 'tags' (eoan & iso-testing have now been added), but since the bug impacts you, I'd suggest downloading the latest ISO & recording a test on [http://iso.qa.ubuntu.com/qatracker/milestones/404/builds](http://iso.qa.ubuntu.com/qatracker/milestones/404/builds) so it appears in eoan ISO testing reports.

---

### Post by kagashe on 2019-09-25
> **guiverc said:**
> I'd suggest downloading the latest ISO & recording a test on [http://iso.qa.ubuntu.com/qatracker/milestones/404/builds](http://iso.qa.ubuntu.com/qatracker/milestones/404/builds) so it appears in eoan ISO testing reports.

I am not sure whether booting from iso is a recognised method for iso testing or not. I prefer booting directly from iso since I could update it through zsync and boot the updated version.

I made a Startup disk from the iso on my existing Ubuntu 18.04 installed system and I could boot into current live Ubuntu 19.10 from the USB, however, the fact remains that I could not boot directly from iso.

Kamalakar

---

### Post by guiverc on 2019-09-25
To me the testcase would be 'live session' and I would expect it to be a standard 'try ubuntu'; as the difference as I saw it, was you're just **not** booting from the usual cd/dvd/thumb-drive, and you can note this in the comments.

The wording does differ for the various flavors (eg. Lubuntu's live says only to "[COLOR=#3B3B3B][FONT=Georgia]Boot up the image[/FONT][/COLOR]") which is what you'd be doing, but if the testcase for your flavor doesn't match, don't do it - or make it clear what you're doing in the comments. If you have problems - then it's a normal launchpad bug report which will be linked to the QA-test once you enter the bug report number (this to me is the point; it allows easy date & frequency automatic bug tracking)

---

### Post by sudodus on 2019-09-25
@kagashe,

Your problem with booting from grub and that bug report made me check if mkusb can create a live drive with the current daily iso file of Ubuntu Eoan.

The reason is that mkusb uses grub to boot both in BIOS mode and UEFI mode when creating a persistent live drive.

I ran mkusb-dus in an installed Ubuntu system with 18.04.x

```

dus eoan-desktop-amd64.iso

```

The result, a persistent live drive with Ubuntu Eoan works as it should.

So maybe something is wrong with your menuentry. I am guessing here: Are you sure that grub can resolve the tilde character **~**? Have you pointed to other (older) iso files that way and it has worked?

[hr][/hr]
**Edit**: After thinking a while, I would like to ask: Where do we think that the bug is located: In the grub that is running or in the iso file?

Also, mkusb is not booting via grub into an iso file, but into a cloned image of an iso file (residing in partition #4). So there is a difference.

---

### Post by kagashe on 2019-09-25
> **sudodus said:**
> @kagashe,
So maybe something is wrong with your menuentry. I am guessing here: Are you sure that grub can resolve the tilde character **~**? Have you pointed to other (older) iso files that way and it has worked?.
The tilde character is not there in the actual path (/home/user/eoan-desktop-amd64.iso) I have indicated it here to show that the iso is placed in the home folder of sdaX. I am using this method to test all Ubuntu Development versions so far. In fact the menuentry for disco-desktop-amd64.iso still exist and I can boot it.

> 
[hr][/hr]
**Edit**: After thinking a while, I would like to ask: Where do we think that the bug is located: In the grub that is running or in the iso file?

There is a hint about the location of the bug by John Little in the reply on [Launchpad Bug]("https://bugs.launchpad.net/ubuntu-cdimage/+bug/1841455")  which is reproduced below:
```
I was trying the Kubuntu eoan daily build. I had a look in the squashfs. In the initramfs-tools/scripts/casper-premount/20iso_scan script, it invokes the find_path function, which is defined in scripts/lupin-helpers. It's line 59 of that script that has the try_mount invocation. In my disco iso the try_mount function is defined in scripts/casper-helpers, but the eoan version does not.

```

Kamalakar

---

### Post by sudodus on 2019-09-25
Thanks Kamalakar,

I have been testing too, with grub booting into the iso files
```

/lubuntu-18.04.1-desktop-amd64.iso
/ubuntu-eoan-desktop-amd64.iso

```
and I have identified the **initrd** files in the iso files, so with /etc/grub.d/40_custom
```

#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

menuentry "Eoan Desktop iso" {
            set isofile="/ubuntu-eoan-desktop-amd64.iso"
            loopback loop (hd0,1)$isofile
            linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile noprompt noeject
            initrd (loop)/casper/initrd
}
menuentry "Lubuntu 18.04.1 Desktop iso" {
            set isofile="/lubuntu-18.04.1-desktop-amd64.iso"
            loopback loop (hd0,1)$isofile
            linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile noprompt noeject
            initrd (loop)/casper/initrd.lz
}

```

Booting from grub (into an iso file) works with the 18.04.1 iso file, but not with the Eoan iso file where I get the same error output as you. In other words, you are right, and I will click 'affects me too' in the bug report.

/Nio

---

### Post by kagashe on 2019-10-03
SOLVED after zsync iso to version 2019-10-01 15:12

Kamalakar

---

### Post by sudodus on 2019-10-04
Yes, now grub-n-iso works for me too, tested with the lubuntu eoan iso file dated Oct 3 :-)

---

