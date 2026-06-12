---
title: "Re:  Are my disks okay ?"
date: 2015-11-28
forum: Server Platforms
---

### Post by soamz on 2015-11-28
I just installed Ubuntu server in one of my server. 
Then opened the terminal and entered sudo fdisk -l

And I got this, 

> 
jet@ubuntu:~$ sudo fdisk -l
[sudo] password for jetplex: 


WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.




Disk /dev/sdb: 3999.7 GB, 3999688294400 bytes
255 heads, 63 sectors/track, 486267 cylinders, total 7811891200 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0a8334fb


Disk /dev/sdb doesn't contain a valid partition table


Disk /dev/sda: 119.5 GB, 119453777920 bytes
255 heads, 63 sectors/track, 14522 cylinders, total 233308160 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b39af


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   166209535    83103744   83  Linux
/dev/sda2       166211582   233306111    33547265    5  Extended
/dev/sda5       166211584   233306111    33547264   82  Linux swap / Solaris

Its a Dell 2950 server. 
I have 3 disks inserted. 
1 is SSD 120GB.
The other 2 are SSHD 2TB each. 

I created 2 virtual disk in RAID0. 

SSD 120GB = 1 Virtual Disk in RAID0
SSHD 2+2 = 4TB = 1 Virtual Disk in RAID0

Then installed Ubuntu Server in the 1st SSD 120GB thing, when it asked me for disk partition thing. 
I simply selected the SSD and wrote to the disk, when it asked. 

Now, I need the Ubuntu to stay in the SSD only, as it is. 

But I want to fill the 2TB SSHDs with my data, so the Ubuntu server should auto accept and adapt to the 2 disk (1 virtual drive) ? 

Or am I missing something ?

---

### Post by darkod on 2015-11-28
Yes, the disks are ok. The 4TB disk has to have gpt table because msdos table can only work with up to 2TB disks. And fdisk does not work good with gpt tables, as the message says. It's best to use parted for partitioning and listing partitions.

Linux works with mount points, which is basically any empty folder that has been created. Then you can mount the wanted partition to the wanted folder (mount point) and use it.

So, what you need to do is use parted for example to create one or more partitions on /dev/sdb. You can find many tutorials for parted on the internet. How many partitions you decide to create and their size is your choice.

