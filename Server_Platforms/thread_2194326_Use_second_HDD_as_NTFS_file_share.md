---
title: "Use second HDD as NTFS file share"
date: 2013-12-17
forum: Server Platforms
---

### Post by RufusThorne on 2013-12-17
I just set up a server:

[TABLE="width: 495"]
[TR]
[TD="class: label tight-fit"]Distribution:[/TD]
[TD]Ubuntu 12.04.3 LTS (precise)[/TD]
[/TR]
[TR]
[TD="class: label tight-fit"]Hardware:[/TD]
[TD][TABLE="class: inner-table, width: 358"]
[TR]
[TD="class: label tight-fit"]Processor:[/TD]
[TD]Intel(R) Pentium(R) 4 CPU 3.00GHz[/TD]
[/TR]
[TR]
[TD="class: label tight-fit"]Memory:[/TD]
[TD]2 GiB RAM[/TD]
[/TR]
[TR]
[TD="class: label tight-fit"]Storage:[/TD]
[TD]Model: HDS728080PLA380
Size: 82 GB

Model: WDC WD800BD-22JM
Size: 80 GB

[/TD]
[/TR]
[TR]
[TD="class: label tight-fit"]Network:[/TD]
[TD]Model: 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller
MAC: 00:16:76:28:00:a4
IP: 192.168.0.32

[/TD]
[/TR]
[TR="class: no-border-bottom"]
[TD="class: label tight-fit"]Video:[/TD]
[TD]82915G/GV/910GL Integrated Graphics Controller[/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[TR]
[TD="class: label tight-fit"]Product identifier:[/TD]
[TD]Dell DV051
[/TD]
[/TR]
[/TABLE]

Basically what I want to do is use this experience to learn my way around Ubuntu Server, since I only have Desktop knowledge (GNOME user for 3 years) and rudimentary Terminal skills.
The 82GB drive (what I assume to be /dev/hda) is the OS drive, but I can't understand how to use FDisk to make the second drive NTFS so I can then install Samba and have this machine also serving files to Windows clients

Thanks for taking time to read my thread  x

---

### Post by Iowan on 2013-12-17
Terrible to get old and rusty...
If I remember correctly, Samba serves files from a Linux (ext4) partition.

---

### Post by SeijiSensei on 2013-12-17
> **Iowan said:**
> Terrible to get old and rusty...
If I remember correctly, Samba serves files from a Linux (ext4) partition.

Indeed it does.  Let's assume this new disk appears as /dev/sdb.

In fdisk, use (n)ew, (p)rimary and follow the prompts to allocate all the cylinders to a single partition.

Then use (t)ype and enter 83, which is the code for Linux.

Save the partition table with (w)rite, then (q)uit.

Now run the command:

```
sudo mkfs -t ext4 /dev/sdb1
```

When it's done formatting, mount the drive some place in the root filesystem.  The standard location these days is in some directory under /media.  Edit smb.conf to export that directory to Windows machines.

PS:  If you do indeed have IDE hard drives that appear as /dev/hdX in the operating system, then you would replace /dev/sdb with /dev/hdb above.

---

### Post by RufusThorne on 2013-12-18
Thank you kindly for your great replies :-)
I found the secondary disk using FDisk, and removed all partitions from it, retstarted and now I don't seem to be able to see it anymore?!

See what I mean :


sudo fdisk -l
[sudo] password for rufus:


Disk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders, total 160836480 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0006416c


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   156661759    78329856   83  Linux
/dev/sda2       156663806   160835583     2085889    5  Extended
/dev/sda5       156663808   160835583     2085888   82  Linux swap / Solaris


Disk /dev/sdb (Sun disk label): 255 heads, 63 sectors, 9729 cylinders
Units = sectors of 1 * 512 bytes


   Device Flag    Start       End    Blocks   Id  System
/dev/sdb1             0 156199995  78099997+  83  Linux native
/dev/sdb2  u  156199995 156296385     48195   82  Linux swap
/dev/sdb3             0 156296385  78148192+   5  Whole disk


Disk /dev/sdb1 (Sun disk label): 255 heads, 63 sectors, 9729 cylinders
Units = sectors of 1 * 512 bytes


    Device Flag    Start       End    Blocks   Id  System
