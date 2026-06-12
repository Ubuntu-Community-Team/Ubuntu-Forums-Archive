---
title: "Remove Windows option"
date: 2020-03-02
forum: Windows
---

### Post by KMJones1 on 2020-03-02
At some point I installed a Windows 10 loader and didn't use it. It appears on the boot list as an option with Ubuntu. It completely fails to work on this very basic machine (after several hours trying!). I would therefore like to remove all the Windows folders etc. and just use Ubuntu.
Can I just delete all those folders that seem to be Windows? Or is there are safer way?
Thanks!

---

### Post by ajgreeny on 2020-03-02
Let's see the output of ***sudo fdisk -l*** in terminal first as that will give us a good idea of the partition setup in your machine.

I'm not sure what you mean by a Windows 10 loader so hopefully you can tell us in more detail what you mean and what you've done.  Have you actually installed Windows 10 or not?

If you have only one hard disk it may also help to see a screenshot of a gparted window which will show detail of partition layout on the disk.

---

### Post by KMJones1 on 2020-03-03
Thanks for that, here is the result:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000e64c5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048     1026047      512000    7  HPFS/NTFS/exFAT
/dev/sda2         1026048   312578047   155776000    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0004b66b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   217169268   108584603   83  Linux
/dev/sdb2       217169918   234440703     8635393    5  Extended
/dev/sdb5       217169920   232347647     7588864   83  Linux
/dev/sdb6       232349696   234440703     1045504   82  Linux swap / Solaris

It is the 160GB disk that has the windows files.
The item "Windows 10 (loader)" appears in the boot list together with the Ubuntu options. I clicked yesterday and it spent many hours apparently trying to install Windows 10, but the screen was blank. This machine is very basic and I can't upgrade from Ubuntu 14 because of lack of space, so I want to simplify things.

---

### Post by ajgreeny on 2020-03-03
Sorry to say this, but I will have to leave this to others who understand Windows 10 installation; I have not used Windows since XP and no longer have any real knowledge that is of use, and I still do not understand what is meant by a Windows 10 loader that appears on your 160G drive.

Others might so wait around for more help, and if you do not get any responses bump the thread every 24 hours by adding a reply post simply with the word "Bump".

---

### Post by The Cog on 2020-03-03
I would be inclined to use gparted to re-format sda1 to ext4. Not necessarily mount it yet, but that should stop it looking like windows any more. 
Then run "sudo update-grub" to update the grub prompt. That should remove the windows prompt from the boot menu.
Then you can think about where to use sda1 - where to mount it and make it available to Linux users.

---

### Post by yancek on 2020-03-03
> At some point I installed a Windows 10 loader and didn't use it 

What do you mean by " windows 10 loader"?  Did you attempt to install windows 10 and fail?  Did you actually install windows 10 and successfully boot it at some point?  Did you try or install a 3rd party bootloader on windows?  What exactly is a "very basic machine"?  How old is it?  What hardware?  If you could not get windows 10 to run, did you check the microsoft site for hardware compatibility or minimum hardware requirements?

Your fdisk output shows that you have 2 physical hard drives.  One of 160GB which is windows only and one of 120GB which is Linux (Ubuntu).  You can simply boot into Ubuntu and format the windows partitions shown as sda1 and sda2 with a Linux filesystem and use them for Ubuntu.  This of course will delete any data on those partitions.  You can use fdisk to do this or you can use the graphical tool GParted which you will probably have to download and put on a CD or usb.

Another thing you should check is which hard drive is set to first boot priority in the BIOS.  Usually, this is sda.  If that's the case you need to understand that if you remove that drive you won't be able to boot Ubuntu on the 2nd drive as some Grub boot code may be on the MBR of that drive.  You could simply install Grub to the MBR of sdb where you have Ubuntu and then set it to boot first from the BIOS.

---

### Post by oldfred on 2020-03-03
Your sda1 & sda2 are NTFS, so those are Windows.
Do you also have data you may want to save in those partitions. Best to backup before any changes.

Do you know if grub is booting from sda or sdb? It looks like you have BIOS/MBR configuration so grub will be in the MBR of a drive. 

Windows boots thru MBR and then to primary NTFS partition with the boot flag or your sda1 which has Windows boot files. It can be a smaller boot partition with just boot files or one partition with everything.
Grub2's os-prober looks for these Windows boot files to add Windows to grub menu. Grub does not use boot flag.
/bootmgr /Boot/BCD

---

### Post by KMJones1 on 2020-03-03
Thanks everybody for this help.
I have Gparted on the machine so I'll use it to reformat the 160GB drive.
:D

---

### Post by KMJones1 on 2020-03-04
However!! Gparted locked up after some time, locking up the whole system, just like the windows loader, with the disk busy light permanently on. It looks like a faulty disk so I'll ditch it.
thanks anyway for help

---

