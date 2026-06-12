---
title: "Speeding up booting Ubuntu"
date: 2017-02-04
forum: Ubuntu, Linux and OS Chat
---

### Post by lammert-nijhof on 2017-02-04
In 2014 I bought a second hand desktop HP Compaq dc5850 (incl. Vista stickers) with a 80GB disk and installed Ubuntu 14.04 on it and later upgrade to 16.04. Somewhat later I took a 500 GB disk with my data and added that to the system. Yesterday I looked at the disk performance, because I thought about replacing the system disk with a SSD. The 80 GB disk speeds were 61/58 MB/s and 11 msec seek time.The 500 GB disk had the following numbers: 134/83 MB/s and 8 msec. [COLOR=#1D2129]I should have realized it earlier, the larger HDD are also automatically faster than the smaller ones. My system has 4 GB of memory and uses an AMD Phenom triple core processor of 2.3 MHz.[/COLOR] So I thought, let's try Ubuntu on the 500 GB disk. 

I reduced the size of the partition on the 500 GB disk and moved it to the right with gparted. I copied the OS to that free space also with geparted. Did rerun grub-install and update-grub and the new copy of the OS was nicely recognized and added to the menu. Whatever I did, it always loaded the old version of the 80 GB disk. After some searching I found, that I had to change the UID in /etc/fstab and in /boot/grub/grub.cfg.
I used find/replace and changed the UID and the drive/partition spec from 'hd0,msdos1' to 'hd1,msdos2'. Thus identifying the 500 GB disk and partition equaling to the last created OS partition sdb2. For the editing I used my dual boot with Ubuntu 17.04. 

[COLOR=#1d2129]In the end loading the OS, typing the password and loading Skype, Whatsie ([/COLOR][COLOR=#1D2129]Whatsapp) en Thunderbird (email) now takes 1 min 16 sec instead of 2 min 25 sec. With a SSD I could reduce it to under 30 seconds, but I'm happy now. The money for the SSD I will spend on the local 'Presidente' brewery, it buys me at least 25 liter of beer.

I still wondering to upgrade the memory from 667 MHz to 800 MHz, how much effective improvement would that bring? My SWAP partition is never used, so going at the same time to 8 GB would not bring anything. If you google for it, the estimate is 5% effective speed improvement.  Any suggestions?[/COLOR]

---

### Post by lammert-nijhof on 2017-02-05
Three more points to speed up the old bastard. I detected that the Dimms were put in the wrong spot, so the PC only used one memory channel instead of two. 

I installed zswap with the default values and did put the swappiness to 25. Linux starts swapping, if it gets close around 2.7 GB of used memory. The total is 3.6 GB. I left 900 MB more or less for zswap. It worked nice, the used RAM only increased slowly adding more programs close to and over that 2.7 GB boundary, while also the swap size increased. I would expect relatively fast, but it increased extremely slowly due to the compression. Probably it was compressing a lot of not used data memory with only zeroes in it. The disk with the SWAP- and 17.04 partitions did not move at all, but the swap in memory did grow to 150 MB or so. 

All values measured in real time with Conky.

---

### Post by mastablasta on 2017-02-06
install form mini.iso and add xfce, then add only the things you need. it should boot faster.

next - suspend it instead of turning it off. it should wake up faster.

you won't benefit from the increase in RAM unless you really need more ram and if you are using the current one regulary. 

are you trying to speed up the OS or just the boot? 

either way, you will hit some hardware limits. 

my winXP takes about 10 minutes to boot. after that it works really well. it takes much less in Linux but that is because many stuff i have in Win is not loaded there. various antivirus, firewall suites, daemon tools, updaters etc etc.

---

### Post by lammert-nijhof on 2017-02-06
mastablasta: The general idea is to get the best price/performance from Ubuntu and my HP5850. Yes in practice I often suspend the machine, but after I started using an USB keyboard the keyboard was blocked afterwards. Probably my USB/PS2 plug will solve it. Boot times are still important if you play also with Ubuntu 17.04 and we also have power breaks almost each day. I still have a free 15 GB partition, Maybe I try Xubuntu again.

 I don't really need more RAM, I use zswap that allows me enough flexibility. Normally I close programs I don't need in the next 5 minutes, old habit from the times of the 486 processor. I was only considering replacing the 667 MHz memory sticks with 800 MHz ones, that could help somewhat in e.g video editing times. My question is what does it bring in practice in speed improvement. If I google they talk about 5% improvement, that seems somewhat low for a 20% increase of the memory frequency.

---

### Post by mastablasta on 2017-02-07
many games that supposedly need at least a core i3 can still run well on my single core Athlon.

what i am trying to say her eis that these frequencies and numbers.... they don't always mean as much as they appear to. 

the most speed up you can still get is from hard disk. you already noticed that when you moved to what was likely an IDE disk with 5400 rpm to whta is likely a 7200 rpm disk. if oyu moved form IDE to sata the increase is even more noticable.

now as for the SSD - unless you need big system disk then, a 32Gb one should do. 6-8 Gb for the OS, add soem apps, you will be on 10, 12 Gb which give you plenty of space left. with ext for as i understand it is not good to have it 90% occupied but with this much space and data disk at hand you should be ok. 

power breaks are bad, but they do have UPS for that to shut it down gracefully, otherwise the only solution would be a generator or to turn it off. in which case boot time is important.

---

### Post by mörgæs on 2017-02-07
Hardware improvements is only part of the solution for getting a faster system. Installing a distro lighter than Ubuntu, which is one of the heaviest, is also worth trying.

I suggest that you install Mate or Lubuntu. The 16.04.2 release is expected in a few days.

---

