---
title: "Can't Use Unallocated Free Space of My HD"
date: 2011-01-31
forum: Ubuntu Studio
---

### Post by Wejdan on 2011-01-31
While Installing Ubuntu-Studio, Manual Partitioning, I had about 160-170 Gb Free Space, Used it as the following:
1) 10 Gb; Swap
2) 100 Gb; Ex4 file system "for system installation"
when I got 59 Gm left "that I intended to use as a separate partition  for my documents to have them availably seen in both, Ubuntu-Studio and  Windows Vista", I received: "Unusable"

so I left it as is and continued installation hoping that I'll format it, fix it later using "disk utility"
 But After I got the system installed, tried the "disk utility", i received: > Unallocated Space (/dev/sda)..

While trying to format it, I got: > One or more partitions are busy on /dev/sda
 

I tried to use Windows Disk Manager, but it told me that the volume is not recognized by the system..
 

I would've ignored it if it was 10 Gb, but It's 59 Gb & I  formatted my pc about 3 times in the last two days so I wanna find some other  less harmful solution
 



would any1 help,, please ..
Thanks in Advance :)

---

### Post by ronnielsen1 on 2011-01-31
Boot from a live cd and post the output of:

sudo fdisk -l

---

### Post by Wejdan on 2011-01-31
I can't boot from Live CD, it's ubuntu studio, I don't have the option "Try Ubuntu"

unless you mean something else..

---

### Post by ronnielsen1 on 2011-01-31
Is Studio booting up OK? If so, open a terminal and type in sudo fdisk -l

---

### Post by Wejdan on 2011-01-31
Done..
got the following:
```
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x76ee09ee

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1275    10240000   1c  Hidden W95 FAT32 (LBA)
/dev/sda2   *        1275        9810    68554687+   7  HPFS/NTFS
/dev/sda3           29186       30402     9765888   82  Linux swap / Solaris
/dev/sda4            9810       22016    98046976   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xcd4684e3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19457   156288321    c  W95 FAT32 (LBA)

```

---

### Post by chaosdx on 2011-01-31
Seeing as there are 4 of the partitions so far, and it doesn't let you create more, I can guess what the error is: all of the partitions created so far are primary, is this so?

The really old legacy thing is, there cannot be more than 4 (primary) partitions on a HDD; and if you want more, you should create one of them as "extended" partition, which would be a container for as many "logical" partitions as you like in the available space.

In the current situation, the easiest thing would be to create a bootable USB stick (or take a Live-CD), boot from it, delete the last partition you have, re-create it as an "extended" partition for the whole rest of your HDD space, and immediately split it into two (or more) logical partitions. One of them you can re-use for / Linux, obviously.

---

### Post by ronnielsen1 on 2011-01-31
You are going to have to use some kind of live cd to fix this. You can't change a partition that you're using. Download a gparted or ubuntu live cd and start gparted. Then you should be able to delete sda4 and then either pull sda2 to the right to make more room for windows or pull sda 3 to the left (which will take more time because it has to copy everything) to make more room for ubuntu, or make a new extended partition (You're only allowed 3 logical partitions) Don't forget to remake a swap file.

[http://ubuntuforums.org/showthread.php?t=1047528](http://ubuntuforums.org/showthread.php?t=1047528)

It should look similar to below. I'm not sure why it's listing your swap as sda4 even though it comes before sda3. That's why I'm suggesting deleting it and making a new one. You shouldn't lose any data as long as you don't delete anything other than swap (but there's always that chance) 
[IMG]http://farm4.static.flickr.com/3522/3217836439_72e9b14ce5.jpg[/IMG]

---

### Post by chaosdx on 2011-01-31
Sorry for hijacking your answer thread, **ronnielsen1**, but seeing the first post stating the space was "Unusable" from the beginning led me to think the issue was with not creating extended partition to begin with. The fdisk report provided by OP reinforced this opinion :)

---

### Post by ronnielsen1 on 2011-01-31
> Sorry for hijacking your answer thread, **ronnielsen1**, but seeing  the first post stating the space was "Unusable" from the beginning led  me to think the issue was with not creating extended partition to begin  with. The fdisk report provided by OP reinforced this opinion
That's why I suggested pulling over gparted to incorporate the partition into an existing one OR to make an extended partition. Sorry if I didn't make it clearer

---

### Post by Wejdan on 2011-01-31
well, what i'm supposed to do is the following:
1) get a live USB (done, using Ubuntu Desktop Remix which is not what im using)  << is this ok, i mean that im running Ubuntu-Studio and intending to use live USB for Ubuntu Desktop?
2) Choose "Try Ubuntu"
3) start "Gparted"
4) Delete both, "Unallocated + Swap"
5) Make 2 logical partitions out of the resulted free space, use 1 of them as swap & the other as whatever I wanna use it for?

