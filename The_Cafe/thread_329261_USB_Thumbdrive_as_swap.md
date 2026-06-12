---
title: "USB Thumbdrive as swap?"
date: 2007-01-01
forum: The Cafe
---

### Post by d3v1ant_0n3 on 2007-01-01
Right, I'm putting this in the cafe, since it's not a request for specific help per se, just a wondering of mine.

I've used Vista a few times, and pretty much the only thing I *really* liked was Readyboost.

For those of you who haven't seen or read about it, Readyboost basically allows you to use USB memory sticks as system memory, rather than just storage. It's pretty neat.

Now, as far as I can work out, it essentially is using the memory sticks as a swap space, in a similar way as linux distros use a swap partition. So basically, is there any way that you can configure ubuntu to use a memory stick as swap?

---

### Post by FurryNemesis on 2007-01-01
I don't see why it wouldn't be possible. The way I'd try and do it would be as follows:

1. Use GPartEd (Gnome partition editor in the repos) or some other partition editor to format a usb stick to linux-swap FS. Then, with the alternate install CD, with the newly formatted stick plugged in, select your swap partition as the stick. Then make sure you've got the stick plugged in at boot time. 

Also you could probably skip the new install and just select the formatted stick as extra swap.

Can anyone who knows more about filesystems than me see any reason why this wouldn't work?

---

### Post by PriceChild on 2007-01-01
You could make a swap file on the usb disc (as opposed to swap partition) and use that in your fstab.

**HOWEVER** please be aware that flash drives have a limited number of writes to each bit... swapping could burn them out reasonably quickly :)

---

### Post by K.Mandla on 2007-01-01
Pricey's right, but given the cost of USB drives these days, you might not care. Or if you had a bunch of leftover drives that don't get used, you could burn them up that way. :rolleyes:

Methinks this might do the trick, but I'm just thinking out loud, so I'm probably wrong.

[LIST=1]
[*]Insert USB stick
[*]*sudo umount /dev/sdXY* #or whatever your stick is mounted as; I don't think you can shred and reformat a mounted stick
[*]*shred -v -n 1 -z /dev/sdXY*
[*]*sudo mkswap /dev/sdXY*
[*]*sudo swapon /dev/sdXY*
[/LIST]
Maybe? :-k Any help?

---

### Post by saulgoode on 2007-01-01
All of the USB memory sticks I have seen are *extremely* slow and would be a poor choice for swap space (on the order of 40 times slower than a hard drive). Granted, I have not investigated this in the last year but, if you are considering it, definitely examine the access speed.

---

### Post by JLB on 2007-01-01
definitely possible to do, but you'll wear that thing out fast as they only support a limited writes. I would not recommend it.

---

### Post by meng on 2007-01-01
The write-cycles limitation has always scared me off putting a swap partition on a flash drive. In fact, I don't even format journaled filesystems on flash drives for the same reason. I quite liked running an installed bootable PCLinuxOS on a flash drive for a while (it was the only way I could seriously run Linux at work).

---

### Post by tageiru on 2007-01-01
> **d3v1ant_0n3 said:**
> Now, as far as I can work out, it essentially is using the memory sticks as a swap space, in a similar way as linux distros use a swap partition.

No, it is more clever than that. Readyboost is used as a cache where memory pages are written to both the memory stick and to the harddrive. So when the kernel needs to retrieve a page it first attempts to load it from the usb-drive, which is faster for random reads than the harddrive, and if that fails it reads it from the harddrive so your system will not die horribly if someone yanks the drive from the usb slot or if the usb-drive fails.

Readyboost also encrypts the swap so that important data can't be read by someone else snatching the memory stick, which is really important as swap can contain sensitive stuff like encryption keys.

---

### Post by d3v1ant_0n3 on 2007-01-01
Thanks for the input guys. It was more a musing of mine rather than something I wanted to try.

---

### Post by BoyOfDestiny on 2007-01-01
> **JLB said:**
> definitely possible to do, but you'll wear that thing out fast as they only support a limited writes. I would not recommend it.

I want to question the benefit period. Is it noticeable, and are there any benchmarks (non MS funded)? 

I know that in general using hd swap is like 10,000x slower than RAM (I mean come on milliseconds seek times vs a few nano seconds with RAM nowadays) 

