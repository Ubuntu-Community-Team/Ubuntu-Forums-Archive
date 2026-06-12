---
title: "Mythbusting Linux"
date: 2015-06-25
forum: The Cafe
---

### Post by michael-piziak on 2015-06-25
Interesting video here.

[https://www.youtube.com/watch?v=y_lhqg_p21k](https://www.youtube.com/watch?v=y_lhqg_p21k)

The 2 most intriguing things to me is the maleware/virus part and the defrag part.  Clamtk is a free anti-virus/anti-malware program we can use.  About the defrag part, does Ubuntu defrag in the background?  I see there is a program in the software center for sale ($7.99) called HDD Ranger that is a defrag program for Ubuntu - is this needed ?

---

### Post by MartyBuntu on 2015-06-25
Here's a little salt to be taken with much of what Matthew Moore disseminates...

[IMG]http://snowclearancedirect.com/_downloads/1_1_Bulk_Bag_-_Rock_Salt.JPG[/IMG]

---

### Post by grahammechanical on 2015-06-25
The Ext4 file system is default on Ubuntu

> **Extents**
[Extents]("https://en.wikipedia.org/wiki/Extent_%28file_systems%29") replace the traditional [block mapping]("https://en.wikipedia.org/wiki/Block_%28data_storage%29")  scheme used by ext2 and ext3. An extent is a range of contiguous  physical blocks, improving large file performance and** reducing  fragmentation**. 


> **Persistent pre-allocation**
ext4 can pre-allocate on-disk space for a file. To do this on most  file systems, zeros would be written to the file when created. In ext4  (and some other files systems such as [XFS]("https://en.wikipedia.org/wiki/XFS")) fallocate(),  a new system call in the Linux kernel, can be used. The allocated space  would be guaranteed and **likely contiguous**. This situation has  applications for media streaming and databases.

> 
**Delayed allocation**
ext4 uses a performance technique called [allocate-on-flush]("https://en.wikipedia.org/wiki/Allocate-on-flush") also known as *delayed allocation*.  That is, ext4 delays block allocation until data is flushed to disk.  (In contrast, some file systems allocate blocks immediately, even when  the data goes into a write cache.) Delayed allocation improves  performance and **reduces [fragmentation]("https://en.wikipedia.org/wiki/File_system_fragmentation")** by effectively allocating larger amounts of data at a time.


[https://en.wikipedia.org/wiki/Ext4](https://en.wikipedia.org/wiki/Ext4)

Regards.

---

### Post by kostkon on 2015-06-25
> **MartyBuntu said:**
> Here's a little salt to be taken with much of what Matthew Moore disseminates...

[IMG]http://snowclearancedirect.com/_downloads/1_1_Bulk_Bag_-_Rock_Salt.JPG[/IMG]
Even that is not enough.

He got the views though.

---

