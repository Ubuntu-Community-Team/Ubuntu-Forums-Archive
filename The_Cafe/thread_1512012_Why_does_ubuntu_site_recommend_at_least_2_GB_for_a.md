---
title: "Why does ubuntu site recommend at least 2 GB for a bootable USB drive?"
date: 2010-06-17
forum: The Cafe
---

### Post by azangru on 2010-06-17
Hi! I've been navigating the Ubuntu.com site and was amazed at how pretty, novice-friendly and informative it's become. Anyway, I was surprised to see that to create a bootable USB stick it [recommends]("http://www.ubuntu.com/desktop/get-ubuntu/download") a stick with at least 2 GB of free space. Why is this? Isn't an Ubuntu .iso image just shy of 700 MB? Doesn't it fit on a 700 MB CD? Why won't a 1 GB stick be enough then?

---

### Post by alphaniner on 2010-06-17
Maybe to give you a comfortable amount of room to save files?  I dunno how Ubuntu's bootable USB installer works, but when I make bootable USBs I make a partition just big enough to hold the OS files and a second partition for persistent storage.

---

### Post by garvinrick4 on 2010-06-17
The Start up Disk Creator  will hold up to 4 gig of persistence (retain changes) and minimum for some sort or decent install they consider 2 Gig, I like 3.5 to 4 Gig for
a good install so like a 4 gig flash drive. A lot of the USB live creators have no persistence so only use the size of the .osi file, under 1 gig so you can use 1 gig flash drives.

---

### Post by C.S.Cameron on 2010-06-17
A 1GB flash drive should be ok for a non persistent install.
120 MB is the minimum size of the casper-rw persistence file.
most 1GB flash drives hold somewhat less than 1GB.

---

### Post by doas777 on 2010-06-17
its great that they are giving realistic min reqs. most companies seriously lowball the min specs to avoid scaring folks off, but the reality is that the min is not nearly enough. when your specs are unrealistic, you're gonna have a bad time.

---

### Post by azangru on 2010-06-17
Oh, I see, the persistent install. I just thought the most common scenario for a new user would be just to plug in the USB stick, boot from it, see that everything works and then install the system on the computer. I didn't consider that people might want to save their live sessions on the stick.

---

