---
title: "Migration from HDD to SSD"
date: 2010-05-24
forum: The Cafe
---

### Post by alpharesearch on 2010-05-24
I want to write down what I did so I don't forget - and this post may serves as a howto for other users.

[SIZE="5"]Setup[/SIZE]

First I booted my HDD Linux installation up to install bootchart and then I rebooted my PC 3-5 times with 5 minutes wait in between
to get some readings how the system performs with the HDD. When I was finished migrating I did that same test again with the SSD Linux
installation to see if the SSD was a good investment.

[IMG]http://www.alpharesearch.de/ocz/hdd_bootchart.png[/IMG]
The little red x is when Firefox starts up and the systems becomes usable; as an excuse I have over 2600 additional packages installed 
and my root is over 17 GB. There are a lot of server things like data bases starting up. 

[SIZE="5"]Hardware and BIOS[/SIZE]

I got a 50 GB Vertex LE and a 100GB Vertex LE (thanks to Newegg for good service!). I also had to order a 2.5" to 3.5" mounting bracket 
for $5.99 - to make this in China in large quantities should not cost more that a couple of cents so please OCZ include something with 
your product.
I still had two SATA II cables at hand, so I didn't need one... but in my opinion it would make sense to offer a retrial box with 
SSD+bracket+cable for a little more and a OEM box with just the SSD of course.

In the next step I installed everything in my PC and changed the BIOS IDE setting to AHCI.

[SIZE="5"]First Benchmark[/SIZE] 

Than I use the 10.04 install CD to boot into a independent live CD system  Please note that the Live CD must be the same as the system 
you are having - either 32-bit or 64-bit (if not then the chroot later will fail)... 
First I started the Gnome Disk Utility (System->Administration->Disk Utility) to check if my AHCI controller can handle the SSD speed. 
ou can only perform the Read/Write Test if the disk is empty so now is the best time to do this type of benchmark. Here are my results, 
it looks just like advertised :) 
[IMG]http://www.alpharesearch.de/ocz/Screenshot-50 GB Solid-State Disk (ATA OCZ VERTEX-LE) &#8211; Benchmark.png[/IMG]
[IMG]http://www.alpharesearch.de/ocz/Screenshot-100 GB Solid-State Disk (ATA OCZ VERTEX-LE) &#8211; Benchmark.png[/IMG]

[SIZE="5"]Partitioning[/SIZE] 