After that create an empty folder and name it as you wish (you can't use a folder name that already exists). For example you can create a folder /data.

Then you can format and mount the partition you created on the /data mount point and use it as /data in your linux system.

This is just an example, you will adjust it to your needs. Also search on google how to use /etc/fstab to make the partition(s) mount each time on boot automatically.

---

### Post by soamz on 2015-11-28
> **darkod said:**
> Yes, the disks are ok. The 4TB disk has to have gpt table because msdos table can only work with up to 2TB disks. And fdisk does not work good with gpt tables, as the message says. It's best to use parted for partitioning and listing partitions.

Linux works with mount points, which is basically any empty folder that has been created. Then you can mount the wanted partition to the wanted folder (mount point) and use it.

So, what you need to do is use parted for example to create one or more partitions on /dev/sdb. You can find many tutorials for parted on the internet. How many partitions you decide to create and their size is your choice.

After that create an empty folder and name it as you wish (you can't use a folder name that already exists). For example you can create a folder /data.

Then you can format and mount the partition you created on the /data mount point and use it as /data in your linux system.

This is just an example, you will adjust it to your needs. Also search on google how to use /etc/fstab to make the partition(s) mount each time on boot automatically.


Any specific set of commands to run ?
I just need the 4TB available, as I have to install 2 of my websites and Plex Media server.

Okay did it!

Can you check if its right ? 


> root@ubuntu:~# parted /dev/sdbGNU Parted 2.3
Using /dev/sdb
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) (parted) mklabel gpt                                             
  align-check TYPE N                        check partition N for TYPE(min|opt) alignment
  check NUMBER                             do a simple check on the file system
  cp [FROM-DEVICE] FROM-NUMBER TO-NUMBER   copy file system to another partition
  help [COMMAND]                           print general help, or help on COMMAND
  mklabel,mktable LABEL-TYPE               create a new disklabel (partition table)
  mkfs NUMBER FS-TYPE                      make a FS-TYPE file system on partition NUMBER
  mkpart PART-TYPE [FS-TYPE] START END     make a partition
  mkpartfs PART-TYPE FS-TYPE START END     make a partition with a file system
  resizepart NUMBER END                    resize partition NUMBER
  move NUMBER START END                    move partition NUMBER
  name NUMBER NAME                         name partition NUMBER as NAME
  print [devices|free|list,all|NUMBER]     display the partition table, available devices, free space, all found partitions, or a particular partition
  quit                                     exit program
  rescue START END                         rescue a lost partition near START and END
  resize NUMBER START END                  resize partition NUMBER and its file system
  rm NUMBER                                delete partition NUMBER
  select DEVICE                            choose the device to edit
  set NUMBER FLAG STATE                    change the FLAG on partition NUMBER
  toggle [NUMBER [FLAG]]                   toggle the state of FLAG on partition NUMBER
  unit UNIT                                set the default unit to UNIT
  version                                  display the version number and copyright information of GNU Parted
(parted) mklabel gpt                                                      
Warning: The existing disk label on /dev/sdb will be destroyed and all data on this disk will be lost. Do you want to continue?
Yes/No? Yes                                                               
(parted) unit TB                                                          
(parted) mkpart primary 0.00TB 4.00TB                                     
(parted) print                                                            
Model: DELL PERC 5/i (scsi)
Disk /dev/sdb: 4.00TB
Sector size (logical/physical): 512B/512B
Partition Table: gpt


Number  Start   End     Size    File system  Name     Flags
 1      0.00TB  4.00TB  4.00TB               primary


(parted) quit                                                             
Information: You may need to update /etc/fstab.                           


root@ubuntu:~# mkfs.ext4 /dev/sdb1
mke2fs 1.42.9 (4-Feb-2014)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
Stride=0 blocks, Stripe width=0 blocks
244121600 inodes, 976485888 blocks
48824294 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=4294967296
29800 block groups
32768 blocks per group, 32768 fragments per group
8192 inodes per group
Superblock backups stored on blocks: 
	32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
	4096000, 7962624, 11239424, 20480000, 23887872, 71663616, 78675968, 
	102400000, 214990848, 512000000, 550731776, 644972544


Allocating group tables: done                            
Writing inode tables: done                            
Creating journal (32768 blocks): done
Writing superblocks and filesystem accounting information: mkdir /data
done


root@ubuntu:~# mkdir /data
root@ubuntu:~# mount /dev/sdb1 /data
root@ubuntu:~# df -H
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1        84G  1.5G   78G   2% /
none            4.1k     0  4.1k   0% /sys/fs/cgroup
udev             17G  4.1k   17G   1% /dev
tmpfs           3.4G  1.2M  3.4G   1% /run
none            5.3M     0  5.3M   0% /run/lock
none             17G     0   17G   0% /run/shm
none            105M     0  105M   0% /run/user
/dev/sdb1       4.0T   72M  3.8T   1% /data
root@ubuntu:~# cd /
root@ubuntu:/# ls
bin  boot  data  dev  etc  home  initrd.img  lib  lib64  lost+found  media  mnt  opt  proc  root  run  sbin  srv  sys  tmp  usr  var  vmlinuz
root@ubuntu:/# cd var
root@ubuntu:/var# ls
backups  cache  crash  lib  local  lock  log  mail  opt  run  spool  tmp  www
root@ubuntu:/var# cd www
root@ubuntu:/var/www# ls
html
root@ubuntu:/var/www# cd html
root@ubuntu:/var/www/html# ls
index.html
root@ubuntu:/var/www/html# 




---

### Post by darkod on 2015-11-29
Yes, it looks good. I usually use MiB as a unit and make sure I start the first partition at 1 because the disk needs the first partition usually to start at 1MiB for good alignment. But I think parted will do that anyway. You can check the exact layout in Mib with:
```
sudo parted /dev/sdb unit MiB print
```

TB is very large unit to work with.

---

### Post by soamz on 2015-11-29
Okay!
Now I want to add 3 more disks, 2TB each. 
And I have configured those 3 new as one RAID0 again. 

So, again run the parted command or will Ubuntu auto recognize it ?

---

### Post by darkod on 2015-11-30
Again the same. The OS does recognize the new disk automatically but it can not know how you want to use it. That's your job, to partition it and format it as you wish, and configure the mount points. So you will need to do the partitioning and formatting again, and create a new mount point for it. You can't use the same /data mount point. Not if you create two separate arrays in the raid configuration.

To use both arrays as continuous space you would have to use LVM but that might be little complicated for you to set up seeing you are complete beginner with servers.

The same from above applies to windows too, not just linux.

---

### Post by soamz on 2015-11-30
oops.. 
So, again run parted command and everything becomes fresh ?

I hope the Ubuntu stays the same and doesnt get deleted.

---

### Post by darkod on 2015-11-30
Nothing becomes "fresh". You will use parted to partition only the new disk (it will probably be called /dev/sdc). Not /dev/sdb again.

---

### Post by soamz on 2015-11-30
Okay amazing. 
Let me insert and see what it shows. 
Fingers crossed.

Okay I did it.. 

> 

root@ubuntu:~# sudo parted -l
Model: DELL PERC 5/i (scsi)
Disk /dev/sda: 119GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start   End     Size    Type      File system     Flags
 1      1049kB  85.1GB  85.1GB  primary   ext4            boot
 2      85.1GB  119GB   34.4GB  extended
 5      85.1GB  119GB   34.4GB  logical   linux-swap(v1)




Model: DELL PERC 5/i (scsi)
Disk /dev/sdb: 4000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt


Number  Start   End     Size    File system  Name     Flags
 1      1049kB  4000GB  4000GB  ext4         primary




Model: DELL PERC 5/i (scsi)
Disk /dev/sdc: 6000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt


Number  Start  End  Size  File system  Name  Flags




root@ubuntu:~# ^C




Can you help here please,
[http://ubuntuforums.org/showthread.php?t=2304800](http://ubuntuforums.org/showthread.php?t=2304800)

---

### Post by Vegan on 2015-12-03
> **soamz said:**
> I just installed Ubuntu server in one of my server. 
Then opened the terminal and entered sudo fdisk -l

And I got this, 



Its a Dell 2950 server. 
I have 3 disks inserted. 
1 is SSD 120GB.
The other 2 are SSHD 2TB each. 

I created 2 virtual disk in RAID0. 

SSD 120GB = 1 Virtual Disk in RAID0
SSHD 2+2 = 4TB = 1 Virtual Disk in RAID0

Then installed Ubuntu Server in the 1st SSD 120GB thing, when it asked me for disk partition thing. 
I simply selected the SSD and wrote to the disk, when it asked. 

Now, I need the Ubuntu to stay in the SSD only, as it is. 

But I want to fill the 2TB SSHDs with my data, so the Ubuntu server should auto accept and adapt to the 2 disk (1 virtual drive) ? 

Or am I missing something ?

Go buy a larger capacity hard disk if you need more storage. Disks are not expensive anymore. 4TB disks are low cost and larger 6TB and now 8TB disks are available.

---

### Post by soamz on 2015-12-05
There is some problem.

df -h 

shows only SSD. 

But if I run fdisk -l, it should 3 mounts. 
SSD + HDD RAID + HDD RAID. 

Then why am I not able to upload files to server ?

how do I know the location for the 2 RAID0 paths ??
One is 4TB and another one is 6TB. 

See this, 

> jetplex@ubuntu:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1        78G   15G   60G  20% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev             16G  4.0K   16G   1% /dev
tmpfs           3.2G  1.2M  3.2G   1% /run
none            5.0M     0  5.0M   0% /run/lock
none             16G  8.0K   16G   1% /run/shm
none            100M     0  100M   0% /run/user
jetplex@ubuntu:~$ ls
plexmediaserver_0.9.12.19.1537-f38ac80_amd64.deb
jetplex@ubuntu:~$ sudo fdisk -l
[sudo] password for jetplex:


Disk /dev/sda: 119.5 GB, 119453777920 bytes
255 heads, 63 sectors/track, 14522 cylinders, total 233308160 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b39af


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   166209535    83103744   83  Linux
/dev/sda2       166211582   233306111    33547265    5  Extended
/dev/sda5       166211584   233306111    33547264   82  Linux swap / Solaris


WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted                    .




Disk /dev/sdb: 3999.7 GB, 3999688294400 bytes
255 heads, 63 sectors/track, 486267 cylinders, total 7811891200 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1  4294967295  2147483647+  ee  GPT


WARNING: GPT (GUID Partition Table) detected on '/dev/sdc'! The util fdisk doesn't support GPT. Use GNU Parted                    .




Disk /dev/sdc: 5999.5 GB, 5999532441600 bytes
255 heads, 63 sectors/track, 729401 cylinders, total 11717836800 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1  4294967295  2147483647+  ee  GPT




[COLOR=#000000][I]/dev/sda shows mounted and in use. 

But why is it not showing [/I][/COLOR][COLOR=#000000]*/dev/sdb and *[/COLOR][COLOR=#000000][I]/dev/sdc ??
How do I use those drives and how to know how much space is left ?[/I][/COLOR]

Tried to mount it and it shows error. 
Seems Im missing something. 

> 

jetplex@ubuntu:~$ mount /dev/sdb
mount: can't find /dev/sdb in /etc/fstab or /etc/mtab
jetplex@ubuntu:~$ mount /dev/sdc
mount: can't find /dev/sdc in /etc/fstab or /etc/mtab
jetplex@ubuntu:~$


---

### Post by cariboo on 2015-12-05
You need a mount point for your disks eg:

```
sudo mount /dev/sdb1 /mnt
```

You can't just mount the disk, you need to mount one of it's partitions.

---

### Post by soamz on 2015-12-05
> **cariboo said:**
> You need a mount point for your disks eg:

```
sudo mount /dev/sdb1 /mnt
```

You can't just mount the disk, you need to mount one of it's partitions.


I have successfully mounted sdb1.

But sdc1 is not getting mounted and it shows this error. 

Can you please look ?


```
root@ubuntu:/# mount /dev/sdb1 /mnt/disk1
root@ubuntu:/# df -h
Filesystem Size Used Avail Use% Mounted on
/dev/sda1 78G 15G 60G 20% /
none 4.0K 0 4.0K 0% /sys/fs/cgroup
udev 16G 4.0K 16G 1% /dev
tmpfs 3.2G 1.2M 3.2G 1% /run
none 5.0M 0 5.0M 0% /run/lock
none 16G 8.0K 16G 1% /run/shm
none 100M 0 100M 0% /run/user
/dev/sdb1 3.6T 68M 3.4T 1% /mnt/disk1
root@ubuntu:/# cd /
root@ubuntu:/# ls
bin data embymedia home initrd.img.old lib lost+found mnt proc run srv tmp var vmlinuz.old
boot dev etc initrd.img jetplexmedia lib64 media opt root sbin sys usr vmlinuz
root@ubuntu:/# cd mnt
root@ubuntu:/mnt# ls
disk1 external
root@ubuntu:/mnt# mkdir disk2
root@ubuntu:/mnt# cd
root@ubuntu:~# mount /dev/sdc1 /mnt/disk2
mount: special device /dev/sdc1 does not exist
```

---

