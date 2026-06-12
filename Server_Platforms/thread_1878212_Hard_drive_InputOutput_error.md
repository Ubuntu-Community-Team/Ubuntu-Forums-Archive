---
title: "Hard drive Input/Output error"
date: 2011-11-09
forum: Server Platforms
---

### Post by HLSolbjorg on 2011-11-09
Hey'all.
* Ubuntu server, newly updated (after disk failure) *

A couple of days back I tried downloading a new release of Ubuntu for my laptop through rtorrent. Near the finish line rtorrent marked the torrent as "inactive: Input/Output error."

I tried rebooting and my boot halted at "Could not mount /dev/sdd1 to /media/serier". I pressed S to skip it and booted normally.
I tried to manually mount /dev/sdd1 to /media/serier by $ sudo mount /dev/sdd1 /media/serier. The result:
```

Failed to mount '/dev/sdd1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

```

I connected an external hdd case to my desktop computer with Windows 7 and opened Device Manager to find the disk. It was marked as "Offline" so I made it go "online". Now I was going to assign a Drive letter to that drive - but the only options I had was to "Delete Volume" or "Properties". The properties prompt told me the device was okay and no problems.

Any ideas on what to do to fix this? I've tried lots of related fixes but none of them have worked for me.
Is it possible to use any data recovering tools to get the data back?

The drive is a WD 1TB Green (WD10EAVS) with 8MB cache.

My other disk (1tb WD green) still runs fine.
Thanks!

---

### Post by vasile002 on 2011-11-09
I believe your drive went bad, you will need to buy a new one unfortunately

---

