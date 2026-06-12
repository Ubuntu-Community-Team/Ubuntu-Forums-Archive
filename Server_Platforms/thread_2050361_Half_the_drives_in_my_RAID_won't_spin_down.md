---
title: "Half the drives in my RAID won't spin down"
date: 2012-08-30
forum: Server Platforms
---

### Post by jickerson on 2012-08-30
Hi, I just installed a fresh version of 12.04 server and have everything configured. When i set the spin down settings on hdparm.conf everything appeared to go fine. However, when i checked the status of the drives later, it appears that 2 of my drives (bot seagate barracudas) spun down successfully while 2 drives (both WD caviar blacks) didn't. I can spin them down using hdparm -y, but not using the normal -S switch. 

Also, I read that you may need to use -B, but when i tried it, i got the following:

    setting Advanced Power Management level to 0xfe (254)
    HDIO_DRIVE_CMD failed: Input/output error
    setting standby to 1 (5 seconds)
    APM_level      = not supported


There is nothing touching the drives, and I followed this link to make sure SMART wasn't interrupting the process. [http://zackreed.me/articles/60-spin-down-idle-hard-disks](http://zackreed.me/articles/60-spin-down-idle-hard-disks)

---

### Post by sandyd on 2012-08-31
drives don't support advanced power management. as a result, the -S flag won't work

---

### Post by rubylaser on 2012-08-31
> **sandyd said:**
> drives don't support advanced power management. as a result, the -S flag won't work

+1. The disks won't spin down if they don't support advanced power management.  I have added a note to my tutorial to explain this limitation to future viewers.  One option could be to roll a script that uses iostat using a tempfile to track disk activity over time, and then spin it down with the -y option once that threshold has been reached.

---

### Post by jickerson on 2012-08-31
> **sandyd said:**
> drives don't support advanced power management. as a result, the -S flag won't work

So there aren't any packages that will monitor disk usage and spin down the disks after inactivity like hdparm does? Just surprised that "relatively" new drives like these wouldn't support this kind of power management. I mistakenly thought that all modern drives had this capability as long as they had SMART

---

### Post by rubylaser on 2012-08-31
What model are the WD drives and how are they connected to the computer (motherboard SATA head, PCI / PCIe card, USB, ESATA, etc)?

---

### Post by jickerson on 2012-08-31
> **rubylaser said:**
> What model are the WD drives and how are they connected to the computer (motherboard SATA head, PCI / PCIe card, USB, ESATA, etc)?


The drives that won't spin down are WD Caviar Black 1 TB (WD1001FALS) drives. They are connected via the SATA header on the motherboard, as are the other two drives that do spin down.

---

### Post by ian dobson on 2012-09-01
Hi,

I purchased several wb 2Tb green drives some time ago for a Backup array on my main server. Even though all the drives where the same model, 2 of them didn't power down. 

After several emails with wd support they recommended I update the firmware, and since then all the drives power down when idle.

So maybe a firmware update might work for you.

Regards
Ian Dobson

---

### Post by jickerson on 2012-09-03
> **rubylaser said:**
> +1. The disks won't spin down if they don't support advanced power management.  I have added a note to my tutorial to explain this limitation to future viewers.  One option could be to roll a script that uses iostat using a tempfile to track disk activity over time, and then spin it down with the -y option once that threshold has been reached.


I had an idea on a script that might do the trick, but wanted to bounce it off of you guys before i learned enough to actually write the script (I know python, but my linux skills are next to nothing).

Leveraging the fact that two of the drives do follow the -S flag of hdparm and spin down as expected, while the other two can be spun down using the -y flag, can i write a script that simply does a check of the well-behaved drives using hdparm -C periodically (every 10 minutes or so) and if it reports that the drives are inactive then it executes hdparm with the -y flag on the other two drive. Will checking the status of the drives reset their spin-down clock? Is there any other reason why doing so would not be advisable? 

Thanks!

---

### Post by rubylaser on 2012-09-03
I would check as ian dobson mentioned for a firmware update, because that could allow the disks to spin down with the -S flag.  If there is no firmware update, then you could use the -C flag as that won't wake your disks up from being spun down. If a firmware update can fix this for you, that's by far the easiest and most reliable way to make this happen.

What is the Make and Model number of your 2 hard drives that won't spin down?

---

### Post by jickerson on 2012-09-10
Sorry it took so long to respond. The drives are Western Digital Caviar Blacks, WD1001FALS-00J7B0. I've been digging around, and have become a little worried that I'll need windows to update the firmware. The problem is that i don't have a windows machine with SATA and i don't think it is going to let me flash the firmware if the drives are connected to an external usb enclosure.

---

### Post by rubylaser on 2012-09-10
> **jickerson said:**
> Sorry it took so long to respond. The drives are Western Digital Caviar Blacks, WD1001FALS-00J7B0. I've been digging around, and have become a little worried that I'll need windows to update the firmware. The problem is that i don't have a windows machine with SATA and i don't think it is going to let me flash the firmware if the drives are connected to an external usb enclosure.

Those drives should be able to be spun down.  I have (4) WD1001FALS of those in my home backup server. How are they connected to your machine?  I'm wondering if it's an old PCI card or something similar, that is preventing it from using it's whole command set.

---

### Post by jickerson on 2012-09-10
They are connected via the motherboard's onboard SATA ports, which is the same way the other two drives are connected (which can be spun down). The motherboard i'm using is a ASROCK E350M1.

---

### Post by rubylaser on 2012-09-10
Maybe the difference is in the version number.  Mine are WD1001FALS-00U9B0, so they are slightly different than yours.

---

