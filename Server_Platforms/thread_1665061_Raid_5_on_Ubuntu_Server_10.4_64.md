---
title: "Raid 5 on Ubuntu Server 10.4 64"
date: 2011-01-11
forum: Server Platforms
---

### Post by 1serveyou on 2011-01-11
I'm using a Intel mac pro running Ubuntu Server 10.4 64bit, and I have it working. Currently, I'm just using Ubuntu using bootcamp, and not using EFI. The OS drive is 250gb which I know is more than enough, but it was what I had free at the time. I added 3 1tb drives to the computer, but not sure how to create a raid with them. I've done some searching, but still haven't been able to get it done successfully. Any help would greatly be appreciated.

---

### Post by sj1410 on 2011-01-12
a super simple recipe 

```

$ cd /
$ sudo -i
# mdadm --create --verbose /dev/md0 --level=5 --raid-devices=3 /dev/sda1 /dev/sdb1 /dev/sdc1
# mke2fs /dev/md0
# mv /home /home2
# mkdir /home
# echo "/dev/md0        /home           ext2    defaults        0       0" >> /etc/fstab
# mount -a
# mv /home2/* /home
# rmdir /home2
# exit
$ cd

```


hope this helps.

Good Luck !!!!!!!

---

### Post by sj1410 on 2011-01-12
you can also find a details explanation here


[http://blog.swapnil.me/2011/01/simple-recipe-to-create-raid5-under.html](http://blog.swapnil.me/2011/01/simple-recipe-to-create-raid5-under.html)

---

### Post by 1serveyou on 2011-01-12
Thank you very much. I actually was able to setup the Raid in webmin. It was saying one of the drives was bad, but this morning it is saying all are ok. When I was trying to mount the raid last night it was saying the folder I wanted to mount was busy, then this morning it was saying that it was an unknown file type. I looked at the fstab and there was nothing in there for /md0. I created "/dev/md0 /Data  auto defaults   0       3" in the fstab, and checked webmin (Disk and Network Filesystems) which finally showed the mount, but said unknown file type, is this correct? Thank you in advance. The drive is formatted in ext4.

---

