---
title: "Raid boot error: md0: unknown partition table"
date: 2012-07-31
forum: Server Platforms
---

### Post by icedfusion on 2012-07-31
I have just finished building an 8 disk (2TB each disk) raid 6 array + lvm + xfs, which is currently empty.

Each drive was first setup using parted:
```

parted -a optimal /dev/sdb
GNU Parted 2.3
Using /dev/sdb
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) mklabel gpt 
(parted) mkpart primary 1 -1
(parted) align-check                                                      
alignment type(min/opt)  [optimal]/minimal? optimal                       
Partition number? 1                                                       
1 aligned
(parted) quit

```

raid setup command:
```

mdadm --create --verbose /dev/md0 --level=6 --raid-devices=8 --chunk=256 /dev/sd[bcdefghi]1

```

created the lvm part using
pvcreate
vgcreate
lvcreate

i then formated each lv using xfs:
```

mkfs.xfs -f /dev/server/name

```



I have all the mount points setup in my /etc/fstab file which i tested work fine, however, when I reboot the system will appear to hang just after grub.

If I hold shift down to get into grub and add the command bootdegraded=true
the system first boots into a busybox shell, where I can then exit which will then fall into the proper shell.

My question is why does the raid not boot up and dmesg outputs the error:
```

md0: unknown partition table

```

I do not mind completely rebuilding to get this right, so if i have to break down the array and do something different please give me some hints.

Cheers

ice.

---

### Post by rubylaser on 2012-07-31
What do you have in your /etc/mdadm/mdadm.conf file?  
```
cat /etc/mdadm/mdadm.conf
```

