---
title: "swap partition problem"
date: 2008-06-11
forum: Server Platforms
---

### Post by Skyhighnemo on 2008-06-11
Hi All,](*,)
I just load Intel64 (HP ML350) with RAID 5 setup (hardware) with 3TB of SATA2 and 8.04server64bit, and the loading using the Ubuntu LVM partition manager on setup and install and it created 1TB of ext3 which auto partitioned that into /boot (250MB) and ext3/ for the rest, but the problem here is that it created a swap of 2TB which should have been only between 20-30GB.   The partition table is as /dev/cciss/c0d0 of 2.73TB and shows in GParted (yes I had to load Gnome min desktop for the computer person) who lives here and will be using this after I leave..  OK well after that in Gparted it further partitions it into two more /root being 250MB and /dev/mapper/comp_name-root (950GB) and dev/mapper/comp_name-swap_1 (1.8TB).  OK after all that..  here is my problem..  I tried to repartition the swap down to a 30GB (10GB RAM) .. but it will not let me do that..  I need to regain all that lost partition in /root (should be 2.7TB)..  How do I get passed the LVM problem...

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/mapper/Aus1-root
UUID=ef049e9c-ee1b-41a1-8e55-7aa5193baeba /               ext3    relatime,errors=remount-ro 0       1
# /dev/cciss/c0d0p1
UUID=fabf46fc-1d33-4a07-8cc5-311e607eae35 /boot           ext3    relatime        0       2
# /dev/mapper/Aus1-swap_1
UUID=35ce8458-abed-429a-afe9-254543e06934 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

Thanks for any help..

---

### Post by molotov00 on 2008-06-11
I'm noticing that people haven't answered your question. I don't know the answer, but I do know this:

Ask your question clearer next time. You only need to know how to resize a partition. That's the relevant part.

What errors are you encountering when you try the resize? The most important part of your question lacks the most detail...

---

### Post by Skyhighnemo on 2008-06-11
Hi,
I just wanted to let whomever know the complete problem.  In answer to your question.. 
Here is the bug report readout..
GParted 0.3.5

Libparted 1.7.1

Shrink /dev/mapper/Aus1-swap_1 from 1.80 TiB to 1.80 TiB  00:00    ( ERROR )
     	
calibrate /dev/mapper/Aus1-swap_1  00:00    ( SUCCES )
     	
path: /dev/mapper/Aus1-swap_1
start: 0
end: 3859873791
size: 3859873792 (1.80 TiB)
calculate new size and position of /dev/mapper/Aus1-swap_1  00:00    ( SUCCES )
     	
requested start: 0
requested end: 3859873289
requested size: 3859873290 (1.80 TiB)
new start: 0
new end: 3859873289
new size: 3859873290 (1.80 TiB)
check filesystem on /dev/mapper/Aus1-swap_1 for errors and (if possible) fix them    ( N/A )
     	
checking is not available for this filesystem
shrink filesystem  00:00    ( ERROR )
     	
create new linux-swap filesystem  00:00    ( ERROR )
     	
mkswap /dev/mapper/Aus1-swap_1
     	
/dev/mapper/Aus1-swap_1: Device or resource busy
check filesystem on /dev/mapper/Aus1-swap_1 for errors and (if possible) fix them    ( N/A )
     	
checking is not available for this filesystem
grow filesystem to fill the partition  00:00    ( ERROR )
     	
create new linux-swap filesystem  00:00    ( ERROR )
     	
mkswap /dev/mapper/Aus1-swap_1
     	
/dev/mapper/Aus1-swap_1: Device or resource busy

Device is busy because it is in use as I am typing and send this forum report..

---

### Post by molotov00 on 2008-06-11
"Shrink /dev/mapper/Aus1-swap_1 from 1.80 TiB to 1.80 TiB 00:00 ( ERROR )"

It looks like you are not shrinking? From 1.8 to 1.8 is no change. I'd do one change at a time, also. Shrink it first. If that works then grow another partition to fill free space.

Also, I didn't think you could be booted while it resized but I'm not 100% sure. Either way, your first error is noted above.

---

### Post by hyper_ch on 2008-06-12
swap partition of 30GB???

---

### Post by Skyhighnemo on 2008-06-13
Hi,:)
Yes good swap size is done in 2 (min) or 3 (best) times the RAM total..  Yes 9GB of RAM..  soon to be upped to 12GB to best suit our needs.. 
Any ideas on the decreasing of the swap space... ???

---

### Post by hyper_ch on 2008-06-13
you only need at least equal swap size to your ram when you want to hibernate... everything else above 2 gb swap is too much IMHO... but it depends what you do.

---

### Post by Skyhighnemo on 2008-06-13
Hi,
Here is some info (now it is the weekend and I have some time) I found on swap size.  I hope that it will be helpful.   As for use, this server will be used for medium size ERP and networked with three others..  It is meant to grow..  That's why I wanted the swap size to 30GB..  Many open user files at one time.. Need large swap.. Also we will be taking the RAM up as need to..  It can go to 32GB limit on this computer...  enjoy..

4.4.2. How large can my swap space be?

Currently, the maximum size of a swap partition is architecture-dependent. For i386, m68k, ARM and PowerPC, it is "officially" 2Gb. It is 128Gb on alpha, 1Gb on sparc, and 3Tb on sparc64. An opteron on the 2.6 kernel can write to a 16 Tb swap partition. For linux kernels 2.1 and earlier, the limit is 128Mb. The partition may be larger than 128 MB, but excess space is never used. If you want more than 128 MB of swap for a 2.1 and earlier kernel, you have to create multiple swap partitions (8 max). After 2.4, 32 swap areas are "officially" possible. See setting up swap for details.

footnote: "official" max swap size: With kernel 2.4, the limit is 64 swap spaces at a maximum of 64Gb each, although this is not reflected in the man page for mkswap. With the 64 bit opteron on the 2.6 kernel, 128 swap areas are permitted, each a whopping 16 Tb! (thanks to Peter Chubb for the calculation)

---

### Post by hyper_ch on 2008-06-13
well, if you have a good reason for that amount of swap then it's ok ;)

---

### Post by Skyhighnemo on 2008-06-13
Hi,
Just found out that GParted does not support LVM created drives..  Does any now and confirm that statement.  Some how it seems correct as I am having difficulty doing so..:(

---

### Post by Skyhighnemo on 2008-06-16
Hi All,
Does anyone know if any Gnome supported program will support LVM editing..??? Thanks...

---

