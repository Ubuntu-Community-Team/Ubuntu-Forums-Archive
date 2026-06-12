---
title: "file server and software raid - recoverable on fail?"
date: 2009-04-27
forum: Server Platforms
---

### Post by chammer on 2009-04-27
after a couple years of trying i was finally able to put myself into a position to build a halfway decent file/backup server from left over parts and new drives. i've done this sort of setup a couple times in the past, but for my mothers company which is using a 4x80gb software raid5 setup on ubuntu server 8.04 presently.

posts in the past led me to believe this was a viable alternative to an expensive hardware raid solution, and with processing power and memory where its at today it can actually be a better solution at times.

after building my personal server and wanting to trust data that absolutely cannot be lost under any circumstance on this new setup, im worried now about the route i've chosen and am looking for someone with more knowledge than i to examine this setup, and offer their opinions on how recoverable this system is should i lose a drive.

as my mothers file server is being scp'ed weekly to my local file server, while data loss is an issue - theirs is quite recoverable based on mine - both servers are setup nearly identical, however.

for my personal file server, fdisk -l spits out:

```

amaterasu: ~> do fdisk -l

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000207e8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         608     4883728+  83  Linux
/dev/sda2             609        1824     9767520   fd  Linux raid autodetect
/dev/sda3            1825       77825   610478032+  fd  Linux raid autodetect

Disk /dev/sdb: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00028e34

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         608     4883728+  82  Linux swap / Solaris
/dev/sdb2             609        1824     9767520   fd  Linux raid autodetect
/dev/sdb3            1825       77825   610478032+  fd  Linux raid autodetect

Disk /dev/sdc: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00030e3d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1         608     4883728+  82  Linux swap / Solaris
/dev/sdc2             609        1824     9767520   fd  Linux raid autodetect
/dev/sdc3            1825       77825   610478032+  fd  Linux raid autodetect

Disk /dev/sdd: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0003c3ca

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1         608     4883728+  82  Linux swap / Solaris
/dev/sdd2             609        1824     9767520   fd  Linux raid autodetect
/dev/sdd3            1825       77825   610478032+  fd  Linux raid autodetect


```

(yes, that does mean i have 15gb of swap... :-s)

leaving me with a (relevant) 'df -h' output of:
```

amaterasu: ~> df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             4.6G  983M  3.7G  21% /
/dev/md1              1.8T  266G  1.5T  16% /shared
/dev/md0               28G  641M   28G   3% /usr

```

and finally, /proc/mdstat...
```

amaterasu: ~> cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid5 sdb2[1] sdd2[3] sdc2[2] sda2[0]
      29302272 blocks level 5, 64k chunk, algorithm 2 [4/4] [UUUU]
      
md1 : active raid5 sdb3[1] sdd3[3] sdc3[2] sda3[0]
      1831433856 blocks level 5, 64k chunk, algorithm 2 [4/4] [UUUU]
      
unused devices: <none>

```

so, the question/issue...

from my reading over the past several years about the state of linux software raid and how recoverable it is (or can be) i feel im safe if one of the drives 2, 3, or 4 die and needs to be replaced as mdadm should have no problem rebuilding the array onto the new replacement disk.

i hadnt really thought about this until after i got everything setup, but...what if disk 1 fails which contains the only copy of / and /boot as well as the mbr?

i have a pair of 72gb raptors and a 250gb disk i pulled out of the chassis that i could use as the server install, with the raid spanning the entire space of the 4 640's for the file share. however, this would mean a re-install and also a re-copy of all data transferred thus far. also re-setting up several services (which isnt bad, but not something i want to do for a while yet).

