---
title: "cryptsetup error ubuntu 11.04:"
date: 2011-08-15
forum: Security
---

### Post by audio1 on 2011-08-15
I just ran sudo apt-get update and updated all my packages which all seemed to update correctly. The problem I have is I got an error message in the last few lines of the terminal as below:

cryptsetup: WARNING: failed to detect canonical device of /dev/sda7
cryptsetup: WARNING: could not determine root device from /etc/fstab

Can someone help me solve this?

Thanks

---

### Post by bodhi.zazen on 2011-08-16
post the contents of /etc/fstab and /etc/crypttab

---

### Post by audio1 on 2011-08-18
Here is as you requested. I also tried sudo as it said permission denied.

x@x-Lenovo-V560:~$ /etc/fstab
bash: /etc/fstab: Permission denied
x@x-Lenovo-V560:~$ /etc/crypttab
bash: /etc/crypttab: Permission denied
x@x-Lenovo-V560:~$ sudo /etc/fstab
sudo: /etc/fstab: command not found
x@x-Lenovo-V560:~$ sudo /etc/crypttab
sudo: /etc/crypttab: command not found

Your help is truly appreciated. I will reply more quickly now I subscribed to this thread.

TKS

---

### Post by Soul-Sing on 2011-08-18
> **audio1 said:**
> Here is as you requested. I also tried sudo as it said permission denied.

x@x-Lenovo-V560:~$ /etc/fstab
bash: /etc/fstab: Permission denied
x@x-Lenovo-V560:~$ /etc/crypttab
bash: /etc/crypttab: Permission denied
x@x-Lenovo-V560:~$ sudo /etc/fstab
sudo: /etc/fstab: command not found
x@x-Lenovo-V560:~$ sudo /etc/crypttab
sudo: /etc/crypttab: command not found

Your help is truly appreciated. I will reply more quickly now I subscribed to this thread.

TKS

please navigate via nautilus to etc/fstab. no root needed to copy paste the content here.

---

### Post by bodhi.zazen on 2011-08-18
To see the contents of a file you need to use a tool such as cat, less, gedit ...

cat /etc/fstab
less /etc/fstab
gedit /etc/fstab

Take your pick. As you are going to be editing the files, you will be using an editor - nano, vim , gedit, as root.

sudo -e /etc/fstab
gksu gedit /etc/fstab

---

### Post by audio1 on 2011-08-19
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda7       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
#UUID=2f15bb05-f238-4e44-9f26-84138356cb4a none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0


/etc/crypttab
# <target name>    <source device>        <key file>    <options>
cryptswap1 /dev/sda8 /dev/urandom swap,cipher=aes-cbc-essiv:sha256

---

### Post by audio1 on 2011-08-22
Hi,

I'm still trying to solve this problem so any help appreciated.

Thankyou.

---

### Post by bodhi.zazen on 2011-08-22
"/dev/sda7" should read "/dev/mapper/root"

ls /dev/mapper

---

### Post by audio1 on 2011-08-22
Thankyou.

My fstab file is now as follows:

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/mapper/root               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
#UUID=2f15bb05-f238-4e44-9f26-84138356cb4a none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0

But I am getting the following error messages in the terminal and my system is still spitting out errors about unmounted disk on boot up.

x@x-Lenovo-V560:~$ sudo gedit /etc/fstab
[sudo] password for x: 

(gedit:1972): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.9BYY0V': No such file or directory

(gedit:1972): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

I did not fully understand the last line of your post ls /dev/mapper, was I supposed to do something with that?

Thanks

---

### Post by bodhi.zazen on 2011-08-22
> **audio1 said:**
> Thankyou.

My fstab file is now as follows:

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/mapper/root               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
#UUID=2f15bb05-f238-4e44-9f26-84138356cb4a none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0

But I am getting the following error messages in the terminal and my system is still spitting out errors about unmounted disk on boot up.

x@x-Lenovo-V560:~$ sudo gedit /etc/fstab
[sudo] password for x: 

(gedit:1972): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.9BYY0V': No such file or directory

(gedit:1972): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

I did not fully understand the last line of your post ls /dev/mapper, was I supposed to do something with that?

