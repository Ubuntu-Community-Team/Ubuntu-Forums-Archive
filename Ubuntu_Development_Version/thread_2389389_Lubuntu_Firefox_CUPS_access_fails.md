---
title: "Lubuntu Firefox CUPS access fails"
date: 2018-04-16
forum: Ubuntu Development Version
---

### Post by VMC on 2018-04-16
The last two ISO's failed to access CUPS page([http://localhost:631/](http://localhost:631/)). 

Bootup live cd/usb/loop-back , open firefox, from link:[http://localhost:631/](http://localhost:631/), should bring up CUPS access.

Ironically, I can update to current, the last one(4/9/18) that worked, and CUPS works.

---

### Post by VMC on 2018-04-16
I found the problem. cups service was not running. Starting it fixed the issue
```
lubuntu@lubuntu:~$ systemctl status cups
&#9679; cups.service - CUPS Scheduler
   Loaded: loaded (/lib/systemd/system/cups.service; enabled; vendor preset: ena
   Active: inactive (dead)
     Docs: man:cupsd(8)

lubuntu@lubuntu:~$ systemctl start cups

lubuntu@lubuntu:~$ systemctl status cups
&#9679; cups.service - CUPS Scheduler
   Loaded: loaded (/lib/systemd/system/cups.service; enabled; vendor preset: enabled)
   Active: active (running) since Mon 2018-04-16 22:34:28 UTC; 2s ago
     Docs: man:cupsd(8)
 Main PID: 5598 (cupsd)
    Tasks: 1 (limit: 4304)
   CGroup: /system.slice/cups.service
           &#9492;&#9472;5598 /usr/sbin/cupsd -l

Apr 16 22:34:28 lubuntu systemd[1]: Started CUPS Scheduler.
```

---

