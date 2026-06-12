---
title: "gpt vs msdos"
date: 2012-03-16
forum: Server Platforms
---

### Post by hallo200 on 2012-03-16
Hallo Forum,

I have 10.04 ubuntu server 32bit.
I formated a 16TB Volume with ext4. I used parted and followed this link:
[http://www.cyberciti.biz/tips/fdisk-unable-to-create-partition-greater-2tb.html](http://www.cyberciti.biz/tips/fdisk-unable-to-create-partition-greater-2tb.html)

I got a error message, that parted recognized a old gpt table, and i was asked wheater i want to use msdos or it is already a gpt partition.

I ansewered with yes.

(i dont remeber the exact error message and i didnt find it with google)

I had a 13 TB volume before and i canged it already to gpt a year ago.

Could this cause problems later on?

thanks 
with kind regards 
hallo200

---

### Post by oldfred on 2012-03-16
When you said yes was that keeping the gpt or not?

You cannot use MBR with drives that large, so you have to have gpt.

Post this or which ever drive it is, if not sda:

sudo parted /dev/sda unit s print

---

### Post by hallo200 on 2012-03-19
Hallo,

thanks for answering


parted /dev/cciss/c0d0 unit s print

OUTPUT:
root@backup:~# parted /dev/cciss/c0d0 unit s print
Model: Compaq Smart Array (cpqarray)
Disk /dev/cciss/c0d0: 33208806832s
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start  End           Size          File system  Name     Flags
 1      2048s  31249999871s  31249997824s  ext4         primary

with kind regards
hallo200

---

### Post by oldfred on 2012-03-19
I get this:
 31249997824 * 512
   	 	 	 	 	 		 	15,999,998,885,888
or about 16GB?

---

### Post by hallo200 on 2012-03-20
That's the size of the volume - 16TB.

So you mean that this is right? 

Because it seems that there was a GPT already existing.

Thanks and with kind regards
hallo200

---

### Post by oldfred on 2012-03-20
The start at sector 2048 is normal, but it does look like you have a few sectors at the end that are not in the partition.

Disk /dev/cciss/c0d0: 33208806832s
end of sda1   31249999871s

---

### Post by hallo200 on 2012-03-22
And what does that mean?
And how to fix it?


with kind regards

hallo 200

---

### Post by oldfred on 2012-03-22
It looks like you have a little more room to expand current partition or create a new small partition. 

I do not know how you create or edit partitions with your array. Normally I use gparted but it does not work with RAID or LVM which have their own partition editing tools. What tools does your system use?

---

### Post by hallo200 on 2012-03-22
I used parted for formating. The default cciss driver is used.
And yes, there is 1TB unformated space left.

What do you mean with "what Tools do your system use"?

Thanks, with kind regards
hallo200

---

### Post by oldfred on 2012-03-22
I did not know you could use parted on your system as gparted/parted does not work on RAID nor LVM as they are different partitioning systems.

---

### Post by hallo200 on 2012-03-22
It is not a fake raid or "mapper"-Thing. And its not a mdadm. 
The device is like a single disk.

So do you thing that i could have problems with this configuration?

Thanks and with kind regards
hallo200

---

### Post by oldfred on 2012-03-22
Then you should not be different than editing any partition (just a lot larger). I do not know if gparted or parted have any issues with very large partitions. Since gpt you may be able to use gdisk also.

Resizing an Ubuntu System Partition Use liveCD so everything is unmounted & swapoff if neccesary
[http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)
[http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html](http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html)
[http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-2/index.html](http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-2/index.html)
Command line version
[http://www.howtoforge.com/linux_resizing_ext3_partitions](http://www.howtoforge.com/linux_resizing_ext3_partitions)
sudo swapoff -a

GPT fdisk Tutorial -srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)
[http://www.rodsbooks.com/gdisk/download.html#obs](http://www.rodsbooks.com/gdisk/download.html#obs)

---

### Post by hallo200 on 2012-03-23
Hallo,

Thanks for Links. 
Aha, now I know the msdos Partionschema is just another name for the MBR Partition schema.
So mine is gpt so everything seems to be good.

But whats with the sectors which are out of range?

Thanks and with kind regards
hallo200

---

### Post by oldfred on 2012-03-23
What sectors out of range. Post exact message.

---

### Post by hallo200 on 2012-03-24
Hallo,

I mean your Post:

> The start at sector 2048 is normal, but it does look like you have a few sectors at the end that are not in the partition.

Disk /dev/cciss/c0d0: 33208806832s
end of sda1   31249999871sWhat did you mean exactly? Is there something that looks strange for you?

Thanks, with kind regards
hallo200

---

### Post by oldfred on 2012-03-24
No that was just to show that disk was 33..... and partition was 31.... so there was some more sectors on drive not in any partition.

---

