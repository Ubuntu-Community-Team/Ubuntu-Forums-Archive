---
title: "Just installed 16 GB RAM on Vivid B2..... 32 GB swap? WHAT"
date: 2015-04-17
forum: Ubuntu Development Version
---

### Post by jimmy-frydkaer on 2015-04-17
Maybe it's just me, but shouldn't my swap file be equal to the amount of installed RAM?

Not that it eats up my hdd but it seems like a LOT of swap space....

---

### Post by lastopier on 2015-04-17
Not really. I had 12 GB of swap and it was huge overkill. It really depends on what you intend to do. But 16 GB of RAM is enough to handle most of standard work. 8 GB should be more than enough for standard usage.
Here is a nice article about swap; it says that only laptops which are shut down to hibernate need that much:
[http://www.cyberciti.biz/tips/linux-swap-space.html](http://www.cyberciti.biz/tips/linux-swap-space.html)

Personally, I never hibernate my laptop. Unlike windows, it loads up quickly so there is no need to do so.

---

### Post by grahammechanical on 2015-04-17
That is a very good article.

I have not noticed any requirement to increase the size of my swap partition because I was installing Vivid Vervet. The swap partition = double the RAM is not something special to 15.04.  My swap partition has stayed the same size since I created it a few years ago.

When I compare Ubuntu's handling of memory in 12.04 with all releases from 14.04 onward I have noticed a big improvement resulting in less use of swap. It could be down to improvements in the Linux kernel.

As the article points out the size of the swap partition only becomes an issue if we are using "suspend to disk" or hibernation. And that would be true even if we were installing 14.04.2 and not 15.04.

Regards.

---

### Post by slickymaster on 2015-04-17
[http://www.cyberciti.biz/tips/linux-swap-space.html](http://www.cyberciti.biz/tips/linux-swap-space.html)

Good article indeed.

---

### Post by QIII on 2015-04-17
It's a 7 year old article, though.  We weren't thinking in terms of 16GB consumer machines at the time.

My two cents:

My primary desktop, at 16GB, has no swap at all.  I don't hibernate it (always on) and if I ever get anywhere near 16GB (when not running VMs, which is why I have that much memory), then I have other problems best not covered over with swap.

For a machine with that much memory, hibernation requires that the state of the entire memory be saved, so 16GB + 10% (rule of thumb for resource management) is plenty.  Any more is a waste.

---

### Post by jimmy-frydkaer on 2015-04-17
Great article 

But now I'm confused - I trashed my system while fooling around with a kernel upgrade. Milk some times wet the floor.

After reinstall of my system I looked in Sysinfo, who told me that my swap now is only 16 GB and now equals the amount of physical RAM.

I have not partitioned the disk manually, the installer did that.

What strikes me is that, in theory, the same installer, used same disk on both installs, partitions the hdd differently.

Only difference in this install is that it isn't a dual-boot install Debian/Ubuntu but clean Ubuntu.

Why the double swap space in dual-boot but not on a clean install?

Why does a dual-boot system need the bigger swap space? 

You only load one OS while the other sits idle/doesn't live, as long as you do not mount the other systems disk - then that system still doesn't "live".

If the partition table were held in swap, swap would not show up as 100% free - That is a 32 GB swap partition on 16 GB RAM system - 100% free swap space means, at least to me, an idle/sleeping swap?

My System does never go into suspend I always shot it down, if I have to, most of the time I just power of my monitor while the system rolls on. 

Kind of lost on this.

---

### Post by Bashing-om on 2015-04-17
jimmy-frydkaer; Hello;

If it is of any help to you; I run with 4 Gigs of ram and I quad boot ( testing, troubleshooting ) 'buntu's . I have a very small swap - just in case - that I share among all the installs: Just point /etc/fstab to the common swap.
```

sysop@1404mini:~$ sudo fdisk -lu
[sudo] password for sysop: 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00065f5e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    10242047     5120000   83  Linux
/dev/sda2        10244096    30724095    10240000   83  Linux
/dev/sda3        34207742   976771071   471281665    5  Extended
/dev/sda5       443795688   443811689        8001   82  Linux swap / Solaris
/dev/sda6       443811753   597409154    76798701   83  Linux
/dev/sda7       597409792   976771071   189680640   83  Linux
/dev/sda8        34207744    44447743     5120000   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x502a9772

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   976768064   488384001   83  Linux

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0002ea65

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048   102402438    51200195+  83  Linux
/dev/sdc2   *   102404096   204804095    51200000   83  Linux
sysop@1404mini:~$

```

I rarely even touch swap . Be aware 'swap' is only used when ram gets tight OR one hibernates the machine ( I too do not ).

[INDENT][INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT][/INDENT]

---

### Post by Cavsfan on 2015-04-17
This article from Mar 17, 2015 [https://wiki.archlinux.org/index.php/Suspend_and_hibernate](https://wiki.archlinux.org/index.php/Suspend_and_hibernate)

Says that you do not need a swap file at all if you are going to just suspend to RAM. Only if you are going to hibernate do you need a swap file.

I had a 1GB swap file for years just for kicks, never seen 1% of it used. I recently restructured my partitions and set up a 4GB swap file to match my 4GB of RAM and tried to suspend.

It seemed to work but when I tried to move the mouse, etc. it was dead. I had to press the power on button and it booted up.

So, I think a swap file is a waste today. Maybe for servers, which I know nothing about. I only suspend, never hibernate anyway because it is like turning it off and if I wanted to shutdown I would.

---

### Post by ventrical on 2015-04-17
I have 16GB of ddr ram and my swap space is 3.2 GB Three point Two GBs!!

Regards..

---

### Post by DogMatix on 2015-04-17
> **Cavsfan said:**
> This article from Mar 17, 2015 [https://wiki.archlinux.org/index.php/Suspend_and_hibernate](https://wiki.archlinux.org/index.php/Suspend_and_hibernate)

Says that you do not need a swap file at all if you are going to just suspend to RAM. Only if you are going to hibernate do you need a swap file.

It seemed to work but when I tried to move the mouse, etc. it was dead. I had to press the power on button and it booted up.
.

Yeah! that's pretty much my experience of hibernate with linux. I've always employed the 2X RAM to SWAP approach, out of habit more than reason.

---

### Post by cariboo on 2015-04-17
I running 16GB on my desktop system, when I did the initial install I created a 2GB swap partition, as far as I remember, it's never been used. Running:

```
free -m
```

always looks like this:

```
free -m
             total       used       free     shared    buffers     cached
Mem:         15945       3857      12088         65        265       2034
-/+ buffers/cache:       1557      14387
**Swap:         1999          0       1999**
```

---

### Post by jimmy-frydkaer on 2015-04-18
Later today I will, as an experiment, reinstall my system, reduce the amount of swap space manually to see if this has any impact on performance at all.

My guess is that reducing the swap space to a minimum, 0.25 GB, will force the use of physical RAM in everyday use. Physical RAM is fast as lightning compared to swap operations - Would the Ubuntu Installer complain if I choose no swap at all?

The reason for that question is that I, at an earlier time, think it was around 8.04 or so, tried to drop the swap all together, but the installer wouldn't let me.

---

### Post by zika on 2015-04-18
> **jimmy-frydkaer said:**
> Later today I will, as an experiment, reinstall my system, reduce the amount of swap space manually to see if this has any impact on performance at all.
My guess is that reducing the swap space to a minimum, 0.25 GB, will force the use of physical RAM in everyday use. Physical RAM is fast as lightning compared to swap operations - Would the Ubuntu Installer complain if I choose no swap at all?
The reason for that question is that I, at an earlier time, think it was around 8.04 or so, tried to drop the swap all together, but the installer wouldn't let me.Swappiness behavior is easily controlled via appropriate [switch]("http://en.wikipedia.org/wiki/Swappiness").
Swap can be enabled or disabled on fly etc...
Last thing that should be done is reinstall.

---

### Post by jimmy-frydkaer on 2015-04-18
Yes I know it can be turned on and off "on-the-fly" but in my opinion it still takes knowledges to do so.

The question is more like: "Do we really need that partition on the powerful desktop computers who does not go into suspend or hibernate?" Servers with really heavy workload, maybe, but what good does swap do on modern desktop computers with 4+ GB RAM?

Don't get me wrong on this, I'm only interested in finding out if swap can be left out all together on computers for desktop-use alone.

As I wrote earlier to day I would reinstall my system to test what no swap would do.

System:
Intel Core i7x4 @ 3.4 GHz
16 GB DDR3 PC3 RAM @ 1600 MHz
Hitachi 1 TB hdd w. 32 MB cache
nVidia GeForce GT440 w/1.5 GB RAM

Clean install of Ubuntu Vivid Beta2 took 15 min. (manual partition of disk included).

Compiz + maver-theme.

System responsive and *fast*. 
Check in Sysinfo reveals 93% RAM free and no swap. So WHAT good does swap really do? Is swap only a leftover from yesterdays dinner table?

---

### Post by zika on 2015-04-18
> **jimmy-frydkaer said:**
> Don't get me wrong on this, I'm only interested in finding out if swap can be left out all together on computers for desktop-use alone.Why would I get You wrong? I do not use swap for quite some time, from the very moment I've got enough memory to do that. That is the sole reason I did respond to Your post... For the sake of fallback I do let OS to create it but I do use switches available to prevent it of interfering into my everyday work... I'm old enough to remember why EMACS is called that way and I do remember dreaming of not having to have swap... ;)

---

### Post by Cavsfan on 2015-04-18
I agree re-installing is not necessary. Install Gparted and turn swap off then delete it there. I believe that'll do the trick.

The only thing I'm curious about concerning not having a swap file is what do you do with your fstab file as it points to the swap file's UUID?

---

### Post by buzzingrobot on 2015-04-18
Swap needs to be there when a process makes a request for a memory allocation that cannot be satisfied from available RAM.  It doesn't need to be there until such a request is made.

That applies today just as much as it did 30 years ago when Unix machines had comparatively tiny RAM allocations and each machine expected to have multiple users on it simultaneously.

Today, we have orders of magnitude more RAM available to us, and it is a rare Linux machine, indeed, that operates as a multiuser system (few users seem even aware that it can).

The difference is that many of us routinely have so much RAM on desktops that swap is never used.

Using the swap partition for hibernation storage is a bit of a dual-use trick.  Otherwise, we'd just have special hibernation partitions.

I've tried those swappiness settings tricks and never seen any change one way or another. 

Also, I'm not sure I see how disabling swap will improve performance on a system that isn't using swap. Meanwhile, if a system is using swap, while disable it?  At that point, the only real solution is more RAM.

---

### Post by lastopier on 2015-04-18
> Check in Sysinfo reveals 93% RAM free and no swap. So WHAT good does swap really do? Is swap only a leftover from yesterdays dinner table?
Sort of. I have 4GB of ram and my linux mint somehow decided to not use that 12GB of swap I gave him. DEAD. But that is 1/4 of your RAM and it took me a week to realize (to run out)
It is very useful on my 11 years old laptop with 512MB of RAM

---

### Post by zika on 2015-04-18
> **Cavsfan said:**
> I agree re-installing is not necessary. Install Gparted and turn swap off then delete it there. I believe that'll do the trick.
The only thing I'm curious about concerning not having a swap file is what do you do with your fstab file as it points to the swap file's UUID?Gparted?```
/usr/bin/sudo /sbin/swapoff -a
```
As for /etc/fstab, just leave it untouched. Those couple of GB does not make so much difference and You can (at any need) with```
/usr/bin/sudo /sbin/swapon -a
```get Your swap back in a click... ;)
Sorry for all this I do prefer as small hammer as possible if any is needed at all.

---

### Post by ventrical on 2015-04-18
Here ..

---

### Post by QDR06VV9 on 2015-04-18
> **ventrical said:**
> Here ..

I like it;) +1

---

### Post by ventrical on 2015-04-18
:) hehehe .. I thought it would be funny..  and it is  :) lol

