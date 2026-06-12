---
title: "Create RAID5 array on Ubuntu"
date: 2007-07-25
forum: Server Platforms
---

### Post by cazz on 2007-07-25
Hi
A friend of my want to use Ubuntu on a computer.
He have 4 disk that have 320GB and like to use RAID5

What I can understand that is I can use mdadm to create RAID on Ubuntu.
I have never create RAID before so I start to read some information about it
I have read now about two days and find some very good tips and that but I dont know what is the easy way to create RAID5

I have read 
[http://www.tldp.org/HOWTO/Software-RAID-HOWTO.html](http://www.tldp.org/HOWTO/Software-RAID-HOWTO.html)
[https://wiki.ubuntu.com/Raid](https://wiki.ubuntu.com/Raid)
[http://www.linuxdevcenter.com/pub/a/linux/2002/12/05/RAID.html](http://www.linuxdevcenter.com/pub/a/linux/2002/12/05/RAID.html)
[http://ubuntuforums.org/showthread.php?t=408461](http://ubuntuforums.org/showthread.php?t=408461)
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

I think I understand some of it but I'm not sure

For exemple I know that I have to manual create partitions but how much?
I have always use gparted and that is very easy to create but I have never done that in terminal
 
Can someone help me and tell me how to make a RAID5 from a new computer with 4x320GB disk so I can help him create and use it on his Ubuntu computer.

---

### Post by jtc on 2007-07-25
1) Make sure you have the mdadm packet installed.

2) Create partions of the type "Linux raid auto" (fd). Note that all of the partions should be of the same size.

3) Run mdadm like this. Substitute with the correct devices: 
```
mdadm --create /dev/md0 --level=5 --raid-devices=4 /dev/sdW1 /dev/sdX1 /dev/sdY1 /dev/sdZ
```

4) Wait for the raid-device to sync. Watch the progress in /proc/mdstat
```
cat /proc/mdstat
```

5) When completed, reboot. If everything has gone well, you ought to have a /dev/md0

EDIT: Of course, this is just an example and might not at all be the setup your friend wants. Feel free to take a look at the man page. It is full of good information.
```
man mdadm
```

---

### Post by cazz on 2007-07-27
Hi 
Thanks for you reply

I have a litte problem with the partions and I need help :)
I run now Ubuntu 7.04 alternate and I have right now boot up and I'm at that point that I going to create partions for my four 320 GB harddrive.

What I understand I need to do that manual but I have now idea how much and what kind of partions more then a swap, boot and root.

I can't find any guide how can help me but I have found RAID and create MD but I dont know what or how much I need to create partions

What I understand that I have 4 GB memory so I have to create 4 GB swap??

Can someone please tell me so I can go on with my install of thís computer

---

### Post by jtc on 2007-07-27
Well, regarding partions. If it's a desktop-system I usually like to have three or four different partions; swap, /boot, root and /home. The optional part is the /boot.

About swap-size I guess the traditional rule of thumb is that, as you yourself suggest, of the same size as the RAM. On the other hand you most likely won't need 4GB, but on yet another hand it won't hurt. Myself I'd go somewhere between 1GB and 4GB. I doesn't really matter much in your case.

/boot really hardly uses any space at all. Give it a 100MB or perhaps 200MB if you really want to be on the safe side.

The root (/) will be your primary system. Give it somewhere between 10GB and 20GB. It most likely won't need that much space, but since you have quite a lot of diskspace it never hurts to play it safe.

/home is where you place the rest of your diskspace. This is where all the data on a desktop-system usually get saved. One big benefit of having /home on a separate partion is that you can reinstall your System and still keep your home directories.


Should be noted that this setup is about desktop-system. On a server it usually is a bit different and then especially so about /var where a lot of data, such as websites, mailboxes and logs, might end up.

---

### Post by cazz on 2007-07-27
Thanks for you quick reply

ok I going to have four diffrent partions (swap, boot, root and home)
Swap = 4 GB
boot = 200 MB
root = 20 GB
home ~295 GB

But I have no idea how to set that up

I like to have the system on RAID so if one of the hardrive go down Ubuntu can continue running.
I have read that if I want to run RAID I need to have partions that is in same size so if I do this