Thanks

Is your root partition encrypted ?

If so , you need to list the proper device in fstab.

use the ls command to list the devices in /dev/mapper and correct your fstab syntax.

If you do not know, you need to tell us what partition is what and show the output of the ls command.

---

### Post by audio1 on 2011-08-22
I do not know how to fix the syntax of fstab on my own - I'm a totally new Ubuntu user...sorry.

x@x-Lenovo-V560:~$ ls /dev/mapper
control  cryptswap1

I have five partitions. I'm running a dual boot Windows 7 and Ubuntu.



 The 4 Gb File System is the swap partition
The 210 Mb partition I'm not sure what that is - possibly windows
The 398Gb partition is for files 
The Lenovo_Part partition is Lenovo recovery files I think
The File System which is 20Gb is for Ubuntu.

Is that what you needed?

---

### Post by bodhi.zazen on 2011-08-22
So the only thing your encrypted is swap ? 

Post the output of 

```
sudo fdisk -l
```

---

### Post by audio1 on 2011-08-23
x@x-Lenovo-V560:~$ sudo fdisk -l
[sudo] password for x: 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x7a690552

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          26      204800    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              26       48469   389121418+   7  HPFS/NTFS
/dev/sda3           48470       55752    58499073    f  W95 Ext'd (LBA)
/dev/sda4           58876       60802    15471640    2  XENIX root
/dev/sda5           55091       55752     5315584    7  HPFS/NTFS
/dev/sda6           54427       55090     5330944   82  Linux swap / Solaris
/dev/sda7           48470       53939    43930624   83  Linux
/dev/sda8           53939       54427     3917824   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/dm-0: 4011 MB, 4011851776 bytes
255 heads, 63 sectors/track, 487 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xcfff6c6c

Disk /dev/dm-0 doesn't contain a valid partition table

---

### Post by bodhi.zazen on 2011-08-23
OK, now tell us what those partitions are.

Specifically, which ones did you encrypt and which ones are for Ubuntu 11.04.

---

### Post by audio1 on 2011-09-12
Hi,
I've been away. Still struggling with this issue.

1. I do not know which partitions I encrypted. If I did encrypt it would only because there was some prompt on the install. How can I tell which partition is encrypted?

2. I ran a partition program to try and mount all the disks. It has made my system more stable, but I still get a mounting error for ext4. The fstab file also shows some errors.

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                        /proc        proc  nodev,noexec,nosuid         0  0  
/dev/mapper/root               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
#UUID=2f15bb05-f238-4e44-9f26-84138356cb4a  none         swap  sw                          0  0  
/dev/mapper/cryptswap1                      none         swap  sw                          0  0  
/dev/sda1                                   /media/sda1  ntfs  nls=iso8859-1,ro,umask=000  0  0  
/dev/sda2                                   /media/sda2  ntfs  defaults                    0  0  
/dev/sda4                                   /media/sda4  ntfs  defaults                    0  0  
/dev/sda5                                   /media/sda5  ntfs  defaults                    0  0  
/dev/sda6                                   /media/sda6  swap  defaults                    0  0  
/dev/sda7                                   /media/sda7  ext4  defaults                    0  0  

3. Here are the informations for my partitions:

   	 	 	 	 	 		 	 	   	 	 		 			[SIZE=3]sda1[/SIZE] 			[SIZE=3]210Mb[/SIZE] 			[SIZE=3]NTFS[/SIZE] 			[SIZE=3]Boot

[/SIZE] 		 		 			[SIZE=3]sda2[/SIZE] 			[SIZE=3]370Gb[/SIZE] 			[SIZE=3]NTFS[/SIZE] 			[SIZE=3]File storage for Windows 7

[/SIZE] 		 		 		 			[SIZE=3]sda4[/SIZE] 			[SIZE=3]15Gb[/SIZE] 			[SIZE=3]
[/SIZE] 			[SIZE=3]Lenovo OneKey Backup
Windows 7

[/SIZE] 		 		 			[SIZE=3]sda5[/SIZE] 			[SIZE=3]5.4Gb[/SIZE] 			[SIZE=3]NTFS[/SIZE] 			[SIZE=3]Driver Backup for Windows 7


