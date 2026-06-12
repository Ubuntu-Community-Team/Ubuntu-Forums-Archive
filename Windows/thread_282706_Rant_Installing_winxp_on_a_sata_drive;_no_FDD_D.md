---
title: "Rant: Installing winxp on a sata drive; no FDD :D"
date: 2006-10-23
forum: Windows
---

### Post by mahy on 2006-10-23
Hi folks, this is my personal experience with winxp.

I bought a laptop (Fujitsu Siemens Amilo Pro V2045) and found it's got a Czech version of windows. I like english all over my computer, so i decided to download a free retail version of winxp+sp2 from MSDNAA (legally!). I burnt the CD and booted it. To my astonishment, "no partitionable media found". So i went to F-S's website and searched for the drivers. I managed to download an exe file, but when i double-clicked on it, a popup told me it hadn't found any floppy disk drive to extract the drivers to. Would you believe it? That should've been designed for a machine without a fdd!! I had to install some virtual floppy drive to outsmart the crappy extractor and later moved the files to a USB pendrive. Next time i pressed F6 to "install a 3rd party scsci or raid driver". Well, it's 2006, but winxp doesn't recognize any usb drive! It told me plainly "no diskette found, unable to install drivers" (exact wording may vary).

I went on searching forums (nothing worse than forums full of windows-only geeks) till i finally came across nLite, which can 'slipstream' the drivers right into the installation disk. That's just what i did and it cost me one extra cd. After that the installation went smooth, until the first boot. Nothing was working! No sound, no wifi, no lan, no usb, no pcmcia, crap graphics only. It took me 2 more days to find all the necessary drivers, burn them onto cd and install to get everything working.

Actually, to do justice to Bill, i must say there was one feature that worked right out of box: an annoying popup, nagging me to activate the darn software! ](*,)

---

### Post by ShadowVlican on 2006-10-25
yeap..... even with SP2 they don't have native support for all the SATA controllers out there

in defense of windows though, i can install WinXP SP2 on my SATA2 drive just fine, but i'm using nVidia chipset that already works out of the box :)

i'm sure by SP3, you'll be able to do the same (i wonder when that is coming out... hahaha)

---

### Post by xlulux on 2006-12-15
just slipstream your drivers into the windows xp install cd ... there is a tutorial on how to do this online, but lemme warn you, its not easy.

---

### Post by meng on 2006-12-15
I reinstalled WinXP recently, and was hoping to share my experience although it's not an original one, so why not hijack someone else's thread instead of starting my own?

