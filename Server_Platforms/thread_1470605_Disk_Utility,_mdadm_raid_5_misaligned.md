---
title: "Disk Utility, mdadm raid 5 misaligned"
date: 2010-05-03
forum: Server Platforms
---

### Post by JigglyWiggly_ on 2010-05-03
Ok so 3x1.5tb hds in RAID 5.

Not hawt after upgrading to 10.4, I went to disk utility and noticed this, well it could have happened before and never noticed but anyway.

It says under the raid array, WARNING: The partition is misaligned by 48128 bytes. This may result in very poor performance. Repartitioning is suggested.

So does that mean I have to delete the RAID array, and do it again? That is the worst solution I have ever heard ever.
And how do I know this won't happen again?

Thanks in advance.

---

### Post by windependence on 2010-05-03
You need to create a partition table on your disks before you create the  array in order to avoid the misalignment error! Disk utility unfortunately does not tell you this.
If you are building a raid array in Disk Utility, make sure to create  partition tables on your disks before creating the array!

I would suggest taking an image of your data and then rebuilding the array. I know that's not what you want to hear but that is the solution.

-Tim

---

### Post by Cracauer on 2010-05-03
Measuring the performance and see whether you actually have a problem is the first step.

I don't know why you got this. Maybe that newfissled diskmanager thingo did something whacky? I have many md arrays on fdisk created partitions and none had this problem.

---

### Post by JigglyWiggly_ on 2010-05-03
> **windependence said:**
> You need to create a partition table on your disks before you create the  array in order to avoid the misalignment error! Disk utility unfortunately does not tell you this.
If you are building a raid array in Disk Utility, make sure to create  partition tables on your disks before creating the array!

I would suggest taking an image of your data and then rebuilding the array. I know that's not what you want to hear but that is the solution.

-Tim

Is this fine? I created msdos partition tables on all the 1.5tb hds, and then with the new 2.73tb hard drive I created a gpt partition table, since I can't create a msdos partition table on a partition >2tb.

---

### Post by JigglyWiggly_ on 2010-05-03
Ok I did that, and the exact same thing happened again?

---

### Post by windependence on 2010-05-03
> **JigglyWiggly_ said:**
> Is this fine? I created msdos partition tables on all the 1.5tb hds, and then with the new 2.73tb hard drive I created a gpt partition table, since I can't create a msdos partition table on a partition >2tb.
I haven't used the disk utility myself, but I would think you would have to create RAID partitions first and then create your file systems on top of that. You should probably do that using the partition manager in the Ubuntu installer. You must create the RAID partitions frst and then create the array. After that you typically set up the file system. I am sure creating DOS partitions won't work.

-Tim

---

### Post by Cracauer on 2010-05-03
The type of partitions doesn't matter and won't cause this.

Again, using fdisk for many arrays I have never seen this. I suspect that some fancier partition manager is doing something stupid here.

I will be out of this thread until benchmark numbers are posted. Need to make sure there is an actual problem here.

---

### Post by windependence on 2010-05-03
> **Cracauer said:**
> The type of partitions doesn't matter and won't cause this.

Again, using fdisk for many arrays I have never seen this. I suspect that some fancier partition manager is doing something stupid here.

I will be out of this thread until benchmark numbers are posted. Need to make sure there is an actual problem here.
This is exactly what I found when researching his problem. One other person had the problem using a non-standard partition manager, hence my suggestion to use the Ubuntu partition manager to partition all the disks.

-Tim

---

### Post by JigglyWiggly_ on 2010-05-03
Fawk
Same thing, I tried the GPD partition table on those drives, (didn't look back here)


My main server, I did the same thing and it doesn't have this problem...?


Anyway, I doubt this effects performance at all.

Here is what I'm code
```

apt-get gparted 

```
Go to gparted, new partition table, GPD
format > ext4
(do this to all 3 hds)

Then
```

sudo mdadm --create --verbose /dev/md0 --level=5 --raid-devices=3 /dev/sda1 /dev/sdb1 /dev/sdc1

```
After that complets after like 5 hours, I go to gparted, and set a GPD partition table.
Then I format it with ext4
Then I go to disk manager, and see it...
GRRR

---

### Post by JigglyWiggly_ on 2010-05-03
Oh wait wut
You can create a RAID array through disk utility? Doing that now...
PS why is the default stripe size 512? That's huge, I did 128.

---

### Post by windependence on 2010-05-03
Yes, but you  don't create an EXT partition first, you have to mark them as RAID and then create the array. After the array is created THEN you format with your favorite file system.

-Tim

---

### Post by JigglyWiggly_ on 2010-05-04
fffffff
I followed the disk manager and it said it is misaligned by 11,3664 bytes!

Ok, I don't even know how to mark the drives as RAID through the disk manager.

ghey
I might just lvie with it, this is wasting so much time.


EDIT: Disk manager already marks the drives as RAID for me!
Argh, doing Windows raid 5 through fakeraid would have been more reliable :?
Well, actually I can't do that, I don't have fakeraid on this ich7 sb motherboard, well I could do Windows software raid?
Ok that is probably a lot worse, I've used it once.

BTW in disk manager, I made all the drives have the GUID type, so like I don't know what else to do. I did it before like semi-through cmi, that has the same error, but a smaller disalignment?

I mean gah... you would think they would test this!
I would go to Debian 5, except like, that is EXT3.

---

### Post by JigglyWiggly_ on 2010-05-05
okay the more I keep doing this the more it is getting disaligned, 244,736 bytes now.

---

### Post by mc_fly on 2010-08-02
Hi @all

I´ve got the same problem. I´am not sure. But can it possible, that the problem is the used hdd. I´ve used the Western Digital Caviar Green drives with the 4 k problem. Can this be the solution? What hdds did you use??

---

### Post by arrrghhh on 2010-08-02
It sounds like both of you are doing something very wrong, with some odd piece of software that is setting up the array, instead of just doing it mdadm.

Both of you, please follow one of these guides.  I placed them in order of ease, the first being the easiest.

[Ubuntu Forums Software RAID How-To](http://ubuntuforums.org/showthread.php?t=408461)
[Linux Home Networking "Quick" How-To](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch26_:_Linux_Software_RAID)
[TLDP.org's Software-RAID How-To](http://tldp.org/HOWTO/Software-RAID-HOWTO-5.html)

---

