---
title: "Computer won't boot to graphics and lots of disk activity and wireless activity"
date: 2013-04-30
forum: Security
---

### Post by jkorten on 2013-04-30
For the past few weeks my computer hangs on boot to this state where there is a lot of wireless activity and disk activity, but the OS never gets to the run level where I can interact with it. (I do see a terminal screen briefly mentioning graphics card signing on)

Is there a known attack/virus/trojan horse that prevents your computer from coming all the way up but starts sending out information?

What log file can I examine to find out what's happening when this occurs?

For a while I assumed my SATA drive had a bad connection (I dual boot through grub and linux is on a completely separate drive from windows with grub on the same separate drive, so I can remove that drive and have a virgin windows system so as not to offend the MS gods).

I run clamtk once a week which only complains about some local adobe files that have been there for quite some time.

Thanks,


Jerry

---

### Post by trundlenut on 2013-04-30
It seems unlikely.  Have you tried using an older kernel version or recovery mode from Grub?

---

### Post by Stonecold1995 on 2013-05-04
ClamAV does not protect from Linux malware, it only protects from Windows and Macintosh malware.  Or at least that's what it's focused on.

---

### Post by jkorten on 2013-05-07
Thanks all for your help. It appears this problem was OS based. A recent series of updates and this problem as disappeared. 

Jerry

---

