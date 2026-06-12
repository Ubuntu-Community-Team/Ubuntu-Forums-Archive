---
title: "PC still boots 16.10 after installing 17.04"
date: 2017-03-25
forum: Ubuntu Development Version
---

### Post by The Cog on 2017-03-25
I have gone through the usual installation process installing 17.04 (beta) from a live USB onto this laptop. However, after the install is finished, the laptop still boots to 16.10 (on a different partition). I suspect that the installer may be writing to the msdos boot area rather than to the efi boot area.

The installer stick is basically OK because I was able to install 17.04 to a different (msdos not uefi) PC with it.

This is my partition table as seen from 16.04:
```
steve@StevesLappy:~$ sudo lsblk -f
NAME   FSTYPE LABEL UUID                                 MOUNTPOINT
sr0                                                      
sda                                                      
&#9500;&#9472;sda4 swap         64a79b1f-b632-47f3-b722-12ed357ecf22 [SWAP]
&#9500;&#9472;sda2 ext4         d82e6acb-2644-4357-baa2-1916f29a9824 /
&#9500;&#9472;sda5 ext4         8b004153-1abf-4991-b541-c8eb2b96298f /home
&#9500;&#9472;sda3 ext4         dd77b6db-1244-44b4-9ec8-de778d85b4d2 
&#9492;&#9472;sda1 vfat         EC08-E69E                            /boot/efi

```

I am installing 17.04 to sda3. The installation process says it is complete as usual, but upon reboot, I just boot straight back into 16.10 on sda2. If I mounbt sda3, I can see that etc/lsb-release says it's Zesty 17.04, so I think the only issue is the bootloader. There doesn't seem to be an option to choose msdos or efi as the boot method but I did see a suggestion that in the partitioner (I choose "something else") that as well as reformatting sda3 and using it as "/" I should use sda1 as /boot/efi. I tried this but no difference. /etc/fstab on sda3 contains the lines:
```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda3 during installation
UUID=dd77b6db-1244-44b4-9ec8-de778d85b4d2 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=EC08-E69E  /boot/efi       vfat    utf8,umask=007,gid=46 0       1
# swap was on /dev/sda4 during installation
UUID=64a79b1f-b632-47f3-b722-12ed357ecf22 none            swap    sw              0       0
```

Any ideas would be welcome. Thanks.

Edit:
P.S. I don't get a grub menu, it just boots straight into 16.10 which is what happened before, when there was no OS on sda3, so again, it appears that grub has not been updated by the installer. 
I don't know it it is significant, but the fstab line for the efi partition is different - in the old 16.10 install, the line reads:
```
UUID=EC08-E69E  /boot/efi       vfat    umask=0077      0       1
```

---

### Post by dino99 on 2017-03-26
Looks like the 'main' grub is managed by sda2 and you was not using the login step. Hitting F8 at boot time let you select the partition.

---

### Post by The Cog on 2017-03-26
> **dino99 said:**
> Looks like the 'main' grub is managed by sda2 and you was not using the login step. Hitting F8 at boot time let you select the partition.

I'm not sure what you mean by that. What do you mean by "you was not using the login step"?

Except that sda2 was the original system installed (I left sda3 empty for future use at the time) so that yes, it seems that the bootloader in use is the one that was written by sda2 when it was the only OS on the system. Maybe I am showing my ignorance, but I am thinking that maybe the sda2 bootloader is located on the efi partition sda1, and the sda3 bootloader is being placed in the MBR which the laptop is not using.

---

### Post by oldfred on 2017-03-26
If UEFI system, you have to switch to BIOS/MBR in UEFI to boot an BIOS install.
Better to install in UEFI mode. And Boot-Repair should be able to convert a BIOS install to UEFI, by uninstalling grub-pc and installing grub-efi-amd64.

Also back up the ESP - efi system partition. Any second install of Ubuntu will overwrite the /EFI/ubuntu folder in the ESP. And new install will then be default install in UEFI and only grub menu will let you boot first install.
I now know I only need to edit /EFI/ubuntu/grub.cfg to point to old install or just restore old grub.cfg from backup to boot my main working install.

How you boot install media, UEFI or BIOS is how it installs. If UEFI and you want UEFI be sure to always boot in UEFI mode.
 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by mc4man on 2017-03-26
