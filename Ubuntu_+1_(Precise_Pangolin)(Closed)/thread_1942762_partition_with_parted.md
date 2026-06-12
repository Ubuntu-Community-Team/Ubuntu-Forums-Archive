---
title: "partition with parted"
date: 2012-03-18
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by learnbash on 2012-03-18
Hello folks,

I have 2.4TB san storage i want to make 4 partition each having 600GB. I use fdisk but not possible to do this because of fdisk limitation. So i tried parted but it make 2.4TB one partition but with parted not possible to make 4 partition having 600GB, may be i m doing wrong, can some one advise me on that how to make 4 partition with parted.

---

### Post by dino99 on 2012-03-18
i've never had issue to partition my hdds, but i also never use parted, preferring booting on a livecd (liveusb) with gparted or partedmagic.
i wonder why you want to format like this instead of following the install needs.

[http://manpages.ubuntu.com/manpages/precise/man8/parted.8.html](http://manpages.ubuntu.com/manpages/precise/man8/parted.8.html)

but it should be helpfull if you describe your config : which hdd(s) specs, how is built that nas, custom fab specs ?

---

### Post by grahammechanical on 2012-03-18
Have you read through this?

[https://help.ubuntu.com/community/HowtoPartition]("https://help.ubuntu.com/community/HowtoPartition")

You do not tell us how you are trying to do this. So, we do not know if you are doing anything wrong.

At this point I can only remind you that to create a partition we first create unallocated space by shrinking the size of the existing partition. Then we create a partition in that unallocated space.

You may already know this. You may have tried this. I do not know.

If I was I wanted to do this I would try to

1) Shrink 2.4TB partition to 600GB.

2) Create a 2nd partiton in the unallocated space.

3) Shrink the 2nd partition to 600GB.

4) Create a 3rd partition in the unallocated space.

5) Shrink the 3rd partition to 600GB.

6) Create a 4th partition in the remaining unallocated space.

Do not forget that these partitions will be primary partitions and 4 is the maximum number of primary partitions. If you should ever want more than 4 partitions you should create at least one of these partitions as an extended partition and then create a 600GB logical partition inside the extended partition.

If you do that you can later (if required) shrink the primary partitions, increase the extended partition and create more logical partitions inside the extended partition. In this way we get around the 4 primary partition limit.

I have explained this just in case others who are viewing this thread do not know this. It is how we all learn.

Regards.

---

### Post by learnbash on 2012-03-18
i am getting message that msdos label do no support devices that have more than 4294967295 sectors.

---

### Post by Gregory Lee on 2012-03-18
I just partitioned a 2TB disk, with 2930277168 sectors, into 4 partitions plus swap, using an msdos partition table.  A rough calculation suggests that a 2.5TB disk should have fewer than 4000000000 sectors, so I don't understand that error message.  However, maybe you'll have to delete the msdos partition table and replace it with a different type of table.  I have never done this, myself.

---

### Post by learnbash on 2012-03-18
Currently i am using gpt partition table, but i need 600GB four partition which i create with parted but not visible with fdisk so how i can format it?

---

### Post by oldfred on 2012-03-18
If drive is over 2.2TB or 2TiB then you cannot use the old standard MBR partitioning but need to use gpt. Gdisk is in the repository or you can download the newest version from the rodsbooks site.

GPT fdisk Tutorial -srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)

I have used gparted to create gpt drives but all  the ones I have done were smaller drives. Gparted is just a graphical front end to parted.

---

### Post by Gregory Lee on 2012-03-18
I used Gparted also.

---

### Post by learnbash on 2012-03-18
So it means if i make partition with parted above then 2.2TB so it will show one partition with fdisk and if i need to see four partition i will use gdisk, please confirm?

---

### Post by ronacc on 2012-03-18
why do you want to format it with fdisk ? gparted will format it to whatever format you wish (except apple formats).

---

### Post by oldfred on 2012-03-18
Yes, fdisk only sees the protective MBR which gpt has for those old tools that do not know about gpt. It creates one gpt partition in the old MBR, and many older tools like fdisk were updated just to give the warning on gpt partitions which it cannot work with. 

To see your partitions:

sudo parted /dev/sda unit s print
gdisk -l /dev/sda

---

### Post by learnbash on 2012-03-18
@[[COLOR=#d40000]**oldfred**[/COLOR]]("http://ubuntuforums.org/member.php?u=852711") friend thanks thanks so much. You made my day.

---

### Post by jerrylamos on 2012-03-19
> **learnbash said:**
> Hello folks,

I have 2.4TB san storage i want to make 4 partition each having 600GB. I use fdisk but not possible to do this because of fdisk limitation. So i tried parted but it make 2.4TB one partition but with parted not possible to make 4 partition having 600GB, may be i m doing wrong, can some one advise me on that how to make 4 partition with parted.

In this testing forum, I use 10 GB partitions for Alpha, Beta, Updates, etc. etc.  I think your 600 GB partition will be almost empty.

Now I do run maybe 4 partitions for testing, a swap partition, and a larger common library Archive partition for storing anything I want to save from the test partitions.  All this fits well within 100 GB.  

What do you plan to do with the rest of the 2.4 TB?  I don't think you need it for precise pangolin Beta testing?

The biggest hard drives I have are 250 GB.  Half of the space has Windoze...7 so my wife can run some specific commercial programs for web support.

Jerry

---

### Post by dino99 on 2012-03-19
> **jerrylamos said:**
> 
What do you plan to do with the rest of the 2.4 TB?  I don't think you need it for precise pangolin Beta testing?


Jerry

but i know what you need Jerry : read the first post, where he talk about a nas storage; i suppose you know what that means ?

---

