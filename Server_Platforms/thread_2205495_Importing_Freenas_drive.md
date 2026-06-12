---
title: "Importing Freenas drive?"
date: 2014-02-14
forum: Server Platforms
---

### Post by Craig71 on 2014-02-14
Hi guys, hope someone can help a newbie out here.

I had until recently, a Freenas home server setup, to stream media to a couple of xbmc boxes I'd built.

Freenas was running of a usb, with all the media on a 2tb sata drive. It started playing up, and long story short, i tried to re-install freenas, but I can't seem to get it to import the old drive. 

Anywhoo.... I'd like to try out Ubuntu server 12.04, is there any 'easy' way to import the media on the 2tb drive. I'd be using another HD for ubuntu.

Any input if much appreciated.

---

### Post by TheFu on 2014-02-14
What file system where you using on freenas?  I thought it was UFS or ZFS mainly.

[http://askubuntu.com/questions/85154/mount-ufs-filesystem](http://askubuntu.com/questions/85154/mount-ufs-filesystem) for UFS.
ZFS is just a aptitude install.

---

### Post by Craig71 on 2014-02-14
I'm not sure, I just let it do it's thing when I installed it, could I check this from Ubuntu?

---

### Post by TheFu on 2014-02-14
Perhaps you can recall which version of freenas was used and lookup which file systems they had available?
Or you could just try to mount it with ufs.

---

### Post by TheFu on 2014-02-14
forum double-post error. - please delete.

---

### Post by Craig71 on 2014-02-14
I think it was Freenas 9.1. I'll try mounting anyway when I get home this evening.

---

### Post by tgalati4 on 2014-02-14
If you have* zfs-fuse* on your system then you should be able to plug it in to your Ubuntu system and just read it like any other drive.

```
apt-cache policy zfs-fuse
```

---

### Post by Craig71 on 2014-02-14
Cheers man, I hope so.I'll check this evening. The command above will tell me if it's installed, will it?

---

### Post by tgalati4 on 2014-02-14
It's not installed by default.  On my laptop:

tgalati4@Mint14-Extensa ~ $ apt-cache policy zfs-fuse
zfs-fuse:
**  Installed: (none)**
  Candidate: 0.7.0-8ubuntu1
  Version table:
     0.7.0-8ubuntu1 0
        500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) quantal/universe amd64 Packages

---

### Post by Craig71 on 2014-02-14
Hi again guys. I'm a little out of my depth here, but here goes;

zfs isn't installed, i get the same message as tgalati4 above. I used the command fdisk -l to check Ubuntu could 'see' the drive, and it can I think:

> craig@server:~$ sudo fdisk -l

Disk /dev/sda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders, total 398297088 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000bd7cb


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   390129663   195063808   83  Linux
/dev/sda2       390131710   398295039     4081665    5  Extended
/dev/sda5       390131712   398295039     4081664   82  Linux swap / Solaris


WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn                          't support GPT. Use GNU Parted.




Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
256 heads, 63 sectors/track, 242251 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000


   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1  3907029167  1953514583+  ee  GPT
Partition 1 does not start on physical sector boundary.


 

What should I do next guys?

---

### Post by TheFu on 2014-02-14
Use **sudo parted -l** output, not fdisk.
```
$ sudo parted -l
Model: ATA HGST HMS5C4040AL (scsi)
Disk /dev/sda: 4001GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End     Size    File system  Name  Flags
 1      1049kB  2097kB  1049kB                     bios_grub
 2      2097kB  258MB   256MB   ext2
 3      258MB   4001GB  4001GB                     lvm
```

The output from **boot-info** would be helpful too, but I'd just install zfs or ufs, then try to mount the partition.

---

### Post by Craig71 on 2014-02-15
Cheers dude, I'll have a go at installing them both. 

Just found this little guide for zfs, does this look ok?

> 
[TABLE="width: 100%"]
[TR]
[TD="class: step_content"]**Install ZFS**

These steps MUST BE DONE IN ORDER or the zfs repository cannot be added.
Run the following commands:
sudo apt-get -y install build-essential gawk zlib1g-dev uuid-dev vim-nox python-software-properties
sudo add-apt-repository ppa:zfs-native/stable
sudo apt-get update
sudo apt-get install ubuntu-zfs[/TD]
[TD="class: screenshot, align: right"][/TD]
[/TR]
[TR]
[TH][10]("http://community.spiceworks.com/how_to/show/56763-create-a-ubuntu-server-with-zfs-storage#10").[/TH]
[TD="class: step_content"]**Add zfs modules to be loaded at boot**

Run the command: 
sudo nano /etc/modules
Add the following entries to the file: 
spl 
zavl 
znvpair 
zunicode 
zcommon 
zfs[/TD]
[TD="class: screenshot, align: right"][/TD]
[/TR]
[TR]
[TH][11]("http://community.spiceworks.com/how_to/show/56763-create-a-ubuntu-server-with-zfs-storage#11").[/TH]
[TD="class: step_content"]**Incorporate new modules into the boot files**

Type this command: 
sudo update-initramfs –u[/TD]
[/TR]
[/TABLE]



---

