---
title: "Can Ubuntu Server serve music/pics/video to iTunes, TiVo, PS3?"
date: 2010-05-07
forum: Server Platforms
---

### Post by Brian Kendig on 2010-05-07
Does Ubuntu Server 10.04 give me a good/easy way to upload music, photos, and videos and automatically have them available to a TiVo, a PlayStation 3, and Macs/PCs running iTunes on the network?

I'd additionally like it to be able to transcode the videos into formats that the PS3 can handle.

---

### Post by HermanAB on 2010-05-07
Yes, it can do anything you want, but whether it is easy depends on *your* level of experience...

---

### Post by arrrghhh on 2010-05-07
> **Brian Kendig said:**
> Does Ubuntu Server 10.04 give me a good/easy way to upload music, photos, and videos and automatically have them available to a TiVo, a PlayStation 3, and Macs/PCs running iTunes on the network?

I'd additionally like it to be able to transcode the videos into formats that the PS3 can handle.

I'd use [Firefly](http://www.fireflymediaserver.org/) (DaaP) if you want other workstations (read: iTunes clients) to be able to play the music locally on their workstations.  MPD if you want a central music server, with one master playlist.  If you want each client to have their own playlist, Firefly is the way to go.

TiVo, I have no clue what standards that device uses.

PS3 - Use PS3MediaServer.  I have a repo for it, includes a startup script & all.  [PMS Homepage](http://code.google.com/p/ps3mediaserver/) and [here's](http://ps3mediaserver.org/forum/viewtopic.php?f=3&t=5589) the thread where I found a repo to use for it :D  If you've got a beefy server, transcoding HD is no issue.  Mine's pretty wimpy, but it handles SD fairly well.

---

### Post by DaF1oh1 on 2010-05-07
Set up a samba server on your Linux box, your PS3 should commune with it.

---

