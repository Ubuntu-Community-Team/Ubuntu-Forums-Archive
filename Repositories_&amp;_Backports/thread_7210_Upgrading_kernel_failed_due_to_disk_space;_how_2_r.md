---
title: "Upgrading kernel failed due to disk space; how 2 resolve?"
date: 2004-12-05
forum: Repositories &amp; Backports
---

### Post by midtoad on 2004-12-05
I've just installed Ubuntu for the first time. Previously I've used Mandrake and Debian for a number of years.  Now I've run into a problem I can't resolve. 

My install went well.  Then I upgraded the kernel to the latest version, and it failed in post-install because there wasn't enough room for the initrd image. (My /boot is only 7 MB in size).  Now I have part of an initrd image!  How can I repair this situation?

For background, I have 2 drives. /dev/hda1 and hda3 are Win C and D, while /dev/hda2 is my small /boot partition.  /dev/hdb1 is /  with lots of room on it.  /dev/hdb2 is /var, /dev/hdb5 is /home, and /dev/hdb6 is swap.  

I thought about try to create a boot folder in /dev/hdb1, but I'm unable to unmount or rename /boot to something else so that I can create the boot folder on /  (plus I'm not sure I can boot to /dev/hdb; doesn't the boot partition have to be on /dev/hda?).   ](*,) 

Any tips appreciated.

thanks
midtoad

---

### Post by Marauder1 on 2004-12-05
If its a fresh install i would say to re-install it with a
bigger /boot.
But im sure there is a way to make a /boot in your
root partition then update Grub to reflect the new
booting partition but i never did it.

---

### Post by yoramdavid on 2008-11-12
I am having the same problem.
I have the following partiontions:
A boot partition (/boot) of 100 MB of which 13 MB free on dev/sda1,
A Ubuntu 8.04 partition (/ )with 10 GB of which 5.66 GB free on dev/sda5,
A home (/home)partition with 2.7 GB of which 1.77 GB free on dev/sda6
A Swap (linux-swap) partition with 1.23 GB on dev/sdb6

I have updated all the Ubuntu releases for a while now and never had this problem.
Why does not the installer download the installation files on "/ " where there is plenty of space instead of on the "/boot"? Can this not be changed? Where did the previous versions downloaded the files? :confused:
What is the solution for this?
I cannot delete all my boot partition can I?

I have searched the Internet and have not found any solution for this.

Thank you for any help.

Yoram

---

### Post by cdtech on 2008-11-12
Upgrades accompany a new kernel revision, each being about 45M in size. If you don't have the space within the /boot folder to hold the new kernel release you will recieve the error.

To correct this you could remove any non used kernel images within the /boot partition. Remember to keep the original as a backup in case you can't boot with the new release.

You could resize the /boot partition before the upgrade with the "Live CD" using the application "gparted".

---

### Post by yoramdavid on 2008-11-12
> **cdtech said:**
> Upgrades accompany a new kernel revision, each being about 45M in size. If you don't have the space within the /boot folder to hold the new kernel release you will recieve the error.

To correct this you could remove any non used kernel images within the /boot partition. Remember to keep the original as a backup in case you can't boot with the new release.

You could resize the /boot partition before the upgrade with the "Live CD" using the application "gparted".

Thank you for your prompt reply.
I am not sure which files I can delete and which one I need to keep ?
The installer was asking for 75 MB of space...

Thank you again.

Yoram

---

### Post by cdtech on 2008-11-12
You can find the current kernel your using with the command:
```
uname -r
```
([COLOR="DarkRed"]Keep this one for a backup[/COLOR])

If you have any other kernel within your /boot partition that your sure your not using, you could delete them. Such as an old config-**2.6.22-14**-generic and initrd.img-**2.6.22-14**-generic as well as the vmlinuz-**2.6.22-14**-generic. As you can see anything associated with that kernel within the /boot partition.

---

### Post by yoramdavid on 2008-11-12
> **cdtech said:**
> You can find the current kernel your using with the command:
```
uname -r
```
([COLOR="DarkRed"]Keep this one for a backup[/COLOR])

If you have any other kernel within your /boot partition that your sure your not using, you could delete them. Such as an old config-**2.6.22-14**-generic and initrd.img-**2.6.22-14**-generic as well as the vmlinuz-**2.6.22-14**-generic. As you can see anything associated with that kernel within the /boot partition.

Sorry to come back again, so if I delete all the entries older than "2.6.24-14"? I have some 2.6.22-14 and 2.6.20-14 files.
What about the old abi-2.6.22-14 and the System.map-2.6.22-14?
If I delete all but the last 2.6.24-14 that only frees up 19 MB.
Recycle bin is empty.
Lost+found is inaccessible (has a folder icon with a lock on it...).

I run this command to delete an entry and it does not work: "sudo rm /boot/config-2.6.22-14-generic"
What am I doing wrong? I says it cannot find the file.
Thank you

Yoram

---

