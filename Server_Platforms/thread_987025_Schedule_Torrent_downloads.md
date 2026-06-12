---
title: "Schedule Torrent downloads"
date: 2008-11-19
forum: Server Platforms
---

### Post by Ameoba on 2008-11-19
Hi,

Does anyone know how to setup a torrent client on a Ubuntu server, and schedule the downloads so that they only download over night? (ie midnight to midday)

I've currently got rtorrent installed but not sure if it has this feature.

Also the ability to just drop a torrent file in a folder and have the server download it is very helpfull.

Regards,

---

### Post by hyper_ch on 2008-11-19
[http://libtorrent.rakshasa.no/wiki/RTorrentCommonTasks](http://libtorrent.rakshasa.no/wiki/RTorrentCommonTasks)  --> Scheduling downlaod rates

Just set it during the day to a very, very low level (not "0" as this would be unlimited).

Otherwise use cron to start / stop rtorrent accoringly.

---

