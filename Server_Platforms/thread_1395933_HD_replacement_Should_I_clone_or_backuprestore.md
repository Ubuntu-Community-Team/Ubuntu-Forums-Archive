---
title: "HD replacement: Should I clone or backup/restore?"
date: 2010-02-01
forum: Server Platforms
---

### Post by nosnetrom on 2010-02-01
[Warning: n00b questions ahead...] We have a Dell PowerEdge 850 server (rack mounted, single space) running Ubuntu Server 8.10; it has a bad SATA 250 GB HD, and no amount of fsck seems to be able to fix the problem.  We have a 1 TB HD ready to replace it, but we don't know the best methodology to move from the old system drive to the new.  (I should clarify; system AND data for the server are all on the one drive.)

My Googling so far has led to three possible solutions: Clonezilla, PartImage, or dd_rescue.  Does anyone have any suggestions on which way to go?

Mitigating factors & questions:

[LIST]
[*]The server only has space for a single drive, so we can't install a new disk side-by-side and dd over to it.
[*]Which solution would prevent us from copying the bad sector(s) from the old disk to the new?
[*]I'm pretty sure that we're only using 2-5 GB on the old drive. Saving to a USB drive or other network drive are options; burning to DVD is not.
[/LIST]

TIA for your help!  :)

---

### Post by fang0654 on 2010-02-01
If the drive itself is bad, then the data on the drive is probably suspect.  Not sure about clonezilla, but I am pretty sure partimage will crash if it hits an unrecoverable read error, and even dd-rescue won't be able to read from an unreadable sector.  

Your best bet is to backup any data files, /etc, and anything else you need to a flash drive or usb hard drive.  Then install the 1TB drive, reinstall a clean copy of the OS, and replace the data.

You can try using partimage to make a copy of the drive, but if the drive has read errors on any important sectors, then it can get ugly.

The best solution is get something that at least supports 2 drives so you can run a mirror and not have this problem ever again :)

---