/dev/sdb1p1             0 156199995  78099997+  83  Linux native
/dev/sdb1p2  u  156199995 156296385     48195   82  Linux swap
/dev/sdb1p3             0 156296385  78148192+   5  Whole disk


Disk /dev/sdb3 (Sun disk label): 255 heads, 63 sectors, 9729 cylinders
Units = sectors of 1 * 512 bytes


    Device Flag    Start       End    Blocks   Id  System
/dev/sdb3p1             0 156199995  78099997+  83  Linux native
/dev/sdb3p2  u  156199995 156296385     48195   82  Linux swap
/dev/sdb3p3             0 156296385  78148192+   5  Whole disk


Disk /dev/mapper/cryptswap1: 2135 MB, 2135949312 bytes
255 heads, 63 sectors/track, 259 cylinders, total 4171776 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/mapper/cryptswap1 doesn't contain a valid partition table
rufus@webserver:~$






Where has my 80GB drive gone?!  What is this 'Sun Disk Label'?

---

### Post by SeijiSensei on 2013-12-18
If you just installed the other drives, I'd check the cables to make sure all the drives are firmly connected.  I've had my share of difficulties with SATA cables and poorly positioned sockets on the motherboard.

Next, I'd check the BIOS to see if the drive shows up there.  If not, it's a hardware issue.

---

### Post by volkswagner on 2013-12-18
From your hardware list I see two hard drives 82gig and 80gig.

From your fdisk -l output I see two hard drives sda and sdb.

I have never seen an output like you have for sdb.

Please post output of following two commands.

```
cat /etc/fstab
```

```
sudo blkid
```

```
sudo mount
```

---

### Post by RufusThorne on 2013-12-18
```
cat /etc/fstab
```

rufus@webserver:~$** cat /etc/fstab**
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=12273d73-196e-4652-91eb-fbd556b5476f /               ext4    errors=remount        -ro 0       1
# swap was on /dev/sda5 during installation
#UUID=fe9a972a-5f4f-4ff2-a9e3-a4e0a1fc9f2b none            swap    sw                      0       0
/dev/mapper/cryptswap1 none swap sw 0 0


```
sudo blkid
```

rufus@webserver:~$ **sudo blkid**
[sudo] password for rufus:
/dev/sda1: UUID="12273d73-196e-4652-91eb-fbd556b5476f" TYPE="ext4"
/dev/mapper/cryptswap1: UUID="d418044e-703f-403a-a98a-d0993f7f9ae6" TYPE="swap"


```
sudo mount
```[/QUOTE]

rufus@webserver:~$ **sudo mount**
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
/home/rufus/.Private on /home/rufus type ecryptfs (ecryptfs_check_dev_ruid,ecryptfs_cipher=aes,ecryptfs_key_bytes=16,ecryptfs_unlink_sigs,ecryptfs_sig=cedfe7f171c73be6,ecryptfs_fnek_sig=f71d654dd3812478)

Can you please explain these commands for my future reference? Thanks for your continued help :-)

---

### Post by volkswagner on 2013-12-18
The file /etc/fstab is the configuration file used to create permanent mount points.  As you can see inside the file, the installer left nice notes about the disk, ie; /dev/sdax and also the UUID #.  The UUID is a unique id for each partition and is the preferred way to identify a partition/mount point in /etc/fstab.  Some BIOS systems can cause linux to see disk1 as /dev/sda then next boot see the same disk as /dev/sdb.  Using the UUID eliminates mounting errors if the disk changes from /dev/sda to /dev/sdb.

The mount command shows all currently mounted partitions/file systems.

The BLKID command shows the UUID for each volume, which will help when you're ready to create a permanent mount point entry in /etc/fstab.

My guess is you may have forgot to use the 'w' command in fdisk to write your changes.

Here is a [general how to]("http://www.howtogeek.com/106873/how-to-use-fdisk-to-manage-partitions-on-linux/") to create a mount point.  As stated you can mount the new partition anywhere you have an empty directory.  So you need to create the path first, like...

```
sudo mkdir /media/sambaDisk
```

---

