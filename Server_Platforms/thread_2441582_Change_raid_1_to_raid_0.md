---
title: "Change raid 1 to raid 0"
date: 2020-04-24
forum: Server Platforms
---

### Post by smiley1448 on 2020-04-24
Since i'm not a linux expert, would anybody be able to help me, change from raid 1 to raid 0, if you need more information, i can give it to you, configuration currently looks like this  ):P


Personalities : [raid1] [linear] [multipath] [raid0] [raid6] [raid5] [raid4] [raid10]
md2 : active raid1 sdb4[1] sda4[0]
      9756537856 blocks super 1.2 [2/2] [UU]
      bitmap: 7/73 pages [28KB], 65536KB chunk

md1 : active raid1 sdb3[1] sda3[0]
      9252864 blocks super 1.2 [2/2] [UU]

md0 : active raid1 sdb2[1] sda2[0]
      499648 blocks [2/2] [UU]

---

### Post by TheFu on 2020-04-24
Overview:

[LIST=1]
[*]Backup all your data.
[*]unmount the raid1 storage;  umount
[*]stop the raid1 array;  mdadm --stop
[*]create a new raid0 array carefully choosing options so you get the striping you want; mdadm -C
[*]assemble the new array;  mdadm --assemble
[*]create a file system on the new raid0 array; mkfs
[*]mount the raid0 array; mount ... or use the fstab
[*]restore any data.
[/LIST]

Beware that if either disk fails, all your data is lost.  There is no fix.  No recovery.   Daily backups are mandatory unless you don't care about the data.

---

### Post by hk42 on 2020-04-25
> **TheFu said:**
> 
Beware that if either disk fails, all your data is lost.  There is no fix.  No recovery.   Daily backups are mandatory unless you don't care about the data.
I agree on that but it is also true that sharing main drive activity between 2 physical ones improves their reliability.
I have an array of 2 x 1To drives that worked non stop for 15 years :-) 
Beware also of raid controller cards failure it is nice to have a spare one.

---

### Post by TheFu on 2020-04-25
> **hk42 said:**
> I agree on that but it is also true that sharing main drive activity between 2 physical ones improves their reliability.
I have an array of 2 x 1To drives that worked non stop for 15 years :-) 
Beware also of raid controller cards failure it is nice to have a spare one.

I’ve lost 80% of your data due to a single dish failure?  After that loss, i got backup religion.
i also have some HDDs that have been spinning at least 9 yrs (last time i looked), 24/7/365.  i've never seen any studies that claim striping improves reliability, just the opposite actually.   MTBF calculations that all engineers learn are pretty clear on that.  More parts == less reliability.

Very few people should be using RAiD controllers these days.  SW-RAiD is faster, more flexible, and doesn't tie the RAiD to any HW.  The only time where HW RAiD make more sense is when a RAiD controller w/ built-in battery backup ON THE CARD is used.  An external UPS isn't the same.  Also, when buying a RAiD controller, buy two at the same time and verify they are actually using the same chips.  RAiD controllers with the same model number from the same vendor aren't always the same and cannot always be swapped to gain access to the data after 1 fails.

---

### Post by hk42 on 2020-04-25
In fact the reason I used raid 0 at that time was that I did a lot of analog video capture 
and hard drive of more than 1 To were quite rare and expensive.
The drives  used were low speed "Green" one's.
For sure Backup is very important in all cases.
The only Linux distribution that recognised the raid at installation was Mandriva.
I was very impressed at the time. :-)

---

### Post by TheFu on 2020-04-25
Video work is an extremely specialized use-case.  I wouldn't assume that someone coming from RAID1 seeking striping was doing that, but we need to see what the OP says.

---

### Post by smiley1448 on 2020-04-25
> **TheFu said:**
> Overview:

[LIST=1]
[*]Backup all your data. 
[*]unmount the raid1 storage;  umount 
[*]stop the raid1 array;  mdadm --stop 
[*]create a new raid0 array carefully choosing options so you get the striping you want; mdadm -C 
[*]assemble the new array;  mdadm --assemble 
[*]create a file system on the new raid0 array; mkfs 
[*]mount the raid0 array; mount ... or use the fstab 
[*]restore any data. 
[/LIST]

Beware that if either disk fails, all your data is lost.  There is no fix.  No recovery.   Daily backups are mandatory unless you don't care about the data.


Is it possible to use the raid 0 in the root directory, i have two 10 tb hdds, and i would like to use all that space in the root directory, is it possible, it's already mounted in the root directory at /

---

### Post by TheFu on 2020-04-25
> **smiley1448 said:**
> Is it possible to use the raid 0 in the root directory, i have two 10 tb hdds, and i would like to use all that space in the root directory, is it possible, it's already mounted in the root directory at /

Possible, sure, but a terrible idea. There are things which can be accomplished, but that doesn't make it a smart idea.

/ should be about 25G in size. No larger.
/var/ should be whatever is needed, usually for people that use LXD or libvirt virtual machines will want /var larger than normal. Often, keeping /var/ and / together is perfectly fine.
/home should be whatever you like for home directories, but normally 25G per user is about the max.
Things that need large amounts of storage need to be placed somewhere else, not in /home nor as part of the OS.

Storage design and configuration is mainly about easy and efficient backups with a little planning for future OS upgrades.

2x10TB scream "data" and running an OS off ether would usually be a bad idea.  Huge storage drives like that aren't designed to be used as OS drives.  The workloads are different.  I’ve seen multiple 4TB disks with an OS die after around 2 yrs of use.

On the record, i think 
* RAiD 0 is a terrible idea, except for 1 very specific use - temporary storage for video editing. No files should be left on RAiD0 storage overnight.
* Putting an OS on a HDD over 1TB in size is a bad idea.

But it is your system to do whatever you like.

---

### Post by smiley1448 on 2020-04-29
I'm running a big web server, that's why i need all that space, i know raid 0 is a bad idea, and i know, that if i will lose all the data if something happens.

---

### Post by smiley1448 on 2020-04-29
Anybody that can help me, if you have the time, i can give login information to the server in rescue mode, is it possible to change from raid 1 to raid 0, without losing the operating system or data?

---

### Post by TheFu on 2020-04-29
> **smiley1448 said:**
> Anybody that can help me, if you have the time, i can give login information to the server in rescue mode, is it possible to change from raid 1 to raid 0, without losing the operating system or data?

No. How would the striping happen? Answer: It wouldn't, so it wouldn't be RAID0.   If you used LVM instead of mdadm, you could use concatenation to increase single-volume storage, but that would entail all sorts of copying the data around between the disks, multiple times, to accomplish.  LVM will support RAID0 too, but LVM has to be laid down on the disks at partition time. No good way to add it after the fact.

Sometimes the best answer is to spend $50-$150 (depending on the size needed), get a spare USB drive, backup everything and start fresh.  $150 should get 8TB-10TB spare.  Plus, you need a backup, I'm assuming, already.  I've seen poor quality USB 2TB HDDs for under $50.

---

