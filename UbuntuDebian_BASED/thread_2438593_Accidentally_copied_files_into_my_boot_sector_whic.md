---
title: "Accidentally copied files into my boot sector which is now full"
date: 2020-03-14
forum: Ubuntu/Debian BASED
---

### Post by Beloved Bob on 2020-03-14
I accidentally copied files into my boot sector. It is 512 mb and is full. Will not let me boot Elementary. How can I fix the boot sector? How do I delete and replace if that is the best way?

---

### Post by yancek on 2020-03-14
Do you have the Elementary install DVD or USB or any other Linuxx?
Do you know how to create a mount point for the partition and mount it using a 'live' system?
If you simply copied files to the wrong partition, why not just remove them?  Or did you overwrite some boot files?

---

### Post by Beloved Bob on 2020-03-16
The files are in the partition which holds the EFI boot loader. I cannot get permission to change anything. I tried to iu increase the size of the partition and could not do that. I do have Elementary on USB and DVD. I also have Ubuntu 18.04 on DVD. I have been a user of Linux for more than 10 years, but this problem has me stumped. 

I believe I did not overwrite any files. I can get Elementary to work on my Virtualbox VM. It simply will not load to my hard drive as the boot sector is "full" according to an alert which comes up each time I boot the Ubuntu 18.04.

Any suggestions will be deeply appreciated. Not sure I can "create a mount point for the partition and mount it using a 'live' system?"

---

### Post by ajgreeny on 2020-03-16
How did you manage to "accidentally" copy files into the EFI or boot partition?

You could only have done that either by acting as root with a sudo command in terminal or perhaps by using a file manager as root; I hope you were not logged in as root.

Does Elementary even allow logging in as root by default or is it like Ubuntu where the root account is disabled by default?

Finally, how many kernels are installed in your system?  If you have added many new kernels without any being removed either manually by you or automatically by the system, there may be too many for the size of the partition.
Let's see the output of terminal command ***df -hT*** which may help us more, and ***sudo ls -la /boot***

---

### Post by Beloved Bob on 2020-03-16
ajgreeny:

I did the deed when I was making a USB to load Elementary using unetbootin. Missed the boot sector was selected by unetbootin. Not being careful.

Here are the results of the commands you asked for:

```
bob@robert-VivoBook-ASUS:~$ sudo df -hT
Filesystem     Type      Size  Used Avail Use% Mounted on
udev           devtmpfs  1.9G     0  1.9G   0% /dev
tmpfs          tmpfs     376M  2.0M  374M   1% /run
/dev/mmcblk0p2 ext4      110G   58G   47G  55% /
tmpfs          tmpfs     1.9G  202M  1.7G  11% /dev/shm
tmpfs          tmpfs     5.0M  4.0K  5.0M   1% /run/lock
tmpfs          tmpfs     1.9G     0  1.9G   0% /sys/fs/cgroup
/dev/loop0     squashfs  9.2M  9.2M     0 100% /snap/canonical-livepatch/94
/dev/loop2     squashfs   90M   90M     0 100% /snap/core/8268
/dev/loop3     squashfs  3.8M  3.8M     0 100% /snap/gnome-system-monitor/127
/dev/loop1     squashfs  4.3M  4.3M     0 100% /snap/gnome-calculator/544
/dev/loop6     squashfs   15M   15M     0 100% /snap/gnome-characters/399
/dev/loop4     squashfs   45M   45M     0 100% /snap/gtk-common-themes/1440
/dev/loop5     squashfs  1.0M  1.0M     0 100% /snap/gnome-logs/81
/dev/loop7     squashfs  161M  161M     0 100% /snap/gnome-3-28-1804/116
/dev/loop8     squashfs   92M   92M     0 100% /snap/core/8689
/dev/loop9     squashfs   55M   55M     0 100% /snap/core18/1668
/dev/mmcblk0p1 vfat      511M  511M     0 100% /boot/efi
tmpfs          tmpfs     376M   20K  376M   1% /run/user/121
tmpfs          tmpfs     376M   28K  376M   1% /run/user/1000
/dev/mmcblk1p1 ext4      117G  7.2G  104G   7% /media/bob/Memory


bob@robert-VivoBook-ASUS:~$ sudo ls -la /boot
total 108632
drwxr-xr-x  4 root root     4096 Mar 16 16:23 .
drwxr-xr-x 24 root root     4096 Mar 16 16:23 ..
-rw-r--r--  1 root root   235810 Feb  3 08:07 config-5.3.0-40-generic
-rw-r--r--  1 root root   235831 Feb 28 07:40 config-5.3.0-42-generic
drwx------ 10 root root     4096 Dec 31  1969 efi
drwxr-xr-x  5 root root     4096 Mar 16 16:23 grub
-rw-r--r--  1 root root 41462198 Mar 14 11:48 initrd.img-5.3.0-40-generic
-rw-r--r--  1 root root 41456176 Mar 16 16:23 initrd.img-5.3.0-42-generic
-rw-r--r--  1 root root   182704 Jan 28  2016 memtest86+.bin
-rw-r--r--  1 root root   184380 Jan 28  2016 memtest86+.elf
-rw-r--r--  1 root root   184840 Jan 28  2016 memtest86+_multiboot.bin
-rw-------  1 root root  4483816 Feb  3 08:07 System.map-5.3.0-40-generic
-rw-------  1 root root  4485514 Feb 28 07:40 System.map-5.3.0-42-generic
-rw-------  1 root root  9138424 Feb  3 08:11 vmlinuz-5.3.0-40-generic
-rw-------  1 root root  9142520 Feb 28 07:41 vmlinuz-5.3.0-42-generic


```
Hope this helps. I am stumped. Thank you for your kind help.

