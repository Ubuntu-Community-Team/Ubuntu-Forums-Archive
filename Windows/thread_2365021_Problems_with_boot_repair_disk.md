---
title: "Problems with boot repair disk"
date: 2017-07-01
forum: Windows
---

### Post by equitube on 2017-07-01
I have a laptop (Acer Aspire 5920) that had a dual boot Win 7 and Mint on it. I was trying to remove the Mint and following the 'helpful' advice on a Windows (sic) forum, I used Windows disk manager to delete the Linux partitions. I didn't realize that Grub had overwritten the Windows MBR. 

I rebooted, expecting it not to boot into anything. I'd read a number of Linux forums by then and had downloaded the Boot Repair Disk and burned it to CD rom. 

I booted from the live cd. Attempted to repair (choosing the auto option) and it didnt' work. I am at grub rescue prompt. Running an ls command gives me the following partitions:

(hd0) (hd0, msdos2) (hd0, msdos1) 

I did get a pastebin url from the disk 
[Https://paste.ubuntu.com/24995357/](Https://paste.ubuntu.com/24995357/)

Thanks in advance for your assistance. I almost never use Windows anymore but this laptop belongs to a family member that doesn't want to learn Linux. 

I should add that I don't have a Windows install or repair disk handy and the only other method I have for Internet access are Android devices. 

Steven Peterson 
Aspiring Android Developer and Recovering Windows Expert

---

### Post by leunam12 on 2017-07-01
There is an option on Boot-Repair to fix the MBR, I have used it in the past to fix windows 7 booting problems, you should try that.
If you are not successful with boot-repair, then, turn the computer on and start pressing F8 repeatedly, maybe you will be able to access the Windows recovery partition, if you can, then go to a command prompt and try to repair MBR from there. Check the guide below

[https://neosmart.net/wiki/fix-mbr/#Fix_the_MBR_in_Windows_7](https://neosmart.net/wiki/fix-mbr/#Fix_the_MBR_in_Windows_7)

Another option is to have a friend or a relative make a Windows recovery disk for you, or maybe buy one online from ebay, such as the one on the link below.

[https://rover.ebay.com/rover/1/711-53200-19255-0/1?icep_id=114&ipn=icep&toolid=20004&campid=5338055221&mpre=http%3A%2F%2Fwww.ebay.com%2Fitm%2FWINDOWS-7-32-64-bit-Recovery-ReInstall-Repair-Disc-Home-basic-Premium-Pro-%2F112077852604%3Fepid%3D844679365%26hash%3Ditem1a185c4fbc%3Ag%3A89UAAOSwUdlWe3w5](https://rover.ebay.com/rover/1/711-53200-19255-0/1?icep_id=114&ipn=icep&toolid=20004&campid=5338055221&mpre=http%3A%2F%2Fwww.ebay.com%2Fitm%2FWINDOWS-7-32-64-bit-Recovery-ReInstall-Repair-Disc-Home-basic-Premium-Pro-%2F112077852604%3Fepid%3D844679365%26hash%3Ditem1a185c4fbc%3Ag%3A89UAAOSwUdlWe3w5)

---

### Post by yancek on 2017-07-01
Simplest method would have been to install Ubuntu to the partition on which you previously had Mint installed and accepted the defaults.  What is preventing you from doing that now?
Trying to repair Grub with boot repair will not work because it needs the files on the Mint partition which you deleted.  Using the Advanced options suggested above or installing Ubuntu to the same partition you had Mint on should work.  Is your windows 7 an MBR install rather than UEFI?

---

### Post by equitube on 2017-07-01
Thank you but I am well aware of the Windows methods. I've administered Win systems for 2 decades.  none of those will work however with the exception of getting a disk. Ironically there's an iso image of Win 7 on the desktop. I didn't have any dvd's or I would have burned one. I've got one across  town. Ill have to get it. 

Tjanks for your help.

What prevents me is that those partitions no longer exist. Perhaps I could use gparted to recreate them, but I don't know. Thanks for your help

If I installed Ubuntu, would that repair Grub? I usually use 3 partitions on a Linux install, program, home, and swap if I recall. Would that need to be replicated? 

I supppse I could d/l a copy of a repair disk and use DriveDroid to boot the laptop from one of my phones. I've done thst before with mixed results

---

### Post by howefield on 2017-07-01
Thread moved to the "*Windows*" forum.

---

### Post by yancek on 2017-07-01
The boot repair output from the link in your original post shows that  the Grub code from the Mint install is in the MBR of the drive and looks for grub.cfg (boot menu file) on sda5 which has been deleted.
It also shows that you have two partitions with windows filesystems that take up almost the entire drive.  The usual process used would be to boot windows and shrink the partition to create unallocated space on which to install Ubuntu then reboot into windows and run chkdsk because you have changed partitions.  You should be able to also do this from a windows Repair disk if you can get one.

You should be able to boot GParted either from a separate CD or from the Ubuntu media which contains GParted.  You can resize (shrink) the windows partition that way although you are always better off using windows to do things of that nature.  The GParted online manual is at the link below.  Scroll down to the section "Resizing a Partition" for specifics.

   [http://gparted.org/display-doc.php%3Fname%3Dhelp-manual](http://gparted.org/display-doc.php%3Fname%3Dhelp-manual)

---

### Post by equitube on 2017-07-01
Thank you for your helpful advice. I am actually trying to remove Linux from this machine. (I know, I'd rather remove Windows but it's not mine. 

I am familiar with gparted. It's the first place I go when doing Linux installs. It never hurts to read the manual though. 

I have a Win 7 disk on the way here. I'll run fix mbr from the recovery console or just do a reinstall. I'm upgrading it to Win 10 anyway. Then it's back to Linux and Android. I've been nearly Winfree since oh-one-three.

---

### Post by oldfred on 2017-07-01
Boot-Repair should have only seen Windows and installed the syslinux boot loader which is a Windows  type boot loader.
You also should be able to use Boot-Repairs' advanced options and choosen Windows and sda options.
Only if Windows is hibernated or if newer Windows 8 or 10 and fast start is on may Linux not correctly see the NTFS partitions to know if it has boot files.

You can also install syslinux or Lilo boot loaders to MBR, not full install of entire boot loader, just the part in the MBR that works like Windows boot loader.

       Boot live cd -  knoppix or Ubuntu 
sudo apt-get install syslinux
sudo dd if=/usr/lib/syslinux/mbr.bin of=/dev/sda

---

### Post by equitube on 2017-07-02
No, boot repair couldn't do it. Neither could the advanced tools. The simple solution for me was  finding an old copy of Tiny Win 7, shrinking the main partition a bit and booting from cd. 

It fixed the MBR automatically and now gives me 2 Windows I can boot to in the Bootloader screen. I will take tiny 7 off by eliminating its partion. Windows handles its own recovery better and easier than Linux. 

However, I still generally refuse to use WinBlows. I administered Win Networks for years and learned what a bloated, patchwork, unstable OS it really is.

---

