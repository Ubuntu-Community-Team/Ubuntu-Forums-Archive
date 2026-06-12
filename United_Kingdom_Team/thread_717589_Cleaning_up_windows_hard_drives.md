---
title: "Cleaning up windows hard drives"
date: 2008-03-07
forum: United Kingdom Team
---

### Post by g7mjv on 2008-03-07
Hi People

l often repair PCs for people.. Usually l end up removing their hard drives, adding them as a slave to my windows machine and then runing various anti-virus and anti-spyware progs to clean them up.

l want to dispense with windows on my home machines but still need to be able to do the above..

Any suggestions please

---

### Post by twin_57103 on 2008-03-07
I do a lot of PC repair, too, but don't remove the hard drives (as long as the OS is functional, I just work directly on that machine).  Have you tried setting up your utilities under Wine?  I wonder if that would work.  Otherwise, perhaps a virtual copy of Windows under VMware?  The programs needed for this are exclusively Windows utilities because that's where they're needed.

Side question...have you found a good free registry cleaner?  The one I use is proprietary, so I have to install it, run it, then remove it.  I'd love to have one I can leave on the computer.  What I've got in mind is pretty black-box - you click a button, it scans, then recommends x number of changes and you click OK (most of the users of these computers need that level of simplicity).

---

### Post by Cybergod on 2008-03-07
> **twin_57103 said:**
> Side question...have you found a good free registry cleaner?  The one I use is proprietary, so I have to install it, run it, then remove it.  I'd love to have one I can leave on the computer.  What I've got in mind is pretty black-box - you click a button, it scans, then recommends x number of changes and you click OK (most of the users of these computers need that level of simplicity).

I also repair PC's and I always install [ccleaner ]("http://www.ccleaner.com/")on them.  It does have a registry cleaner, just check it out and see for yourself.

---

### Post by twin_57103 on 2008-03-07
I came across CCleaner a few months back.  I haven't used it much, but I'll see about using it on future projects.  Thanks!

---

### Post by UBUSNAFU on 2008-03-07
Try [http://www.eusing.com/free_registry_cleaner/registry_cleaner.htm](http://www.eusing.com/free_registry_cleaner/registry_cleaner.htm)
It should clean things up for you. It's free and they have the right attitude.

---

### Post by Cybergod on 2008-03-07
> **UBUSNAFU said:**
> Try [http://www.eusing.com/free_registry_cleaner/registry_cleaner.htm](http://www.eusing.com/free_registry_cleaner/registry_cleaner.htm)
It should clean things up for you. It's free and they have the right attitude.

What's the right attitude?

---

### Post by g7mjv on 2008-03-08
l also use ccleaner and it certainly seems to do the job

---

### Post by cybervegan on 2008-03-20
I have often used ntfstools to repair borked xp disks (recovers unbootable volumes far better than windows recovery console). I also use clamav to de-louse them - try out the excellent "insert live" cd. On many occasions, I've set up Ubuntu on the machine (multi-boot) and told the user they have that as backup if (when) windows fails again.

You wouldn't be able to easily use wine to run windows clean-up programs on a windows volume under linux, because wine emulates windows - even the C: drive is emulated (i.e. fake - it's just a hidden subdirectory). The registry you'd end up cleaning is the wine one, not the one on the disk you are trying to clean up (wine also emulates this - it's stored in a text file).

To be honest, the only way to be sure you have thoroughly de-loused an infested windows box is to wipe the hard disk and reinstall. Contemporary spy-ware is so polymorphic that it's almost impossible to definitively say you've removed every bit of mal-ware. Of course, the ultimate fix is to get rid of windows entirely and upgrade to a system with proper security and no real problems with malware. I think you know what I mean.

-cybervegan

---

### Post by Cybergod on 2008-03-20
> **cybervegan said:**
> Of course, the ultimate fix is to get rid of windows entirely and upgrade to a system with proper security and no real problems with malware. I think you know what I mean.

-cybervegan

Amen to that :)

---

