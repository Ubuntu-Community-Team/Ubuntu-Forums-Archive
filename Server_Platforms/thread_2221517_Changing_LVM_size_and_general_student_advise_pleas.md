---
title: "Changing LVM size and general student advise please."
date: 2014-05-02
forum: Server Platforms
---

### Post by Double.J on 2014-05-02
Hi all!

So this is my first question in a while! I've been using linux for many years now, however, like most I guess my learning curve has been a bit like this:
```
 _____
/
``` i.e. I know how to do the things I do, and not much else. My goal this year has been to learn a lot more and it's been going really well. 

Most of this has been creating a number of CLI only VM's and learning to do things. My latest is an ubuntu server. I've only really used ubuntu server for file serving - backups / media and the such around the home. I'm going to use it for a number of learning topics, but none will have a lot of data as it's just for learning. I made 4x virtual disks and partitioned them as:
```

md0 - RAID0 - 991MB - Third logical partition - swap
md1 - RAID1 - 248MB - First partition, primary, EXT4 - /boot
md2 - RAID1 - 4.5GB - First logical partition, LVM group ubuntu main - devided into logical partitions for /, /tmp, /var, /usr, /home, /var/mail.
md3 - RAID5 - 10.7GB- Second logical partition, LVM group data - /data 
```

Now I've been using it for basic guide following and experiments for the last couple of weeks, and my usage looks like:
```
$ df -h | tee ~/docs/usage
Filesystem                          Size  Used Avail Use% Mounted on
/dev/mapper/ubuntu--lvm--main-root  922M  300M  558M  35% /
none                                4.0K     0  4.0K   0% /sys/fs/cgroup
udev                                152M  4.0K  152M   1% /dev
tmpfs                                33M  520K   33M   2% /run
none                                5.0M     0  5.0M   0% /run/lock
none                                165M  4.0K  165M   1% /run/shm
none                                100M     0  100M   0% /run/user
/dev/mapper/ubuntu--lvm--main-var   453M  283M  143M  67% /var
/dev/mapper/ubuntu--lvm--main-tmp    86M  1.6M   78M   2% /tmp
/dev/md1                            226M   41M  169M  20% /boot
/dev/mapper/ubuntu--lvm--main-home  1.4G   18M  1.3G   2% /home
/dev/mapper/ubuntu--lvm--data-data  9.8G   23M  9.2G   1% /media/data
/dev/mapper/ubuntu--lvm--main-usr   922M  566M  292M  66% /usr
/dev/mapper/ubuntu--lvm--main-mail  364M  2.1M  339M   1% /var/mail
``` As you can see I'm at 2/3 usage on /usr and /var. I've looked up quite a number of different guides on resizing LVMs. I was wondering what would be the preferred method to resize these logical partitions without a system shutdown (such as would be used in an enterprise situation)?

Additionally if any more experienced people have any recommendations that'd be awesome - I'm just hear to learn.

Jj

---

### Post by nerdtron on 2014-05-03
You can grow LVM partitions on the fly if the files system you used on those partitions is XFS. You can also increase LVM partitions on ext4 by unmounting and remounting them again.

---

### Post by LHammonds on 2014-05-05
In my how-to thread, I cover partition management including LVM design, increasing LV's and their filesystems and backing up using file-copy methods as well as backing up at the partition level...all automated and while the server is online.

You can have a look here: [How to Install and Configure an Ubuntu Server 12.04 LTS](http://www.hammondslegacy.com/forum/viewtopic.php?f=40&t=191)

I'm also updating that same thread for [14.04](http://www.hammondslegacy.com/forum/viewtopic.php?f=40&t=200) but it is not finished yet but not much changes in regards to these particular steps.

LHammonds

---