Also,  is there a reason you require LVM (it's not needed to allow expansion, or growth as many older mdadm tutorials demonstrate)?  Finally, unless, you are set on XFS, I don't touch that with a 10 foot pole.  I've experienced too many corruption issues with large datasets both and home and at work.  ext4, or jfs have worked much better for me.

---

### Post by icedfusion on 2012-08-01
Thanks for the response. It is appreciated. 
I did initially start following your raid guide that you link to in your signature as I have seen you answer a lot of these type of questions and your info is very helpful.

I have not read much about the failings of xfs, if the advantages are not that great compared to ext4, then I can always use that.

I used LVM so that I could grow and shrink my volumes as required and be able to take manageable 'copies' of the logical volumes for backup and also be able to add new larger disks in the future - rather than just have one massive raid disk with folders on them - which from your guide is what you seem to have done?

However, I am not set on using raid6+lvm+xfs - this is my first raid system and really this is what i have read about when doing some googling on the subject.

my mdadm.conf file output:
```

DEVICE partitions
HOMEHOST fileserver
MAILADDR <my_email>
ARRAY /dev/md/0 metadata=1.2 name=iceserver:0 UUID=723d62ee:a1bef912:ebcc884c:c14df931

```

Cheers

ice.

---

### Post by rubylaser on 2012-08-01
> **icedfusion said:**
> Thanks for the response. It is appreciated. 
I did initially start following your raid guide that you link to in your signature as I have seen you answer a lot of these type of questions and your info is very helpful.

I have not read much about the failings of xfs, if the advantages are not that great compared to ext4, then I can always use that.

I used LVM so that I could grow and shrink my volumes as required and be able to take manageable 'copies' of the logical volumes for backup and also be able to add new larger disks in the future - rather than just have one massive raid disk with folders on them - which from your guide is what you seem to have done?

However, I am not set on using raid6+lvm+xfs - this is my first raid system and really this is what i have read about when doing some googling on the subject.

my mdadm.conf file output:
```

DEVICE partitions
HOMEHOST fileserver
MAILADDR <my_email>
ARRAY /dev/md/0 metadata=1.2 name=iceserver:0 UUID=723d62ee:a1bef912:ebcc884c:c14df931

```

Cheers

ice.

Yes, I have set up a massive RAID volume, but it's easily incrementally backed up via rsnapshot or to my Openindiana ZFS servers at home or work, so LVM is really unnecessary for me except in situations where I want to take virtual machine snapshots (I connect to my Openindiana via ISCI and use ZFS snapshots instead of LVM on my Ubuntu boxes).  You can easily add more disks to an mdadm array and even shrink an array and it's filesystem without LVM if you choose (LVM does make shrinking a little easier though).

I would suggest modifying your /etc/mdadm/mdadm.conf file.  It is not going to make itself available at /dev/md0 consistently based on what you have.  I'd change it as follows (all the extra portions are unnecessary for assembly and can actually cause problems) and update your initramfs.

```
DEVICE partitions
HOMEHOST fileserver
MAILADDR <my_email>
ARRAY /dev/md0 UUID=723d62ee:a1bef912:ebcc884c:c14df931
```

```
update-initramfs -u
```

Finally, make sure that you are mentioned /dev/md0 in your /etc/fstab.

---

### Post by icedfusion on 2012-08-01
Thanks for the input, after reading more about 'why use lvm' and 'why use xfs' - for my personal home server, having these is probably overkill - I suspect a raid6+ext4 and using rsync will meet my needs. 

I don't have/need to grow the disks - I just thought it would be nice to have a play, in fact I don't have any space left for more drives, just replacement ones. I will destroy my lvm setup and reformat the whole raid array using ext4.

I will also do the actions you mentioned as well.

What is the purpose of doing:
```

update-initramfs -u

```

I have not seen that command being used in any raid/filesystem setup?

Cheers

ice.

---

### Post by rubylaser on 2012-08-01
The update-initramfs update the initial ramdisk filesystem used to boot into Ubuntu.  This will integrate the changes that you make to the mdadm.conf file and ensure that they are used properly.  This is not typically necessary, but I always do it when I'm changing my mdadm.conf file.

As a caveat for using ext4, you'll need to use a newer version of e2fsprogs if you want to create a filesystem that will support 16TB+.  Ubuntu 12.04 comes with e2fsprogs version 1.42, and this version supports creating a 64bit filesystem (will support > 16TB) like this.

```
mkfs.ext4 -O 64bit /dev/md0
```

---

### Post by icedfusion on 2012-08-01
Thanks for the info - it is really helpful. When I finish work I will have another play with my server.

I noticed from your wiki that you manage VMs at work. 

I do eventually want to do more with my server than it just being a massive file store, i.e. possibly put some vm's on it, ampache etc, so is just going for the 'raid6+ext4' good enough?

The hardware is pretty high for a home server as well - i.e. 8 core amd processor lots of RAM etc...

The actual OS lives on a 128GB SSD - a bit overkill, but hey someone said that about 128k being enough memory for anyone!

Cheers

ice.

---

### Post by icedfusion on 2012-08-01
on another note:

You mention that I should add:

/dev/md0 to my fstab?

Why do I do this as it is not formatted to anything - I just created the raid6 array, add my lvm ontop and formatted those then added created lvm to my fstab.

How do I add /dev/md0 if I do not have it formatted to anything?


Cheers

ice.

---

### Post by rubylaser on 2012-08-01
> **icedfusion said:**
> Thanks for the info - it is really helpful. When I finish work I will have another play with my server.

I noticed from your wiki that you manage VMs at work. 

I do eventually want to do more with my server than it just being a massive file store, i.e. possibly put some vm's on it, ampache etc, so is just going for the 'raid6+ext4' good enough?

The hardware is pretty high for a home server as well - i.e. 8 core amd processor lots of RAM etc...

The actual OS lives on a 128GB SSD - a bit overkill, but hey someone said that about 128k being enough memory for anyone!

Cheers

ice.

At home, I have an All-in-One box with my ZFS server.  It is an ESXi host, with (2) IBM m1015 HBA pci passed through to my Openindiana box that has access to all of my disks. I use a RAIDZ2 array there (like RAID6) and share out a folder via NFS for ESXi to use as a virtual machine store.  This has worked great for me.  My home ESXi server is all server hardware.

Xeon E3-1230 V2, SUPERMICRO MBD-X9SCM-F-O, 32GB of ECC RAM, (2) IBM m1015's, and (10) 2TB hard drives + (2) Intel 320's mirror for my log, a Dell Silicom PEG6I Six Port Gigabit Ethernet.

At work, I have a mix of Hyper-V, ESXi, and Proxmox boxes for virtualization.  I don't really use Virtualbox for anything other than testing scenarios quickly at work.

---

### Post by rubylaser on 2012-08-01
> **icedfusion said:**
> on another note:

You mention that I should add:

/dev/md0 to my fstab?

Why do I do this as it is not formatted to anything - I just created the raid6 array, add my lvm ontop and formatted those then added created lvm to my fstab.

How do I add /dev/md0 if I do not have it formatted to anything?


Cheers

ice.

I mentioned adding it to /etc/fstab if you where going to remove LVM from your array setup.  If so, you'd want to mount the ext4 formatted /dev/md0.

---

### Post by icedfusion on 2012-08-01
OK, so i removed all my logical volumes, group and physical volume so I was back to just my raid6 array.



I then went back and followed the rest of the steps from your tutorial and what you have mentioned here then just formated ext4 with optimised settings (created settings by using the link to calc you gave).

Added line to fstab - test and all mounts fine.

However, do a reboot and I still get the same error command:
```

md0: unknown partition table

```
and the system appears to hang. I then have to force a reboot and add 
```

bootdegraded=true

```

I have attached my dmesg output if that helps as I am at a bit of a loss now - googling this error does not appear to give any real help.

Cheers

ice.

---

### Post by rubylaser on 2012-08-01
Your array should not have a partition on it if you don't have LVM in place.  You will apply the filesystem to the block level md0 device.  Are you saying your array isn't mounting and you're having to push the "s" key to continue on a reboot?  From your dmesg output it says that it's mounting the array.  
```
[  119.904210] EXT4-fs (md0): mounted filesystem with ordered data mode. Opts: (null)
```
The lack of a partition is not a bad message based on what I mentioned above.

What's the output of these?
```
cat /etc/mdadm/mdadm.conf
```
```
cat /etc/fstab
```
```
mdadm --detail /dev/md0
```
```
mount
```
```
df -h
```

Also, did you update your initramfs after doing all of these changes?

---

### Post by icedfusion on 2012-08-02
> **rubylaser said:**
> Your array should not have a partition on it if you don't have LVM in place.  You will apply the filesystem to the block level md0 device.  Are you saying your array isn't mounting and you're having to push the "s" key to continue on a reboot?  From your dmesg output it says that it's mounting the array.  
```
[  119.904210] EXT4-fs (md0): mounted filesystem with ordered data mode. Opts: (null)
```
The lack of a partition is not a bad message based on what I mentioned above.

What's the output of these?
```
cat /etc/mdadm/mdadm.conf
```
```
cat /etc/fstab
```
```
mdadm --detail /dev/md0
```
```
mount
```
```
df -h
```

Also, did you update your initramfs after doing all of these changes?

Thanks for the help - I would be really stuck otherwise as I have no idea about what is going wrong.
These have been obtained after booting with bootdegraded=true

It does appear as though there is a problem with the array - as my screen will just go blank after it reaches 'booting Operating system' - If I then reboot and press shift, then modify the grub line to include 'bootdegraded=true', it will start to boot then drop out at an initramfs prompt. If I then type 'exit' it will continue booting and everything seems ok? I don't really know what the consequence of booting with 'bootdegraded=true' means - I just read that it worked for someone else so tried it.

So to answer your questions:

1. 
```
cat /etc/mdadm/mdadm.conf
```
```
 
DEVICE partitions
HOMEHOST fileserver
MAILADDR <my_email>
ARRAY /dev/md0 UUID=723d62ee:a1bef912:ebcc884c:c14df931

```

2.
```
cat /etc/fstab
```
```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=b82505a6-94f2-4148-a33f-3948cdcfe6b5 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=3e76de3b-89a1-4a6a-8dce-c10df7c909d9 none            swap    sw              0       0
#/dev/icefileserver/movies /media/movies xfs defaults 0 0
#/dev/icefileserver/tv /media/tv xfs defaults 0 0
#/dev/icefileserver/music /media/music xfs defaults 0 0
#/dev/icefileserver/backup /media/backup xfs defaults 0 0
#/dev/icefileserver/working /media/working xfs defaults 0 0

/dev/md0 /media/storage ext4 defaults 0 0

192.168.1.2:/home/icedfusion /media/icetv nfs defaults 0 0

```

3.
```
mdadm --detail /dev/md0
```
```

/dev/md0:
        Version : 1.2
  Creation Time : Mon Jul 30 20:34:55 2012
     Raid Level : raid6
     Array Size : 11721073152 (11178.09 GiB 12002.38 GB)
  Used Dev Size : 1953512192 (1863.01 GiB 2000.40 GB)
   Raid Devices : 8
  Total Devices : 8
    Persistence : Superblock is persistent

    Update Time : Thu Aug  2 09:49:04 2012
          State : active 
 Active Devices : 8
Working Devices : 8
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 256K

           Name : iceserver:0
           UUID : 723d62ee:a1bef912:ebcc884c:c14df931
         Events : 20

    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       8       33        1      active sync   /dev/sdc1
       2       8       49        2      active sync   /dev/sdd1
       3       8       65        3      active sync   /dev/sde1
       4       8       81        4      active sync   /dev/sdf1
       5       8       97        5      active sync   /dev/sdg1
       6       8      113        6      active sync   /dev/sdh1
       7       8      129        7      active sync   /dev/sdi1


```

4.
```
mount
```
```

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
/dev/md0 on /media/storage type ext4 (rw)
rpc_pipefs on /run/rpc_pipefs type rpc_pipefs (rw)
nfsd on /proc/fs/nfsd type nfsd (rw)
192.168.1.2:/home/icedfusion on /media/icetv type nfs (rw,vers=4,addr=192.168.1.2,clientaddr=0.0.0.0)


```

5.
```
df -h
```
```

Filesystem                    Size  Used Avail Use% Mounted on
/dev/sda1                     104G  3.1G   96G   4% /
udev                          3.9G  4.0K  3.9G   1% /dev
tmpfs                         1.6G  672K  1.6G   1% /run
none                          5.0M     0  5.0M   0% /run/lock
none                          3.9G     0  3.9G   0% /run/shm
/dev/md0                       11T   83G   11T   1% /media/storage
192.168.1.2:/home/icedfusion  183G  113G   70G  62% /media/icetv

```

Also, I did do the update-initramfs -u as well.

I would also be interested to know what is using 83G of space when it is a fresh raid array - that is a monster amount of space for 'nothing', I even did the tune2fs that you pointed out in your guide.

Cheers

ice.

---

### Post by rubylaser on 2012-08-02
It appears that there may still be remnants of a partition on your mdadm device.  Can you provide the output of these?

```
fdisk -l
```

Also, if you comment out your /dev/md0 line in /etc/fstab and reboot, does the array assemble correctly automatically after a reboot and not halt the system boot process?

```
cat /proc/mdstat
```

---

### Post by icedfusion on 2012-08-02
> **rubylaser said:**
> It appears that there may still be remnants of a partition on your mdadm device.  Can you provide the output of these?

```
fdisk -l
```

Also, if you comment out your /dev/md0 line in /etc/fstab and reboot, does the array assemble correctly automatically after a reboot and not halt the system boot process?

```
cat /proc/mdstat
```

Here is the info:
```
fdisk -l
```
```


WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


WARNING: GPT (GUID Partition Table) detected on '/dev/sdc'! The util fdisk doesn't support GPT. Use GNU Parted.


WARNING: GPT (GUID Partition Table) detected on '/dev/sdd'! The util fdisk doesn't support GPT. Use GNU Parted.

Disk /dev/md0 doesn't contain a valid partition table

WARNING: GPT (GUID Partition Table) detected on '/dev/sde'! The util fdisk doesn't support GPT. Use GNU Parted.


WARNING: GPT (GUID Partition Table) detected on '/dev/sdf'! The util fdisk doesn't support GPT. Use GNU Parted.


WARNING: GPT (GUID Partition Table) detected on '/dev/sdg'! The util fdisk doesn't support GPT. Use GNU Parted.


WARNING: GPT (GUID Partition Table) detected on '/dev/sdh'! The util fdisk doesn't support GPT. Use GNU Parted.


WARNING: GPT (GUID Partition Table) detected on '/dev/sdi'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00084f92

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   217702399   108850176   83  Linux
/dev/sda2       217704446   234440703     8368129    5  Extended
/dev/sda5       217704448   234440703     8368128   82  Linux swap / Solaris

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1  3907029167  1953514583+  ee  GPT
Partition 1 does not start on physical sector boundary.

Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1  3907029167  1953514583+  ee  GPT
Partition 1 does not start on physical sector boundary.

Disk /dev/sdd: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1  3907029167  1953514583+  ee  GPT
Partition 1 does not start on physical sector boundary.

Disk /dev/md0: 12002.4 GB, 12002378907648 bytes
2 heads, 4 sectors/track, -1364699008 cylinders, total 23442146304 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 262144 bytes / 1572864 bytes
Disk identifier: 0x00000000


Disk /dev/sde: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1  3907029167  1953514583+  ee  GPT
Partition 1 does not start on physical sector boundary.

Disk /dev/sdf: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1  3907029167  1953514583+  ee  GPT

Disk /dev/sdg: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1               1  3907029167  1953514583+  ee  GPT

Disk /dev/sdh: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdh1               1  3907029167  1953514583+  ee  GPT

Disk /dev/sdi: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdi1               1  3907029167  1953514583+  ee  GPT


```

The 'error's at the top of this file were not printed out like this, i think that my redirect was incorrect:

fdisk -l > fdisk.txt 2>>1


I commented out the /dev/md0 line and the same problem still persists. Once I rebooted and added bootdegraded=true, I was able to get back in:



```
cat /proc/mdstat
```
```

Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid6 sdg1[5] sdh1[6] sdi1[7] sdf1[4] sde1[3] sdb1[0] sdd1[2] sdc1[1]
      11721073152 blocks super 1.2 level 6, 256k chunk, algorithm 2 [8/8] [UUUUUUUU]
      
unused devices: <none>


```

Cheers

ice.

---

### Post by icedfusion on 2012-08-02
OK, so I *think* I may have solved the issue.


I found this blog:
[http://www.bomski.com/ubuntu-11-10-with-raidnot-booting-after-installing-mdadm-read-on/]("http://www.bomski.com/ubuntu-11-10-with-raidnot-booting-after-installing-mdadm-read-on/")


Which is a link to a post on ubuntu forums:
[http://ubuntuforums.org/showpost.php?p=11388915&postcount=18]("http://ubuntuforums.org/showpost.php?p=11388915&postcount=18")

Basically, the solution lies with allowing all udev rules to complete before actually doing a check on the raid array.

Whilst I do not have an error specifically with degraded arrays, I believe inserting this command allows for my disks to activate before any other checks are done.

```

degraded_arrays()
{
        mdadm --misc --scan --detail --test >/dev/null 2>&1
        return $((! $?))
}

```
and change it to:

```


degraded_arrays()
{
        udevadm settle
        mdadm --misc --scan --detail --test >/dev/null 2>&1
        return $((! $?))
}

```
then do a:

```

sudo update-initramfs -k all -u

```


I guess my question is, how do I check that my raid is working as expected?
I can always try 'failing' a disk to see what happens??

Cheers

ice.

---

### Post by rubylaser on 2012-08-02
I wouldn't suggest failing a disk. You will have a massive resync time, unless you add in internal bitmap first, but that's like cheating :)  Your array has been and continues to work, and this sounds like the solution.  I find it weird, I've never hit this problem with my 8 disk RAID6 mdadm array. 

Thanks for posting back with this.  I was looking at this post a couple days ago, and didn't even think about it as a possible solution to your problem ](*,) Glad you got it figured out.

---

### Post by icedfusion on 2012-08-02
You shouldn't be thanking me. I appreciate that you stuck with my questions and offered some possible solutions.

I am not 100% sure why I have this issue without a 'degraded raid array' being reported.

It is entirely possible that it is my setup. I have a dell SAS>SATA where I plugin in 4 SATA drives and have the other 4 on the motherboard. I have 8 ports on the motherboard, but only 6 of them work as the chipset for the last 2 is Marvel and there are some issues with that (I tried the solutions offered but none worked).

I did have two of those SAS>SATA cards, but only 7 of my 8 disks were being shown in ubuntu - it could very well be due to this issue with udev and the disks not being ready/responding in time.

However, I ramble. I hope that someone else finds this thread useful.

Cheers

ice.

---