---

### Post by yancek on 2020-03-16
> /dev/mmcblk0p1 vfat      511M  511M     0 100% /boot/efi 

Above is the EFI partition which shows as 100% full so you can simply navigate to /boot/efi  in a terminal (cd /boot/efi) and remove the incorrect files, you need to use sudo as the files are owned by root.

---

### Post by Beloved Bob on 2020-03-17
Yahcek:

Got into the sector by using sudo...now I am not sure what files to delete. Do I delete everything but the EFI? Not sure how to proceed after getting into the files. Any suggestions?

Thanks for your help this far. Much appreciated.

---

### Post by ajgreeny on 2020-03-17
Post back here the output of ***sudo ls -la /boot/efi/EFI*** and we are more likely to be ale to tell you what can be deleted.

---

### Post by Beloved Bob on 2020-03-17
ajgreeny:

Here is the output:

bob@robert-VivoBook-ASUS:~$ sudo ls -la /boot/efi/EFI
[sudo] password for bob: 
total 16
drwx------  4 root root 4096 Mar  6 22:10 .
drwx------ 10 root root 4096 Dec 31  1969 ..
drwx------  2 root root 4096 Mar 13 12:21 BOOT
drwx------  3 root root 4096 Mar  6 22:11 ubuntu

Thanks for your help on this. Much appreciated. And next time I use unetbootin I will be much more careful...measure twice and cut once as they say.

---

### Post by yancek on 2020-03-18
The directories you show from the /boot/efi/EFI output are all standard directories expected to be there so would need to look in the various directories to see what is there.  If you don't know what is expected, you could run the same command but show what is in the directories BOOT and ubuntu.

---

### Post by Beloved Bob on 2020-03-18
yancek:

Here is the output from both directories:

root@robert-VivoBook-ASUS:/boot/efi/EFI# ls
BOOT  ubuntu
root@robert-VivoBook-ASUS:/boot/efi/EFI# cd BOOT
root@robert-VivoBook-ASUS:/boot/efi/EFI/BOOT# ls
bootia32.efi  bootx64.efi  fbx64.efi  grubx64.efi
root@robert-VivoBook-ASUS:/boot/efi/EFI/BOOT# cd /boot/efi/EFI/ubuntu
root@robert-VivoBook-ASUS:/boot/efi/EFI/ubuntu# ls
BOOTX64.CSV  fw  fwupx64.efi  grub.cfg  grubx64.efi  mmx64.efi  shimx64.efi

Not sure what to do. Any suggestions are greatly appreciated.

---

### Post by yancek on 2020-03-18
> bootia32.efi grubx64.efi 

The above files you show under BOOT are the only 2 that I do not have on my install.  That does not mean they are not needed.  I have several operating systems installed with directories for each which contain the same or similar files you show under Ubuntu which would include a lot more files aand my efi partition is only 112MB.  I think you might want to look under /mnt/efi to see what is there.  Hopefully, you have some idea of what you accidentally copied.

---

### Post by Beloved Bob on 2020-03-18
yancek:

I have not been able to look under /mnt/efi. I can get into /mnt but the efi returns no such directory. What am I doing wrong?

Thanks for your help.

---

### Post by yancek on 2020-03-18
> I have not been able to look under /mnt/efi. I can get into /mnt but the efi returns no such directory. What am I doing wrong?
 

Wrong path.  In an earlier post you indicated you were using an Elementary live usb.  If you are, you need to mount the partition shown below.  You see it is not going to be /mnt/efi bur rather:  /mnt/boot/efi 

> /dev/mmcblk0p1 vfat      511M  511M     0 100% /boot/efi 			 		 

---

### Post by Beloved Bob on 2020-03-18
yancek:

here is the output from /mnt/boot/efi

root@robert-VivoBook-ASUS:/boot/efi# ls
boot  casper  dists  EFI  isolinux  live  pool  ubninit  ubnkern  ubnpathl.txt

Unfortunately, I have no idea what I copied. Unetbootin did it so fast I did not note anything until it stopped saying the sector was full. I am guessing the only thing I may need here is the EFI file. Any thoughts?

And thank you so much for all the help. I really do want to get this fixed. I am feeling like we are close..

---

### Post by ajgreeny on 2020-03-19
What we really need from you is ```
ls -l /mnt/boot/efi
``` which will show us the size of all those entries in the folder whereas your ls command shows names only, though from the names alone it looks rather as if the copy placed the parts of the live system that would fit into the /boot partition.

