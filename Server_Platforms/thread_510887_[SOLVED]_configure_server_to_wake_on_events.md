---
title: "[SOLVED] configure server to wake on events?"
date: 2007-07-27
forum: Server Platforms
---

### Post by a_posse_ad_esse on 2007-07-27
I have a sort of off-beat question...  Is it possible to configure my home server to enter a suspend mode, and wake on events (i.e. a scheduled mythtv recording, uploading files, backups, etc)?  This is a preferable option rather than having the thing running full-on all the time.  

Thanks for your responses.

---

### Post by noof on 2007-07-27
Haven't try this one but this might be a possibility:
[http://www.linuxcommand.org/man_pages/apmsleep1.html](http://www.linuxcommand.org/man_pages/apmsleep1.html)

---

### Post by a_posse_ad_esse on 2007-07-29
Interesting.  Would a scheduled event cause an RTC interrupt?  I am not familiar with this aspect.

---

### Post by HermanAB on 2007-07-29
Depending on your hardware, "Wake on LAN" may be a BIOS feature.  It will start the machine if the BIOS detects network traffic.

'Hope that helps!

Herman

---

### Post by a_posse_ad_esse on 2007-07-30
The machine in question is a Tyan Tiger MP, so it has the Wake on LAN functionality.  The network traffic waking the machine make sense to me, but I am unclear on if internal functions (such as cron jobs, etc) would do so.  A major part of the server's functionality would be as a mythtv recorder, and it not waking up in time (or not at all) would be counterproductive in this case.

---

### Post by HermanAB on 2007-07-30
A cron job cannot start a system, since cron isn't running if the system isn't running...

I suggest that you ensure that the power saving features (clock speed control) and HDD spin down (also stop syslogd, else it won't spin down) are enabled, then leave the machine running.

---

### Post by a_posse_ad_esse on 2007-07-30
Sounds like a plan.  Thank you everyone for your contributions.

---

