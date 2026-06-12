---
title: "[Windows 10] Ext2Fsd doesn't reveal anymore appear ext partitions in the Win Explorer"
date: 2015-11-18
forum: Windows
---

### Post by M_2_M on 2015-11-18
Hello,

I used to execute Ext2Fsd with my Windows 10 in order to open my ext3 partition shared with my Ubuntu (I have also a second NTFS partition: D ). I like this software because it "mounts" my ext3 partition as the other NTFS partition : I can see seem in the explorer ( C: D: F: ...), write, delete and launch software in it, either with Windows or Wine.

But after the latest update of W$10 (you know, the update that makes 3 or 4 reboot of the system! ), when I launch Ext2Fsd everything seems good, as usual, but now in the explorer I see only the C: the D: and nothing else: no F: :confused:

I've tried other sowftwares but no one could "mount" partitions as Ext2Fsd do, they are only "viewer".

So if you have an idea of the problem (maybe change a stupid parameter in the registry? ), or an other programs that could work fine with my needs (launch win programs with data in the ext partition), or bad news, I would be grateful!

M 2 M

---

### Post by howefield on 2015-11-19
Having a quick look around, seems that there are a some who say it works fine with Windows 10 and others who are not not so lucky, have you tried the obvious and reinstalled it ?

---

### Post by Pwnsmack on 2015-11-19
> **M_2_M said:**
> Hello,

I used to execute Ext2Fsd with my Windows 10 in order to open my ext3 partition shared with my Ubuntu (I have also a second NTFS partition: D ). I like this software because it "mounts" my ext3 partition as the other NTFS partition : I can see seem in the explorer ( C: D: F: ...), write, delete and launch software in it, either with Windows or Wine.

But after the latest update of W$10 (you know, the update that makes 3 or 4 reboot of the system! ), when I launch Ext2Fsd everything seems good, as usual, but now in the explorer I see only the C: the D: and nothing else: no F: :confused:

I've tried other sowftwares but no one could "mount" partitions as Ext2Fsd do, they are only "viewer".

So if you have an idea of the problem (maybe change a stupid parameter in the registry? ), or an other programs that could work fine with my needs (launch win programs with data in the ext partition), or bad news, I would be grateful!

M 2 M

I'm having this exact same problem after new Windows 10 update.  I tried uninstalling/reinstalling ExtFsd to no avail.  ExtFsd can recognize my EXT3 partition and pretends to map it but it does not show up in Windows Explorer.  I'm guessing this is an incompatibility with the driver and the new version of Windows 10.

---

### Post by M_2_M on 2015-11-19
> **howefield said:**
> Having a quick look around, seems that there are a some who say it works fine with Windows 10 and others who are not not so lucky, have you tried the obvious and reinstalled it ?

Sure!

wnsmack -> maybe the next update of win10 will be good for us ! *joke*

The problem is that Wine/POL need ext3, and can't work with NTFS (or doesn't *like* very much), so I will have to change my habits ;)

---

### Post by M_2_M on 2015-12-29
It seems that this situation is not hopeless. Developpers have found a way to fix it: [http://www.ext2fsd.com/?p=182](http://www.ext2fsd.com/?p=182) :D

A little tamper and it works ;)

Windows 10 tends to use more en more the command line! It's a bit paradoxal ...

---