Am I getting it right?

---

### Post by Wejdan on 2011-01-31
what if Gparted doesn't start?
any other program could do that?

---

### Post by chaosdx on 2011-01-31
> **Wejdan said:**
> well, what i'm supposed to do is the following:
1) get a live USB (done, using Ubuntu Desktop Remix which is not what im using)  << is this ok, i mean that im running Ubuntu-Studio and intending to use live USB for Ubuntu Desktop?
2) Choose "Try Ubuntu"
3) start "Gparted"
4) Delete both, "Unallocated + Swap"
5) Make 2 logical partitions out of the resulted free space, use 1 of them as swap & the other as whatever I wanna use it for?

Am I getting it right?

Yes, that sounds about right.

1) It's not important that you run a slightly different distro. You just need it to access the hdd.

And if Gparted doesn't start.. well, it usually signifies of worse problems than this :) Try it first, as it's the simplest way.

---

### Post by Wejdan on 2011-02-01
Gparted still wouldn't start
it crashes before it starts !!

I've tried two images so far, to make sure the issue is not the "iso" file


any other solution ??

---

### Post by Wejdan on 2011-02-01
Ok.. Gparted finally started
but, i couldn't make a "logical" partition, it wasn't highlighted
i can only do extended and primary :S

---

### Post by Wejdan on 2011-02-01
I used the unallocated, add it to "vista", hoping that I can use windows disk manager to shrink vista again, use the result unallocated as a separate partition... Again!! I couldn't :confused:

but anyways, @ least it's usable now :D

thanks a lot  :KS 

"but yet, if there's a way to amke a "logical" separate partition, that would be great"

---

### Post by Pablo_F on 2011-02-01
You can make as many logical partitions as you want provided you make an extended partition instead of a primary one beforehand.

---

### Post by Wejdan on 2011-02-01
> **Pablo_F said:**
> You can make as many logical partitions as you want provided you make an extended partition instead of a primary one beforehand.

Well, the current situation is:
4 primary partitions:  vista + Ubuntu-Studio + Swap + "healthy primary"

Can I change one of them, so that I can make more logic partitions?

thx.. :)

---

### Post by chaosdx on 2011-02-01
> **Wejdan said:**
> Well, the current situation is:
4 primary partitions:  vista + Ubuntu-Studio + Swap + "healthy primary"

Can I change one of them, so that I can make more logic partitions?

thx.. :)


As I've said before: an extended partition, if you create one, will be a container for logical partitions, so you have to do something like this:

```
[COLOR="DeepSkyBlue"][PRIMARY1] [PRIMARY2] [PRIMARY3][/COLOR] [COLOR="Red"][[/COLOR][COLOR="DeepSkyBlue"][LOGICAL1][LOGICAL2][/COLOR][COLOR="Red"]]<--EXTENDED[/COLOR]
```

As soon as you create an extended partition, creating a logical partition inside it will be available to you.

You can't really "change" a partition's type, so you'll have to delete-recreate it as the other type...

---

### Post by Wejdan on 2011-02-01
Worked! :D:D:D:D:D

Thank you so much :KS

---