No offence intended...;)

---

### Post by Cavsfan on 2015-04-18
@zika - nice reply!

@ventrical - lol!

---

### Post by zika on 2015-04-19
> **ventrical said:**
> Here ..> **ventrical said:**
> :) hehehe .. I thought it would be funny..  and it is  :) lol
No offence intended...;)No offence taken:
[img]http://twistedsifter.files.wordpress.com/2010/08/carving-a-lead-pencil-tip.jpg[/img][img]http://twistedsifter.files.wordpress.com/2010/08/smallest-hammer-ever.jpg[/img][img]http://twistedsifter.files.wordpress.com/2010/08/mini-pencil-art-carving.jpg[/img]

---

### Post by zika on 2015-04-19
> **ventrical said:**
> Here ..> **ventrical said:**
> :) hehehe .. I thought it would be funny..  and it is  :) lol
No offence intended...;)No offence taken:
[IMG]http://twistedsifter.files.wordpress.com/2010/08/carving-a-lead-pencil-tip.jpg[/IMG][IMG]http://twistedsifter.files.wordpress.com/2010/08/smallest-hammer-ever.jpg[/IMG]
Indeed:[IMG]http://twistedsifter.files.wordpress.com/2010/08/mini-pencil-art-carving.jpg[/IMG]

---

### Post by ventrical on 2015-04-19
:) Awesome... :)

---

