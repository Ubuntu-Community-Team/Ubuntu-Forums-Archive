---
title: "Help on setting up server!!"
date: 2008-02-06
forum: Windows
---

### Post by obdata on 2008-02-06
Hello,

I know this isn't the best forum to be posting Windows stuff, but I like this one the best!

We recently bought a used SuperMicro SuperServer 7043M-6, with 2 3.06 Ghz Xeon processors, 2 GB RAM, an Adaptec 3210S RAID controller, and 4 36 GB Hitachi SCSI drives. I want to install Windows XP Pro SP2, but it seems the hard drives are not being recognized. The server had been setup as RAID 5, and thats how we want it too. I deleted the RAID 5 array and tried to create a new one, but it said there are no RAID capable HBAs or no free devices. I also got Windows to install partly, but it said there was a missing file on bootup, and I tried to just reinstall it, but now it wont recognize my drives again.

BTW: Part of the problem is that I've never setup a RAID system before:(

Hopefully someone can help!!

---

### Post by LaRoza on 2008-02-06
Do you have the SCSI drivers for XP?

---

### Post by obdata on 2008-02-06
Yes, I selected in the Windows setup to install those from a floppy.

BTW. The Adaptec Setup utility didn't even recognize the drives, so I'm guessing that drivers wont make any difference? The drives were wiped clean, it came without any OS, so I'm installing from the ground up.

---

### Post by dca on 2008-02-07
Try reading this how-to on installing Windows XP....
 
[http://www.theeldergeek.com/clean_installation_of_windows_xp.htm](http://www.theeldergeek.com/clean_installation_of_windows_xp.htm)

---

### Post by obdata on 2008-02-11
OK, got it running, just a cable plugged in wrong on the RAID controller.

---

