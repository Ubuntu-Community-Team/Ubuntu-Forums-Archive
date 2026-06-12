---
title: "Samba/Free AV"
date: 2006-01-10
forum: Server Platforms
---

### Post by Video Toaster on 2006-01-10
Hello everyone,

I recently set up a Breezy Bager system and it is now successfully running Samba and sharing with some of my school's Windows machines.  However, I'm afraid of the Windows PCs that access the file share spreading viruses via the unprotected share.

I tried using ClamAV and got manual scans to work, but I don't know how to get real-time scanning working; when I try adding the setting to clamd.conf, it says clamuko is not available.  I also tried setting up a daily scan with a crontab, but that scan never completes (the log shows the start time but never actually scans or logs anything else).

In looking at samba-vscan, I found that it does not support the version of Samba that comes with Breezy.

Is there a way to get ClamAV to sufficiently protect Samba?  Is there better (free) solution?

Please excuse me if these are stupid questions... I've been searching all over for answers and have been unable to find answers that work for me.  It's hard to get used to Linux after using Windows for years... :D

Thanks in advance!

---

### Post by Video Toaster on 2006-01-19
*bump*

Anybody?  Am I posting in the wrong forum?

---

### Post by Video Toaster on 2006-03-18
Oh well.  I've finally got Clamuko up, so that's good.  I still can't get samba-vscan to compile, though.  Get the following error message:

```
configure:  error:  ../../../source is not readable
```
That sends me to the root of the drive, so I'm not sure why it's trying to do that. :-k

---

