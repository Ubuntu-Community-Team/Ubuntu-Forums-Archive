---
title: "Large Raid"
date: 2015-02-24
forum: Server Platforms
---

### Post by adamjseed on 2015-02-24
Hi all, 

I have found my self in a bit of a sticky situation. 

I have currently got a software ext4 raid5 mdadm array of 4x4tb disks (12tb of usable space). I have just added 3 more disks and hit the wonderful 32bit limit of ext4 (or the tool that deals with it). Specifically I get the error "resize2fs: New size too large to be expressed in 32bits" when resizing it. I see people going down the ZFS route but I cant as I have 11.50tb of data and I cant create a new ZFS array and grow it. 

I am finding it hard to see how people have resolved this issue. I have checked my mkfs.conf and it has the 64bit option under ext4 set: 
	ext4 = {
		features = has_journal,extent,huge_file,flex_bg,uninit_bg,dir_nlink,extra_isize
		auto_64-bit_support = 1
		inode_size = 256
	}

I assume this means that my disks have been created in 64bit mode? but I don't understand why it wont resize now.
Does anyone know how I can resolve this?

---

### Post by MAFoElffen on 2015-02-24
The ext4 filessystem can support much larger, but the toolset to work with it, is a little behind. What I did a few years back was by following these two:
[http://blog.ronnyegner-consulting.de/2011/08/18/ext4-and-the-16-tb-limit-now-solved/](http://blog.ronnyegner-consulting.de/2011/08/18/ext4-and-the-16-tb-limit-now-solved/)
[http://www.unix-ninja.com/p/Formatting_Ext4_volumes_beyond_the_16TB_limit/](http://www.unix-ninja.com/p/Formatting_Ext4_volumes_beyond_the_16TB_limit/)

Which were basically the same processes. 

I would have thought... You would have thought that it four years since, that the tools would have caught up already.

*** What you have above in your post (the config) is the same as in the last, so that may be caught up now... and just the congfig entires needed now, may be all that is needed now. Not sure. If it is caught up now, please tell me.

---

### Post by adamjseed on 2015-02-25
Thanks for the reply MAFoElffen,

I have seen these two posts. After a bit more analysis it looks like my e2fsprogs tool is version:1.42.5-1.1 amd64 and i need 1.42.7 as mentioned in these guides. 

So my question now is, can i simply upgrade this tool and make it work? from what I read I can not and need to recreate my partitions. Which means I will need to remove my 3 new disks from the array and create a separate raid, shift the data and grow it.

---

### Post by darkod on 2015-02-25
I know it's not directly your question, but are you running a very old OS? In such case, it would be close to end of support. Would you be willing to consider upgrading it? Which should sort out the e2fsprogs version...

Or you can probably try upgrading e2fsprogs manually but in such case you might need to chase up dependencies... also manually

---

### Post by adamjseed on 2015-02-25
I must confess that I'm using Proxmox version 3.3 (Debian 7.7) but posted here as its the best community for general answers. Of course if I start running into OS specific issues I post accordingly. I consider ubuntu as my main OS of choice as all of my VM's are Ubuntu based. 

I am about to go down the manual build of e2fsprogs but just weighing up my options before I choose a route

---

### Post by adamjseed on 2015-03-04
Hi All, 

I have got to the effort of:
1) building the e2fsprogs
2) shrinking my array to 4 disks again
3) copying everything off it on to my 3 spare drives
4) Reforming my array with the new tools and -O 64bit flag
5) copying everything back onto the raid
6) adding and growing the array again

...But I have hit another issue

after I rebuilt the array, the 'Array Size' has not changed, see the output of MDADM:

        Version : 1.2
  Creation Time : Wed Oct  9 10:28:00 2013
     Raid Level : raid5
     Array Size : 11720655360 (11177.69 GiB 12001.95 GB)
  Used Dev Size : 3906885632 (3725.90 GiB 4000.65 GB)
   Raid Devices : 7
  Total Devices : 7
    Persistence : Superblock is persistent

    Update Time : Wed Mar  4 12:03:58 2015
          State : clean
 Active Devices : 7
Working Devices : 7
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 512K

           Name : this:0
           UUID : df7b7df0:e02346b9:060ad3b8:cab6b7b0
         Events : 38995

    Number   Major   Minor   RaidDevice State
       0       8       33        0      active sync   /dev/sdc1
       1       8       49        1      active sync   /dev/sdd1
       2       8       81        2      active sync   /dev/sdf1
       4       8       65        3      active sync   /dev/sde1
       7       8      113        4      active sync   /dev/sdh1
       6       8       97        5      active sync   /dev/sdg1
       5       8        1        6      active sync   /dev/sda1

Each disk is 4TB so my array size should be 4x7-4 = 24tb. Last time I grew the array it showed 24tb. so now when i try and re-size the FS it thinks its already at the max. Any ideas?

---

### Post by darkod on 2015-03-04
Look at the man page of mdadm. If I'm not mistaken there was a --size option to set array size. I don't know if it does that automatically after the grow.

See if it can help to set the max array size. Only after that you can try expanding the fs of course.

---

### Post by adamjseed on 2015-03-04
So it looks like a reboot fixed doh! 

and it looks like it has expanded successfully: 

/dev/md0                  22T  9.6T   11T  47%

---

