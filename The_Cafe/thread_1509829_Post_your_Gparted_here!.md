---
title: "Post your Gparted here!"
date: 2010-06-14
forum: The Cafe
---

### Post by the8thstar on 2010-06-14
Post your gparted here... I'm curious to see how you guys set up your partitions.

Here's mine!

[IMG]http://omploader.org/vNGx4ZQ[/IMG]

---

### Post by ubunterooster on 2010-06-14
No swap on yours?

---

### Post by scouser73 on 2010-06-14
Here's Mine,

[IMG]http://omploader.org/vNGx4aQ[/IMG]

---

### Post by J V on 2010-06-14
```
/dev/sda4            5100       28572   188546810+   5  Extended
/dev/sda5           23474       28572    40957717+  83  Linux
/dev/sda6            5100        5342     1951834+  82  Linux swap / Solaris
/dev/sda7            7835       23473   125620236   83  Linux
/dev/sda8            5343        7834    20016958+  83  Linux
```Long story... I didn't know you couldn't resize extended partitions >.>

---

### Post by FuturePilot on 2010-06-14
[[IMG]http://stashbox.org/927561/1/GParted.png[/IMG]]("http://stashbox.org/927561/GParted.png")

---

### Post by sisco311 on 2010-06-14
[[img]http://omploader.org/tNGx4bw[/img]](http://omploader.org/vNGx4bw)

---

### Post by NightwishFan on 2010-06-14
Palimpsest and not gparted, but here it is. I have mine set up to easily reinstall and have all data, but with a fresh configuration. I link my data folders from the third partition to my /home under the second.

---

### Post by MooPi on 2010-06-14
Ho Hum,

---

### Post by NCLI on 2010-06-14
```
root@NCLI-SERVER:~# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              53G  5,7G   45G  12% /
none                  2,0G  304K  2,0G   1% /dev
none                  2,0G     0  2,0G   0% /dev/shm
none                  2,0G  328K  2,0G   1% /var/run
none                  2,0G     0  2,0G   0% /var/lock
none                  2,0G     0  2,0G   0% /lib/init/rw
/dev/md0              4,1T  2,4T  1,7T  59% /home/seph/Media
/dev/sdd2             459G  291M  435G   1% /home/seph/Backup
```

---

### Post by towheedm on 2010-06-14
/dev/sda is my old windows drive.  /dev/sdb14 is my testing Lucid partition.

---

### Post by amauk on 2010-06-14
```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              18G  6.9G   11G  41% /
none                  2.0G  300K  2.0G   1% /dev
none                  2.0G  4.4M  2.0G   1% /dev/shm
none                  2.0G  232K  2.0G   1% /var/run
none                  2.0G     0  2.0G   0% /var/lock
none                  2.0G     0  2.0G   0% /lib/init/rw
/dev/sda4             342G  249G   77G  77% /home
tony-server:/music    3.6T  2.7T  720G  80% /media/raid5/music
tony-server:/dump     3.6T  2.7T  720G  80% /media/raid5/dump
tony-server:/tony     3.6T  2.7T  720G  80% /media/raid5/tony
tony-server:/roms     3.6T  2.7T  720G  80% /media/raid5/roms
tony-server:/scripts  185G  352M  176G   1% /home/tony/scripts
tony-server:/media    3.6T  2.7T  720G  80% /media/raid5/media
```

---

### Post by NightwishFan on 2010-06-14
By Grabthar's hammer what a disk layout!

Well I guess you will never have to worry about errors due to running out of space, everything has hard limits. :D

---

### Post by Daisuke_Aramaki on 2010-06-14
[IMG]http://omploader.org/vNGx4eg/cdf.png[/IMG]

---

### Post by de Bacon on 2010-06-14
sda1 - linux-swap -                - 996.22 MiB -
sda2 - ext4       - (MountPoint) / -  39.06 GiB -  15.82 Used -boot
sda3 - ext3       -                - 422.73 GiB - 321.05 Used -

---

### Post by ububaba on 2010-06-14
My drive 1

---

### Post by garvinrick4 on 2010-06-14
[attach]160473[/attach]

---

### Post by ubunterooster on 2010-06-14
Why the unallocated spaces?

---

### Post by FuturePilot on 2010-06-14
> **garvinrick4 said:**
> [attach]160473[/attach]

:shock:

---

### Post by Phrea on 2010-06-14
```
phrea@pb2:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              19G  3.8G   14G  22% /
none                  2.0G  316K  2.0G   1% /dev
none                  2.0G  236K  2.0G   1% /dev/shm
none                  2.0G  292K  2.0G   1% /var/run
none                  2.0G  4.0K  2.0G   1% /var/lock
none                  2.0G     0  2.0G   0% /lib/init/rw
none                   19G  3.8G   14G  22% /var/lib/ureadahead/debugfs
/dev/sda6             271G  4.4G  253G   2% /home
/dev/sdb1              49G  6.8G   40G  15% /media/downloads
/dev/sdb2             846G  600G  204G  75% /media/video
/dev/sdb3             480G   37G  419G   9% /media/overig

```

---

### Post by garvinrick4 on 2010-06-14
> **ubunterooster said:**
> Why the unallocated spaces?
If that was for me it is incase I want to increase the size of one of my partitions
at a later time.

---

### Post by ubunterooster on 2010-06-14
okay, thanks

---

### Post by 23dornot23d on 2010-06-14
My Main Drive .... sda ..... nice and tidy .... :lolflag:

[IMG]http://sites.google.com/site/23dornot23d/home/snapshot8.jpg[/IMG]

Second Drive a total mess

[IMG]http://sites.google.com/site/23dornot23d/home/snapshot6.jpg[/IMG]

Third Drive learning to organize it a bit better ..... 

[IMG]http://sites.google.com/site/23dornot23d/home/snapshot5.jpg[/IMG]

---

### Post by spcwingo on 2010-06-14
Here's mine:

---

### Post by the8thstar on 2010-07-07
Thanks to all who shared and posted so far. 

To the rest: feel free to add to this thread! :p

---

### Post by The Real Dave on 2010-07-07
My main drive on my main system. I thought about this hard before I partitioned it, so it's nice and tidy :) The data partition is NTFS to share files nicely with XP.

[[IMG]http://linuxexpresso.files.wordpress.com/2010/07/7-july-2010-gparted.png?w=300h=100[/IMG]]("http://linuxexpresso.files.wordpress.com/2010/07/7-july-2010-gparted.png")

---

### Post by jpeddicord on 2010-07-07
[IMG]http://imgur.com/LfUUt.png[/IMG]

Yeah, I'm a traitor. Wine doesn't cut it for most Steam games. :D

---

### Post by markp1989 on 2010-07-07
```
mark@torrentslave:~$ df -h 
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              14G  6.2G  7.0G  47% /
none                  1.9G  272K  1.9G   1% /dev
none                  1.9G  3.4M  1.9G   1% /dev/shm
none                  1.9G  432K  1.9G   1% /var/run
none                  1.9G     0  1.9G   0% /var/lock
none                  1.9G     0  1.9G   0% /lib/init/rw
none                   14G  6.2G  7.0G  47% /var/lib/ureadahead/debugfs
/dev/sda2             4.6G  1.4G  3.1G  31% /home
/dev/sdb1             1.4T  1.3T  129G  91% /media/data
/dev/sda5             1.4T  123G  1.2T  10% /media/torrents
/dev/loop0             50G  853M   46G   2% /srv/install
mark@torrentslave:~$ 
```

---

### Post by Cavsfan on 2010-07-07
My son in the traitor if anyone wants to know. Wine cannot handle some games.
And I see I have 1MB that is being unused.

[IMG]http://omploader.org/vNHY2dg[/IMG]

---

### Post by v1ad on 2010-07-07
here you go

---

### Post by xpod on 2010-07-07
This is my Desktop at home although the partition table posted doesn`t show the 200G drive that is also in there. It`s disconnected just now although it`s basically just a carbon copy of the connected drive with a bit more space and a little less mess. I`ll reconnect it when i upgrade it in the next month or so.
```

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              15G  7.2G  6.8G  52% /
none                 1003M  308K 1003M   1% /dev
none                 1007M  1.2M 1006M   1% /dev/shm
none                 1007M  120K 1007M   1% /var/run
none                 1007M     0 1007M   0% /var/lock
none                 1007M     0 1007M   0% /lib/init/rw
/dev/sda2             167G   70G   89G  45% /home

``` 

This is the laptop i`m currently using.
[ATTACH]162719[/ATTACH]

There are quite a few more i could do if i was actually down at the house but suffice to say they`re all pretty similar in layout most of the time.

---

### Post by Dustin2128 on 2010-07-07
interesting idea for a thread

---

### Post by Penguin Guy on 2010-07-07
This thread could be quite useful.

---

### Post by doorknob60 on 2010-07-07
It won't let me change the width of the columns, and since I have a chroot I have a lot of mountpoints, so you can't see the sizes and stuff, but oh well, you can tell that stuff by looking at the graph thing :P

[IMG]http://i26.tinypic.com/344oy20.png[/IMG]

---

### Post by MooseDog on 2010-07-07
great idea, really interesting stuff.  

in my pic, the sdb drive is my windows install.  grub2 is fantastically easy to configure to play nice with its neighbors, which is why this disk is first in the boot order.

---

### Post by White Rasta on 2010-07-09
[IMG]http://farm5.static.flickr.com/4137/4777384292_fe9d899a9e.jpg[/IMG]

---

### Post by papangul on 2010-07-09
Three primary partitions are reserved to be boot partitions.

---

### Post by cj.surrusco on 2010-07-09
My setup is kind of a mess at the moment since I just set up software RAID 5.

sda- First partition is the first RAID, second is an old Ubuntu install that I'm still transferring settings/data from.

sdb- First partition is the second RAID (Don't know why it comes up as 'unknown'), second is the boot partition for the RAID setup, and third is a data partition.

sdc- First partition is the last RAID, second is my Windows XP partition.

---

### Post by fancypiper on 2010-07-09
```
Fri Jul 09 11:45 AM phil@tinwhistle ~ $ df
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              20G   13G  6.1G  68% /
/dev/sda3             896G  667G  184G  79% /home
/dev/sdb1             147G   56G   84G  41% /pub
/dev/sdc1             147G   92G   48G  66% /home/phil/Music
/dev/sde1             147G  121G   19G  87% /pub/storage
/dev/sdd1             230G  177G   42G  81% /home/phil/Videos/more
```
I think I might be able to cram one more drive in this box.

---

### Post by fancypiper on 2010-07-09
Dupe!

---

### Post by Austin25 on 2010-07-09
Here's mine. I don't think I need quite that much swap with 4GB of RAM, but I'm glad I don't need my Windows partition anymore.

---

### Post by Matti L on 2010-07-09
This is my perfect partitioning (until I change my mind).

---

