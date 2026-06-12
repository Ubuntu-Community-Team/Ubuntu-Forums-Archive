---
title: "BootCamp Style Grub / Burg control"
date: 2014-08-13
forum: Ubuntu, Linux and OS Chat
---

### Post by gushy on 2014-08-13
Hi Guys,

At home I use a standard PC dual booting Ubuntu and Windows 7 and at work I've got a dual boot Mac with Windows 7.

I've really come to like the BootCamp utility in Windows (and the BootChamp app for OSX) that allows you to select to reboot into the other OS.  I'd love to have 0 seconds set on my Grub (or Burg) and be able to do this with Ubuntu / Windows at home.

Does anyone know of any GUI utilities that do this? - Yes I could just edit my grub.conf when in Ubuntu but that's a pain in the backside and I'm not aware of a way I can do this from Windows.

Thanks,

---

### Post by oldfred on 2014-08-13
I had a gui app for that with OS/2 back when installing that was a big stack of floppy disks. Not sure how that worked. Whether OS/2 controlled boot or just dd'd a new MBR with a script. Not even sure how to do that in Windows. Or maybe it moved the boot flag and had boot code in PBR or partition boot sector as that is how Windows does it, but grub2 does not like to be installed to a PBR.

You could force grub2 into PBR even though not recommended and create scripts to run commands to move boot flag from Windows to Ubuntu partition. If Ubuntu is in a logical partition you would have to use the Lilo boot loader. Windows checks for primary only, where Lilo works the same to use boot flag, but does not care if primary or logical partition.

You also could just create a separate FAT32 grub only boot partition. And then create two boot stanza's for Windows & Ubuntu and scripts to change default from 0 or 1.

Or it will take a bit of work, unless someone knows of an application to do it.

Some just decide to use an external flash drive for grub and leave internal for Windows boot loader.

With new systems & UEFI boot loader you can easily choose boot from one time boot key and using efibootmgr change boot order or even a one time boot entry.

---

### Post by gushy on 2014-08-13
I never considered a fat32 partition or a grub usb, both seem so obvious now you've said it.

My other reason for wanting a bootcamp style app is that my usb bluetooth dongle doesn't work at the bios or grub and it's a pain to have to plug in a wired keyboard when I want to change OS.

Thanks for the advice.

---

### Post by oldfred on 2014-08-13
You can install several ways to flash drive. You can just install grub from your working Ubuntu to MBR and then entire rest of flash drive can be used for data. Only MBR is used.

Or you can install grub to flash drive with its own partition. You can then create a grub.cfg with whatever entries you want. I do this and put multiple ISO on drive and use grub to boot them and add an entry or two to also boot my installs on hard drive. Then I have a multi-use repair/boot flash drive.

 #reinstall from working (not liveCD/DVD/USB) system - first find Ubuntu drive (example is drive sdb but use your drive not partitions):
sudo fdisk -l
#if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb
#If that returns any errors run:
sudo grub-install --recheck /dev/sdb
sudo update-grub

[http://askubuntu.com/questions/388382/multi-partition-multi-os-bootable-usb/388484#388484](http://askubuntu.com/questions/388382/multi-partition-multi-os-bootable-usb/388484#388484)       

 Install grub2 to USB -general info, note that path for 12.10 and later to flash drive includes your $USER name
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB)

   [https://wiki.archlinux.org/index.php/GRUB2#Booting_an_ISO_Directly_From_GRUB2](https://wiki.archlinux.org/index.php/GRUB2#Booting_an_ISO_Directly_From_GRUB2)
Reported to have a few typos? But shows process on one page
[http://www.pendrivelinux.com/install-grub2-on-usb-from-ubuntu-linux/](http://www.pendrivelinux.com/install-grub2-on-usb-from-ubuntu-linux/)


 This will boot an ISO from a hard drive or any second drive
ISO Booting with Grub 2 from Hard drive - drs305
[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)
Examples - you may copy & edit for your path & ISO version
[https://help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples)
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)

If you create a full grub flash drive you want an entry that you do not have to maintain. Something like this boots the link to the most current kernel in / (root) that dpkg maintains with Debian based installs.

 menuentry "Latest Kernel in sda1" {
insmod ext2
set root=(hd0,1)
linux /vmlinuz root=/dev/sda1 ro
initrd /initrd.img
}

Or if you want a link to the grub.cfg in the install. This is to a gpt partitioned drive.
 configfile (hd0,gpt7)/boot/grub/grub.cfg

---