[/SIZE] 		 		 			[SIZE=3]sda6[/SIZE] 			[SIZE=3]unknown[/SIZE] 			[SIZE=3]swap[/SIZE] 			[SIZE=3]unknown appears blank



[/SIZE] 		 		 			[SIZE=3]sda7[/SIZE] 			[SIZE=3]45Gb[/SIZE] 			[SIZE=3]ext4[/SIZE] 			[SIZE=3]Linux File System[/SIZE] 		 	  



I'm not sure what has happened to my 5Gb swap file for linux? How can I check this.

Thanks for assistance.

---

### Post by predato on 2013-01-07
I met similar error message when I run "sudo update-initramfs -u -k all" command. I fixed it at last. 
Before I tell how, unfortunately Ubuntu lovers suffer from lack of getting help in the forums. I meet many unanswered threads. 
How I fixed it:
 The error is printed by "/usr/share/initramfs-tools/hooks" as it was stated in this topic [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=671056](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=671056)
Main source of the error is corrupted swap partition linking.
First you need to get UUID of your swap partition. Just run blkid command. In my case error message was"cryptsetup: WARNING: failed to detect canonical device of /dev/sda5" so I noted down UUID of /dev/sda5. It was ede93e1b-0b68-468f-b6f6-ebf7a0c9d7ac
If you don't know how to create swap partition, take a look at this link [http://askubuntu.com/questions/33697/adding-swap-partition-after-system-installation?lq=1](http://askubuntu.com/questions/33697/adding-swap-partition-after-system-installation?lq=1)
sudo gedit /etc/crypttab I deleted the related/dev/sda5 line in crypttab
sudo gedit /etc/fstab I opened fstab and added line UUID=ede93e1b-0b68-468f-b6f6-ebf7a0c9d7ac  none         swap  sw                   0  0  


sudo gedit /etc/uswsusp.conf I opened uswsusp.conf file and changed resume device=/dev/sda5 to 
resume device = UUID=ede93e1b-0b68-468f-b6f6-ebf7a0c9d7ac

finally I issued sudo update-initramfs -u -k all command and I got rid of that damn message. I hope it works for you too
I also benefitted from this topic [http://techpatterns.com/forums/about1178.html](http://techpatterns.com/forums/about1178.html)
I hope it also fixes hibernating problem.

---

### Post by predato on 2013-01-07
I met similar error message when I run "sudo update-initramfs -u -k all" command. I fixed it at last. 
Before I tell how, unfortunately Ubuntu lovers suffer from lack of getting help in the forums. I meet many unanswered threads. 
How I fixed it:
 The error is printed by "/usr/share/initramfs-tools/hooks" as it was stated in this topic [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=671056](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=671056)
Main source of the error is corrupted swap partition linking.
First you need to get UUID of your swap partition. Just run blkid command. In my case error message was"cryptsetup: WARNING: failed to detect canonical device of /dev/sda5" so I noted down UUID of /dev/sda5. It was ede93e1b-0b68-468f-b6f6-ebf7a0c9d7ac
If you don't know how to create swap partition, take a look at this link [http://askubuntu.com/questions/33697/adding-swap-partition-after-system-installation?lq=1](http://askubuntu.com/questions/33697/adding-swap-partition-after-system-installation?lq=1)
sudo gedit /etc/crypttab I deleted the related/dev/sda5 line in crypttab
sudo gedit /etc/fstab I opened fstab and added line UUID=ede93e1b-0b68-468f-b6f6-ebf7a0c9d7ac  none         swap  sw                   0  0  


sudo gedit /etc/uswsusp.conf I opened uswsusp.conf file and changed resume device=/dev/sda5 to 
resume device = UUID=ede93e1b-0b68-468f-b6f6-ebf7a0c9d7ac

finally I issued sudo update-initramfs -u -k all command and I got rid of that damn message. I hope it works for you too
I also benefitted from this topic [http://techpatterns.com/forums/about1178.html](http://techpatterns.com/forums/about1178.html)
I hope it also fixes hibernating problem.

---

