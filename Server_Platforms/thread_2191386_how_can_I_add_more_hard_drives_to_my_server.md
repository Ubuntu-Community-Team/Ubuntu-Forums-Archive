---
title: "how can I add more hard drives to my server?"
date: 2013-12-02
forum: Server Platforms
---

### Post by kustomjs on 2013-12-02
Guys
I am just wondering if anybody can tell me how I can add more hard drives to my ubuntu server 12.04.2 lts and I have owncloud on it with 160 gig hard drive?

this was the guide I was pointed to [http://doc.owncloud.org/server/5.0/admin_manual/configuration/custom_mount_config_gui.html](http://doc.owncloud.org/server/5.0/admin_manual/configuration/custom_mount_config_gui.html) by owncloud forums and I just wanted to know how to mount hard drives to just add more storage?

---

### Post by CharlesA on 2013-12-02
Couldn't you just add the drives to the server, format them with your file system of choice (I like EXT4), create a place the mount them and then have them automount on boot via an entry in fstab?

Your question is a bit vague on what you need help with other than adding more hard drives to owncloud.

Basically:

Install drive in server
Format drive with mkfs (I use mkfs -t ext4)
Create mountpoint with mkdir
Add entry to fstab via UUID. Use blkid to get the UUID of the drives.
```
sudo blkid -c /dev/null
```

---

### Post by kustomjs on 2013-12-02
well I dont want to copy the settings from 160gig hard drive to new hard drive I am just looking to add more space.

---

### Post by CharlesA on 2013-12-02
> **kustomjs said:**
> well I dont want to copy the settings from 160gig hard drive to new hard drive I am just looking to add more space.

If you add the drive to the server and mount it, then point owncloud to it, it looks like it'll just add that space to the pool. At least that's what it looks like according to the link in the OP.

---

### Post by nerdtron on 2013-12-03
That would depend on owncloud itself. Adding a drive and mounting is easy as long as you have a spare space and connection in the server.
Would owncloud allow you add another seperate "drive/folder" for your storage? If so, then you would be good. If not, just copy the 160GB drive. With today's hard drives that wouldn't' take long.
If you are worried about downtime. Use rsync for initial copying, then the next updated copy when you stop owncloud the copy would be very fast.

---

### Post by kustomjs on 2013-12-04
Again I dont want to copy 160gb hard drive to new one I am just looking to add more space.

---

### Post by CharlesA on 2013-12-04
Have you tried doing what the link suggests in your OP?

---

### Post by kustomjs on 2013-12-12
alright I added 2 more disk but I dont know how really just mount them for more space. Here is the picture: [IMG]http://i43.tinypic.com/2rr5pvs.jpg[/IMG]

---

### Post by CharlesA on 2013-12-12
You'd need to format the drives and then create a mountpoint for them (just make a folder somewhere on the file system) and mount the drives with the mount command.

---

### Post by bab1 on 2013-12-12
> **kustomjs said:**
> Guys
I am just wondering if anybody can tell me how I can add more hard drives to my ubuntu server 12.04.2 lts and I have owncloud on it with 160 gig hard drive?

this was the guide I was pointed to [http://doc.owncloud.org/server/5.0/admin_manual/configuration/custom_mount_config_gui.html](http://doc.owncloud.org/server/5.0/admin_manual/configuration/custom_mount_config_gui.html) by owncloud forums and I just wanted to know how to mount hard drives to just add more storage?...> Again I dont want to copy 160gb hard drive to new one I am just looking to add more space. 

Owncloud manages multiple remote sites that hold your data such as: 
[LIST]
[*]FTP (or FTPS)
[*]SFTP
[*]SMB
[*]WebDAV
[*]Amazon S3
[*]Dropbox
[*]Google Drive
[*]OpenStack Swift (dropbox or googledrive
[/LIST]
None of these require more local HDD space.

The link you mentioned is very specific about this* "...to mount **external storage providers into ownCloud’s virtual file system**"*.  If Owncloud is running on your computer right now you can add these remote sites as it is.

Do you also want to add **local** strorage capacity to your *ubuntu server 12.04.2 lts* machine?  If so do you want this capacity in some specific file system area, like /home or /data?  The 2 hard drives you have added can be combined into one partition and added to the OS operating system where ever you want.

To summarize;  you have 3 questions - 1. How do I add remotely administered file storage sites (locally managed by Owncloud) - 1. How do I add local partitions to my local file systems - 3. Should I combine the additional storage (sdb and sdc) and if so how do I do that?

Tell us what you want, then we can give you more specific help.

---

### Post by kustomjs on 2013-12-12
Again Bab1 didnt you read what I posted before 160gig is where I got the owncloud/os server stuff and I am just adding 3 more hard drives to the system to add more storage. I do not want to add any external sites to my owncloud period for more storage that is why I 3 more hdd to add more storage. Basically its going to come down to is that I want to add more storage for Owncloud for my customers.

---

### Post by CharlesA on 2013-12-12
Read this:
[http://www.ranjith.info/p/owncloud.html](http://www.ranjith.info/p/owncloud.html)

I just tested it with ownCloud 5 and it worked as expected.

---

### Post by kustomjs on 2013-12-12
charles that is what I am after so how do I format and mount the drives to the server then how do I add it to owncloud?

---

### Post by CharlesA on 2013-12-12
If you want to keep expanding the storage avalible to owncloud, you would be better off looking for a way to pool the disks together. LVM can do this.

Otherwise you will have to create mount points for each new drive and partition and format them, then add the path to owncloud.

See here, about half way down the page, to see what you need to do to partition and format the drives:
[http://zackreed.me/articles/38-software-raid-5-in-debian-with-mdadm](http://zackreed.me/articles/38-software-raid-5-in-debian-with-mdadm)

```
sudo parted -a optimal /dev/sdb
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

```
sudo mkfs -t ext4 /dev/sdb
```

---

### Post by kustomjs on 2013-12-12
what happens if there was already drive under ide formated as sdb because sata drive is also under sdb I dont want to screw it up.

---

### Post by CharlesA on 2013-12-12
It doesn't matter if the drive is sata or ide, they all show up as sdXY in the newer versions of Ubuntu.

Judging from your fdisk, sdb does not have any partitions on it, and neither does sdc.

---

### Post by kustomjs on 2013-12-12
so do the formatting like you said on about 3 hours ago by this:


```

Code:

sudo parted -a optimal /dev/sdb
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

Code:

sudo mkfs -t ext4 /dev/sdb


```

then should I make an directory for these drives for owncloud?

---

### Post by CharlesA on 2013-12-13
Yes. Create the directory and mount the drive there then follow the instructions here:
[http://www.ranjith.info/p/owncloud.html](http://www.ranjith.info/p/owncloud.html)

---