The next step is to create the partitions, the Disk Utility could do this but I wanted the correct alignment so I used the
[Linux%20-%20Tips,%20tweaks%20and%20alignment"]fdisk method from this forum]("http://www.ocztechnologyforum.com/forum/showthread.php?54379-Linux-Tips-tweaks-and-alignment). 
I created one root (/) a /home and a /boot (for future RAID) partition. I will use the swap partition from on my existing HDD. 

sudo fdisk -H 32 -S 32 /dev/sda starts for first hard drive, use the Disk Utility to find your device name, then use "o" creates a new partition 
table and "n" creates the partitions (I followed the [Linux%20-%20Tips,%20tweaks%20and%20alignment"]guide]("http://www.ocztechnologyforum.com/forum/showthread.php?54379-Linux-Tips-tweaks-and-alignment) and created a primary partition starting with sector 2), 
"t" with 83 sets the partition type to Linux, and "w" writes everything to disk. 

Here is the example form TortureTest guide:
```
$ sudo fdisk -H 32 -S 32 /dev/sda

The number of cylinders for this disk is set to 15711.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help): o
Building a new DOS disklabel with disk identifier 0x8cb3d286.
Changes will remain in memory only, until you decide to write them.
After that, of course, the previous content won't be recoverable.

The number of cylinders for this disk is set to 15711.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)
Warning: invalid flag 0x0000 of partition table 4 will be corrected by w(rite)

Command (m for help): n
Command action
   e   extended
   p   primary partition (1-4)
p
Partition number (1-4): 1
First cylinder (1-15711, default 1): 2
Last cylinder, +cylinders or +size{K,M,G} (2-15711, default 15711):
Using default value 15711

Command (m for help): t
Selected partition 1
Hex code (type L to list codes): 83

Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.
Syncing disks.
```

Here are my result:
[IMG]http://www.alpharesearch.de/ocz/fdisk.png[/IMG]

[SIZE="5"]Format the partition[/SIZE]
I used gparted or the Disk Utility to format it to EXT4 (with the next kernel version this will support trim I guess)

[SIZE="5"]Copy your files[/SIZE] 

[URL="http://www.linuxjournal.com/content/copy-your-linux-install-different-partition-or-drive"]For the next copy step I used this 
article as an inspiration.[/URL] Still in the live CD system you can use the Disk Utility to mount both your old HDD partition and the 
new SSD partition. To copy use this command: 
   sudo cp -afv /path/to/source/* /path/to/destination 
(Don&#8217;t forget the asterisk after the source path and just copy the path from Disk Utility or Nautilus). Unmount both partitions with Disk 
Utility and repeat this for all your other partitions.

[SIZE="5"]Tweak some files on the new SSD root[/SIZE]

To boot from the SSD you need to change the fstab file on the new partition, so mount your new SSD root partition and edit path/to/new/ssd/etc/fstab: 
I used "sudo gedit /media/large UUID number/etc/fstab" in command line to do this. Replace the HDD UUID with the SSD UUID for your directory. 
To see all the UUIDs use this command: 
   ls -l /dev/disk/by-uuid/ 
or as an alternative the Disk Utility tool will show the UUID as mount point name if you never entered a partition name. 
Unmount all drives.

Next I added those lines to my path/to/new/ssd/etc/rc.local file
```

echo cfq > /sys/block/sda/queue/scheduler
echo noop > /sys/block/sdb/queue/scheduler
echo noop > /sys/block/sdc/queue/scheduler
echo cfq > /sys/block/sdd/queue/scheduler
echo 0 > /proc/sys/vm/swappiness
```
cfq is for HDD and
noop or deadline is for SSD
To make sure the swap is not used to much I used swappiness = 0

Because I boot from the SSD and I have GRUB 2 I added as the default to /etc/default/grub
```
GRUB_CMDLINE_LINUX="elevator=noop"
```
(if you change this later you need to run sudo update-grub)


[SIZE="5"]Make drive boot with GRUB 2[/SIZE] 

Since Ubuntu 9.10 Grub 2 is the default so there are some other steps necessary that are not covert on the other web page, but if you still 
use Grub 1 just [follow the link]("http://www.linuxjournal.com/content/copy-your-linux-install-different-partition-or-drive") for the 
old Grub modification.

[For Grub 2 I used METHOD 3 - CHROOT from here]("https://help.ubuntu.com/community/Grub2") 

Still in Live CD Desktop in a terminal use: 
   sudo fdisk -l 
(the switch is a lowercase "L") again to remember the device names to use in the next step. Now you need to mount the file system to the /mnt folder. 
Mount your new SSD system root partition, substitute the correct partition: sda1, sdb5, etc. 
sudo mount /dev/sdXX /mnt # Example: 
   sudo mount /dev/sda1 /mnt

Only if you have a separate boot partition, sdYY is the /boot partition designation (for example sdb3)
   sudo mount /dev/sdYY /mnt/boot 

Mount the critical virtual filesystems:
   sudo mount --bind /dev  /mnt/dev
   sudo mount --bind /proc /mnt/proc
   sudo mount --bind /sys  /mnt/sys

Chroot into your normal system device:
   sudo chroot /mnt

To update the grub files run: 
   update-grub

Now reinstall GRUB 2:
Substitute the correct device - sda, sdb, etc. Do not specify a partition number. 
   grub-install /dev/sdX

Exit chroot: CTRL-D on keyboard

Unmount virtual filesystems:
   sudo umount /mnt/dev
   sudo umount /mnt/proc
   sudo umount /mnt/sys

If you mounted a separate /boot partition:
   sudo umount /mnt/boot 

Unmount last device:
   sudo umount /mnt

Now reboot and take the CD out and it should boot with the new SSD, you can use the Disk Utility to check for this. For bootchat 
I recommend to do more than on boot up to get an average result. 

[SIZE="5"]Compare your Bootcharts[/SIZE]

As you can see the performance gain is huge!
[IMG]http://www.alpharesearch.de/ocz/ssd_bootchart.png[/IMG]
The little red x is when Firefox starts up and i can start using the system.


[SIZE="5"]Conclusion[/SIZE]

Like I said I do have a lot of extra packages installed I guess if I would not need all the other software and if I would do a clean install
I would be able to boot even faster. But from 35-75 seconds down to 15-20 is very good.

I will hopefully be able to edit this post soon to add more details.

Regards,
Markus Schulz

PS: For TRIM I use the whiper.sh script with the sandforce option and it seams to work.

---

### Post by 98cwitr on 2010-05-24
I just took an image with my machine with partimage and laid it back down onto my hdd...had to shrink the partition to smaller than the new drive though :guitar:

---

### Post by Barrucadu on 2010-05-24
That's quite an improvement; I've considered getting an SSD to store the majority of my OS and keep around a smaller HDD for things like /var, maybe /home.

---

### Post by Penguin Guy on 2010-05-24
> **Barrucadu said:**
> That's quite an improvement; I've considered getting an SSD to store the majority of my OS and keep around a smaller HDD for things like /var, maybe /home.
I was thinking of doing this with a very small-capacity, fast SSD, but couldn't find SSDs much smaller than 32GB ([post here]("http://ubuntuforums.org/showthread.php?t=1458818")).

> **alpharesearch said:**
> Please note that the Live CD must be the same as the system 
you are having - either 32-bit or 64-bit (if not then the chroot later will fail).
Actually you can chroot into a 32-bit system from a 64-bit system, just not the other way round.

---

### Post by alpharesearch on 2010-06-30
Here are the additional steps for the raid0 I did:

1. If you boot in Ubuntu Live CD you need to install the mdadm with:
sudo apt-get install mdadm

2. I did the similar partitioning steps except for ID (t command) is 'fd' for Linux raid autodetect.
```

$ sudo fdisk -l /dev/sdb

Disk /dev/sdb: 50.0 GB, 50020540416 bytes
32 heads, 32 sectors/track, 95406 cylinders
Units = cylinders of 1024 * 512 = 524288 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00084b62

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               2       28674    14680576   fd  Linux raid autodetect
/dev/sdb2           28675       95406    34166784   fd  Linux raid autodetect
$ sudo fdisk -l /dev/sdc

Disk /dev/sdc: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0009ea19

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        1828    14680576   fd  Linux raid autodetect
Partition 1 does not end on cylinder boundary.
/dev/sdc2            1828        6082    34166784   fd  Linux raid autodetect
Partition 2 does not end on cylinder boundary.
/dev/sdc3            6082        6146      519873   83  Linux
/dev/sdc4            6147       12161    48315487+   7  HPFS/NTFS
markus@markus-desktop:~$ 

```

3. create the raid array:
```
$ sudo mdadm --create /dev/md0 --chunk=512 --level=raid0 --raid-devices=2 /dev/sdb1 /dev/sdc1
mdadm: array /dev/md0 started.
$ sudo mdadm --create /dev/md1 --chunk=512 --level=raid0 --raid-devices=2 /dev/sdb2 /dev/sdc2
mdadm: array /dev/md1 started.
$ sudo su
#  sudo mdadm --examine --scan >> /etc/mdadm/mdadm.conf 

```
[IMG]http://www.alpharesearch.de/ocz/Screenshot-70 GB RAID-0 Array (70 GB RAID-0 Array) – Benchmark.png[/IMG]

4. format all the new partitions and copy all the files to md0 and md1 and boot partition:
sudo cp -afv /path/to/source/* /path/to/destination

5. I'm not sure if i have to do this, but while I was in change root I also did a:
update-initramfs -u
apt-get install mdadm
mdadm --examine --scan >> /etc/mdadm/mdadm.conf 

6.Looks like the raid is very fast but the boot is not faster...
[IMG]http://www.alpharesearch.de/ocz/raid_bootchart.png[/IMG]

7. To me it feels like raid may perform a little bit better after boot, but just one ssd alone is very good. 

Regards,
Markus Schulz

PS: I suggest to save the mdadm configuration file to a non raid file system, if you do so you can copy the file later to the live CD and use the 
mdadm --assemble --scan
command to reassemble your raid.

---

### Post by andrewabc on 2010-07-01
@alpharesearch
What SSD are you using?

I'm trying to figure out the 70gb raid. indilinx 30*2=60, intel 40gb x2 = 80

I presume you have 10gb unpartitioned or something?

---

