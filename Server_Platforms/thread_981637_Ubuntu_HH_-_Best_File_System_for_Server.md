---
title: "Ubuntu HH - Best File System for Server"
date: 2008-11-13
forum: Server Platforms
---

### Post by badm4n on 2008-11-13
can you help me about this ?

1. best File System for Storage Server
2. best File System for WebServer
3. best File System for PROXY server
4. best File System for LAMPP + Squid Server
5. best File System for LAMPP + DMZ + Squid Server

my PC is = DELL PE SC1430

thx for your answer

---

### Post by Vegan on 2008-11-13
I am using the default ext3 file system, seems fine.

:guitar:

---

### Post by gtdaqua on 2008-11-13
> **badm4n said:**
> can you help me about this ?

1. best File System for Storage Server
2. best File System for WebServer
3. best File System for PROXY server
4. best File System for LAMPP + Squid Server
5. best File System for LAMPP + DMZ + Squid Server

my PC is = DELL PE SC1430

thx for your answer

I use a Dell SC1435 and the performance is not that great even on RAID-0 SAS 15K RPM drives. Ext3 is an all rounder. Rock Solid. 

But if you want to tweak your performance, you should use combinations. XFS is quite stable and better than Ext3 if you are handling files with huge sizes. ReiserFS is champion for handling files under 4k (consider email servers). JFS in many cases is better than Ext3. If you have rock solid power source, consider mounting Ext2 drives with data=writeback parameter. 

There are various options. The point is what kind of files are going to be handled and how often?

Give an extensive reading here; definitely worth it: 
[Filesystem Comparison on Debian Etch]("http://www.debian-administration.org/articles/388").

Dont worrry about the title saying 'Debian'. Ubuntu is based on debian and because the article deals with filesystem, the readings inside are not strictly relevant to specific distros.

---

### Post by cariboo on 2008-11-13
I would stay away from reiserfs until we see what happens to it now that the author is in jail.

Jim

---

### Post by badm4n on 2008-11-14
> **cariboo907 said:**
> I would stay away from reiserfs until we see what happens to it now that the author is in jail.

Jim

oot reply : the author in the jail ? prison you mean ?

back to topic

@gtdaqua and other helper :
overall
what you suggestion for number 1 ? 2 ? 3 ? 4 ? 5 ? ( each )
with this partition concept

HDD split 2
swap space = 2x RAM
rest space mount to / ( root )

---

### Post by baeksu on 2008-11-14
In general, ext3 can be considered just fine. It handles sudden power loss better than xfs.

Reiserfs is pretty well tested too. Reiser being in jail will only affect the inclusion of reiserfs4 in to the kernel (probably not going to happen anymore), but the current reiserfs (v.3) will remain supported. But reiserfs has same problems as xfs with sudden power losses.

Ext3 will be easy to convert to ext4, which provides some new features.

As for partitioning, it might make sense to make a separate partition for the system and the data. Often /var is put on another partition to reduce fragmentation. So you would have one partition for /, one for /var, and a third one where you would put your data.

This partitioning scheme makes it easier to make backups of the parts you want, and also it will be easier to reinstall the system without losing your data.

---

### Post by badm4n on 2008-11-14
> **baeksu said:**
> In general, ext3 can be considered just fine. It handles sudden power loss better than xfs.

Reiserfs is pretty well tested too. Reiser being in jail will only affect the inclusion of reiserfs4 in to the kernel (probably not going to happen anymore), but the current reiserfs (v.3) will remain supported. But reiserfs has same problems as xfs with sudden power losses.

Ext3 will be easy to convert to ext4, which provides some new features.

As for partitioning, it might make sense to make a separate partition for the system and the data. Often /var is put on another partition to reduce fragmentation. So you would have one partition for /, one for /var, and a third one where you would put your data.

This partitioning scheme makes it easier to make backups of the parts you want, and also it will be easier to reinstall the system without losing your data.

But reiserfs has same problems as xfs with sudden power losses. <-- can you explain me more

---

