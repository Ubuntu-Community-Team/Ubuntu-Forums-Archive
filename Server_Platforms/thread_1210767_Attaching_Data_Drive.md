---
title: "Attaching Data Drive"
date: 2009-07-11
forum: Server Platforms
---

### Post by Duwady on 2009-07-11
Hi Folks,

I had previously installed Ubuntu Server in 80GB drive, and had attached another 300GB drive for data.

Because I was playing too much with the changes, I was having problems with the Server, so I decided to wipe out everything on the 80GB drive, and reinstall Ubuntu Server, as my Data was secure on the 300GB drive.

Now that I have re-installed Ubuntu, I am lost on how to attach (mount) the 300GB drive, and access all my data there.

Could anybody point out where I can read-up on it? Or give me some pointers.

TIA.

---

### Post by druhboruch on 2009-07-11
Just create a folder and mount it:

mkdir /media/disk
sudo mount /dev/sdb1 /media/disk

If you want to mount it permanently just google /etc/fstab

[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)

---

### Post by Duwady on 2009-07-11
> **druhboruch said:**
> Just create a folder and mount it:

mkdir /media/disk
sudo mount /dev/sdb1 /media/disk

If you want to mount it permanently just google /etc/fstab

[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)

I use Webmin to manage my Server, and I was able to mount it, but am unable to get my data. 

TIA

---

### Post by cariboo on 2009-07-12
You may have to adjust the mount point permissions. I would suggest using ssh to go into the server and check the permissions of /media/disk change the permission to 777 just to see if you can access the data at the prompt type:

```
sudo chmod -R 777 /media/disk
```

If you can now access the files on the drive, then you can follow the link that druhboruch provided to setup /etc/fstab.

---

### Post by R.Bucky on 2009-07-12
Permanently mount your drive in /etc/fstab using >

```
/dev/sdb1 /mount-pint ext3 defaults 0 0

```
or if a samba share

```
//external/box /local-mount smbfs username=your-username,password=your-password 0 0
```

---

### Post by Duwady on 2009-07-12
> **cariboo907 said:**
> You may have to adjust the mount point permissions. I would suggest using ssh to go into the server and check the permissions of /media/disk change the permission to 777 just to see if you can access the data at the prompt type:

```
sudo chmod -R 777 /media/disk
```

If you can now access the files on the drive, then you can follow the link that druhboruch provided to setup /etc/fstab.

Nope, chmod 777 also did not bring out my old data.  I can create new "folders" add other data, but can not see nor access my old data.  It seems to be there still, as free space is reduced, but I just can not see it, nor access it.

Did I mount it wrong? Like I mentioned before, I use Webmin for managing the server, and maybe I mounted the disk (or the partition, if that makes a difference) in a wrong way.

Also another information: This data disk was still in and connected when I reinstalled Ubuntu Server on the smaller drive.

TIA

---

### Post by druhboruch on 2009-07-12
Maybe you have more than one partition on your drive.

Try to mount /dev/sdb2 and /dev/sdb3...

What file system was data drive formated with?

---

### Post by Duwady on 2009-07-13
> **druhboruch said:**
> Maybe you have more than one partition on your drive.

Try to mount /dev/sdb2 and /dev/sdb3...

What file system was data drive formated with?

The drive has only one partition, and it was formatted as linux partition, ext3.  

Just curious, Ubuntu now has some other filesystem, LVM or something like that, which I guess is ext4.  Does this make a difference?

TIA

---

### Post by az on 2009-07-13
> **Duwady said:**
> The drive has only one partition, and it was formatted as linux partition, ext3.  

Just curious, Ubuntu now has some other filesystem, LVM or something like that, which I guess is ext4.  Does this make a difference?

TIA

No.  Ubuntu can support many different filesystems at the same time.

And LVM is just a way of making several drives (partitions) into one volume.  You can put any filesystem you want on a volume.  I think Ext4 is the default for the next release of Ubuntu.  The default filesystem right now is still ext3.

---

### Post by Duwady on 2009-07-13
> **az said:**
> No.  Ubuntu can support many different filesystems at the same time.

And LVM is just a way of making several drives (partitions) into one volume.  You can put any filesystem you want on a volume.  I think Ext4 is the default for the next release of Ubuntu.  The default filesystem right now is still ext3.

Which brings me back to my original question, why do I not see my data on the mounted drive, which had only one partition and had been formatted with ext3?  

Another thought, (because I am a newbie in linux)... I am under the impression that I can mount the drive (or partition) under any name, and under any folder (Media or MNT). Please correct me if I am wrong.

Until I can resolve this, or understand what is going on and why, I am scared to put any data in it anymore.

TIA

---

### Post by az on 2009-07-13
> **Duwady said:**
> Which brings me back to my original question, why do I not see my data on the mounted drive, which had only one partition and had been formatted with ext3?  

Another thought, (because I am a newbie in linux)... I am under the impression that I can mount the drive (or partition) under any name, and under any folder (Media or MNT). Please correct me if I am wrong.


You, you can mount it anywhere.

mkdir mountpoint
sudo mount /dev/sdc1 mountpoint
ls mountpoint/
sudo umount mountpoint

Why is the data not there?  I dunno.  Maybe you erased it.  Maybe you never really were saving it there in the first place.  

The reinstall should not have affected the other drive, unless you told it to format the other drive while installing - but it doesn't do that by default.

What's in the filesystem now?  Any directories at all?

What does 
sudo tune2fs -l /dev/sdb1 (or whatever the deive is...)
show?

---

### Post by Duwady on 2009-07-13
> **az said:**
> Why is the data not there?  I dunno.  Maybe you erased it.  Maybe you never really were saving it there in the first place.  

