---
title: "Netbooks do not require swap partitions?"
date: 2011-03-08
forum: The Cafe
---

### Post by PatrickMoore on 2011-03-08
I was reading an article regarding linux distributions on netbooks and I was perplexed by the following

> One word of caution: You can put any distribution on your netbook, but it’s not advised. Why? Because of the nature of the netbook, you need to avoid too many writes to the RAM drive and you don’t need a swap partition. So you’ll want to favor distributions that offer a version specifically for the netbook. You can use a regular distribution, especially if your netbook uses a standard hard drive — but you may have some problems down the road

I figured that a netbook was basically a less powerful notebook pc. I would love some input on this subject. Are you running a netbook if so what is your experience?

---

### Post by NightwishFan on 2011-03-08
To be honest, I would want a swap partition/file in either case. New SSDs are unlikely to fail. Space would be the only consideration.

In the event you run out of ram, a swap partition will keep the out of memory killer from wiping out gnome to keep that 18000x18000 pixel image in memory. :D

---

### Post by Chronon on 2011-03-08
That makes no sense to me.  Some netbooks use SSDs instead of HDs, but this doesn't seem to have any bearing on the passage you quoted.  

No idea what they mean by "avoid too many writes to the RAM drive".  I thought RAM drives were only commonly used when running from a LiveCD.

---

### Post by aG93IGRvIGkgdWJ1bnR1Pw== on 2011-03-08
I haven't used a swap partition in 6 years. All they do is allow poorly written programs to abuse your HDD/SDD.

---

### Post by PatrickMoore on 2011-03-08
I have always had a swap partition. that is why this article has really confused me. I want a netbook but I want to run a full fledged linux distro. Arch or Ubuntu would be my intention so should I have a swap? I would assume so

---

### Post by JDShu on 2011-03-08
I think what its trying to say is that you want to minimize writes to the hard disk (unless its SSD I guess) in order to use less power.

---

### Post by meborc on 2011-03-08
I usually have a swap partition, BUT turn the swap off by default... meaning that it is not used unless I specifically allow it. That gives me control over when my HDD is used and the option to have extra 2 gig ram space when needed.

I have never used a SSD so can't really comment on that

---

### Post by PatrickMoore on 2011-03-08
maybe I am misreading the article, but I Still think the article is confusing. I have run linux for a while now and this is contradicting the way i have run my system for over 3 years. although I normally run a typical laptop

---

### Post by wyliecoyoteuk on 2011-03-08
Most SSDs have wear levelling incorporated, so a swapfile is not too much of an issue, and you can fine tune the "swappiness". The main fear is that repeated writes to the same area of the SSD will cause it to fail prematurely. Of course, if you have a hard disk, it is immaterial.
Unlike certain other OSes, Linux does not use the swap file much anyway, unless you are really short on ram, its main use seems to be hibernation.
I run my netbook without a swap file, and have no problems other than hibernation doesn't work.

---

### Post by amauk on 2011-03-08
This depends on when the article was written, because with early SSDs you had to be quite careful how you wrote to them

SSDs do have a limit on the number of times a specific "cell" (the SSD equivilent of HDD "sectors") can be written to

Early SSDs had no safeguards in place to ensure the same cell was not written to continuously

Later drives introduced "wear-levelling", where the drive's firmware would ensure that writes were spread out over the entire drive, and no single cell was hammered with writes
Wear-levelling means that SSDs now could easily out-live HDDs by many years

Even so, operating systems are still largely geared toward HDD usage by default, and certain kernel / filesystem tweaks may give you better performance when using SSDs (the argument to using distros specifically designed for netbooks)

I see no reason not to use a swap partition on an SSD netbook
I would have thought journaling filesystems were more of a concern than paging out to swap

---

