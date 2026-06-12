---
title: "OT and such"
date: 2012-07-16
forum: The Cafe
---

### Post by mc4man on 2012-07-16
> **SevenMachines said:**
> No, thats the one. Manual patching not necessary now
Ot - have to ask
you are listed as maybe a 'bug maintainer' for gst-plugins-bad0.10. is that true?

---

### Post by SevenMachines on 2012-07-16
Think thats from a long way back, I've unsubscribed from bug reports now, if I'm down anywhere else let me know. Not that I won't touch them but probably not best as the port of call for gstreamer

---

### Post by mc4man on 2012-07-16
> **SevenMachines said:**
> Think thats from a long way back, I've unsubscribed from bug reports now, if I'm down anywhere else let me know. Not that I won't touch them but probably not best as the port of call for gstreamer

Too bad - have this longstanding that I've done all possible but still not a peep from anyone other than users
(found issue, got upstream commits to fix in .23 & 1.0, modified .23 commit to fix in .22 & attached patch, got someone to file against .23 in Debian
[https://bugs.launchpad.net/ubuntu/+source/gst-plugins-bad0.10/+bug/973014](https://bugs.launchpad.net/ubuntu/+source/gst-plugins-bad0.10/+bug/973014)
Maybe only hope for 12.04/12.10 is a ppa?

---

### Post by SevenMachines on 2012-07-16
If it's fixed upstream then it's probably worth an SRU for 12.04 If I have time I'll try and do it myself but I'm not as active on these things these days

---

### Post by SevenMachines on 2012-07-16
Looks like the SRU procedure has changed since I last did one, I've no idea what a bug supervisor is, getting the patch into QQ is still the priority before backporting I believe. Anyway, I'll not put this thread anymore off topic :)

---

### Post by xebian on 2012-07-16
> **mc4man said:**
> Too bad - have this longstanding that I've done all possible but still not a peep from anyone other than users
(found issue, got upstream commits to fix in .23 & 1.0, modified .23 commit to fix in .22 & attached patch, got someone to file against .23 in Debian
[https://bugs.launchpad.net/ubuntu/+source/gst-plugins-bad0.10/+bug/973014](https://bugs.launchpad.net/ubuntu/+source/gst-plugins-bad0.10/+bug/973014)
Maybe only hope for 12.04/12.10 is a ppa?

I have gst0.10 and gst1.0 plugins-bad installed and your video plays well in vlc and gnome-mplayer.  I have NV 304.22, 3.5 rc6

---

### Post by mc4man on 2012-07-16
> **xebian said:**
> I have gst0.10 and gst1.0 plugins-bad installed and your video plays well in vlc and gnome-mplayer.  I have NV 304.22, 3.5 rc6
We've drifted off track so to put a capper on  - vlc & mplayer don't use gstreamer.

---

### Post by xebian on 2012-07-16
> **mc4man said:**
> We've drifted off track so to put a capper on  - vlc & mplayer don't use gstreamer.

Got you, but I did some testing and removing gst0.10 plugins-bad and installing gst1.0 plugins-bad made totem play it nicely.

A warning though - there are still apps that require gst0.10 like clementine.

---

### Post by sffvba[e0rt on 2012-07-18
Moved out of the original thread by request... no idea where to go with it or what to call it...


404

---

