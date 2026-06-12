---
title: "Jaunty server file system label: what does it do?"
date: 2009-07-26
forum: Server Platforms
---

### Post by raymondvillain on 2009-07-26
I've absolutely no experience with servers.

Setting up 9.04 server for home use, primarily to store music files.
In the process of partitioning disks and it asks what I want to use

> Label for the file system in this partition

and I don't know what the file system label does.

I have chosen ext4 for the files in this particular partition.  Is the label important?  Where does it appear in the normal every day use of the machine?

---

### Post by redmk2 on 2009-07-26
> **raymondvillain said:**
> ...
In the process of partitioning disks and it asks what I want to use and I don't know what the file system label does.

The label is one more way for you to be able to identify the particular partition.  The only time I have seen it used is in the setup of /etc/fstab.  

Typically you ID the partition with it's device name i.e /dev/sda or sdb.  Better yet you can ID the partition with the UUID.  But you can also ID the partition with its label if you gave it one. 

On one of my hosts I have 3 partitions.  They are / (labeled "root") and /home (labeled "home") and /smb (labeled "samba").  You can see the labels using ```
sudo blkid
```  The results are ```
>sudo blkid
/dev/sda1: UUID="c2ff646e-4884-4c77-ab85-e8e958f1422b" TYPE="ext2" LABEL="root" 
/dev/sda2: TYPE="swap" UUID="f21ea669-94b0-4df5-bc93-b948fa986177" 
/dev/sda3: LABEL="home" UUID="223b331e-418a-4bb1-b86e-b0c2b28abc03" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda4: UUID="d49556bd-a3d7-4c5a-a87d-4679db6817f3" SEC_TYPE="ext2" TYPE="ext3" LABEL="samba" 

```  I see that I also labeled the swap partition.  No reason to do that :D> 

I have chosen ext4 for the files in this particular partition.  Is the label important?  Where does it appear in the normal every day use of the machine?

No real reason to label them.  most of the time I don't.  I use the UUID.

---

### Post by LepeKaname on 2009-07-27
label is just like the name of the partition (like Disk1 or anything else). In most of the cases you will not need it. And if needed, for identification (as stated by redmk2) you can change it anytime.

---

