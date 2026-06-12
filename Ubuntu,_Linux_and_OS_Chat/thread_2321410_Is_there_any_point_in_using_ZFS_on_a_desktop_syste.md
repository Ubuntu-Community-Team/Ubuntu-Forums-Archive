---
title: "Is there any point in using ZFS on a desktop system?"
date: 2016-04-22
forum: Ubuntu, Linux and OS Chat
---

### Post by orange2k on 2016-04-22
I was very happy when it was announced that 16.04 would have ZFS built-in, but I am wondering if it is of any use on a desktop system...:confused:

---

### Post by QDR06VV9 on 2016-04-22
Here is a how to by Dustin Kirkland. And a basic review.
[https://insights.ubuntu.com/2016/02/16/zfs-is-the-fs-for-containers-in-ubuntu-16-04/](https://insights.ubuntu.com/2016/02/16/zfs-is-the-fs-for-containers-in-ubuntu-16-04/)

> Dustin Kirkland is part of Canonical's Ubuntu Product and Strategy team, working for Mark Shuttleworth.
Other than that I have yet to try the ZFS yet.
Maybe others here will chime in.
Kind regards

---

### Post by dino99 on 2016-04-22
ZFS is relatively new on Linux; i've not seen any benchmark nor reported bug with ubuntu. So use it at your own risk. Seems to be recommended to replace a multi devices under raid.

[https://wiki.ubuntu.com/ZFS](https://wiki.ubuntu.com/ZFS)

---

### Post by dino99 on 2016-04-23
Some tests  [http://www.phoronix.com/scan.php?page=article&item=ubuntu-xenial-zfs&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu-xenial-zfs&num=1)

---

### Post by grahammechanical on 2016-04-24
What convinces me that ZFS is not suited to a desktop system is the same thing that convinces me that BTFS is not suited to a desktop system and that is the lack of any GUI management utility. Everything has to be done through the command line. As far as I am concerned both file systems are more suitable for server systems and similar set ups.

I have used BTFS on my home PC. And when we install apt-snapshot we get a recovery mode option so that we can roll back a snapshot of the system from recovery mode. But as I run the development version which I update almost daily then I got such a large number of snapshots that house cleaning became a chore. 

Regards.

---

### Post by mastablasta on 2016-04-25
then again, Opensuse has BTRFS it as default: [https://news.opensuse.org/2014/11/12/what-to-expect-from-btrfs-on-opensuse-13-2/](https://news.opensuse.org/2014/11/12/what-to-expect-from-btrfs-on-opensuse-13-2/)

so they might develop more GUI tools.

Opensuse look like is using Snapper and Yast.
[https://www.suse.com/documentation/sles-12/stor_admin/data/sec_filesystems_major.html](https://www.suse.com/documentation/sles-12/stor_admin/data/sec_filesystems_major.html)

if almost no one is using it on desktop, no one is developing the GUIs. 

btrfs (like ZFS) seem to be more aimed at data rather than soem faster changing system files. so that you can easilly pull older version or something. although it does seem like they are trying to use it on system part with various solutions. i mean wouldn't it be great when the OS crashes completelly you would calmly revert to older shapshot and continue from there (jus like in virtualbox, where you can make a mess and then recover original image in seconds...).

---

### Post by UbuntuAddict99 on 2016-04-26
Hello orange2k,

I think the REAL question is not if it is any good for a desktop. But rather do i need to use it for a desktop at the moment! ZFS is a huge thing on BSD but really ETX3 and ETX4 are pretty good. Now i would like to point out i have only read about ZFS two days ago and i have never personally used it. But one thing i do know is that it is BSD "territory" so to speak.

I think it would be better to wait UNTIL ZFS is supported better before anyone starts experimenting, unless you want to. that is my personal opinion,
but me personally i have learned to NEVER, EVER. Use a product when it is completely fresh. Even though in this case it is a file system type for a operating system.
my point is this.

Just research the heck out of it, and research tests for it that have been done for Linux and then give it the old pros and cons for if you need to use ZFS over ETX for a desktop.

Happy Linuxing.

P.S. I personally will only be using ETX4 for a long time before i switch to ZFS.

"Linux Ubuntu the final frontier!"
                                             -UbuntuAddict99

---

### Post by kurt18947 on 2016-04-26
One downside I've read about re ZFS is that it uses quite a bit of RAM relative to other file systems. I suspect that for desktop systems it's probably overkill. I have used BTRFS on temporary installs and had no problem with it. I did not try snapshots or other 'advanced' operations. I'll continue to use ext4 is  for daily use machines though.

I suspect that including ZFS has more to do with Canonical's efforts in cloud and large scale server installations. In that space ZFS seems to be preferred.

---

### Post by coldraven on 2016-04-26
This article is a bit technical but it seems that there are huge savings in the time it takes to sync big folders. 
Obviously this is not your standard desktop scenario but it is interesting to know about. 

[http://arstechnica.co.uk/information-technology/2015/12/rsync-net-zfs-replication-to-the-cloud-is-finally-here-and-its-fast/](http://arstechnica.co.uk/information-technology/2015/12/rsync-net-zfs-replication-to-the-cloud-is-finally-here-and-its-fast/)

---

### Post by ChuangTzu on 2016-04-26
If the OS is for desktop I suggest staying with ext. 3 or 4 for the time being.  openSUSE as mentioned above does use BTRFS by default with many subvolumes for /root, and many people on their forums as well as Mageia have reported problems with it.  BTRFS has a tendency to fill the root volume with snapshots causing the system to freeze and/or loop.  Suggestion usually given is to turn of the snapshot feature, but then you lose the benefit of BTRFS to begin with.

---

### Post by kurt18947 on 2016-04-27
> **coldraven said:**
> This article is a bit technical but it seems that there are huge savings in the time it takes to sync big folders. 
Obviously this is not your standard desktop scenario but it is interesting to know about. 

[http://arstechnica.co.uk/information-technology/2015/12/rsync-net-zfs-replication-to-the-cloud-is-finally-here-and-its-fast/](http://arstechnica.co.uk/information-technology/2015/12/rsync-net-zfs-replication-to-the-cloud-is-finally-here-and-its-fast/)

That article seems to confirm that for individuals & small businesses with small data needs ZFS is massive overkill.

---

### Post by lukeiamyourfather on 2016-05-11
ZFS can be used on a desktop. It uses more memory than other file systems but you get better performance in exchange for the higher memory usage (search for information about the ARC). For the most part the features are beneficial to large storage arrays and data management in a production environment.

---

### Post by ZoiaGuyver on 2016-05-11
ZFS has very little going for it on a desktop machine imo.  EXT3/4 and XFS are great for desktop use.

ZFS excels at scalability that is needed in servers and has probably some of the best if not the best fault tolerance around. A desktop has little use for such things. ZFS for Ubuntu is more aimed at the IoT and Cloud stuff as that is where ZFS will show its real strengths.

---

