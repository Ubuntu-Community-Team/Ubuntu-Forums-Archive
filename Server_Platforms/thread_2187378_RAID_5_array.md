---
title: "RAID 5 array"
date: 2013-11-11
forum: Server Platforms
---

### Post by manneyp on 2013-11-11
Am installing server 12.04LTS on a server with 2 hardware-controlled arrays. The O/S installed on one, but do not know how to get to the other. Fairly new Linux Server user, but have been with command-line interfaces since CP/M and Vax/VMS, just not familiar with Linux. Thanks for looking at my question--I searched for this answer, but may not have known the right questions to ask. 

Installed from CD on an HP Proliant M350 G5 with 7 drives, two 70GB and five 154GB. I have configured the two 70GB in a RAID1 array via the HP setup utility, and the five 154 GB drives as RAID5. There is no spare. I see the two arrays in the HP E200i Smart Array RAID controller utility if I enter it during boot. The RAID1 array is one controller, the RAID5's on the second.

When the setup gets to the partitioning, it thinks it sees two arrays, it did not ask me for any drivers. I told the setup to configure the first array in what seemed to be a good fashion, and it boots to the O/S OK. Either I missed the opportunity to format the second array, or that's handled later.

The O/S and my home directory appear to be living on the 70 GB RAID1 array. I'd expect it to show as a single 70 GB drive, which it does: f -h gives the following result.
Filesystem             Size  Used Avail Use% Mounted on
/dev/cciss/c0d0p1       66G  1.2G   61G   2% /
udev                   990M  4.0K  990M   1% /dev
tmpfs                  401M  420K  400M   1% /run
none                   5.0M     0  5.0M   0% /run/lock
none                  1001M  4.0K 1001M   1% /run/shm
/home/username/.Private   66G  1.2G   61G   2% /home/username

fstab makes reference to c0d0p1 and c0d0p5 (partition 5?) I see instructions that refer to drives as sda and such; I am guessing that setup decided to name my drive as c0d0p1. (Controller 0, drive 0, partition 1?)

Questions:
1) How do I get prepare (partition, format, mount) the second RAID5 array so I can use it? I can easily wipe the drive and start over and see if I can do it during setup, but would rather not. I've already had fun setting up SAMBA and SSH (Yay, me! Without asking for help...)

2) The Linux server 12.04 documentation says to run dpkg- reconfigure mdadm, but doing so tells me that mdadm is not installed. I thought it was setting up using mdadm, as setup mentioned that in the introduction. Was it just recognizing the controller without needing drivers and is that best, or should I try to use mdadm?

3) Since I will be using the RAID5 array purely for storage on a mostly Windows 7 (sorry) network, what recommendations? ext4, I assume, but since the O/S drive has a swap area, should the storage drive have one?

Again, thanks for answering my questions; I apologize if it has been handled previously.

---

### Post by nebileix on 2013-11-12
> 
1) How do I get prepare (partition, format, mount) the second RAID5 array so I can use it? I can easily wipe the drive and start over and see if I can do it during setup, but would rather not. I've already had fun setting up SAMBA and SSH (Yay, me! Without asking for help...)
do "fdisk -l" to see if your 2nd disk is listed.
> 
2) The Linux server 12.04 documentation says to run dpkg- reconfigure mdadm, but doing so tells me that mdadm is not installed. I thought it was setting up using mdadm, as setup mentioned that in the introduction. Was it just recognizing the controller without needing drivers and is that best, or should I try to use mdadm?
mdadm is for soft raid. Yours is hardware raid.
> 
3) Since I will be using the RAID5 array purely for storage on a mostly Windows 7 (sorry) network, what recommendations? ext4, I assume, but since the O/S drive has a swap area, should the storage drive have one?

Again, thanks for answering my questions; I apologize if it has been handled previously.
you might want to add "user_xattr" to mount options in /etc/fstab if using ext4. no swap required for storage drive.

---

### Post by manneyp on 2013-11-16
Thank you for the reply. 

1) fdisk -l returns nothing--just gives me another prompt
2) I suspected as much

...so how do I partition and format a drive with hardware RAID?

Thanks

---

### Post by jfolsom2 on 2013-11-16
You need to run fdisk -l with sudo...

sudo fdisk -l

---

### Post by manneyp on 2013-11-17
Ahh-HA! It lists a 581 GB disk in /dev/cciss/c0d1. The below tells me I need to partition /dev/cciss/c0d1p1? Fdisk documentation tells me it does not work for large partitions, but 600GB is small nowadays.
```
Disk /dev/cciss/c0d1: 587.1 GB, 587127480320 bytes
255 heads, 63 sectors/track, 71380 cylinders, total 1146733360 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00064580
           Device Boot      Start         End      Blocks   Id  System
/dev/cciss/c0d1p1            2048  1146732543   573365248   83  Linux
Disk /dev/mapper/cryptswap1: 2144 MB, 2144337920 bytes
255 heads, 63 sectors/track, 260 cylinders, total 4188160 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xaa2bb30b
Disk /dev/mapper/cryptswap1 doesn't contain a valid partition table
```

