---
title: "Space issue on on root drive with 1.2 GB free"
date: 2014-04-10
forum: Server Platforms
---

### Post by Coder68 on 2014-04-10
I am trying to run apt-get upgrade and get an error saying the drive is full. df -h shows 1.2 GB free. The upgrade is just under 70 mb.
I have followed every how to on this site and others to try and get this to clean space/fix this issue. None of them have worked.
The purge tries to install the kernel, which gives me the same error... no free space, so no install.

I have run autoclean, clean, etc. I have emptied the trash. I am not sure what else to do!

**Last few sites/steps I tried**
[http://ubuntuforums.org/showthread.php?t=2078057&page=2](http://ubuntuforums.org/showthread.php?t=2078057&page=2)
[http://askubuntu.com/questions/26336...n-boot-is-full]("http://askubuntu.com/questions/263363/how-can-i-remove-old-kernels-install-new-ones-when-boot-is-full")
[http://ubuntuforums.org/showthread.php?t=2078057](http://ubuntuforums.org/showthread.php?t=2078057)
[http://askubuntu.com/questions/17120...old-kernels-to]("http://askubuntu.com/questions/171209/my-boot-partition-hit-100-and-now-i-cant-upgrade-cant-remove-old-kernels-to")
[http://www.joomlaworks.net/blog/item...ntu-server-vms]("http://www.joomlaworks.net/blog/item/168-resizing-the-disk-space-on-ubuntu-server-vms") (I get no sectors available when I try to add a partition)

This is a production server, and I do not want to have to rebuild it as it is complex... it takes a very long time to build.

Please see attachments for output of commands, and the error I am getting.

Thank you, [ATTACH=CONFIG]251902[/ATTACH][ATTACH=CONFIG]251903[/ATTACH][ATTACH]251904[/ATTACH]

---

### Post by thnewguy on 2014-04-10
This error is almost always a result of running out of inodes.  Run the df command with the -i flag to see how many inodes you have available on each partition. (df -i)

To fix the problem you will need to remove files you no longer need. Typically locations such as /var and /tmp fill up with small files that gobble up inodes and cause the out of space error.

---

### Post by SeijiSensei on 2014-04-10
The other possibility is the default 5% of the filesystem that is reserved for root by default.  See the discussion of the "-m" switch for "reserved-blocks-percentage" in "man mke2fs".  I'm not sure you can change that once the filesystem has been created, though.  On modern hard drives, the 5% figure is generally much larger than it need be.  On a 20 GB hard drive, reserving 1 GB for root made sense.  On a 200 GB drive, it would be overkill to reserve 10 GB for root, much less 100 GB on a 2 TB drive.

---

### Post by Vegan on 2014-04-10
in this age, monster capacity disks are very low in cost

there are adapters for antique EIDE systems

I suggest getting a couple of 2 TB disks, unless you have UEFI when disk size does not matter

---

### Post by LHammonds on 2014-04-10
If you ever do create a new "production" server, I strongly suggest not choosing the default to put everything on the root partition.  Use LVM and separate your partitions so that you don't have to worry about an out-of-control user folder growing out of control which fills up your root partition as well if it is all 1 partition.

To see how I setup my servers, take a look here: [How I setup an Ubuntu Server]("http://www.hammondslegacy.com/forum/viewtopic.php?f=40&t=191")

But as thnewguy mentioned, you probably ran out of inodes is my guess.

LHammonds

---

### Post by Coder68 on 2014-04-11
I will give these a try on Monday, (Too many meetings today.), and let you know what I find. 

As for space, the SAN admin limited me... I have another 32 GIG now. :)

Thank you!

---

### Post by Coder68 on 2014-04-11
I will give these a try on Monday, (Too many meetings today.), and let you know what I find. 

Thank you!

---

