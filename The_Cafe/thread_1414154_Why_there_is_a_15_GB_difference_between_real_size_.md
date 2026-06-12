---
title: "Why there is a 15 GB difference between real size of the partition &amp; what Ubuntu says"
date: 2010-02-23
forum: The Cafe
---

### Post by legolas_w on 2010-02-23
Hi
my home partition is about 35 GB as you can see in the image I attached. The size is based on what GParted is showing.

[IMG]http://img9.org/uploads/b5a659e6d49840cd65728ce2a1ad96fd.png[/IMG]

Now when I right click inside the /home/legolas or /home and check the size I see that 7.5 GB is used and 13.2 GB is unused as you can see in the nautilus properties picture.

[IMG]http://img9.org/uploads/88891ccd8d137e56f209d9fd15f32768.png[/IMG]


has anything like this ever happened to you? if it was windows I could use the check disk thingy to fix the issue but I do not know what to do now.

---

### Post by LMP900 on 2010-02-23
Most likely an issue of binary vs. decimal measure of disk space.

i.e.

1000MB = 1GB
1024MiB = 1GiB

Edit: In your case, however, the difference shouldn't be as large as it is. It does say "some contents unreadable." Perhaps the issue lies there?

---

### Post by swoll1980 on 2010-02-23
> **LMP900 said:**
> Most likely an issue of binary vs. decimal measure of disk space.

i.e.

1000MB = 1GB
1024MiB = 1GiB


There's no way that would account 13GB of missing space.

---

### Post by LMP900 on 2010-02-23
> **swoll1980 said:**
> There's no way that would account 13GB of missing space.

Yes, you're right. I read the post too quickly. The "some contents unreadable" comment from Nautilus is suspect. Perhaps a permissions issue?

Although, I would imagine a disk usage analysis would still account for content that do not "belong" to the user.

---

### Post by MasterNetra on 2010-02-23
Well it the home folder thing. Its looking solely in the homefolder for total size of contents and not the main directory " / " The freespace on the other hand is based off of the main  directory. Or at least that would be the case if you just had a basic partition with Ubuntu installed.

Also though I noticed it claimed that some contents were unreadable so perhaps then 7.5 GB is only of what it could read.

EDIT: LMP900 beat me to it lol

---

### Post by Cabs21 on 2010-02-23
> **legolas_w said:**
> Hi
my home partition is about 35 GB as you can see in the image I attached. The size is based on what GParted is showing.

[IMG]http://img9.org/uploads/b5a659e6d49840cd65728ce2a1ad96fd.png[/IMG]

Now when I right click inside the /home/legolas or /home and check the size I see that 7.5 GB is used and 13.2 GB is unused as you can see in the nautilus properties picture.

[IMG]http://img9.org/uploads/88891ccd8d137e56f209d9fd15f32768.png[/IMG]


has anything like this ever happened to you? if it was windows I could use the check disk thingy to fix the issue but I do not know what to do now.


Ok as you will see your Gparted says you have a 37.25 GiB partition.  But what you failed to notice is that you have used 22.18 GiB of that space with Data of some kind.  NOW your home folder does not contain EVERYTHING on that partition.  The filesystem folder contains **ALL** the stored data on that partition.  Nautilus is showing you the correct amount of free space.  Let me show you the math

37.25 GiB - 22.18 GiB = roughly 15 GiB

of that 22.18 GiB your home **folder** takes up only 7.5 GB.  Your "missing" storage is actually being used somewhere else on that partition.  Go further back into the system before the home folder and check your properties there to see what your data is and compare with gParted.

Edit: Oh Too slow! Damn.

---

### Post by pbpersson on 2010-02-23
Part of this could also be that Nautilis is reporting the size of the files - but a file smaller than four kilobytes will still take up 4K on the disk because that is the default block size.  That is assuming we are discussing ext4

A 5K file will take up 8K on the disk,
A 9K file will take up 12K on the disk....

It always rounds up to the next block boundary

---

### Post by pbpersson on 2010-02-23
This is normal, my numbers do not match up either

---

### Post by swoll1980 on 2010-02-23
> **pbpersson said:**
> Part of this could also be that Nautilis is reporting the size of the files - but a file smaller than four kilobytes will still take up 4K on the disk because that is the default block size.  That is assuming we are discussing ext4

A 5K file will take up 8K on the disk,
A 9K file will take up 12K on the disk....

It always rounds up to the next block boundary

This would not account for 13GB of a 33GB partition either. The problem has been solved, I'm sure. There is data stored on that partition that isn't in the home folder.

---

### Post by pbpersson on 2010-02-23
It appears this is all calculated in different ways.  GPartED reported that the /home was taking 79GB of space.  However doing this from the command line gave a result of 76GB:

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             230G  4.4G  214G   2% /
udev                  2.0G  228K  2.0G   1% /dev
none                  2.0G  1.7M  2.0G   1% /dev/shm
none                  2.0G  324K  2.0G   1% /var/run
none                  2.0G     0  2.0G   0% /var/lock
none                  2.0G     0  2.0G   0% /lib/init/rw
/dev/sda5             222G   76G  136G  36% /home
```

When I use a root session of Nautilus to check the size of /home it reports total space used as 68.8GB but when I do the same operation from a root command line it reports 78.96 GB:

```
78964340	/home
78964340	total
```

I have always said that Linux was about variety and having choices, this is just another example of this philosophy :D

---

### Post by MichealH on 2010-02-23
Listen I went to User nautilus and It told me 16.2 GB left that may be right but its not GParted shows 17.14GB left.Hmm but thats with priveleges so I ran

```
gksu nautilus
```

but no It still said 16.2GB so its not a issue with privelages.

Is it a fault with Nautilus or GParted???

---

### Post by LMP900 on 2010-02-23
> **MichealH said:**
> Listen I went to User nautilus and It told me 16.2 GB left that may be right but its not GParted shows 17.14GB left.Hmm but thats with priveleges so I ran

```
gksu nautilus
```

but no It still said 16.2GB so its not a issue with privelages.

Is it a fault with Nautilus or GParted???

It didn't apply to the OP, but the decimal vs. binary measure of disk space most likely is the cause of the discrepancy in your case.

1024 MiB = 1 GiB
1000 MB = 1 GB

---