---

### Post by nebileix on 2013-11-18
MSDOS partition can support up to 2TB. *If I remember correctly. :p

That c0d1p1 seems been formatted with linux filesystem type. Just be sure that you got no data in it b4 you really go into partition it.

Would suggest you to use gparted for a start b4 doing it from the commandline.

---

### Post by CharlesA on 2013-11-18
> **nebileix said:**
> MSDOS partition can support up to 2TB. *If I remember correctly. :p

I've always used GPT for the partition type, even on 2TB drives.

> **nebileix said:**
> That c0d1p1 seems been formatted with linux filesystem type. Just be sure that you got no data in it b4 you really go into partition it.

Would suggest you to use gparted for a start b4 doing it from the commandline.

I've never seen something referenced as cryptoswap in LVM, unless you created it yourself.

Fire up gparted (or even parted) and check out the partition structure. If it is ok, add a file system to it and you will be good to go.

---

### Post by manneyp on 2013-11-22
I ran gparted from a live CD. It said there is no partition on C0D1--I therefore created an EXT4 partition. It played with its toes for a few minutes, then reported that it had finished. 

Managed to mess up the fstab file when editing, so re-ran the Ubuntu server 12.04 setup, not touching c0d1. Now, fdisk -l tells me there is a c0d0 and a c0d0p1. 

Got UUID of c0d1 from fdisk -l 
Added to /etc/fstab this line -- UUID=XXXXXXXXXXXXXXX   / ext4    defaults     0        2

Now, I want to create a directory. I try mkdir /dev/cciss/c0d0p1/share
It tells me, "cannot create a directory /dev/cciss/c0d0p1/share: Not a directory".

Do I need to do something first?

---

### Post by CharlesA on 2013-11-22
> **manneyp said:**
> I ran gparted from a live CD. It said there is no partition on C0D1--I therefore created an EXT4 partition. It played with its toes for a few minutes, then reported that it had finished. 

Managed to mess up the fstab file when editing, so re-ran the Ubuntu server 12.04 setup, not touching c0d1. Now, fdisk -l tells me there is a c0d0 and a c0d0p1. 

Got UUID of c0d1 from fdisk -l 
Added to /etc/fstab this line -- UUID=XXXXXXXXXXXXXXX   / ext4    defaults     0        2

Now, I want to create a directory. I try mkdir /dev/cciss/c0d0p1/share
It tells me, "cannot create a directory /dev/cciss/c0d0p1/share: Not a directory".

Do I need to do something first?

You need to mount the drive first. You can't create files in the /dev/ folder as that is just a virtual directory that kernel creates during boot.

Are you sure that line in fstab is correct? You are mounting that drive on the root (/) of the file system. I have my array set to mount to /array/ (:rolleyes:).

---

### Post by manneyp on 2013-11-27
I pulled the drives in order to wipe three more of the same type (ah, the joy of freebie drives.) The system is tied up: in the meantime, have been looking at fstab syntax here--[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab).

I spy, with my little eye, the following syntax...
[Device] [Mount Point] [File System Type] [Options] [Dump] [Pass] 

[Device]=uuid, have that
[Mount Point]=??A directory in my existing Linux file structure on the existing drive, such as /home/username? I also see I must create the mount point by the sudo mkdir command.
[File System Type]=ext4, or whatever type I used to create the partition and format it
[Options] defaults? I do not see any other applicable options
[Dump] 0 
[Pass] 2

You refer to mount point /array/.  Thus, I issue, from the command line,
sudo mkdir /array or /user_xattr, from the first reply
--Is this right?

...and my syntax for the applicable line is-- 
# Mount RAID5 array
UUID=XXXXXXXXXXXXXXX   /array ext4    defaults     0        2

(that is, no second slash after array)?
Thanks,

---

### Post by CharlesA on 2013-11-27
That looks fine as long as you have already created the /array/ directory.

Mine is set like this:

```
UUID=blahblah /array ext4 noexec 0 0
```

But I do manual fsck of the array. :)

---

### Post by manneyp on 2013-11-28
Thanks, everyone! Looks as if it worked; I can now see the array. 

I still cannot write data to it from Win7 (I can see it as a samba share, but cannot authenticate), but that's something else. Thanks again: I look forward to gaining enough experience to be able to help others, as I do in the Windows and Android environments.

---

