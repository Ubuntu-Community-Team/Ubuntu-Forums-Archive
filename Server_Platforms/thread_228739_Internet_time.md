---
title: "Internet time"
date: 2006-08-03
forum: Server Platforms
---

### Post by alecjw on 2006-08-03
IS there any way of updating the time from the internet?

---

### Post by MJN on 2006-08-03
Sure - Network Time Protocol (NTP) is what you're after using here.

Check out the simple guide at [https://help.ubuntu.com/community/NTPTimeSynchronisation](https://help.ubuntu.com/community/NTPTimeSynchronisation) - as it says ntpdate is set to run at boot (and could be run periodically by a cronjob) however I went for the ntpd option (ntp-simple) instead as I rarely reboot and wanted it to just look after itself.

Mathew

---

### Post by Chymera on 2007-08-21
i set everything accordingly but i cant seem to get it to work, the synchronize now button is grayed out and it doesnt synchronize itself either (i set the time 2 hours back 10 minutes ago and it's still the same ) :confused:

---

