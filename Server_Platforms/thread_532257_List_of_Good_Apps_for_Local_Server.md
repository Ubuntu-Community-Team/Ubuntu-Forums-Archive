---
title: "List of Good Apps for Local Server?"
date: 2007-08-22
forum: Server Platforms
---

### Post by i.wanna.corndog on 2007-08-22
I just finished configuring a local file server with Ubuntu (LAMP setup). So far, I have installed phpMyAdmin, SWAT, and Torrentflux. Are there any other apps out there that would be worthwhile on a local server? To be more specific, I am looking for an app that could somehow share music files on the server using iTunes' share protocol (DAAP). But I would also be interested to know if anyone else has the same sort of setup and has any other apps they'd recommend.

Thanks!

---

### Post by a9k on 2007-08-23
mt-daapd is what I use to server tunes better than iTunes does on the Macs at home. The project has been renamed Firefly but the package is still mt-daapd

You might want openssh-server installed if you are going to run your server by using ssh to connect to it.

You might want netatalk if you want to have file sharing for Macintosh.

You also may want a independent firewall between this server and the net. Expect to be attacked often via www, ssh and everything PC fileshare related.

---

