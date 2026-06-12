---
title: "Esata Vs USB 3.0 - a quick test -enjoy!"
date: 2011-11-10
forum: The Cafe
---

### Post by jonnny_j22 on 2011-11-10
Hi all, just spent an evening setting up my brother's brand new shiny computer for him, and despite being made pretty jealous that the computer it's replacing is probably better than my old xp box I refuse to give up on, I did get the opportunity to test something I've been wondering - how much faster is USB 3.0 against Esata? Skip to the bottom to avoid my method and waffling!

As I saw the opportunity to do this test whilst setting up their PC, and didn't plan it, I should point out there are a few flaws in the tests I did - 

Firstly the drives used weren't new - a pair of WD 5000GB 7200 drives that have just finished a three year service in a RAID 1 array as the primary drives of their old PC. I also forgot to check their cache size, and whether they were SATA I or II, but as I remember setting up the raid array three years ago it seems safe to assume they were SATA I.

I also didn't think to check the information regarding the host computer's HDD. I know it was a 128GB SSD split evenly between Ubuntu and Windows 7 (both 64bit). I did however check the target drive - a 3TB WD Caviar Green, Which I understand (from googling just now) is a 5400 drive, but does support the higher transfer speeds and is connected directly to the motherboard at SATA1.

Also aside from noticing that there was 12GB of ram, I didn't think to get it's specs - though I'm sure we can assume it's ddr3. The processor was an i7, but I can't testify to 4/6 core.

Finally as I didn't plan to share this information, and just did it out of interest, whilst I wrote down my average speeds, I didn't think to use benchmark  - so no high/low or screen shots I'm afraid.
 


What I did do -
Whilst this is obviously not scientific! I think it gives a real world example. So may be of interest. I plugged the old HDDs into their identical caddies (which support both USB 3.0 and Esata) and connected these to the media card/multi port bay on the computer (it had multicard slots, an Esata port, and 2 USB 3.0 ports, and connected to PCIe on the motherboard) 

Next I used Gparted to format both drives in FAT32 (a single partition on each drive as after the test they will just be used as external drives connected to a PCI RAID card)

Finally the tests - I picked a nice big file - a 20.4GB VHD residing on the internal WD green drive and copied it to the first external drive via Esata. Then I copied it back. I repeated this with drive 2 then repeated the whole process with the drives connected to one of the USB 3.0 ports. 

I did do it staright after restarting Ubuntu, with no other apps open, but nothing disabled, I also did not disconnect any of the USB devices connected to the other (motherboards USB2.0 ports) - mouse, keyboard, printer, a third external hdd (not used in tests) I may have forgot one but I think that's it. 

I timed the transfers with my wristwatch - starting from when I clicked 'paste' and ending when the copy window closed (not accurate enough I know but like I said, it only just occurred to me to share this info. Oh yeah and I used my phone's calculator to work out the MB/s (remembering that a GB is 1024MB!)

Anyhoo the speeds-

Internal drive to external drive Via Esata
Test 1 - 48.6MB/sec
Test 2 - 46.2MB/sec

External drive to Internal drive via Esata
Test 1 - 44.2 MB/sec
Test 2 - 41.4 MB/sec

Internal drive - external drive via USB 3.0
Test 1 - 41.0 MB/sec
Test 2 - 38.8 MB/sec

External drive to internal drive via USB 3.0
Test 1 - 36.1 MB/sec
Test 2 - 33.5 MB/sec

I don't think it was scientific enough to draw conclusions... but I'll let you draw your own.

---

### Post by vehemoth on 2011-11-10
I too have been wondering this as eSATA doesn't seem to be that popular. Thanks for the info anyway

---

### Post by vcrpcant on 2012-05-01
Thanks!:)

---

### Post by koleoptero on 2012-05-01
From the data it seems that the bottleneck was the drives or their controllers, judging from the numbers you got vs the speeds the protocols themselves boast. But it does give a nice conclusion: they're the same unless the drive+controller used is super-fast. :)

---

