---
title: "zRAM on Ubuntu 13.04 x86/x86_64."
date: 2012-12-10
forum: Ubuntu Development Version
---

### Post by serdotlinecho on 2012-12-10
zRAM will be default on 13.04 x86/x86_64 installation? 
I read that it's good for netbook and machines with low amounts of system memory and what is pros and cons of zRAM?

[http://www.phoronix.com/scan.php?page=news_item&px=MTI0NjQ]("http://www.phoronix.com/scan.php?page=news_item&px=MTI0NjQ")

---

### Post by zika on 2012-12-10
> **serdotlinecho said:**
> zRAM will be default on 13.04 x86/x86_64 installation? 
I read that it's good for netbook and machines with low amounts of system memory and what is pros and cons of zRAM?

[http://www.phoronix.com/scan.php?page=news_item&px=MTI0NjQ](http://www.phoronix.com/scan.php?page=news_item&px=MTI0NjQ)Been there with AMD64, 3G (now 4) and ran out of there with cuts and bruises... Nothing life threatening but would not get into these bushes again... I even have swap turned off... But who knows, if a need emerges...

---

### Post by pressureman on 2012-12-10
I have a Thinkpad T530 and 12GB RAM... the only reason I even have a swap partition is because the Ubiquity installer seems to have a bug that won't allow you to proceed past disk partitioning without a swap partition.

Hard disks are cheap, but SSDs aren't, so if/when I replaced the 500GB HDD with an equivalent size SSD, I don't want to lose any space to swap. I'd rather use a swap *file* that I could easily delete/move/resize, in the extremely unlikely event that my system would run out of RAM.... or use zRAM.

---

### Post by grahammechanical on 2012-12-10
This sounds to me that the memory requirements of Ubuntu are going to creep upwards.

> The zRAM capability is mostly a win for netbooks/mobile devices and other cases with very restricted amounts of RAM. 

How big or small is "very restricted?"

Regards.

---

### Post by jfernyhough on 2012-12-10
In theory, zRam has the largest benefit on low-RAM systems with a CPU that can cope with the compression. zRam should always be faster than on-disk swapping for devices that have a suitable disk but the biggest gains should be for SSD-based mobile devices. These don't have swap capability (normally) so when they run out of memory bad things happen.

In my experience of zRam in Ubuntu, my 1749 has enough RAM that it's never (noticably) used. On my 311c the CPU can't cope and bogs down - this is despite the fact that 3GB should be enough to run the system normally (I'll have to try it again, though, as I've just replaced that multiple-upgrade with a clean quantal install).

On my Desire Z, zRam appears to make little difference. On the one hand, I can run more programs. On the other, it interferes with Android's memory management meaning more apps simply run more slowly as "stale" memory isn't reclaimed as often. It also has the effect of slowing the phone when in a low memory condition, rather than killing a background application. This can effect functionality such as receiving phone calls. Disclaimer: I run unofficial CM builds (currently CM10+) so YMMV.

Overall though, if done properly zRam should provide a benefit to most users without them noticing it. It should provide an extra safety zone for low memory conditions without requiring horrible disk churning. The benefits, though, will be limited to newer machines. Older ones are better off without it.

---

### Post by serdotlinecho on 2012-12-11
> This sounds to me that the memory requirements of Ubuntu are going to creep upwards.

Maybe because they will increase the number of lens and scopes installed by default in Ubuntu 13.04? Err...100 scopes? 
Uninstall and get rid of the scopes and lens that I don't want would be painful...Is there an options for me during the installation to choose which scopes and lens should I install like a checkbox or something?

---

### Post by BertN45 on 2012-12-21
Zram is installed by default in the Zorin OS Core 6, It works fine and I like it. On my 1.5MB PC there is no real limit anymore for the number of programs I can run at the same time. Also I can run more virtual machines. They reserve half the memory as compressed swap-drive and compression is in general better then 1:2. By the way this Zorin gives a real nice imitation of Windows 7.

Zorin OS Lite 6 has the same zram and I installed that on a 448MB Dell Inspiron 1000 for my brother in law, who constantly had problems with XP on that machine. The machine has a 2.2 gHz processor, so that is a good combination for zram. The Lite version is basically Lubuntu with some minimal tweaks, but because of zram, I prefer it for the moment.

I hope it will be introduced in 13.04 and I think Xubuntu and Lubuntu really need it. The coming period I will try to install zram in my Ubuntu 12.04 main OS.

---

### Post by jerrylamos on 2012-12-21
> **pressureman said:**
> I have a Thinkpad T530 and 12GB RAM... the only reason I even have a swap partition is because the Ubiquity installer seems to have a bug that won't allow you to proceed past disk partitioning without a swap partition.

Hard disks are cheap, but SSDs aren't, so if/when I replaced the 500GB HDD with an equivalent size SSD, I don't want to lose any space to swap. I'd rather use a swap *file* that I could easily delete/move/resize, in the extremely unlikely event that my system would run out of RAM.... or use zRAM.I seem to be able to "bull" past the install swap question and install without a swap.  My SSD isn't that big and I have several ubuntu partitions on it, latest raring update, previous raring that was working, 12.04.1 LTS, and a linuxmint for when I get tired of wrestling unity and want to get something done. 

On this netbook with 1G memory and dual processors, I just did free which said it had  95756 used swap likely from doing an apt-get update, apt-get dist-upgrade.  I've thought about adding more memory but on my Acer Aspire 1 that involves removing the mother board.....what do I expect for $250.

---

### Post by zika on 2012-12-22
[http://www.phoronix.com/scan.php?page=news_item&px=MTI1MDM](http://www.phoronix.com/scan.php?page=news_item&px=MTI1MDM)

---

### Post by cariboo on 2012-12-22
> **jerrylamos said:**
> I seem to be able to "bull" past the install swap question and install without a swap.  My SSD isn't that big and I have several ubuntu partitions on it, latest raring update, previous raring that was working, 12.04.1 LTS, and a linuxmint for when I get tired of wrestling unity and want to get something done. 

On this netbook with 1G memory and dual processors, I just did free which said it had  95756 used swap likely from doing an apt-get update, apt-get dist-upgrade.  I've thought about adding more memory but on my Acer Aspire 1 that involves removing the mother board.....what do I expect for $250.

You probably aren't ***bulling*** past the fat that you aren't installing a swap partition for each installation. If you already have a swap partition setup for your stable installation, all the other installations, whether they are on the same hard drive, or others, will automagically use your already configured swap partition. 

In other words, you don't need a separate swap partition for every install you have on your system. I'm currently using 1 2GiB swap partition for 4 installs on this system I'm using.

---

### Post by serdotlinecho on 2012-12-23
> **zika said:**
> [http://www.phoronix.com/scan.php?page=news_item&px=MTI1MDM](http://www.phoronix.com/scan.php?page=news_item&px=MTI1MDM)

No.... [https://flippa.com/2850785-phoronix-com-pr5-linux-compatible-hardware-reviews-adsense-and-cpm-monetized](https://flippa.com/2850785-phoronix-com-pr5-linux-compatible-hardware-reviews-adsense-and-cpm-monetized) :(

---

### Post by pressureman on 2012-12-23
> **serdotlinecho said:**
> No.... [https://flippa.com/2850785-phoronix-com-pr5-linux-compatible-hardware-reviews-adsense-and-cpm-monetized](https://flippa.com/2850785-phoronix-com-pr5-linux-compatible-hardware-reviews-adsense-and-cpm-monetized) :(

Can't say I'm surprised. Phoronix occasionally has some interesting articles, and is often the first to publish breaking news, but the articles get a bit repetitive, and Michael's benchmark/testing methodology leaves a bit to be desired. Some of the graphs portray highly accurate, useless information.

The Phoronix site itself is pretty unbearable without an ad-blocker. Were it not for AdBlock Plus, I wouldn't visit the site at all. So, I'm not surprised at all that Larabel is selling out.

---

### Post by pressureman on 2012-12-23
> **jerrylamos said:**
> I seem to be able to "bull" past the install swap question and install without a swap.

I just tried installing on my old T500 with a fresh daily image from today. The partitioner still warns me that I haven't configured a swap partition, and asks me if I want to go back to the partitioning menu. If I click "No", it takes me back anyway. If I click "Continue", it proceeds with the install (which didn't happen a few weeks ago when I installed on my T530).

So... still buggy, but at least not as bad as before. Next time I reinstall the T50 (probably in April, with the official release), it'll be with no swap partition :)

---

### Post by sgage on 2012-12-23
> **pressureman said:**
> I just tried installing on my old T500 with a fresh daily image from today. The partitioner still warns me that I haven't configured a swap partition, and asks me if I want to go back to the partitioning menu. If I click "No", it takes me back anyway. If I click "Continue", it proceeds with the install (which didn't happen a few weeks ago when I installed on my T530).

So... still buggy, but at least not as bad as before. Next time I reinstall the T50 (probably in April, with the official release), it'll be with no swap partition :)

What's the matter with just installing w/swap and deleting it afterwards?

---

### Post by pressureman on 2012-12-23
> **sgage said:**
> What's the matter with just installing w/swap and deleting it afterwards?

Nothing, except that it's an unnecessary step as a result of a bug in the installer. The point of a beta testing is to find/classify/fix bugs, is it not?

Besides, if I took your approach, I'd also have to use gparted to extend the remaining partitions on the disk, after deleting the swap partition... or tolerate unused/unpartitioned space on an expensive SSD.

---