### Post by yoramdavid on 2008-11-13
OK, I finally managed to eliminate all the old entries using the synaptic manager tool. Did not know I could use it for that too. Great. :)
I installed Ubuntu 8.10, all went well until I rebooted as prompted and I got the Grub error 17. :( I let the installation replace my menu.lst, knowing I could change it back again to boot either Ubuntu or Windows.
I did a search on the net and found some topics related to this.
I ran the Super Grub disk to repair Grub with no success.
It looks to me Ubuntu has the hardrives in reverse order.
I checked the new menu.lst and saw that the addresses are wrong:
(hd2,0) instead of (hd0,0).

Now, I manage to change the menu.lst from windows (could not find anywhere how to do it from the live CD or from  the Super Grub floppy).
Then I booted from the Super Grub floppy and restored Grub, but as I do so, it replaces the menu.lst I just modifyed with another one (one just the same there was before - where does it gets that from??).

Any idea how to do this?
Still cannot boot into Ubuntu due to the error 17 to edit the menu.lst

Yoram

---

### Post by yoramdavid on 2008-11-15
Supergrub disk did not help. Cannot boot any partition (errors 15 and 13 were shown in two different occasions.
I uninstalled and reinstalled grub from live cd, no luck either.
Tryed what they said in some threat to "teach" grub the order of the partitions, no luck.

How do I edit menu.lst from the live CD if grub is in hd0,0 ?

---

### Post by cdtech on 2008-11-15
In a terminal, lets see what you get with the command:
```
sudo fdisk -l
```
And also the /boot/grub/menu.lst:
```
cat /boot/grub/menu.lst
```

---

### Post by yoramdavid on 2008-11-15
The command: sudo fdisk -l
gives the following 

Disk /dev/sda: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7fab3f16

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           2       36483   293041665    f  W95 Ext'd (LBA)
/dev/sda5               2       36483   293041633+   7  HPFS/NTFS

Disk /dev/sdb: 60.0 GB, 60040544256 bytes
255 heads, 63 sectors/track, 7299 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc027c027

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1          13      104391   83  Linux
/dev/sdb2   *          14        1322    10514542+   7  HPFS/NTFS
/dev/sdb3            1323        7299    48010252+   f  W95 Ext'd (LBA)
/dev/sdb5            1323        2629    10498446   83  Linux
/dev/sdb6            2630        2980     2819376   83  Linux
/dev/sdb7            2981        6906    31535563+   7  HPFS/NTFS
/dev/sdb8            6907        7299     3156741    7  HPFS/NTFS

Disk /dev/sdc: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc539c539

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        3921    31495401    7  HPFS/NTFS
/dev/sdc2            3922        9964    48540397+   f  W95 Ext'd (LBA)
/dev/sdc5            3922        9803    47247133+   7  HPFS/NTFS
/dev/sdc6            9804        9964     1293201   82  Linux swap / Solaris

Note: sda (SATA disk) used to be sdb and vice-versa with all the previous Ubuntu versions.

The command cat /boot/grub/menu.lst gave an error (cannot find file).
I browsed and the partition named boot is not there anymore, it has been replaced with one called media (I just ran the Ubuntu installation to try to solve the problem this way... I have a boot partition just for the /boot and set it up as /boot on the partition table).

Menu.lst looks like this (without the comments):

default		0
timeout		10

Now, when I boot, I get a blank screen for a moment, then it goes to Windows. It did even not write on the MBR.

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		a1401ca4-22cd-48e3-9489-5769e7c650d8
kernel		/vmlinuz-2.6.27-7-generic root=UUID=90da8b30-08be-41b7-a921-fc8efc2c950f ro locale=pt_PT quiet splash 
initrd		/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		a1401ca4-22cd-48e3-9489-5769e7c650d8
kernel		/vmlinuz-2.6.27-7-generic root=UUID=90da8b30-08be-41b7-a921-fc8efc2c950f ro locale=pt_PT  single
initrd		/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		a1401ca4-22cd-48e3-9489-5769e7c650d8
kernel		/memtest86+.bin
quiet

---

### Post by yoramdavid on 2008-11-15
I had a hard time. Got many errors installing Ubuntu, had to reinstall.
Now it is installed and boots Ubuntu but not windows.
Did some upgrades of packs in ubuntu and after that, I get into Ubuntu, there is a desktop but no menus, nothing but the background image.
What to do to fix this? I already uninstalled nVidia drivers, tought it might be the problem.
I did the following:
sudo apt-get remove nvidia-settings
sudo apt-get install nvidia-glx
no results.

I then wanted to reconfigure the xserver (I am only able to have a 800x600 resolution @ 60 Hz), but when I run the command:
sudo dpkg-reconfigure -phigh xserver-xorg,
I just get a message that a a backup of the xorg.conf file has been done:
xserver-xorg postinst warning: overwriting possibly-customized configuration file; backup in /etc/X11/xorg.conf.20081115233431

---

### Post by yoramdavid on 2008-11-16
OK,

I managed to boot Windows now changing the menu.lst from (hd1,1) to (hd0,1) and also removing a line that said map (hd1,0) and map (hd0,1).
But in Ubuntu I still do not get the task bar and menus. Programs work, I am able to open programs through the shortcuts from my keyboard such as file explorer and Firefox.
Screen resolution is fixed, I restored a backup of the xorg.conf from the last ubuntu which worked good.
But I neeed my desktop back, is it something I uninstalled? All I uninstalled was Evolution mail.
Thank you for any help.

OK, I am going to open a new threat with this one, it has nothing more to do with this one, it is getting too messy here.

Reinstalling gnome solved my problem. It was probably due to a bad upgrade. Command used:
sudo apt-get install --reinstall ubuntu-desktop

---