The **casper** file listed  is the complete live filesystem from your live install medium which for most Ubuntu live systems is about 1.5GB in size.

We may need to simply delete that, but before saying that you should do so let's see my ***ls -l*** command output.

---

### Post by Beloved Bob on 2020-03-19
ajgreeny:

Here is the output:

root@robert-VivoBook-ASUS:/boot/efi# ls -l
total 76492
drwx------ 3 root root     4096 Mar 13 12:21 boot
drwx------ 2 root root     4096 Mar 13 12:21 casper
drwx------ 3 root root     4096 Mar 13 12:21 dists
drwx------ 4 root root     4096 Mar  6 22:10 EFI
drwx------ 2 root root     4096 Mar 13 12:21 isolinux
drwx------ 2 root root     4096 Mar 13 12:21 live
drwx------ 5 root root     4096 Mar 13 12:21 pool
-rwx------ 1 root root 69143419 Feb  4 13:54 ubninit
-rwx------ 1 root root  9146616 Feb  4 13:54 ubnkern
-rwx------ 1 root root     3582 Mar 13 12:21 ubnpathl.txt

My best guess is everything dated "Mar 13" needs to be removed. It is the date I made the error. Thoughts?

Thanks for your help!

---

### Post by yancek on 2020-03-19
It looks like you were trying to write to a usb and selected he wrong drive/partition.  The only thing you should have there is the EFI directory.  Everything else looks like unetbootin files trying to create the usb.  I would go into the /boot/efi and rather than delete the directories/files, copy them to another location, your /home/user directory for example then reboot and see if it works before deleting the directories/files you copied from /boot/efi in your /home/user partition.  No harm being paranoid.

---

### Post by Beloved Bob on 2020-03-19
Thank you, yancek, I will do that. Yes, I did copy the usb files to the wrong destination when trying to make a bootable usb. Since this mistake I have become super paranoid...will copy first, delete and try it. 

Much appreciated...your help and ajgreeny.

---

### Post by Beloved Bob on 2020-03-19
Success!!! Deleted the files and rebooted. Went well. Fast and no notification the partition is full. 

Thank you, both for all the help. It is much appreciated.

---

### Post by ajgreeny on 2020-03-19
That is brilliant news!!!!!

Please now mark as SOLVED from the Thread Tools menu up-top if this is solved to your satisfaction, which it would appear to be. It is a great help to other users searching the forum.

Just for a comparison with what you saw originally please show now the output of command ***df -hT***, and make sure you carefully choose which device is shown if you use unetbootin again.
In fact I suggest you use [mkusb]("https://help.ubuntu.com/community/mkusb") instead; it's much safer and in my opinion, better.

---

### Post by Beloved Bob on 2020-03-19
Thank you, ajgreeny. Here is the output you asked for:

root@robert-VivoBook-ASUS:/home/bob# df -hT
Filesystem     Type      Size  Used Avail Use% Mounted on
udev           devtmpfs  1.9G     0  1.9G   0% /dev
tmpfs          tmpfs     376M  2.0M  374M   1% /run
/dev/mmcblk0p2 ext4      110G   58G   47G  56% /
tmpfs          tmpfs     1.9G  253M  1.6G  14% /dev/shm
tmpfs          tmpfs     5.0M  4.0K  5.0M   1% /run/lock
tmpfs          tmpfs     1.9G     0  1.9G   0% /sys/fs/cgroup
/dev/loop1     squashfs  9.2M  9.2M     0 100% /snap/canonical-livepatch/94
/dev/loop0     squashfs  3.8M  3.8M     0 100% /snap/gnome-system-monitor/127
/dev/loop2     squashfs  1.0M  1.0M     0 100% /snap/gnome-logs/81
/dev/loop3     squashfs  4.3M  4.3M     0 100% /snap/gnome-calculator/544
/dev/loop4     squashfs   45M   45M     0 100% /snap/gtk-common-themes/1440
/dev/loop5     squashfs   90M   90M     0 100% /snap/core/8268
/dev/loop6     squashfs   15M   15M     0 100% /snap/gnome-characters/399
/dev/loop7     squashfs   92M   92M     0 100% /snap/core/8689
/dev/loop9     squashfs   55M   55M     0 100% /snap/core18/1668
/dev/loop8     squashfs  161M  161M     0 100% /snap/gnome-3-28-1804/116
/dev/mmcblk0p1 vfat      511M  7.5M  504M   2% /boot/efi
tmpfs          tmpfs     376M   20K  376M   1% /run/user/121
tmpfs          tmpfs     376M   32K  376M   1% /run/user/1000
/dev/mmcblk1p1 ext4      117G  7.4G  104G   7% /media/bob/Memory
tmpfs          tmpfs     376M     0  376M   0% /run/user/0

I will use mkusb in the future. Appreciate the info. Thanks, again for your help.

---

### Post by ajgreeny on 2020-03-20
That's much better!

Now the boot partition is back to only 2% so well done.

---