It has not been erased, and it did have a large colelction of music.  It was shared through Samba, and all the other Windows computers were reading the files.

> **az said:**
> What's in the filesystem now?  Any directories at all?I have mounted it as ext3 (as I believe it was originally ext3) and I have tried creating some test directories in it. Come to think about it, I believe it was mounted before as "\", though I do not know if that makes a difference.

> **az said:**
> What does 
sudo tune2fs -l /dev/sdb1 (or whatever the deive is...)
show?

I have not tried this out.  I will try this in the evening as I am at work right now.

Thanks.

---

### Post by az on 2009-07-13
> **Duwady said:**
> It has not been erased, and it did have a large colelction of music.  It was shared through Samba, and all the other Windows computers were reading the files.

Could the directory you were sharing have been on the other drive?


> **Duwady said:**
> I have mounted it as ext3 (as I believe it was originally ext3) and I have tried creating some test directories in it. Come to think about it, I believe it was mounted before as "\", though I do not know if that makes a difference.

You can't mount it as "/".  You have to mount it somewhere relative to / like /media/disk or /otherdrive

---

### Post by Duwady on 2009-07-13
> **az said:**
> Could the directory you were sharing have been on the other drive?

I doubt that the directory was in the other smaller drive.  

Like mentioned earlier, I use WebMin, and it clearly shows that some part of the drive has been used, and has reduced the free space available on the drive.  So it seems the data is still on the drive, however, I am not able to see it or access it.


> **az said:**
> You can't mount it as "/".  You have to mount it somewhere relative to / like /media/disk or /otherdrive

Oops, that clearly shows how much of a newbie I am in Linux. :) What I meant was, when I originally used this drive, I had partitioned it as single partition with "\", and had mounted it later with another name. 

Thanks for your patience.

---

### Post by TwiceOver on 2009-07-13
Just to help eveyone out, you might want to post the output of fdisk -l so we can tell where and what your drives are.

As for the disk being partially used, you lose some to formatting and another 5% to disk administration.  Not sure what this actual number is but I would think around 8gb lost for every 100.

EDIT:  Looking at my 500gb drive after formatting and 1% assigned to disk administration I only have 458gb to work with.  So looks like you lose about 12gb for every 100 assuming you have 5% to disk administration.

---

### Post by Duwady on 2009-07-13
> **TwiceOver said:**
> Just to help eveyone out, you might want to post the output of fdisk -l so we can tell where and what your drives are.

I will post the info later today, as I am at work right now.

TIA

---

### Post by Duwady on 2009-07-13
> **TwiceOver said:**
> Just to help eveyone out, you might want to post the output of fdisk -l so we can tell where and what your drives are.

Here is the output of fdisk -l.  Of course, we are talking about sda1 here.

Disk /dev/sda: 320.0 GB, 320072933376 bytes

255 heads, 63 sectors/track, 38913 cylinders

Units = cylinders of 16065 * 512 = 8225280 bytes

Disk identifier: 0x000d41dd

   

Device Boot      Start         End      Blocks   Id  System

/dev/sda1   *           1       38913   312568641   83  Linux

Disk 

/dev/sdb: 80.0 GB, 80026361856 bytes

255 heads, 63 sectors/track, 9729 cylinders

Units = cylinders of 16065 * 512 = 8225280 bytes

Disk identifier: 0x0fdb0fda

   

Device Boot      Start         End      Blocks   Id  System

/dev/sdb1               1        9355    75144006   83  Linux

/dev/sdb2            9356        9729     3004155    5  Extended

/dev/sdb5            9356        9729     3004123+  82  Linux swap / Solaris

---

### Post by Duwady on 2009-07-13
> **az said:**
> What does 
sudo tune2fs -l /dev/sdb1 (or whatever the deive is...)
show?

This is what I get when I ran tune2fs -1 on sda1.  I did notice that the filesystem created shows the old date when I had actually created it earlier.


tune2fs 1.41.4 (27-Jan-2009)

Filesystem volume name:   Storage

Last mounted on:          <not available>

Filesystem UUID:          57fe0a16-0848-4cdf-8ecf-33e07e14801e

Filesystem magic number:  0xEF53

Filesystem revision #:    1 (dynamic)

Filesystem features:      has_journal ext_attr resize_inode dir_index filetype needs_recovery sparse_super large_file

Filesystem flags:         signed_directory_hash 

Default mount options:    (none)

Filesystem state:         clean

Errors behavior:          Continue

Filesystem OS type:       Linux

Inode count:              19537920

Block count:              78142160

Reserved block count:     3907108

Free blocks:              76867059

Free inodes:              19537902

First block:              0

Block size:               4096

Fragment size:            4096

Reserved GDT blocks:      1005

Blocks per group:         32768

Fragments per group:      32768

Inodes per group:         8192

Inode blocks per group:   512

Filesystem created:       Sun Jan 18 14:59:59 2009

Last mount time:          Sun Jul 12 00:12:48 2009

Last write time:          Sun Jul 12 00:12:48 2009

Mount count:              3

Maximum mount count:      20

Last checked:             Sat Jul 11 23:21:02 2009

Check interval:           15552000 (6 months)

Next check after:         Thu Jan  7 22:21:02 2010

Reserved blocks uid:      0 (user root)

Reserved blocks gid:      0 (group root)

First inode:              11

Inode size:	          256

Required extra isize:     28

Desired extra isize:      28

Journal inode:            8

Default directory hash:   half_md4

Directory Hash Seed:      14a6807f-07de-4aa1-a784-4b8ce2d41a05

Journal backup:           inode blocks

TIA

---

### Post by az on 2009-07-13
So what do you see when you run:

mkdir mnt
sudo mount /dev/sda1 mnt
cd mnt
ls -lah

---

