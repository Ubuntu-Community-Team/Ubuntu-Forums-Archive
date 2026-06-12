---
title: "Basic questions about building a home NAS with RAID 1"
date: 2010-12-13
forum: Server Platforms
---

### Post by HimeNoHogosha on 2010-12-13
My plan is to build a small Atom based NAS which will run 2x1TB drives in RAID 1 config. The purpose is to store media which can be accessed by both Mac and Windows computers on my home network.

I've got the following hardware wired up and waiting for software:
2x1TB Seagate drives
Atom 330 mini-itx board 
2GB RAM

Now I've kind of hit a roadblock that I hadn't considered during my preplanning.. where do I install the OS?

It sounds like most people in this situation have a 3rd smaller hard drive to install the OS on. However I don't really have room for this physically in my mini-itx case. My motherboard does have "fakeRAID" I guess, but I was planning on running Ubuntu Server then using that for software RAID 1 (I just want to prevent losing data in the case of a disk failure) which I am assuming will give me more options instead of the fakeRAID. 

I've found a lot of instructions about how to load Ubuntu Server onto a bootable USDB drive, and I've read that the full install of Ubuntu Server is only ~1GB (currently I only have a 2GB usb flash drive), but I haven't found any instructions on actually running Ubuntu Server off of a flash drive. Is this not possible?

I probably have more questions about how to set up the samba shares for windows access and the raid 1 mirroring, but I need to get the actual OS going first :P

---

### Post by elico on 2010-12-13
well if you need it only for nas then you should consider other os that will fil you needs.
ubuntu is a great OS but there is a nice solution that will might fit your needs much more like
FREENAS at
[http://freenas.org/](http://freenas.org/)
the current version is [0.7.2.5543]("https://sourceforge.net/projects/freenas/files/stable/0.7.2/")  and it's the most simple to use OS for your needs iv ever found.
freenas takes less then 100MB and can boot from cd\dvd\usb ..

---

### Post by stek_87 on 2010-12-13
I don't agree.. Ubuntu is perfect for a simple home NAS. Use mdadm software raid and set up 3 raid-1 volumes. One for swap, one for the root filesystem and a large one for your data and mount it in /mnt/data (for example).

If you had 3 disks, you would set up 1 raid-1 volume 200MB for /boot, one raid-5 for swap, another raid-5 for / and a last big raid-5 for your data

Maybe later on you will have some other needs and you will be glad that you installed Ubuntu and not freenas..

But this is just my opinion.

---

### Post by elico on 2010-12-13
it's perfect for simple use home NAS but if the only thing he needs is nas then FREENAS is like the best and nice for small\simple user.
the SOFTWARE RAID is not os dependent so he can always switch os to ubuntu in case he wont like freenas.

ubuntu takes about 1-2 GB fully optional as LAMP NAS and other services.
so it's his call.
im using ubuntu server 10.04 as my home server nas\gw\lamp and much more and im happy.

---

### Post by bigsigh on 2010-12-13
Have you read this?
[https://help.ubuntu.com/10.04/serverguide/C/advanced-installation.html](https://help.ubuntu.com/10.04/serverguide/C/advanced-installation.html)

It's what I used with a pair of 500GB drives, though, as you could see from my other thread on this forum, it apparently didn't go as I intended.

---

### Post by fistv on 2010-12-13
Usually your drives are limited by your case. Which one did you pick ? Personally I usually use a sans digital two drive case with built in raid choice set by a slider switch in the case itself, then use the USB connector to the PC or server case. So far the 4 I have here have been good, each one of those have 2 1tb seagates in them. You might also consider using a laptop drive, 5400rpm, small and can be tucked almost anywere, you just need a laptop to ide adapter if it's a pata drive.

---

### Post by HimeNoHogosha on 2010-12-13
The reason I wanted to go with Ubuntu over freenas was because of the study done by smallnetbuilder, where they found that ubuntu server had a significant performance increase over freenas. I also figured that ubuntu would leave the door open for running some other things in the future.

I know I could buy a larger case that would fit a 3rd hard drive, but that would cost more and I wanted this to be small to not take up too much space anyway. I am also using seagate 1TB 7200.12 drives since I got a pair of those on a good cyber weekend deal :P

I think my question(s) is/are still unanswered? Is it possible to install ubuntu on one of the disks that I plan on setting up for RAID 1? Or must ubuntu be installed on a separate disk? And if so, is it possible to install ubuntu server on a usb drive?

Thanks guys!

---

### Post by HermanAB on 2010-12-13
Howdy,

Partition the disk.  You only need 3 partitions: /, /swap and /nas (or whatever you want to call it).

---

### Post by HimeNoHogosha on 2010-12-13
I'm guessing / is the partition with the OS, /nas is the partition for the data, but what is the /swap partition for? 

If I do this, does this mean I will be mirroring exactly the same 3 partitions on the other RAID1 disk? I remember reading somewhere that it may not be a good idea to install the OS on the same disk that will be part of the RAID array?

---

### Post by elico on 2010-12-14
ok then ubuntu it is!!
you can always build the raid array after installing the os.
i would suggest you to first install the os itself on only one drive and after you finished the system basic setup over let say 10GB max of one HD + swap of 2-5 GB build your software raid you want and mount it using the fstab. 
and there you go a fully functional server with raid 1 or 0 what ever you choose.

---

### Post by HimeNoHogosha on 2010-12-14
Alrighty, I'll give this a shot and report back later :) Thanks!

---

### Post by SaturnusDJ on 2010-12-16
Consider using LVM also. This makes adding more space (future) to an array/partition etc etc way easier.

---

### Post by rubylaser on 2010-12-16
Just my preference, but I never add LVM on top of mdadm anymore.  It's one more layer to have to troubleshoot if you have problems.  mdadm can very simply grow an array with 2 commands...
Add a disk
```
sudo mdadm --add /dev/md0 /dev/sdd1
```
Grow the array
```
sudo mdadm --grow /dev/md0 --raid-devices=4
```

The final thing you have to do is grow the filesystem which is also very easy to do with many Linux filesystems.

---