Although I've set Ubuntu to have a 2 gig swap on my laptop with 1 gig ram... I've yet to see my swap usage exceed about 19 kilobytes (I made it big for hibernate purposes, and out of habit, 2x was what I always used back in the day...) 

So I don't think the tech would benefit me...

So you have a flash thingy, limited writes (what if it's yanked out during use), using usb bandwidth?, drawing more power?, if it's encrypted the computational overhead and possible lag? 

Hopefully faster than a hard drive, but no way it's faster than RAM (correct me if I'm wrong)

Anyway, I'm one of those folks that is happy Ubuntu and apps use up RAM vs trying to stay in swap...

Also who is this tech targeted toward, high end machines with small amounts of RAM? Or what?

---

### Post by tageiru on 2007-01-01
> **BoyOfDestiny said:**
> Hopefully faster than a hard drive, but no way it's faster than RAM (correct me if I'm wrong)
Of course, but it is way cheaper. Microsoft stated a performance increase of about 10x in some cases which is plausible as harddrives suck at randomly distributed reads as they need to move the read/write arm all over the platters.

---

### Post by seijuro on 2007-01-01
aside from the limited writes to a usb thumbdrive since swap is intended to be used like extra memory it would be rather silly too, being that usb transfer speeds are much slower.

---

### Post by smoker on 2007-01-01
i think it might be the way to go in the future as flash memory evolves, and am i right in thinking there are already hard drives being developed with a certain amount of flash memory built in, for buffer, or whatever. will try to find a link

