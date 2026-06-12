---
title: "Installing Ubuntu Server w/ multiple Hard drives"
date: 2011-07-11
forum: Server Platforms
---

### Post by zafiros bonitos on 2011-07-11
I wasn't sure where the best place to post this was, so here I am. I'm a complete linux noob, I've been using ubuntu on my laptop for a few days now (think I finally got the hang of it.) I've built a computer that I will be using as a media server with a 40GB hd to install ubuntu server, a 2TB hd for my videos, and a 320GB hd for my music. I was wondering how I can set it up so my video folder is on the 2TB hd and my music folder is on my 320GB hd, either during or after installation.
 
I already installed it once but the part about setting up partitions was kind of confusing. I'm not against reinstalling the OS since I haven't set anything else up yet. Thanks for any help.

---

### Post by CharlesA on 2011-07-11
You can do it after install by editing fstab.

See [here]("https://help.ubuntu.com/community/Fstab").

---

### Post by zafiros bonitos on 2011-07-11
Thanks, it all looks pretty confusing, but I'll try to figure it out once I have some time. I'm still really confused about the whole concept of partitioning and mounting drives and what not.

---

### Post by CharlesA on 2011-07-11
> **zafiros bonitos said:**
> Thanks, it all looks pretty confusing, but I'll try to figure it out once I have some time. I'm still really confused about the whole concept of partitioning and mounting drives and what not.

Basically, you mount a drive to an empty folder and then put files you want to move to that drive in that folder.

take a look [here]("https://help.ubuntu.com/community/Mount").

---

### Post by karlson on 2011-07-11
> **zafiros bonitos said:**
> Thanks, it all looks pretty confusing, but I'll try to figure it out once I have some time. I'm still really confused about the whole concept of partitioning and mounting drives and what not.

In a nutshell you can think of the partitions as drives, the only difference between the physical drives and partitions is that the partitions reside on the same physical device.

Now as far as mounting think of it is getting access to the data on the drive, similar to just accessing the drive as C:\, which basically means the same thing as mounting a drive(partition) as C:\.

The UNIX/Linux filesystems provide you with much greater flexibility than Windows by allowing you to provide a separate space in a directory where it is needed.

So once you get past the initial set up of the Operating System you can add additional space on different devices to provide space.

So in order to do this you will need to determine the name of the devices that have your 2TB and 320GB devices e.g. /dev/hdb or /dev/sdb.  Then you will need to create a filesystem on it and add the devices to the /etc/fstab to gain access.  If you don't want to subdivide the space on those drives you can create filesystem on /dev/sdb or /dev/hdb directly.  You can use the /etc/fstab wiki to explain what you will need to add to it to mount.

---

### Post by zafiros bonitos on 2011-07-11
I appreciate all the help. I have a hypothetical question just to help me understand better: If I choose to manually set up partitions during install, and I choose /home/[whatever]/Videos as the mount point for the 2TB drive, is that right? And would I need swap space on my 320GB drive if I already have it on the 40GB? (I assume not.) I had another question, but I forgot it. I think I might invest in Linux for Dummies :)

---

### Post by CharlesA on 2011-07-11
> **zafiros bonitos said:**
> I appreciate all the help. I have a hypothetical question just to help me understand better: If I choose to manually set up partitions during install, and I choose /home/[whatever]/Videos as the mount point for the 2TB drive, is that right? And would I need swap space on my 320GB drive if I already have it on the 40GB? (I assume not.) I had another question, but I forgot it. I think I might invest in Linux for Dummies :)
Yep. You'd have to set the mountpoint to something like:

```
/home/user/Videos
```

Or something like that.

You wouldn't need swap space on any drive except the OS drive. :)

---

### Post by Fury24 on 2012-05-16
Thank you so much for posting this. Im in the middle of reinstalling my Linux server (long story don't ask) and had this same question.

---

