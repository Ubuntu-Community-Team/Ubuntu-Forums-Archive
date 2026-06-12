---
title: "RAID-5 with multiple sized Hard Drives."
date: 2008-02-20
forum: Server Platforms
---

### Post by misconfiguration on 2008-02-20
All,

I have 2x500gb sATA drives with a RAID controller card also 2x200gb IDE drives.

Anyone ever hear of having RAID-5 with two different types of hard drive topologies?

From my understanding I think I could create 2 200gb partitions on both 500gb hard drives and use the full IDE drives and RAID that up?

Such as
200 x 200 | 200 x 200 | 200 | 200

And throw all of that into one partition, then use the rest of the space for the OS. or would the extra 200gb need to be used for parity?

---

### Post by Holmes89 on 2008-02-20
-

---

### Post by Holmes89 on 2008-02-20
I'm interested in doing this as well but with a lot smaller drives haha. (like 20 gigs)

Yeah I think you need a parity drive but I'm not sure about the idea of having that on the same drive as one of your raid drive because if the  drive fails with the parity on it and one of the raid drives you might lose all of your data, wouldn't you?

---

### Post by astrotech226 on 2008-02-20
There isn't a designated parity drive in a raid5 configuration.  The parity information is striped as well is the data.

If you want to use different size drives, you are correct.  You will need to bust up the 500G drives and use it accordingly.  But there is nothing that says you must use all of towards the raid5, either.  You could do this:

Drive A:
  /dev/sda1 200G
  /dev/sda2 300G
Drive B:
  /dev/sdb1 200G
  /dev/sdb2 300G
Drive C:
  /dev/sdc1 200G
Drive D:
  /dev/sdd1 200G

Set up sda1, sdb1, sdc1 and sdd1 as a raid5 giving you 600G of storage.

Then use sda2 and sdb2 as something else.  Raid1, Raid0, two separate partitions.

I would strongly advise *against* what you are thinking about taking the 500G drive and creating two 200G partitions and using it in the raid5.  It can be done, but raid5 is tolerant of a single drive failure.  When you make two partitions out of one drive, you are essentially creating two "virtual" drives out of one physical drive.  When that drive fails, you've lost two parts of the raid and your data becomes unavailable.

---

### Post by Holmes89 on 2008-02-21
now how do you partition the drives in command line?

---

### Post by faulkes on 2008-02-21
> **Holmes89 said:**
> now how do you partition the drives in command line?

Using the fdisk command.  Due to the nature that fdisk can have serious consequences if you misuse it 
(i.e. pick the wrong drive, etc.) I will not post the exact commands.

Alternatively you can also use the parted command which has the same general purpose as
fdisk.

However, an example use of fdisk would be to list existing partitions and this is very safe to do:

```

sudo fdisk -l

```

Please see the man page which documents the procedure fairly well.

```

man fdisk
man parted

```

Faulkes

---

### Post by misconfiguration on 2008-02-21
> **astrotech226 said:**
> There isn't a designated parity drive in a raid5 configuration.  The parity information is striped as well is the data.

If you want to use different size drives, you are correct.  You will need to bust up the 500G drives and use it accordingly.  But there is nothing that says you must use all of towards the raid5, either.  You could do this:

Drive A:
  /dev/sda1 200G
  /dev/sda2 300G
Drive B:
  /dev/sdb1 200G
  /dev/sdb2 300G
Drive C:
  /dev/sdc1 200G
Drive D:
  /dev/sdd1 200G

Set up sda1, sdb1, sdc1 and sdd1 as a raid5 giving you 600G of storage.

Then use sda2 and sdb2 as something else.  Raid1, Raid0, two separate partitions.

I would strongly advise *against* what you are thinking about taking the 500G drive and creating two 200G partitions and using it in the raid5.  It can be done, but raid5 is tolerant of a single drive failure.  When you make two partitions out of one drive, you are essentially creating two "virtual" drives out of one physical drive.  When that drive fails, you've lost two parts of the raid and your data becomes unavailable.

I suppose I had the initial idea down-pat. I appreciate your very informative response; may I also ask you about the controllers? I have to use a sATA raid controller because the board I'm using doesn't support sATA. 

Do you see problems between IDE and sATA drives being mixed?

---

### Post by astrotech226 on 2008-02-21
I'm a fan of fdisk to partition drives from the command line.  Let's assume you have sdb available to do whatever you want and don't care about the data on it.

```
sudo fdisk /dev/sdb
```

The commands you will most likely use will be:

p: Print the current partition table (this could still be unwritten to disc)
n: Create a new partition
d: Delete a partition
t: Change the partition type
w: Write the partition table

Much of this depends on what you are trying to accomplish, but here's a general outline of what you would do.

1) Run fdisk on the drive you want to partition.
2) Print the partition table to see if anything is already there.
3) Delete any unwanted partitions.
4) Create any needed partitions.  For the starting cylinder, you will usually just hit enter.  Sizes can be entered in formats like "+200G".
5) Change the partition type to match what you are doing.  It defaults to a Linux type things like ext3.  If you are using the partition for raid, chnage the type to "fd".  Pressing "L" will give you a listing of all the types.
6) Write the partition table when you are done.
7) Repeat this process for all of your drives.

---

### Post by astrotech226 on 2008-02-21
> **misconfiguration said:**
> 
Do you see problems between IDE and sATA drives being mixed?

I've never tried mixing technologies.  In theory, I guess it should work.  I am also going to guess that you will lose performance from the Sata drives because the stripping will only be as fast as the slowest drives which should be the IDE ones.

It would be interesting to test if this works or not because I can't tell you for certain what to expect out of it.  If you do attempt this, please post your results, I'm curious :)

---

### Post by misconfiguration on 2008-02-21
I most definitly will; the hard drive write speeds are not a huge concern for me at the moment; considering this will just be a media server data will rarely be written to it; mostly just reads VIA the network.

Thanks again for your help!

---

