---
title: "SYN Flooding From Torrent Client"
date: 2009-08-29
forum: Server Platforms
---

### Post by zemon_ on 2009-08-29
My torrent client is causing SYN floods and the webui becomes unconnectable

Is there a way to prevent this?

---

### Post by lelamal on 2009-10-07
Hi, I have the same issue with Transmission. Changing ports won't help, nor does disabling UPnP protocol change a thing. Reducing values in its settings didn't seem to produce any result either: reduced *Maximum peers overall* and *per torrent* (Peers tab) as well as download speed, but nothing. I also paused all the uploads (for, as I understood, SYN flooding is triggered when the computer thinks its under attack for the high number of connections from outside users), but to no avail. The system is effectively stopping both all my downloads and uploads in Transmission (by reducing their speed to zero), while aMule interestingly keeps going. I'm clueless. Can anyone advise a solution, other than disabling syn cookies. Or would the latter still be safe, anyway? Many thanks in advance!

---

