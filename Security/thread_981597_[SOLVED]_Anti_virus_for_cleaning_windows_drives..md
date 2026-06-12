---
title: "[SOLVED] Anti virus for cleaning windows drives."
date: 2008-11-13
forum: Security
---

### Post by indiapavan on 2008-11-13
Ubuntu has been more than a close friend to me till now. I know it will continue to be in the future too. But I still dual boot into Windows XP to play games and use some particular developing applications. It sucks. The whole OS is infected. And when I try installing ANY anti virus in windows, the system restarts. The guy who wrote the virus is quite intelligent. Are there any suggestions on what I can do?

Also, I installed the ClamTK virus scanner provided by Ubuntu. It asks for a root login to update the virus signatures file. How do I login to root? Is it required? Or is there any other way I can update the signatures file? Thank you in advance to any help.:)

---

### Post by randy78 on 2008-11-13
If you were to bring this computer to me to fix, I would back up your data, perform a data wipe on the partition and re-install Windows.

To update Clam, in a terminal, type: sudo freshclam

---

### Post by aysiu on 2008-11-13
Reinstall. That's the only way to know for sure that it's all gone.

---

### Post by oldsoundguy on 2008-11-13
clone the ENTIRE drive (ALL PARTITIONS) to a new drive 
(I use an Apricorn setup and their EASY GIG software and go USB) .. 
use almost any good AV to scan the cloned drive out of the existing computer (don't boot to it, just plug it into a usb port on a clean computer  .. 
clean it with stuff living on the c drive on that clean computer ... you can tell the programs what to clean up and where it is located.  Be sure to run SUPERAntiSpyware, Glary Utilities, Malwary Bytes also. AND maybe Spybot Search and Destroy and A Squared Free.
Then wipe the infected drive in the infected computer and clone the clean version back. (all partitions)
Then install SUPERAntiSpyware, Spyware Blaster and Spyware Guard along with AVG or Avast as an AV program (ClamWin is a great scanner but it is not a real time protector in the free version) in your Windows partition.  
Your Linux partition will just go back as it is.

Easy Gig works ALL platforms, so no issue there .. I have cloned several Linux drives with it and never had a problem with it.

---

### Post by CholericKoala on 2008-11-13
You could even use Ubuntu to partition off another XP and install the antivirus in there, then run the sweep across your current XP which would be a slave drive and not affect the new one.  Good luck.

---

### Post by indiapavan on 2008-11-14
> **randy78 said:**
> If you were to bring this computer to me to fix, I would back up your data, perform a data wipe on the partition and re-install Windows.

To update Clam, in a terminal, type: sudo freshclam

Thank you very much. That fixed the problem. :)

---

### Post by randy78 on 2008-11-14
You're welcome :)
Please mark as solved by using the Thread Tools tab near the top of the page :D

---

