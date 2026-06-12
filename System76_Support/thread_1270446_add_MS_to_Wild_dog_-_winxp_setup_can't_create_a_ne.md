---
title: "add MS to Wild dog - winxp setup can't create a new partition"
date: 2009-09-19
forum: System76 Support
---

### Post by eaone2 on 2009-09-19
Hi,

I am trying to add an XP partition to my wilddog desktop using the instruction on 
[http://knowledge76.com/index.php/Windows_-_Add_MS_Windows_to_Your_System76_Machine#Resize_Your_Ubuntu_Partition](http://knowledge76.com/index.php/Windows_-_Add_MS_Windows_to_Your_System76_Machine#Resize_Your_Ubuntu_Partition)

I followed the steps til "Install Windows" with an XP installation CD. The windows setup screen displays the following partitions:
```
c: partition1 14305 mb
e: partition2 3711 mb
f: partition3 258923 mb
   unpartitioned space 199997 mb
```

 I got the following error message after I selected the "unpartitioned space" 
> setup cannot create a new partition in the space you selected because the max number of partitions already exists on the disk

so I went back to ubuntu, and here is what I see on gparted

/dev/sda1     ext3            13.97G
/dev/sda2     linux-swap     3.62G
unallocated   unallocated    2.35M
/dev/sda3     ext3           252.85G
unallocated   unallocated  195.31G    (the partition XP to be installed on)

I did some research online.  someone suggested to create a FAT32 partition on the unallocated space for XP to get around the problem.  Someone suggested to remove extra partition.  I want to know which way is a better choice.

Is the unallocated space of 2.35M a hidden partition?  I did not create the space.  It came with the original package of wild dog.  Can I delete it?  I am wondering if windows XP setup consider the extra unallocated space a "partition", even tho it cannot see it (as demonstrated above, windows only sees 4 partitions, not 5)

Any pointers to resolve the problem will be greatly appreciated.  Thanks!

---

### Post by PatrickVogeli on 2009-09-19
I'd try to use gparted to make a fat32 or ntfs partition. If I'm not wrong, an hdd can hold up to 4 primarty partitions, and you only have 3. Yeah, I'd made the fourth using gparted and then try to install XP there.

As for the unallocated space.. don't worry to much, it shouldn't hurt, since it isn't a partition.

---

### Post by Lee_Machine on 2009-09-19
There "shouldn't" be a problem using the XP install disk to create the partition, actually that is the preferred way. 

What version of XP are you using? SP2, or 3? 64bit?

---

### Post by Derath on 2009-09-19
The other thing to look at is Windows might still want to be the first OS on the system, which means basically that it has to reside on the "C drive". Also of note, iirc, you are only "allowed" 3 partitions on a hard drive for Windows (1 primary and 2 extended partitions according to how fdisk reads them I think).

Again, I may be wrong on these it's been a long time since I've done non-standard installs for Windows

---

### Post by thomasaaron on 2009-09-21
That smaller unallocated partition didn't come on the system. We image from a server that puts a standard image on everything. It must have happened accidentally when you were creating your new partition. You probably can use gparted to slide one of your partitions to the left to occupy that space. 

How old is your XP CD? Customers dual-boot our computers with XP all the time without getting the partition error.

---

