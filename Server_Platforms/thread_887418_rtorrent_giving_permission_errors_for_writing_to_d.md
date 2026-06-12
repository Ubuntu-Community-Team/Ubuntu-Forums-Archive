---
title: "rtorrent giving permission errors for writing to disk?"
date: 2008-08-12
forum: Server Platforms
---

### Post by subliminalcecil on 2008-08-12
Hi,

I recently transferred my rtorrent data from a 32bit Ubuntu server 8.04 box to a different headless box running 64bit Ubuntu server 8.04. I cleared all the session data and added the location with the half completed torrents into the .rtorrent.rc file. rtorrent was installed through apt-get on the new machine.

Storage error: [File chunk write error: Permission denied.]

Is the error i get once hashing has been completed and it find's trackers to connect to and tries to download data. It can upload fine, and it uploads other completed torrents from the old machine, in the new location with the incomplete torrents.

All the previously downloaded data is still there.

Any advice is appreciated




Thanks for your time!

---

### Post by hyper_ch on 2008-08-12
sounds to me like rtorrent hasn't the permissions to write to the folders where you want it to.

---