DISK 1
Swap = 4 GB
boot = 200 MB
root = 20 GB
home ~295 GB (RAID5 or what??)

DISK 2
????????
????????
????????
home ~295 GB (RAID5 or what??)

DISK 3
????????
????????
????????
home ~295 GB (RAID5 or what??)

DISK 4
????????
????????
????????
home ~295 GB (RAID5 or what??)


After I have create/convert a partions to RAID I go up and create a RAID system (MD) and choose RAID5
then that is time to continue installation of Ubuntu.

But what kind of partions are I going to create in DISK 2, DISK 3 and DISK 4?
Do I have to leave them to be nothing?

---

### Post by h3lmut on 2007-07-27
You would need to have an identical set of partitions on all four drives, and create a RAID device for every set of partitions. This is, in my opinion, kind of a needlessly over-complex and silly setup. I'd encourage you to either add a 5th, unRAIDed harddisk to the system to hold your partition set up, or use LVM instead of partitions. With either of these options, you'd only create a single partition, spanning the whole disk, for the harddisks in your RAID. With LVM, you would then use the LVM manager to create logical volumes for /boot,swap,etc. (instead of partitions).

If you want to do it with static partitions, remember that the partitions on each disk only need to be 1/(number of harddisks in RAID - 1) * total size you want. As in, if you want 4GB of swap on a 4 drive RAID5, you would create a ~1.33GB partition on each of the four drives (1.33*3 being approximately 4GB, remember you lose one disk's capacity in a RAID5 because of the redundant encoding).

Also, if one of your disks in a RAID5 fails, yes, the system will continue to function and won't lose any data. It will also be **AMAZINGLY** slow until you replace the failed disk and rebuild the array.

---

### Post by jtc on 2007-07-27
I'm not sure if I've understood your questions in their whole, and it seems like I've for that reasons only answered them in part. Sorry about that.

Actually, nowdays (kernel 2.6) you can create a partitionable raid-device, on which you then can create your different partitions, just like on a normal harddrive. If that is the way Ubuntus alternative installer does it I have no idea. To be honest I haven't really used it at all so I won't be able to help you with the practical details.

Another solution, which I kind of prefer myself, is, like h3lmut mentions, to have a separate non-raided harddrive to use as a systemdisk for your root-partion etc. That way your system can always boot without having to rely on the RAID.

---

### Post by cazz on 2007-07-27
Hmm ok
But if he use a non-raided harddrive to the system and that harddrive stop working my Ubuntu stop too.
Have never use LVM but if that is better I going to try it.

I know that if one of the harddrive fails that computer going to be very slow but I dont loose any information and what I understand easy repair with a new harddrive

The idea is that I can use RAID5 to have a secure ubuntu that my friend going to use like a fileserver (He want to have graphic so he can easy manage Ubuntu) so all config and that have a backup and that why I going to use RAID5 and also a backupscript to a extern USB harddrive.


After I have read a little more about boot in RAID
[http://www.tldp.org/HOWTO/Software-RAID-HOWTO-7.html#ss7.3](http://www.tldp.org/HOWTO/Software-RAID-HOWTO-7.html#ss7.3)

I understand I maybe have to change the kernel to make it work


I have to ask him if that is ok to add another harddrive that is non-raided and have the Ubuntu there and all his work and file in the Raid partions (md0).
Maybe have a image of that Ubuntu so if that go down he can easy repair Ubuntu.

---

### Post by StonedSidney on 2008-02-13
Hi all,
Not sure if this thread is still active, but thought I'd make a comment.

Having the OS on a sep drive is also useful if you need to rebuild due to something major like a main board replacement. You will have to reinstall (unless you can find the same exact m/b in say 3 years time) and you are likely to want a newer version of the OS for supportability.

For me, my data is irreplacable and I want to keep if _forever_ (pron? - no, it's music & video), whereas I can easily reinstall the OS. With sep drives I can (even) unplug the data drives for absolute surety. And by keeping the original install image, I can always go backwards in need, but hopefully keep up to date.

Note you can always boot a live CD periodically and backup your OS to the RAID array (thats more to protect me from *me* though).

mdadm rocks.

---

