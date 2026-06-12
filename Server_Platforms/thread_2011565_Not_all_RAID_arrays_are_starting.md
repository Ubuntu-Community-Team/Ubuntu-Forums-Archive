---
title: "Not all RAID arrays are starting"
date: 2012-06-27
forum: Server Platforms
---

### Post by Chris on 2012-06-27
I just upgraded a server from 10.04 to 12.04 and I'm having problems with the RAID arrays not starting.  Some of them start and some don't and sometimes it's random as to which ones but it appears to only start two of the arrays no matter what I do and even after boot I can't get to the third array at all.

I have 3 RAID arrays built from 3 drives (each with 3 partitions that make up the arrays).  All the drive have the exact same GPT:
```
Number  Start (sector)    End (sector)  Size       Code  Name
   1              40             295   128.0 KiB   EF02  BIOS boot partition
   2             296          195311   95.2 MiB    FD00  Boot
   3        20971816      3907029134   1.8 TiB     FD00  Linux RAID
   4          195312        20971815   9.9 GiB     FD00  Root
```My mdadm.conf looks like this:
```
ARRAY /dev/md0 level=raid5 metadata=1.2  num-devices=3 UUID=4ec0f6ef:0ec46c5f:3e867509:21c008e9 name=archiso:0
ARRAY /dev/md1 level=raid5 metadata=1.2  num-devices=3 UUID=b039189e:dee2e214:eee4dee5:5c2c6483 name=archiso:1
ARRAY /dev/md2 level=raid5 metadata=0.90 num-devices=3 UUID=dd5d644d:a2cc2cc8:bac90dff:87020025
```But at any given boot only two of the arrays will start.  For example on the boot I just did I now have:

```
# mdadm --detail --scan
ARRAY /dev/md1 metadata=0.90 UUID=dd5d644d:a2cc2cc8:bac90dff:87020025
ARRAY /dev/md/0 metadata=1.2 name=archiso:0 UUID=4ec0f6ef:0ec46c5f:3e867509:21c008e9
``````
# cat /proc/mdstat 
Personalities : [raid6] [raid5] [raid4] [linear] [multipath] [raid0] [raid1] [raid10] 
md0 : active raid5 sdb2[1] sda2[0] sdc2[3]
      194560 blocks super 1.2 level 5, 512k chunk, algorithm 2 [3/3] [UUU]
      
md1 : active raid5 sdb3[1] sda3[0] sdc3[2]
      3886057088 blocks level 5, 64k chunk, algorithm 2 [3/3] [UUU]
```It seems the /dev/md1 is actually the /dev/md2 from the mdadm.conf.

Where did the other array go?  There are no other "md" devices in "/dev".  The third array is just gone.  Now I'm not sure if it's completely random or maybe dependant on the order of the devices in mdadm.conf.  In any case only two arrays start and "something" makes it only start a particular two (that can change).  I have never been able to get all three to come up at once but I can get each of the three to come up by rebooting multiple times and/or changing the order in the mdadm.conf file.

Any ideas?

---

### Post by Chris on 2012-06-27
OK, I can confirm that changing the device name in mdadm.conf changes which arrays start.  It never starts whichever one is labeled /dev/md1.  It then starts whichever is labelled as /dev/md2 as /dev/md1.  :?

I changed my mdadm.conf like so:
```
ARRAY /dev/md0 level=raid5 metadata=1.2  num-devices=3 UUID=4ec0f6ef:0ec46c5f:3e867509:21c008e9 name=archiso:0
ARRAY /dev/md1 level=raid5 metadata=0.90 num-devices=3 UUID=dd5d644d:a2cc2cc8:bac90dff:87020025
ARRAY /dev/md2 level=raid5 metadata=1.2  num-devices=3 UUID=b039189e:dee2e214:eee4dee5:5c2c6483 name=archiso:1
```And now I have:
```
# mdadm --detail --scan
ARRAY /dev/md/1 metadata=1.2 name=archiso:1 UUID=b039189e:dee2e214:eee4dee5:5c2c6483
ARRAY /dev/md/0 metadata=1.2 name=archiso:0 UUID=4ec0f6ef:0ec46c5f:3e867509:21c008e9
``````
# cat /proc/mdstat 
Personalities : [raid6] [raid5] [raid4] [linear] [multipath] [raid0] [raid1] [raid10] 
md0 : active raid5 sdb2[1] sda2[0] sdc2[3]
      194560 blocks super 1.2 level 5, 512k chunk, algorithm 2 [3/3] [UUU]
      
md1 : active raid5 sdb4[1] sda4[0] sdc4[3]
      20773888 blocks super 1.2 level 5, 512k chunk, algorithm 2 [3/3] [UUU]
```

Seriously, what the hell.

---

### Post by rubylaser on 2012-06-27
Your name lines in your mdadm.conf file are goofing up mdadm's detection and assembly of arrays.  Only include what you need for it to assemble here's what I would include.

```
DEVICE partitions
HOMEHOST fileserver
MAILADDR youruser@gmail.com
ARRAY /dev/md0 metadata=1.2  UUID=4ec0f6ef:0ec46c5f:3e867509:21c008e9 
ARRAY /dev/md1 metadata=1.2 UUID=b039189e:dee2e214:eee4dee5:5c2c6483
ARRAY /dev/md2 metadata=0.90 UUID=dd5d644d:a2cc2cc8:bac90dff:87020025
```

All other options on the ARRAY lines are not necessary for mdadm to correctly assemble the array.  Finally update your initramfs and reboot and post back what it looks like.

```
update-initramfs -u
```

---

### Post by Chris on 2012-06-28
Actually I ended up just removing all the arrays from the mdadm.conf.  I get "random" names but at least all the arrays start.   md0, md1, and md127.

If the array lines aren't needed then the installer shouldn't put them in there.  Or it should at least build the mdadm.conf file correctly.  Probably should submit a bug but I'm too lazy to search for an existing one and then possibly write up a new one.

---

### Post by rubylaser on 2012-06-28
The array lines ensure that your arrays end up in the order you'd like them to be /dev/md[0,1,2].  I didn't say the ARRY lines where unnecessary, I said that the name section in them is not needed.  If you follow the directions I posted, they should come up in the proper order and at the proper locations every time.

This [thread]("http://ubuntuforums.org/showthread.php?t=1764861") covers what I am talking about.

---

### Post by Chris on 2012-06-28
I know.  I didn't mean that you said all that, I was just thinking out loud.

The original mdadm.conf that the installer created was wrong though.  It did have all that information filled out and it didn't have all the arrays in it (ie. the installer is at least somewhat broken).

---

