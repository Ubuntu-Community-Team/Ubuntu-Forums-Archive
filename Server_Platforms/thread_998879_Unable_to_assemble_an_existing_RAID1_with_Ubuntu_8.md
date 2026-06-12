---
title: "Unable to assemble an existing RAID1 with Ubuntu 8.10 - 64bit"
date: 2008-12-01
forum: Server Platforms
---

### Post by andy80 on 2008-12-01
Hi all,

this is my PC configuration:

/dev/sda1   WindowsXP
/dev/sda2   Ubuntu 8.10 - 64bit

/dev/sdb1   / of Ubuntu 8.10 - 32bit in RAID1   (/dev/md0)
/dev/sdc1   / of Ubuntu 8.10 - 32bit in RAID1

/dev/sdb2   /home of Ubuntu 8.10 - 32bit in RAID1   (/dev/md1)
/dev/sdc2   /home of Ubuntu 8.10 - 32bit in RAID1

since I've installed Ubuntu 8.10 64bit, I'd like to use the same /home partition, so I don't have to duplicate my documents.

I've installed mdadm on Ubuntu 64bit: sudo apt-get install mdadm
In the attachment you can see my mdadm.conf file, anyway there are two lines that make me think the array is recognized:

```

# definitions of existing MD arrays
ARRAY /dev/md0 level=raid1 num-devices=2 UUID=5c7c967b:58c2a816:7ff42eed:7c82eb40
   spares=1
ARRAY /dev/md1 level=raid1 num-devices=2 UUID=594efe5c:7ee2560b:86bd34d3:2fc2d4bd

```

If I try to assemble the array I get an error:

```

andy80@andy80-desktop-64:~$ sudo mdadm --assemble /dev/md1 --config=/etc/mdadm/mdadm.conf
mdadm: error opening /dev/md1: No such device or address

```

and /proc/mdstat doesn't exist!

Anyway mdadm can see the two partition:

```

andy80@andy80-desktop-64:~$ sudo mdadm --examine --scan -c partitions
ARRAY /dev/md0 level=raid1 num-devices=2 UUID=5c7c967b:58c2a816:7ff42eed:7c82eb40
   spares=1
ARRAY /dev/md1 level=raid1 num-devices=2 UUID=594efe5c:7ee2560b:86bd34d3:2fc2d4bd

```

How can I fix this problem?
I've found an [howto]("http://ascendwiki.cheme.cmu.edu/Installing_Raid_1_on_Existing_Ubuntu_Server") that tell me to use this command: 

```

sudo mdadm --create --verbose --auto=yes /dev/md0 --level=1 --raid-devices=2 /dev/sdb1 /dev/sdc1

```

but I'm worried about destroying all my data, giving a --create to an existing array!

Have you any idea to resolve this problem?

On my Ubuntu 32bit, I've all these modules loaded:

```

andy80@centurion:~$ lsmod | grep raid
raid10                 30592  0
raid456               135184  0
async_xor              11392  1 raid456
async_memcpy           10112  1 raid456
async_tx               15312  3 raid456,async_xor,async_memcpy
xor                    23688  2 raid456,async_xor
raid1                  30080  2
raid0                  15488  0
md_mod                 93724  8 raid10,raid456,raid1,raid0,multipath,linear

```

but these modules are not automatically loaded in Ubuntu 64. Could this be the problem?

Thanks for your help and please let me know if you need more informations.

---

### Post by andy80 on 2008-12-01
I was able to assemble the RAID1, but I still have a problem.

1) I loaded the raid1 module manually: 

```
sudo modprobe raid1
```

2) I assembled raid1 in this way: 

```
sudo mdadm --assemble /dev/md1 --config=/etc/mdadm.conf
```

3) I mounted the /home in a temporary directory:

```
sudo mount -t auto /dev/md1 /mnt/hometemp
```

and I was able to browse my home directory!

At this point I've added this line to my /etc/fstab:

```
/dev/md1 /home ext3 relatime 0 2
```

and restarted my Ubuntu 64 bit. During boot I get an error: system says it cannot find /dev/md1. Off course! It doesn't load raid1 module automatically :(

Why Ubuntu doesn't load it at startup? What's wrong with my configuration?

Thanks again!

---

### Post by obg123 on 2008-12-01
I wouldn't worry so much about mdadm.conf. How did you create the arrays in the first place?

I would start with something like:

```
mdadm -Av /dev/md0 -l1 -n2 /dev/sdb1 /dev/sdc1
```

What reply do you get from that?

Edit: Oops. - Obsolete I guess...

---

