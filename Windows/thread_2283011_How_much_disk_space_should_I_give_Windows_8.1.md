---
title: "How much disk space should I give Windows 8.1?"
date: 2015-06-18
forum: Windows
---

### Post by t0p on 2015-06-18
Recently got a new laptop.  It came with Windows 8.1 installed, but I plan to make it a Windows 8.1/Ubuntu 15.04 dual-boot.  I don't plan to use Windows very much (my previous computer came with Windows 7, which I logged into maybe 10 times over 2 years); and the HDD has 1 TB space...  But I *do* want it to be workable, just in case...

Sooo... can anyone advise me how much of my disk space I should give over to Windows 8.1?  Cheers.

---

### Post by dino99 on 2015-06-18
cant answer directly, but as the w8.1 installation is already done, you can shrink the free space to get room for ubuntu. Load the windows live tool (to get an unmounted system) and let about 15 % of free space to allow w8.1 breathing (mainly for the cache & tmp files). As windows needs to be installed at the biginning of the hdd, dont move the first partition, only shrink the partition(s); ubuntu can be installed where you want, it never complaint.

---

### Post by chideock on 2015-06-18
I just clean loaded, on a new 120gb ssd, win8.1 pro - with firefox, chrome, adobe acrobat, and bonjour service AND Kodi the space used was 23.1 gb. After that it would be up to you.

---

### Post by Duck_Dude on 2015-06-18
If your new computer has 1TB of space, do as dino99 said in regards to partitioning and just leave Windows with ~100GB.  That'll be TONS and you'll never use the rest up with Ubuntu.

---

### Post by ajgreeny on 2015-06-18
I would highly recommend that you create the Win8 recovery DVDs then start by defragging Win8 a couple of times. Now shrink the Windows partition using Windows own disk management tool (you'll have to find that yourself as I don't know, and do not have Windows any more).  I don't know what the "windows live tool" is, and I've never heard of that, but it may be worth investigating; as I say, I don't use Windows any more.

Then let Windows run chkdsk a couple of times to be sure that it still boots OK.

Now you can think about installing Ubuntu, but bear in mind that you will probably need to understand UEFI and all that it means before you jump into installation.
[UEFI - Ubuntu Documentation]("https://help.ubuntu.com/community/UEFI")

If  were you I would also think about installing 14.04 which is supported until 2019, not 15.04 which has only 7 months of support remaining.  14.04 is extremely good, very stable, and is undoubtedly my choice at the moment, and unless your hardware needs 15.04 for some item I think 14.04 is the better OS.

---

### Post by oldos2er on 2015-06-18
Moved to Other OS Support, Windows.

---

