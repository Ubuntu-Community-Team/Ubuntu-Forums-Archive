---
title: "[Non-Ubuntu] Download speeds"
date: 2005-03-10
forum: The Cafe
---

### Post by krusbjorn on 2005-03-10
Hey all,

something strange just happened. i registered to a new BT-tracker, and suddenly i got "Port 6881 is blacklisted", on downloads from that tracker only. So i changed the incoming TCP port to 49152. Download speeds from torrents downloaded from that site rocketed up to 800kb/s, even though im on a 2mbit ADSL line. Speeds on torrents downloaded from other torrent sites seem to stay at the usual rate though (about 200kb/s total). 

I called my ISP and they didnt know why i got such speeds. I checked what IP's i was downloading from, and none of them matched any IP from our city's internal network.

Anyone have an explanation?

---

### Post by jdong on 2005-03-10
1. Inaccurate algorithm -- speed calculation algorithms may not be accurate if the timer starts after a burst of data. If you kept 800kb/s consistently, this would not explain it.

2. Bad capping algorithm -- if you have a couple thousand connections open, you may be able to push a bit more out of your cap -- I'm capped at 324KB/s, but with a download manager, I can download 1GB files in 410KB/s 's time.

---