### Post by baeksu on 2008-11-14
All three filesystems use journaling ([wikipedia link](http://en.wikipedia.org/wiki/Journaling_file_system)), but only ext3 writes the data before the metadata to the disk.

If the power is cut while data is being written to the disk, there can be inconsistencies between the data and the metadata. Ext3 will handle this better than xfs.

Reiserfs can be made to write the data before metadata by mounting it with the option "data=ordered".

There's a short explanation of this issue [here](http://foolhill1.blogspot.com/2006/10/reiserfs-vs-ext3-vs-xfs.html).

Mind you, ext3 journaling method does come with a slight performance penalty, but there's always a trade off between performance and stability. Hence some people will prefer xfs, some ext3, some reiserfs.

---

### Post by badm4n on 2008-11-14
> **baeksu said:**
> All three filesystems use journaling ([wikipedia link](http://en.wikipedia.org/wiki/Journaling_file_system)), but only ext3 writes the data before the metadata to the disk.

If the power is cut while data is being written to the disk, there can be inconsistencies between the data and the metadata. Ext3 will handle this better than xfs.

Reiserfs can be made to write the data before metadata by mounting it with the option "data=ordered".

There's a short explanation of this issue [here](http://foolhill1.blogspot.com/2006/10/reiserfs-vs-ext3-vs-xfs.html).

Mind you, ext3 journaling method does come with a slight performance penalty, but there's always a trade off between performance and stability. Hence some people will prefer xfs, some ext3, some reiserfs.

ok. now back to my question
let say i use reiferfs for number 1 2 3 4 5
tell me ... your opinion
( actually im start with reiferfs from slacky 5 or 6.0 in that day reifers in the only FS using journaling system ( if im not wrong about slack version ) = dont think im use linux from slacky so im getting expert :( im still newbie and i start again since my friends introduce me ubuntu 5.x )

---

### Post by loomsen on 2008-11-14
[http://www.debian-administration.org/articles/388](http://www.debian-administration.org/articles/388)

This link is actually very good. Read some articles on Linux FS in general. You got many different kinds of data. I assume you don't want it simple as one /home one / partition, otherwise you wouldnt have asked, right. 

For instance, files and folders in /proc aren't actually files and folders, but a virtual abstraction layer. Your kernel uses all the files and folders in /proc for example to communicate with your hardware.

Just for a basic example, if you send the adress of your graphics device to /proc/audio (or how your soundcard is called) you will hear what your graphics device sounds like :)

That's meant by Kernel alive. So one's able to interact with his hardware live, 

another example:
```

me@tiffany:~$ cat /proc/acpi/battery/BAT1/info
present:                 yes
design capacity:         4800 mAh
last full capacity:      4800 mAh
battery technology:      rechargeable
design voltage:          11100 mV
design capacity warning: 420 mAh
design capacity low:     156 mAh
capacity granularity 1:  264 mAh
capacity granularity 2:  3780 mAh
model number:            PA3465U 
serial number:           3658Q
battery type:            Li-Ion
OEM info:                COMPAL  
me@tiffany:~$ 

``` 
I can parse the file using the cat command, but as it isn't a file in fact, I'm not able to open it up with gedit or so.

Other files, like your /boot/ nearly never change. OK, when you upgrade your kernel... Here it would make sense to specify noatime, nodevatime, norelatime, and so on.

/etc/ for example are configs, which aren't static neither. 

Just read some articles about linux FS and you'll find your prefered mount options pretty fast I'm sure.
Mounting /tmp/ as RAM and disabling SWAP or stuff like this.

---

### Post by gtdaqua on 2008-11-14
> **badm4n said:**
> ok. now back to my question
let say i use reiferfs for number 1 2 3 4 5
tell me ... your opinion
( actually im start with reiferfs from slacky 5 or 6.0 in that day reifers in the only FS using journaling system ( if im not wrong about slack version ) = dont think im use linux from slacky so im getting expert :( im still newbie and i start again since my friends introduce me ubuntu 5.x )

Boss, looking at your infrastructure, Ext3 is good to go. You wont notice a performance loss unless you REALLY stress the server.

---

### Post by badm4n on 2008-11-14
> **gtdaqua said:**
> Boss, looking at your infrastructure, Ext3 is good to go. You wont notice a performance loss unless you REALLY stress the server.

so if we talk about performa .... etx3 is the best ?

---

### Post by JNelson on 2008-11-14
Uhh ext3 has limits that will eventually be ran into for a server
1.It has a limted amount of inodes.
2.It has a Subdirectory limit of 32k.

---

### Post by djamu on 2008-11-15
I usually go for:
ext3 as system FS 
> depending on kernel compile max filesize 16GB-2TB max volume size 2-32TB 

reiserfs for small to medium RAID's 
 > as previously said reiserFS is awesome for small files &  you can do online volume resizing ( enlarge ) max filesize 8TB max volume size 16TB


larger systems 
I very much like XFS, great speed  max filesize 8EB ( 1EB = 1.000.000.000 GB ) max volume 8EB

huge FS
ZFS is real nice too > max filesize 8EB max volume 2**18 EB

insane FS :lol:

Lustre + Google FS  > check it out yourself 


a nice comparison of all > [http://en.wikipedia.org/wiki/Comparison_of_file_systems](http://en.wikipedia.org/wiki/Comparison_of_file_systems)
:lolflag:

---

### Post by Matthaeus on 2008-11-26
> **djamu said:**
> I usually go for:
ext3 as system FS 
> depending on kernel compile max filesize 16GB-2TB max volume size 2-32TB 


What block size does the ubuntu kernel use?
The 4KB? So 2TB file size and 8TB volume size limitations?

Thanks, Matthaeus.

---

