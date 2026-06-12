---
title: "Poor picture quality with latest VLC?"
date: 2014-08-27
forum: Ubuntu Development Version
---

### Post by kurros on 2014-08-27
So the utopic VLC packages recently updated to 2.2.0-pre2, but I am noticing horrible picture quality, at least with h.264 videos.

[ATTACH=CONFIG]255873[/ATTACH]
[Screenshot]("http://ezri.org/uglyvlc.png") (totem on left, vlc on right)
1313x510 542.2 KB

I checked the filter chain and nothing is enabled, but I think it may be a decoder issue as it periodically (keyframes?) clears up for a moment.

Anyone else experiencing this?

Using Intel Haswell Desktop graphics for reference.

---

### Post by fjgaude on 2014-08-27
With VLC, all the movies I've tried work fine: avi, mov, etc.

---

### Post by mc4man on 2014-09-01
It's ok here with Haswell (mobile) though I do switch vlc's video out from Automatic (xv), to OpenGl GLX 
(Also here I have to use prior version of xserver-xorg-video-intel, currently 2.99.910-0ubuntu1.1 from trusty

vlc 2.2.4 (pre) is showing some other issues - 
http/https that previously worked with no issue is completely borked, bug & some randomly chosen samples from yt & nasa - 
[https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/1364186](https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/1364186)

DVD_VIDEO stream (mpeg2) shows a colored line on right side, easily fixed by switching to OpenGl GLX from Auto.. which is XV (XCB

---

### Post by kurros on 2014-09-06
The new vlc/libav11 packages yesterday fixed the picture quality issue for me.

---