did find this link though:[http://www.bitmicro.com/products_edisk_35_ide.php](http://www.bitmicro.com/products_edisk_35_ide.php)

---

### Post by Polygon on 2007-01-01
it would work, but it would be hella slow, i personally think that swap space on the hard drive is a better option... its faster and will be cheaper in the long run (using a flash drive as a swap space will burn it out VERY quickly.... if it gets used a lot). Not to mention that one can buy a 200+ gb hard drive for less then 100 dollars now a days

and what troubles me is that vista advertises this as a feature... whats the feature? that it requires so much memory and cpu that you need a flash drive for it to actually run fast?

---

### Post by 3rdalbum on 2007-01-02
1 gigabyte of RAM in my system. I've got a mixture of Gnome and KDE programs running, and no swap is being used. Back when I had 256 megabytes of RAM, it never used much more than 50 megabytes of swap.

From what I hear, Windows Vista uses swap from startup onwards even if you've got 1 gigabyte of RAM and aren't running any extra applications.

Therefore, we can conclude that the only Ubuntu systems that would benefit from it are running with less memory than Windows Vista will run with.

---

### Post by tageiru on 2007-01-02
> **3rdalbum said:**
> 1 gigabyte of RAM in my system. I've got a mixture of Gnome and KDE programs running, and no swap is being used. Back when I had 256 megabytes of RAM, it never used much more than 50 megabytes of swap.
That is only because the default vm setting is pretty conservative of swapping out process mapped pages when memory is needed for page cache. The vm system is always balancing whether untouched process mapped pages should be swapped out when memory could be used to speed up IO. If you configure the kernel to prioritize page cache (echo "100" > /proc/sys/vm/swappiness) you would see much more swap usage.

In that case technology like Readyboost will be very useful as you can prioritize page cache without the downside of heavy disk activity when you are context switching.

---

### Post by saulgoode on 2007-01-15
According to [this discussion on TWiT.tv (This Week in Tech)](http://www.grc.com/sn/SN-068.htm), ReadyBoost is not intended to be used as "swap space" for Vista; but is instead a cache of system settings and libraries that are needed during boot. Putting these files on a thumbdrive is the proposed way of reducing the prolonged boot times that Vista experiences. 

This concept makes more sense to me than using a thumbdrive for swap.

---

### Post by golem3 on 2007-01-15
> **K.Mandla said:**
> Pricey's right, but given the cost of USB drives these days, you might not care. Or if you had a bunch of leftover drives that don't get used, you could burn them up that way. :rolleyes:

Methinks this might do the trick, but I'm just thinking out loud, so I'm probably wrong.

[LIST=1]
[*]Insert USB stick
[*]*sudo umount /dev/sdXY* #or whatever your stick is mounted as; I don't think you can shred and reformat a mounted stick
[*]*shred -v -n 1 -z /dev/sdXY*
[*]*sudo mkswap /dev/sdXY*
[*]*sudo swapon /dev/sdXY*
[/LIST]
Maybe? :-k Any help?

Yep...I think that worked. Thanks. Although the shred takes a while, there isn't a way to "rm" the drive, right? (Still mastering all the BASH commands, so bear with me)

---

### Post by tarball on 2007-02-02
At the end of the day, if your system is using swap space on a regular basis you don't have enough memory.

However I can see how this might be popular if you can plug in a £20 2GB usb key and increase memory by 2GB.

---

### Post by Brunellus on 2007-02-02
this is a BAD IDEA.  

USB flash media has a limited number of write/rewrite cycles. Flash gets read and written to. . . lots.  Think about it.

---

### Post by kerry_s on 2007-02-02
I used a 512 usb key as swap for a year running DSL in ram on an ancient laptop with 500 mhz 256ram and no HD. I still have and use that same 512 usb key long after that laptop died.

---

### Post by PriceChild on 2007-02-05
Yeah I'm beginning to think that the limited writes has been overplayed a bit too much...

---

### Post by ReiKn on 2007-02-28
> **PriceChild said:**
> Yeah I'm beginning to think that the limited writes has been overplayed a bit too much...

With vista they at least claim that 
> 
Q: Won't this wear out the drive?
A: Nope. We're aware of the lifecycle issues with flash drives and are smart about how and when we do our writes to the device. Our research shows that we will get at least 10+ years out of flash devices that we support.

From a [FAQ]("http://blogs.msdn.com/tomarcher/archive/2006/06/02/615199.aspx").

I'm afraid though that using it as plain linux swap partition doesn't qualify as "being smart about how and when" writing..

---

### Post by pgoffa01 on 2010-10-22
I thought I would revive this old post because I'm doing this now.  

Ubuntu 10.10 Maverick Meerkat
[U]+1GB Ram
[/U]TOO SLOW

I'm taking a transcend 8 GB flash, doing a shred and creating a swap.  

I just want to mention that I used this drive as a flash drive for probably a year, then I used it for ready boost for another year and it still works great.  I'm an IT major in college and we were taught that a flash has at least 10,000 write cycles on average and could be significantly more as long as the drive is not oft subject to direct sunlight etc...

Just a thought....

---

### Post by sgosnell on 2010-10-22
Yes, flash memory has a somewhat limited number of writes (reads cost nothing, just writes), but that number is so large that you would have to make constant write/erase/write cycles, as fast as your computer can do it, 24/7, for years before you would wear one out.  With 2GB USB drives costing about $5US, who cares if it does wear out?  They will be cheaper by that time, so I can buy another without worrying about it.  The main drawback to using a USB flash drive as swap is the slow speed, but if you can live with that, it's easy enough to do.  On my netbook, with 1GB of RAM, swap almost never gets used.  I only have a swap partition in the event I ever use hibernate, which I don't normally do, but if the battery gets really close to dying, it's set to hibernate, and that needs the swap space.  I don't really worry about wearing out the SSD with swap, but if I did, I would vastly prefer wearing out a cheap USB drive instead of my SSD.

---

### Post by andrewabc on 2010-10-22
> **pgoffa01 said:**
> I thought I would revive this old post because I'm doing this now.  

Ubuntu 10.10 Maverick Meerkat
[U]+1GB Ram
[/U]TOO SLOW

I'm taking a transcend 8 GB flash, doing a shred and creating a swap.  

I just want to mention that I used this drive as a flash drive for probably a year, then I used it for ready boost for another year and it still works great.  I'm an IT major in college and we were taught that a flash has at least 10,000 write cycles on average and could be significantly more as long as the drive is not oft subject to direct sunlight etc...

Just a thought....

Umm, are you on desktop or laptop? How fast is hdd? It is possible that hdd is faster than thumbdrive. Although I guess seek time and random read/write is faster on usb thumb drive.

Unless you have lots of apps open, 1gb ram should be enough without having to worry about swap slowing computer down. You can tell ubuntu to [not use much swap](https://help.ubuntu.com/community/SwapFaq#What%20is%20swappiness%20and%20how%20do%20I%20change%20it?).

---

### Post by pgoffa01 on 2010-10-23
It doesn't use that much swap but I have to use some proprietary software that does.  I'm a computer networking major in college working with C**co products.  Pretty big GUI's for lan management and Sec Admin practice.  Also love Virtual Box so i can test drive all the new distros.  I just like to have that extra elbow room just in case.

---