### Post by TheFu on 2014-02-15
ZFS isn't that hard to install anymore. Packages exist in normal ubuntu repos now.  However, we just need to figure out which file system is installed quickly.  THAT is not hard. After that, you can go to all the trouble you want.  I find it highly unlikely that zfs was used on a 1 disk setup in freenas, but I haven't a clue.  I've only used UFS on SunOS and Solaris machines.

Don't make this step harder than it needs to be. It isn't like you have anything to lose.

---

### Post by Craig71 on 2014-02-15
Ah, I see (sort of)

Looking at this, i think it's ufs then? 

> 
craig@server:~$ sudo parted -l
[sudo] password for craig:
Model: ATA Maxtor 6B200M0 (scsi)
Disk /dev/sda: 204GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start   End    Size    Type      File system     Flags
 1      1049kB  200GB  200GB   primary   ext4            boot
 2      200GB   204GB  4180MB  extended
 5      200GB   204GB  4180MB  logical   linux-swap(v1)




Model: ATA ST2000DM001-1CH1 (scsi)
Disk /dev/sdb: 2000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt


Number  Start   End     Size    File system  Name  Flags
 1      65.5kB  2148MB  2147MB
 2      2148MB  2000GB  1998GB  freebsd-ufs


---

### Post by Craig71 on 2014-02-16
Hmmm, lost again. I think I've sussed out that it's ufs, but I cant seem to understand how to get it to mount and provide access to the media on there.

---

### Post by TheFu on 2014-02-16
What have you tried? Just like in Math - show your work.

---

### Post by Craig71 on 2014-02-16
Well, here is the output from sudo parted -l:

> 
craig@server:~$ sudo parted -l
Model: ATA Maxtor 6B200M0 (scsi)
Disk /dev/sda: 204GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start   End    Size    Type      File system     Flags
 1      1049kB  200GB  200GB   primary   ext4            boot
 2      200GB   204GB  4180MB  extended
 5      200GB   204GB  4180MB  logical   linux-swap(v1)




Model: ATA ST2000DM001-1CH1 (scsi)
Disk /dev/sdb: 2000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt


Number  Start   End     Size    File system  Name  Flags
 1      65.5kB  2148MB  2147MB
 2      2148MB  2000GB  1998GB  freebsd-ufs




If I'm understanding this right, I need to mount /dev/sdb partition 2?

How would one go about that? I've tried googling, but I'm just getting more confused!

*edit*

Ok, I've created a directory, > sudo mkdir /data 
Enabled access to all users: > *sudo chmod -R 777 /data*

But when I try to actually mount it, this happens: > craig@server:~$ sudo mount /dev/sdb /data
mount: you must specify the filesystem type




---

### Post by tgalati4 on 2014-02-16
I don't believe parted can recognize zfs, so it's possible that /dev/sdb2 is either ufs or zfs.

Make a directory:

```
cd
mkdir usf_drive
sudo mount -r -t ufs  /dev/sdb2 usf_drive
```

---

### Post by Craig71 on 2014-02-16
Thanks dude, but this is the message i get when trying that:

> 
craig@server:~$ mkdir usf_drive
craig@server:~$ sudo mount -r -t ufs  /dev/sdb2 usf_drive
mount: wrong fs type, bad option, bad superblock on /dev/sdb2,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


craig@server:~$




---

### Post by TheFu on 2014-02-16
> **Craig71 said:**
> Thanks dude, but this is the message i get when trying that:
Well, there is your answer - 
It isn't ufs.

Time to move onto ZFS.

---

### Post by Craig71 on 2014-02-16
Man, i get more & more confused! I thought it showed as ufs?

Anywhoo, if it is zfs, is there an easy way of installing it, and allowing all local users full read & write access?

---

### Post by TheFu on 2014-02-16
> **Craig71 said:**
> Man, i get more & more confused! I thought it showed as ufs?

Anywhoo, if it is zfs, is there an easy way of installing it, and allowing all local users full read & write access?

UFS and ZFS are not primary file systems on Linux, so support for the built-in tools is not always perfect.

"Easy" is subjective.  I thought someone already provided instructions for ZFS in this thread.

---

### Post by tgalati4 on 2014-02-16
Install *zfs-fuse* and play with it.

```
sudo apt-get install zfs-fuse
```

[http://manpages.ubuntu.com/manpages/precise/man8/zfs-fuse.8.html](http://manpages.ubuntu.com/manpages/precise/man8/zfs-fuse.8.html)

[http://askubuntu.com/tags/zfs/hot](http://askubuntu.com/tags/zfs/hot)

---

### Post by steeldriver on 2014-02-16
I don't think the mount error necessarily means it's not ufs - you can try checking the filesystem using the file command

```
sudo file -sL /dev/sdb2
```

If it is ufs, then you may need to enable ufs kernel support by loading the module explicitly before you mount it

```
sudo modprobe ufs
```

---

### Post by Craig71 on 2014-02-19
Thanks for the input guys.

After some consideration, I found a Windows utility that could read the ufs files, copied them over to my main pc, and I've formatted the drive, and I'm currently in the process if trying to set up samba shares. Which is probably a new help post...

Thanks again guys.

---

### Post by brokenhachi on 2014-02-20
oops, nevermind

---

