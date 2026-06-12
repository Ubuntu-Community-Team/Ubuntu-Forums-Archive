---
title: "Ubuntu 16.04 LTS ZFS, RAID and some architecture inquiries"
date: 2016-04-21
forum: Server Platforms
---

### Post by karlo on 2016-04-21
Hello,

It's been awhile since I have posted in this forum. I am completely nostalgic about this. I've been a member in the Ubuntu Forums since the year 2008. It feels great to be back here!

Moving forward, I was just wondering if you guys can help me out utilizing the new technology that is natively supported when Ubuntu 16.04 was released. It is the ZFS file system. That term is familiar for me because I was trying to study more about FreeBSD a month ago.

Apparently, LeaseWeb (VPS) does not entirely support it and does not want to get the latest stable and release versions. I don't know if it is just them but it seems that other hosts are beginning to offer installers or templates for the 64-bit architecture alone. For me, if a server has less than 4 GB of RAM then a 32-bit version of the server should be used so that the memory won't be entirely wasted. Although, feel free to correct me if I'm wrong.

Going back, I asked LeaseWeb that Ubuntu 16.04 was released and hopefully they'll have an install image for it. I also told them that it would be great if they can completely utilize the ZFS feature for their installer template. The reply that I received is that they recommend me to use FreeBSD since currently, ZFS is supported there. I informed them that even though ZFS has been around for a long time, the moment that it is included in an Ubuntu LTS release, it is considered stable. I shared them the articles [ZFS]("https://wiki.ubuntu.com/ZFS") and [ZFS Reference]("https://wiki.ubuntu.com/Kernel/Reference/ZFS"). After a few minutes, they replied that my inquiry is going to be forwarded to the programming department. And I have no idea why that department in the first place.

As for my other server which is hosted under online.net, I haven't asked them about Ubuntu 16.04. Although, I'll be asking them about it after this post and it is the same with OVH.

Now, as for Hetzner, I informed them about the new version of Ubuntu LTS and ZFS. They told me that they can easily create an installimage script for it. Although, it will only be available in the 64-bit architecture. It will have LVM and non-LVM versions. I asked them how about ZFS. They said ZFS isn't stable for now. I told them everything that I explained to LeaseWeb. They haven't replied up until now. It is pretty simple. They have a script that they prompt the user to modify and decide. For example, for non-LVM partition, the user can just uncomment a few lines and same thing for the LVM-partition as well as activating and deactivating SWRAID. I was sincerely asking them to make a script that would activate ZFS and additional commands that would activate ZFS' RAID feature. It seems that RAID is integrated to it so why not utilize it? If ever you guys are interested to check their so called installimage script, feel free to visit [this]("https://wiki.hetzner.de/index.php/Installimage/en") and [this one]("https://wiki.hetzner.de/index.php/Eigene_Images_installieren/en").

I sure do hope that you guys can help me out with the installation of Ubuntu 16.04 with ZFS (and ZFS RAID) configuration. By the way, I usually use CentOS 6 and CentOS 7 for my servers. Apparently, I think it is time to shift to Ubuntu 16.04 LTS. It is simply because when I was experimenting with nginx and HHVM from scratch (reading online articles about them), the PPAs are addictive. Although it is just sad that adding modsecurity to nginx means I'd have to compile it from scratch. I was also able to try out EasyEngine although it seems that their version of nginx is old since nginx wanted to use spdy instead of http2. Plus, PHP 5.6 automatically gets installed. I just find it weird since I wanted to focus on HHVM and PHP 7 (fallback) with redis cache (that doesn't actually work plus I have no idea what's the purpose of it), PHP 5.6 still gets installed. HHVM is also set to fallback to PHP 5.6 instead of PHP 7. Just weird.

By the way, I am looking forward to use the new feature called "Snap" or "Snaps" too and definitely interested to be part of the mentoring program.

Thanks so much, everyone.

---

### Post by mastablasta on 2016-04-22
why do you need ZFS?

Would BTRFS fill in your needs?

a 2 year old comparison: [http://marc.merlins.org/linux/talks/Btrfs-LinuxCon2014/Btrfs.pdf](http://marc.merlins.org/linux/talks/Btrfs-LinuxCon2014/Btrfs.pdf)

and to add BTRFS improved a lot since then...

4 GB RAM is considered low for ZFS. 8 Gb is min, recommended is 16 Gb. depends how much data you have, how much movement on server...

---

### Post by karlo on 2016-04-25
> **mastablasta said:**
> why do you need ZFS?

Would BTRFS fill in your needs?

a 2 year old comparison: [http://marc.merlins.org/linux/talks/Btrfs-LinuxCon2014/Btrfs.pdf](http://marc.merlins.org/linux/talks/Btrfs-LinuxCon2014/Btrfs.pdf)

and to add BTRFS improved a lot since then...

4 GB RAM is considered low for ZFS. 8 Gb is min, recommended is 16 Gb. depends how much data you have, how much movement on server...

Thanks for replying. I find BTRFS interesting. Although, it seems that ZFS is integrated in the latest version of Ubuntu 16.04 (LTS) because it's mature and stable enough. I have two dedicated servers. The first one has 4 GB of RAM and the second one has 12 GB of RAM. And I also have 2 VPS, the first one has 1 GB of RAM and the other one has 2 GB of RAM.

I did a research regarding BTFS and it seems that even though there are companies who used it for actual production servers, it is still unstable and will not be able to recover data most of the time.

[https://www.diva-portal.org/smash/get/diva2:822493/FULLTEXT01.pdf](https://www.diva-portal.org/smash/get/diva2:822493/FULLTEXT01.pdf)
[https://btrfs.wiki.kernel.org/index.php/Production_Users](https://btrfs.wiki.kernel.org/index.php/Production_Users)
[https://www.reddit.com/r/linux/comments/32cu9w/zfs_vs_btrfs/](https://www.reddit.com/r/linux/comments/32cu9w/zfs_vs_btrfs/)

---

