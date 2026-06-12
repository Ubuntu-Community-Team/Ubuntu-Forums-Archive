---
title: "Missing - Swap Partition ??"
date: 2008-06-26
forum: Server Platforms
---

### Post by zaarch on 2008-06-26
This is the terminal output to :sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xed1f86f7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          31      248976   83  Linux
/dev/sda2              32       19457   156039345    5  Extended
/dev/sda5              32       19457   156039313+  8e  Linux LVM

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x208eb01c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121601   976760001   83  Linux


So, if I understand correctly my system current does not have a swap partition...

is this possible?? I did a pretty standard install using 8.04 server edition...

or is there another way to see the swap..

I am running 8.04 Desktop on another machine..and fdisk -l does bring up the swap partition..

so does the server ed. not create a swap by default and you have to create one yourself...???

---

### Post by pastalavista on 2008-06-27
to see and manage your partitions:```
sudo gparted
```you can create a swap partition (but you must have some unallocated space so you may have to shrink another partition first)

if you haven't installed it:```
apt-get install gparted
```

---

### Post by hyper_ch on 2008-06-27
yes, no swap partition there... how did you install the server? seems to me like you chose manual partitioning there...

---

### Post by zaarch on 2008-06-27
> **pastalavista said:**
> to see and manage your partitions:```
sudo gparted
```you can create a swap partition (but you must have some unallocated space so you may have to shrink another partition first)

if you haven't installed it:```
apt-get install gparted
```

using 8.04 server ed. gparted out of question..no existing X server. thanks for the reply though. ;)

---

### Post by zaarch on 2008-06-27
> **hyper_ch said:**
> yes, no swap partition there... how did you install the server? seems to me like you chose manual partitioning there...

if i remember correctly (not a good scenario)...i did guided partition..>> using the whole hard drive...

so i assumed that that i should have a swap..

now..i already have a lot of stuff ( vms, file server, web server) running of this machine..and ...

i dont want to try to create a swap and have it go wrong..and then have to re do everything..

whats the best possible / safest way to create swap via CLI..

--- on a funny note..

i created a vm ..did a server install..thought..may be if i dont get a swap partition again..maybe i can try adding one on the vm and if it crashes..no problem..

just my luck ..my vm ( 8.004 server)..had the swap this..time..

looks like i have to create swap on my production server....and all i have is one shot..

Any help would be appreciated !! Thanks.

---

### Post by hyper_ch on 2008-06-27
> **zaarch said:**
> if i remember correctly (not a good scenario)...i did guided partition..>> using the whole hard drive...
Guided will create a swap...

> **zaarch said:**
> i dont want to try to create a swap and have it go wrong..and then have to re do everything..
Resizing is fairly safe BUT there's always a chance something goes wrong... safest method would be to put a new harddisk in it and make a swap partition on there...
However I'd try to resize.... if you have a Desktop cd, boot the server with that one, then install gparterd (if necessary) and resize /dev/sdb1 a bit... I'd resize that and not the ext3 lvm partition...

Format the newly emptied room to linux swap.

If that works, then add an entry to your /etc/fstab like this:

```

/dev/sdX    none         swap   sw

```

---

### Post by zaarch on 2008-06-27
could it be possible that there is an existing swap partition...but during the actual booting of the server..it fails to be loaded ??

---

### Post by unixbills on 2008-06-27
I don't think you could even get it started without swap.

Go look at /proc/swaps.  You can use "fdisk".  Be carefull and do not change anything.  "print" will print the table.

```

desktop:~# fdisk /dev/sda

The number of cylinders for this disk is set to 9726.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help): print

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41ab2316

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            9478        9726     2000092+  82  Linux swap / Solaris
/dev/sda2            8262        9477     9767520   83  Linux
/dev/sda3   *        4128        8261    33206355   83  Linux
/dev/sda4               1        4127    33150096    5  Extended
/dev/sda5               1        3951    31736344+  83  Linux
/dev/sda6            3952        4127     1413688+  82  Linux swap / Solaris

Partition table entries are not in disk order

Command (m for help): q

```


```

desktop:~# cat /proc/swaps
Filename                                Type            Size    Used    Priority
/dev/sda6                               partition       1413680 0       -1

```

Bill

---

### Post by hyper_ch on 2008-06-27
why shouldn't you be able to boot without swap?

---

### Post by unixbills on 2008-06-27
I just wouldn't have thought you could.  I wouldn't know why you would want to.  

Is this a normal Linux thing to be able to run without any swap space?

---

### Post by unixbills on 2008-06-27
OK I pounded out all of my swap from fstab and it boots.  It doesn't even seem to notice.  

(What happens when you need it?)

Bill

---

### Post by zaarch on 2008-06-27
well i am no expert..but i believe a swap is the linux version of the windows page file..

when the ram becomes full..rather is about to become full..processes are moved from ram to swap/page file..

so as to free up more ram...without shutting down the processes..

its therefore possible to have a working linux without swap as long as it has ram.

---

### Post by mrpeenut24 on 2008-06-28
Yes you can run linux without swap space, although it's not advised.  I ran Suse for two years without it.  I'd do what hyper_ch said and use a desktop cd and gparted.  If you don't have one handy, you can download the [GParted LiveCD]("http://gparted.sourceforge.net/livecd.php") (it's a bit smaller/quicker to download than the Ubuntu livecd).

---

### Post by consoko on 2008-06-28
Can you use a partition manager on hirent boot Cd to create a new swap?

---

### Post by mrpeenut24 on 2008-06-28
I don't know if Hiren's bootcd has many tools for linux.  I remember using it a bit for windows, but I'm not sure about linux.  [This]("http://www.sysresccd.org/Main_Page") cd is also a pretty good disk manager cd.  But again, I'm not sure about Hiren's.  I think most windows partition managers don't include tools for linux file systems.  If you want, you can look up the tools that are on there and see.

---

