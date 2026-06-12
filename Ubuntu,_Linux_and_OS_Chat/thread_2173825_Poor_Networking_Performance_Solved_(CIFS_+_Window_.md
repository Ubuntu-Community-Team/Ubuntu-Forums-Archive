---
title: "Poor Networking Performance Solved (CIFS + Window Share)"
date: 2013-09-11
forum: Ubuntu, Linux and OS Chat
---

### Post by gabe5 on 2013-09-11
Hey all,

I just wanted to post this in case anyone else runs into this issue.  I'm a bit new to Ubuntu however I made the decision recently to start converting one of my many media PCs from Windows 7 over to Ubuntu due to Windows 8's new licensing structure for WMC and Windows in general.

Nonetheless, the major issue I encountered during the proof of concept was that I was seeing extremely poor performance on my gigabit network (400KB/s - 1MB/s transfers from Windows to Linux) using a CIFS mount set up in /etc/fstab.  The card for both the client Linux box and server Windows 7 box were both negotiated at 1Gbps full duplex.  I assumed the problem was on the client side so I spent a number of days trying to tweak the CIFS and Settings in:

/etc/fstab
/etc/samba/smb.conf

With really no luck.  Last night I decided to change my MTU settings on the windows box (server) from it's default (unsure what it was and the client was set to 1500) over to 9000 (jumbo frames).  This little change took me from 1MB/s transfers to 77MB/s transfers.  So changing the MTU on the Windows server made a drastic difference in speed without adversely impacting my Windows to Windows transfer speed.

This feels like a bug to me but I can't say for sure.  Nonetheless, I hope this tidbit helps someone in the future.

---

