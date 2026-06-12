---
title: "How to create a nice chainloader gurb list that will not get erased or renamed?"
date: 2012-09-15
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by heavyonion on 2012-09-15
What an absolute mess I have on my hands! I just want to create a nice grub menu to choose between distros. I have PC-BSD 9 on sda1 , Windows 7 on sda2 , openSUSE 12.2 on sda 4, extended sda3 ,  swap on sda5, Ultimate Edition 3.4 on sda 6 , Sabayon 9 on sda 7 , and Ubuntu 12.10 on sda 8. I can't seem to generate a consistent and reliable Grub menu. Your help would be greatly appreciated.
Thanks for your time.

---

### Post by Quackers on 2012-09-15
heavyonion, you say that you can't get a consistent grub menu.
What exactly is happening? How is it inconsistent?

---

### Post by darkod on 2012-09-15
Another thing you fail to mention is which grub are you using from all those distros? And is it grub1 or grub2?

You can use ubuntu's grub2 for example, which offers great flexibility and user control.

---

### Post by heavyonion on 2012-09-15
I am using Ubuntu 12.10 default grub i believe it is grub2. In the past I have just installed distros and the menu kind of takes care of itself. If there is a problem then I just run Boot-Repair cd and whala! This time I have installed the list of OS's as stated above and I cannot boot into Windows or PCBSD. I obviously need to set the boot menu manually. I need to know how to do this. Also anytime I update a system it changes the boot menu. I need to set up a grub menu that will not be affected by updates and that I can boot to any system listed. Thank you.

---

### Post by Elfy on 2012-09-15
moved

The grub in 12.10 has recently changed, it is I believe having some issues with other older grubs.

You might be better having one of the other systems controlling grub if you are not wanting the issues you might get using a dev version and letting it control grub and boot.

---

### Post by sgage on 2012-09-15
> **Elfy said:**
> moved

The grub in 12.10 has recently changed, it is I believe having some issues with other older grubs.

You might be better having one of the other systems controlling grub if you are not wanting the issues you might get using a dev version and letting it control grub and boot.

Another thing to keep in mind is to have the other distros' partitions mounted at the time you run update-grub...

---

### Post by Elfy on 2012-09-15
> **sgage said:**
> Another thing to keep in mind is to have the other distros' partitions mounted at the time you run update-grub...

new one on me = useful stuff, thanks :)

---

### Post by oldfred on 2012-09-15
I have not experimented with grub2 2.00 much yet. But it does some things differently.

We have found that with LVM installs for example they have to be mounted to get grub to find them. I think grub now has so many add in modules and does not always load them unless you tell it.

How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[http://ubuntuforums.org/showthread.php?t=1542338](http://ubuntuforums.org/showthread.php?t=1542338)
I find the partition boot to my 12.10 gives a partition not found then boots?

But I use a config file to boot my ISO and find that simplies menu greatly. The issue is updating a fixed menu. You lose the automation that os-prober gives. 

Total Custom menu:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu)
[http://ubuntuforums.org/showthread.php?t=1483827](http://ubuntuforums.org/showthread.php?t=1483827)

Do not know if this works with grub2 2.00 or not:
HOWTO: Grub Customizer Updated for grub 1.99 
[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)
The Grub 2 Guide (formerly Grub 2 Basics) manual way
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by YannBuntu on 2012-09-17
Hello

> **heavyonion said:**
> I am using Ubuntu 12.10 default grub i believe it is grub2. In the past I have just installed distros and the menu kind of takes care of itself. If there is a problem then I just run Boot-Repair cd and whala! This time I have installed the list of OS's as stated above and I cannot boot into Windows or PCBSD.

- What is the URL returned by Boot-Repair please?

- as said above, 12.10's GRUB is in development... do you have the same problem with 12.04?

---

### Post by jerrylamos on 2012-09-17
When I want human readable grub menu's I use this file to create menu's appearing before Grub's usual set, make up an entry and copy it to: 

/etc/grub.d/06_custom

sudo update-grub

And/or to create menu's appearing after grub's set I append it to:

/etc/grub.d/40_custom

sudo update-grub
 
Here's a sample:

/etc/grub.d/40_custom
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry 'meerkat on sdb1' {
set root=(hd1,1)
linux /vmlinuz root=/dev/sdb1 ro quiet
initrd /initrd.img
}
menuentry "quantal sda6" {
set isofile="/quantal-desktop-i386.iso"
loopback loop (hd0,6)$isofile
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile noprompt noeject
initrd (loop)/casper/initrd.lz
}

You can try various configs.  I've found Ubuntu is quite happy to boot with menu entries a whole lot simpler than the complex mess that Grub creates.  Do note the file needs to be executable if it isn't already:

sudo chmod +x /etc/grub./40_custom

The second menu entry is for directly booting a hard drive .iso file into a live ubntu.  I do installs from such a live, but do note it is necessary to open a terminal and do a 
df
to find out which partition is mounted as the isodevice, /dev/sda6 in this case:

sudo umount -r -l /dev/sda6

and then I can test the .iso live and even go ahead and do an install.  No CD or DVD ir USB required.

After install or after any update where Ubuntu update changes /boot/grub/grub.cfg I then

sudo cp -dpuv 40_custom /etc/grub.d/40_custom
sudo update-grub

As I try various things sometimes they don't work so I scramble a bit.  Fun.

---

### Post by kansasnoob on 2012-09-17
*oldfred* already included a link to this but I always use this on my htpc:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu)

of course that box doesn't get changed nearly as often as my other boxes that get changed sometimes almost daily ;)

---