so, assuming disk 1 fails i had thought maybe i could get away with installing a new 1st disk, doing a mirror of the partition setup of the first disk on this new drive, and then re-installing the os. during the install choosing NOT to touch disks 2, 3, and 4, and then marking those disks for raid5 while choosing not to format them. would the ubuntu server install be able to handle this? would mdadm, during the installation, be able to get the array rebuilt onto this new disk with no problem and/or be able to use the software raided /usr immediately so that ubuntu may re-install? i have had to manually mark disks in the past using another terminal when the curses installer has fouled up, and getting the md raid going...could i do this again behind the scenes as to not lose data?

my only other alternative to provide comfort to myself would be to separate the os and data completely by using one of the 3 old disks as the os disk, and the 4 new 640's as data only.

i really need a software option as a hardware based solution is too expensive for my current budget, and then there's the worry i hear about in regards to a certain card no longer being available should the card itself die...thus leaving your data stranded. :(

any thoughts on this (setup or otherwise...)

---

### Post by AK Dave on 2009-04-27
The "what if drive 1 fails" issue is precisely why my NAS is built with the OS on a bootable USB thumb drive.

---

### Post by chammer on 2009-04-28
> **AK Dave said:**
> The "what if drive 1 fails" issue is precisely why my NAS is built with the OS on a bootable USB thumb drive.

thank you for the input. i had been looking at drive enclosures and such for esata (which i believe i mentioned above), but nothing i've been happy with.

im currently looking at:

[http://www.newegg.com/Product/Product.aspx?Item=N82E16820220252](http://www.newegg.com/Product/Product.aspx?Item=N82E16820220252)

...and am ready to purchase. my only question is what is the usual lifetime of these drives when used in this way? i've heard they're only good for a certain amount of writes before they will never write again (though data could still be read from them). assuming that the data will always be safe regardless, i have no issues (at this price) purchasing one even once a year and re-installing the os, but i'd rather not have to do this.

i dont imagine too much writing will be occurring on the root file system anyway short of weekly package updates, and log writes.

8gb seems plenty as im currently only using 2gb between / and /usr at the present, but any suggestions on going to the 16gb version would be heeded as well.

---

### Post by cariboo on 2009-04-28
Even if you are running a raid array, you still need to have a good backup strategy, I would suggest two external usb hard drives, one of which is kept off site in case of fire or theft. This is especially important if you data is irreplaceable.

---

### Post by chammer on 2009-04-28
> **cariboo907 said:**
> Even if you are running a raid array, you still need to have a good backup strategy, I would suggest two external usb hard drives, one of which is kept off site in case of fire or theft. This is especially important if you data is irreplaceable.

cariboo: thanks for the heads up. i do plan to mirror, but off site via rsync to my colo server until i find a more permanent solution. most of the used space thus far are because i have moved my backup location to this new server for 3 machines, but my personal data which cannot be lost under any circumstance is quite minimal. rsync should do the job until i can find a more permanent and spacious solution (especially if i happen to fill this up...i dont have any way of supporting a backup or backups even split of this size which was a big concern.

have already been looking at external enclosures and i think two of those and two 1tb drives would be perfect.

---

### Post by radek_42 on 2009-04-29
Hi,

I am looking into similar solution myself. I am looking into 2 or 4 disk software raid 1 box.

I considered installing OS on USB flash drive to separate OS and data. On the other hand I do not see point in doing that. From what I understood you can boot from raid 1 device. So I feel the best solution would be installing OS on raid device to have OS redundancy as well.

Cheers, R>

---

### Post by jsowoc on 2009-05-02
I'm looking at a similar solution for a home NAS that needs to be in software RAID. I would probably do a RAID-1 for the root disks, and a RAID-5 for the data.

Does anyone know of a "how to make a home NAS for under $1k"? Ideally a guide that would guide through the tradeoffs between data security (running a 5-way RAID-1) and cost effectiveness.

---

### Post by crimsondr on 2009-05-29
> **AK Dave said:**
> The "what if drive 1 fails" issue is precisely why my NAS is built with the OS on a bootable USB thumb drive.

AK Dave,

What is the OS on your USB thumb drive?  And do you have any links on setup/configuration?

Thanks.

---

