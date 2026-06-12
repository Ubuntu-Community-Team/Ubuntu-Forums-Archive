---
title: "another PUA"
date: 2015-05-30
forum: Security
---

### Post by StrobeWylan on 2015-05-30
Hello, 
I've use Xubuntu 12.04 on several computers. On one box I use WINE so as to use a unique and trusted app that is for Windoze.  Because of this I occasionally scan with ClamTk. The last 2 scans found "pua.win.Exploit.cve_2012_0110" in file "home/[user name]/tmp/remaster-root/usr/share/mime/mime.cache". The file is not deletable or quaranteenable (if that's a word). The box is behind 2 Netgear routers via Ethernet cables, has UFW enabled, and the modem has it's own firewall (I'm told). I don't get weird e-mails or visit questionable sites.  

Not sure if I should care about this?

---

### Post by DuckHook on 2015-05-31
> **StrobeWylan said:**
> Hello, 
I've use Xubuntu 12.04 on several computers. On one box I use WINE so as to use a unique and trusted app that is for Windoze.  Because of this I occasionally scan with ClamTk. The last 2 scans found "pua.win.Exploit.cve_2012_0110" in file "home/[user name]/tmp/remaster-root/usr/share/mime/mime.cache". The file is not deletable or quaranteenable (if that's a word). The box is behind 2 Netgear routers via Ethernet cables, has UFW enabled, and the modem has it's own firewall (I'm told). I don't get weird e-mails or visit questionable sites.  

Not sure if I should care about this?Highly likely to be a false positive. See [this]("http://ubuntuforums.org/showthread.php?t=2274088") recent thread for what seems to be the same issue.

I am probably starting a recurring controversy with what comes next, but I feel it must be said: false positives of this sort are only one of the reasons that I don't believe in having AV installed on my pure Linux systems. It's different with mail servers or machines that also have Windows installed, but the case for AV in a pure Linux desktop is very weak, as it brings very few positives, but a lot of negatives to the table.

It is especially important to note the last two entries in that referenced thread, and to *not* delete the file generating the false positive. The user who tried that borked his system and could no longer log in.

---

### Post by StrobeWylan on 2015-05-31
Thank you for the input. I don't know why my search didn't bring that up. Maybe it typed something wrong. Sorry.

---

### Post by DuckHook on 2015-05-31
> **StrobeWylan said:**
> ...Sorry.Goodness, Strobe. No need to be sorry. That's what we're here for.

Good Luck and Happy Ubuntuing!

---