The short of it: Initial install took 40 minutes and required wiping my hard drive completely (good thing I had my linux partitions backed up), I'm guessing Windows doesn't like being installed on a logical partition but needs to be on a primary one (sigh). Two devices (video card and modem) NOT recognized out of the box but required separate driver downloads and installs. In the first 24 hours, there were FOUR rounds of updates, each requiring a reboot. (admittedly my starting point was XP SP1, because that's all I had) Total time for install - several hours.

When it came to reinstalling Ubuntu subsequently (from 6.10), the whole process took much less than an hour (with updates). All devices recognized out of the box.

Again, I admit this is not an original theme, but who the heck peddles this FUD about Linux being difficult to install?

---

### Post by smoker on 2007-01-02
weird thing is, i keep getting asked by windows gurus(!), "how did i get linux to detect my sata drives?" they find it hard to believe ubuntu detected them no prob and installed in about 30minutes!

most of them believed this sata driver thing would be remedied in vista, but i was given this link the other day:
[http://vistasupport.mvps.org/installing_raid_sata_drivers.htm](http://vistasupport.mvps.org/installing_raid_sata_drivers.htm)

who says they don't make it easy for windows vista users?

No. 1 - Turn your PC on!!!

---

### Post by KaroSHiv0n on 2007-01-02
Judging by a lot of these posts some of you have never had to instal windows? i do about 10+ a week at my current job, let me say, the amount of times i EVER see a windows install with ALL drivers already in is slim to none, unless its a old model of a huge selling system (some dells, once with a packard bell) usb and audio usually are the most common ones missing, if you have a seperate graphics card then it came with a disk, so it shouldent be an issue.
as much as i try to use linux for everything at home i dont think its fair to expect windows (or linux !) to have native support for *everyones* machine.

---

### Post by aberry5555 on 2007-01-03
I had this exact same problem the other day, it's a rediculously huge flaw in the windows installation. I had to do it on a friends newly built pc that had a floppy connector on the mobo but none on the PSU, I tried to rebuild windows and nearly got there but the iso editor I was using sucked. In the end I had to put two pc's side by side, one powering the other's floppy! Rediculous I tell you.

*thwomps MS on the head for deliberately outdating their products before selling them on*

---

### Post by Dr. C on 2007-01-05
> **aberry5555 said:**
> I had this exact same problem the other day, it's a rediculously huge flaw in the windows installation. I had to do it on a friends newly built pc that had a floppy connector on the mobo but none on the PSU, I tried to rebuild windows and nearly got there but the iso editor I was using sucked. In the end I had to put two pc's side by side, one powering the other's floppy! Rediculous I tell you.

*thwomps MS on the head for deliberately outdating their products before selling them on*

One option (I have not tried this but please don't laugh since this may actually work!) is to find an old 5.25in floppy drive, the corresponding media, and cable.  An old 286 or 386 is a suitable source! They use the standard as opposed to the mini power connectors. Install the 5.25in floppy in a PC that also has access to the SATA drivers. Transfer the SATA drivers to the 5.25 floppy media. Then move the 5.25in floppy drive to the new PC with the SATA drive and install the drivers from the 5.25in floppy. 

This also begs the question: Does Vista support 5.25in floppy drives since apparantly there is no native support for SATA?

---

### Post by Sunflower1970 on 2007-01-05
> **meng said:**
> I reinstalled WinXP recently, and was hoping to share my experience although it's not an original one, so why not hijack someone else's thread instead of starting my own?

The short of it: Initial install took 40 minutes and required wiping my hard drive completely (good thing I had my linux partitions backed up), I'm guessing Windows doesn't like being installed on a logical partition but needs to be on a primary one (sigh). Two devices (video card and modem) NOT recognized out of the box but required separate driver downloads and installs. In the first 24 hours, there were FOUR rounds of updates, each requiring a reboot. (admittedly my starting point was XP SP1, because that's all I had) Total time for install - several hours.

When it came to reinstalling Ubuntu subsequently (from 6.10), the whole process took much less than an hour (with updates). All devices recognized out of the box.

Again, I admit this is not an original theme, but who the heck peddles this FUD about Linux being difficult to install?

Just needed to say, Yup. When one of my hard drives crapped out in July and I had to buy a new hard drive it took me about a week to get the system up and running like it was before the crash. I took a Saturday and it took 16 to install the disk I had (SP1) and start the update process, and finding all the drivers.  (and now I'm starting all over with XP problems *sigh*--detailed in another thread)

On an older computer I installed Ubuntu this past Saturday. The Ubuntu install took less than an hour with all updates. And, although I'm just using it as a test system to learn Linux, it's been less painful than XP.

---

### Post by mysticrider92 on 2007-01-06
> **FineE said:**
> One option (I have not tried this but please don't laugh since this may actually work!) is to find an old 5.25in floppy drive, the corresponding media, and cable.  An old 286 or 386 is a suitable source! They use the standard as opposed to the mini power connectors. Install the 5.25in floppy in a PC that also has access to the SATA drivers. Transfer the SATA drivers to the 5.25 floppy media. Then move the 5.25in floppy drive to the new PC with the SATA drive and install the drivers from the 5.25in floppy. 

This also begs the question: Does Vista support 5.25in floppy drives since apparantly there is no native support for SATA?

I don't think there are that many people with working 5.25 inch floppy drives out there, and then you have to find a floppy in working condition, also, M$ might have already dropped support for something that old in exchange for the brand new technology EIDE (*gasp*). 

I have heard that XP MCE (and maybe Pro) comes with SATA drivers. I don't know if that is true, but it would be nice.

---

### Post by nsleiman on 2007-01-06
i got also fujitsu-siemes laptop and got the same difficulties installing XP. but mine worked with plugging in the usb memory stick with the sata drivers. now i only have ubuntu running,only the internal modem is not working. Ubuntu rocks :)

---

