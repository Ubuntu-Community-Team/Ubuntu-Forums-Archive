---
title: "Almost installed Windows 7 this evening..."
date: 2010-07-01
forum: The Cafe
---

### Post by beastrace91 on 2010-07-01
And then I discovered its 2010 and Windows still refuses to install to a GPT formatted drive. After over and hour of hunting around online all the HOWTOs I found suggested that I need to reformat the drive and install Windows 7 as the first partition, but I do NOT feel like setting up OSX again on my system.

Anyone know of a way to install 7 to a GPT formated drive that already has OSX on it with out wiping OSX? Or is 7 just a turd of an operating system like all past Windows versions?

~Jeff

---

### Post by NightwishFan on 2010-07-01
Do you just have OSX? I read somewhere there was a tool to set up dual boots. Boot camp?

---

### Post by TheNerdAL on 2010-07-01
> **NightwishFan said:**
> Do you just have OSX? I read somewhere there was a tool to set up dual boots. Boot camp?
Boot Camp helps.

---

### Post by kaldor on 2010-07-01
> **TheNerdAL said:**
> Boot Camp helps.

mmmmmmhm.

---

### Post by DoubleClicker on 2010-07-01
bootcamp doesn't support GPT partitions.  it map an MBR partition map on top of it.

---

### Post by SmittyJensen on 2010-07-01
> **beastrace91 said:**
> And then I discovered its 2010 and Windows still refuses to install to a GPT formatted drive. After over and hour of hunting around online all the HOWTOs I found suggested that I need to reformat the drive and install Windows 7 as the first partition, but I do NOT feel like setting up OSX again on my system.

Anyone know of a way to install 7 to a GPT formated drive that already has OSX on it with out wiping OSX? Or is 7 just a turd of an operating system like all past Windows versions?

~Jeff
No, that's what boot camp is for & works around AFAIK. just use it.

---

### Post by BenAshton24 on 2010-07-01
> **beastrace91 said:**
> Or is 7 just a turd of an operating system like all past Windows versions?

this :)

---

### Post by SmittyJensen on 2010-07-01
> **BenAshton24 said:**
> this :)
still has the same windows flaws, but it is faster than vista & has much more features than xp.

---

### Post by szymon_g on 2010-07-01
> **beastrace91 said:**
> Or is 7 just a turd of an operating system like all past Windows versions?

... but it's still more popular than all 10k of linux distros taken together (well... even Beta/RC was more popular on desktop than Linux) :)

---

### Post by beastrace91 on 2010-07-01
> **NightwishFan said:**
> Do you just have OSX? I read somewhere there was a tool to set up dual boots. Boot camp?

How about Multi-Boots? I have 10.04 on the system as well for obvious reasons. Was hoping to use grub2 as my boot manager after installing all the operating systems - ended up only getting OSX and Ubuntu on it though xD

~Jeff

---

### Post by NightwishFan on 2010-07-01
> **szymon_g said:**
> ... but it's still more popular than all 10k of linux distros taken together (well... even Beta/RC was more popular on desktop than Linux) :)

Yeah because they do not leaverage their already massive user base, and that does not change anything... Because the most popular things are always the best, just check out the most popular youtube videos! Yeah im done. The NT kernel still annoys me. The user experience is not my cup of tea but I have no room to judge. :)

---

### Post by v.cecchetto on 2010-07-01
I have dualboot lucid lynx + win7 and when i have time i wanna try to put macosx on my laptop (GPT partition, GRUB2 bootloader).

If you wanna install win7 on GPT you have to play dirty. Beside GPT partition table you have to create by yourself or by gdisk a MBR partition table ([http://www.rodsbooks.com/gdisk/hybrid.html](http://www.rodsbooks.com/gdisk/hybrid.html)), better if you study in deep what is a partition table before doing this. 

Remember also that linux partition can starts at every sectors, instead winXP partition have to respect CHS partition alignment, and for your happiness winVISTA and win7 have to respect instead 1MB alignment (=2048 sector or multiple like starting point for win7 partition). Try to respect also 4KB partition alignment for harddisk performance or for SSD harddisk. ([http://en.wikipedia.org/wiki/Logical_Disk_Manager](http://en.wikipedia.org/wiki/Logical_Disk_Manager))

A lot of things i know, sorry, but there aren't tool to help you if you mess things up with hybrid MBR and you have to provide by yourself, you have to know what are you doing. Gdisk is a great help. Gparted is good but have some bugs in partitioning ntfs partition like reserved microsoft partition, a flag that you can remove by hand with gdisk or you cannot install on those partition win7.

Yes GRUB2 is the right way to boot the system.

Sorry, no easy way. 

I spent a lot of time working to make all work, only because Microsoft guys doesn't 'want' to support GPT partitions yet (and GPT is much better than MBR), and force you to start the partition only at well specific sectors of your drive. Linux is another planet.

For your help my gdisk partitions:

GPT partition table:

Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 1250263694
Total free space is 0 sectors (0 bytes)

Number  Start (sector)    End (sector)  Size       Code  Name
   1              34             289   128.0 KiB   EF02  BIOS boot partition
   2             290          204799   99.9 MiB    0700  Linux/Windows data
   3          204800        98703359   47.0 GiB    0700  Linux/Windows data
   4        98703360       197406719   47.1 GiB    AF00  Linux/Windows data
   5       197406720       296110079   47.1 GiB    0700  Linux/Windows data
   6       296110080       592220159   141.2 GiB   0700  Linux/Windows data
   7       592220160      1250263694   313.8 GiB   0700  Linux/Windows data

MBR partitions:

Number	 Boot	 Start (sector)	 Length (sectors)	Type
   1	    	            1	      197406719 	0xEE
   2	   *	    197406720	       98703360 	0x07
   3	    	    296110080	      296110080 	0x07
   4	    	    592220160	      658043568 	0x0A

---

### Post by WinterRain on 2010-07-01
> **szymon_g said:**
> ... but it's still more popular than all 10k of linux distros taken together (well... even Beta/RC was more popular on desktop than Linux) :)

I hear a certain German leader was pretty popular too during the 30's and 40's. Popular doesn't mean good.

---

### Post by McRat on 2010-07-01
I almost installed Win7.
 
After 2 days I gave up and put Ubuntu on it.

---