### Post by NightwishFan on 2011-03-08
Ubuntu includes a feature called compcache which is handy for mobile/low power devices.
[https://wiki.ubuntu.com/Compcache](https://wiki.ubuntu.com/Compcache)

---

### Post by mikewhatever on 2011-03-08
The quote passage is complete nonsense, hope the rest of the article wasn't the same.

---

### Post by LowSky on 2011-03-08
To be fair netbooks often have slower drives if they are conventional Hard drives. so add slow Processor, plus last gen ddr2 800 RAM, plus slow speed HD you have a huge bottleneck.

Swap is pointless on any system with 2GB or more RAM anyway.

---

### Post by red_Marvin on 2011-03-08
The only way I can get
"you need to avoid too many writes to the RAM drive"
to make sense is if I assume the writer does not know or care about the
difference between SSD and RAM memory.

Technically it is a little blurred, because both RAM and SSD circuits are **r**andom **a**ccess **m**emory and **s**olid **s**tate.
However if it is a **d**rive depends on the implementation/use...

But RAM generally refers to DRAM or in some cases SRAM which have no write limit, and SSD's are usually built with non-volatile (NVRAM) of some sort
eg flash.

---

### Post by Paqman on 2011-03-08
> Because of the nature of the netbook, you need to avoid too many writes to the RAM drive

This person sounds a bit confused. There's no reason you'd want to avoid writes to a ramdisk, but it's pretty unlikely you'd be using a ramdisk on a netbook anyway.

What I suspect they're talking about is the early solid state drives that some netbooks (such as the eeePC 700s) had. Those lacked effective wear levelling, so reducing writes would increase reliability in the long term.

It's absolutely not an issue if your netbook has a traditional magnetic hard drive, or if you've fitted a decent SSD.

---

### Post by t0p on 2011-03-08
I have one of the early netbooks - an Asus EeePC 701, with a 4GB(!!!) SSD.  I don't bother with a swap partition.  But I have upgraded the memory to 2GB.  And my lil ol' EeePC zooms along quite happily.

---

### Post by 3rdalbum on 2011-03-08
If the netbook has 1 GiB of RAM or more, then chances are that no data will ever get put into swap anyway. Unless you're using your netbook for non-netbook-y things.

---

### Post by dh04000 on 2011-03-08
I don't believe in swap partitions either. The swap is just plain annoying..... why create a whole partition to save a few files in swap? Can't we just use the win/mac approach here and save to a swap file within our file system when ram usage exceeds physical memory?

---

### Post by aeiah on 2011-03-08
even if you wrote to your netbooks SSD constantly you're still more likely to sit on it or throw it away before the SSD wears out

---

### Post by aeiah on 2011-03-08
> **dh04000 said:**
> I don't believe in swap partitions either. The swap is just plain annoying..... why create a whole partition to save a few files in swap? Can't we just use the win/mac approach here and save to a swap file within our file system when ram usage exceeds physical memory?

if you want. the downside is that the swap space would be sat on a filesystem layer instead of a direct disk partition, and if you boot more than one version of linux you'd need more than one swap file.

the only advantage having a swap has for most people now is with hibernation functionality. if you dont use it then yea, dont bother with a swap partition/file.

---

### Post by HermanAB on 2011-03-08
A totally nonsense article.  You absolutely DO need swap space, since a netbook is a mobile device and you need it to suspend and hibernate when you close the lid.

If you are worried about writes to disk, stop the syslog daemon.

BTW, I'm writing this on my Lenovo S10e netbook.  It works purrrrrfectly with Fedora.

---

### Post by fuduntu on 2011-03-08
> **Paqman said:**
> This person sounds a bit confused. There's no reason you'd want to avoid writes to a ramdisk, but it's pretty unlikely you'd be using a ramdisk on a netbook anyway.

What I suspect they're talking about is the early solid state drives that some netbooks (such as the eeePC 700s) had. Those lacked effective wear levelling, so reducing writes would increase reliability in the long term.

It's absolutely not an issue if your netbook has a traditional magnetic hard drive, or if you've fitted a decent SSD.

Actually a ramdisk is quite handy on a netbook for /tmp and /var/log.  It allows the disk to sleep more often on battery, and reduces seek times for things like flash playback w/ firefox.

There is no reason not to use a ramdisk for these two fs locations, unless you are developing software or building ISOs (aka advanced usage).

---

### Post by uRock on 2011-03-08
My Netbook has a swap partition. IMO, anything with less than 2GB RAM needs a swap.

---

### Post by HermanAB on 2011-03-08
> What I suspect they're talking about is the early solid state drives that some netbooks (such as the eeePC 700s) had.

My Eee PC 701 still works perfectly.  SSDs are very hardy.

---

### Post by aysiu on 2011-03-08
> **aG93IGRvIGkgdWJ1bnR1Pw== said:**
> I haven't used a swap partition in 6 years. All they do is allow poorly written programs to abuse your HDD/SDD.
Same here. I've never run into a problem *not* using a swap partition, and I don't hibernate my computer (only put it to sleep). My netbook has 16 GB of SSD space, so I'm not going to waste any of that on a swap partition when I have 2 GB of RAM already.

---

### Post by aysiu on 2011-03-08
> **HermanAB said:**
> A totally nonsense article.  You absolutely DO need swap space, since a netbook is a mobile device and you need it to suspend and hibernate when you close the lid. Actually, what you just said it incorrect. A swap partition is needed for hibernation, not for suspend-to-RAM. I know this because I have been suspending-to-RAM for years without a swap partition.

---