You could also for curiosity's  sake boot into 16.10 & run sudo update-grub to see if it finds 17.04

---

### Post by The Cog on 2017-03-26
Well, that's interesting. I ran sudo update-grub on 16.10 and it added 17.04 to the boot menu (I wasn't getting to see a boot menu before, presumably because there was no choice of OS). So I booted 17.04 and ran sudo update-grub from there. It says it's adding boot menu entry for efi firmware, but grub menu I see next time I reboot still defaults to 16.04 with 17.10 Zesty beneath, so clearly it is still not actually updating the bootloader properly.

I am tempted to try grub-install from 17.04, but can't do any more until later today - have to go out now.

---

### Post by mc4man on 2017-03-26
> **The Cog said:**
> Well, that's interesting. I ran sudo update-grub on 16.10 and it added 17.04 to the boot menu (I wasn't getting to see a boot menu before, presumably because there was no choice of OS). So I booted 17.04 and ran sudo update-grub from there. It says it's adding boot menu entry for efi firmware, but grub menu I see next time I reboot still defaults to 16.04 with 17.10 Zesty beneath, so clearly it is still not actually updating the bootloader properly.

I am tempted to try grub-install from 17.04, but can't do any more until later today - have to go out now.

There is a command that I never remember so I just re-install grub from the install I want to take precedence/control. 
(- could of been sudo dpkg-reconfigure grub-efi-amd64 though as I remember it asks too many questions for me...

So here that would be the  grub-efi-amd64 package, i.e. boot to 17.04 & re-install that package, 

sudo apt install  --reinstall grub-efi-amd64

---

### Post by dino99 on 2017-03-26
> **The Cog said:**
> Well, that's interesting. I ran sudo update-grub on 16.10 and it added 17.04 to the boot menu (I wasn't getting to see a boot menu before, presumably because there was no choice of OS). So I booted 17.04 and ran sudo update-grub from there. It says it's adding boot menu entry for efi firmware, but grub menu I see next time I reboot still defaults to 16.04 with 17.10 Zesty beneath, so clearly it is still not actually updating the bootloader properly.

I am tempted to try grub-install from 17.04, but can't do any more until later today - have to go out now.

nothing special here ;)  grub menu is not displayed on system with only one os/version installed (useless because there is no choice to boot on something else :lolflag: )

---

### Post by The Cog on 2017-03-26
OK, using synaptic I can see that grub-pc is installed on 17.04 and not grub-efi. On the old 16.10, grub-efi-amd64 is installed. To my mind, this confirms that the wrong grub was installed by the 17.04 installer. Now, I guess that I could just install grub-efi-amd64 by hand, but what I would really like to know is how to get the installer to install the efi version of grub. Otherwise I will keep on hitting this problem every time I install.

How on earth do you tell ubiquity to install grub-efi instead of grub-pc?

---

### Post by mc4man on 2017-03-26
I just put in a new Ubuntu 17.04 install on a Haswell machine & no issue, it choose EFI. Before that did try Xubuntu beta2 thru starting an install & it also would have been EFI, no obvious choice to do otherwise..

However on an older laptop which can use EFI (Ivybridge) on the boot selection screen there would be 2 choices for the usb device, one would just say something like Usb Device (Sandisk), the other Usb EFI Device (Sandisk). I'd assume the former choice would do a bios/grub-pc install if chosen.
Do you have something like this?

---

### Post by The Cog on 2017-03-27
> **mc4man said:**
> However on an older laptop which can use EFI (Ivybridge) on the boot selection screen there would be 2 choices for the usb device, one would just say something like Usb Device (Sandisk), the other Usb EFI Device (Sandisk). I'd assume the former choice would do a bios/grub-pc install if chosen.
Do you have something like this?

AAh!!!
Yes. Because it lists the options in a strange order, I didn't notice the USB stick (UEFI) option amongst the other hard disk and ethernet boot options - I just saw the USB stick option at the end of the list. Choosing the USB (UEFI) option did the trick. Thank you. I will remember this in future.

I would think ubiquity would be better off with a couple of checkboxes for install in BIOS or UEFI or both, but maybe there is a good reason why not.

---

