---
title: "viewing Facebook embedded videos in in Firefox on 12.04 requires updated libavcodec"
date: 2015-12-25
forum: Ubuntu, Linux and OS Chat
---

### Post by egstern on 2015-12-25
My wife views Facebook with Firefox on an Ubuntu 12.04 system.  Recently, the audio of embedded videos started coming out as static.  This doesn't happen on a 14.04 system that I have.  I used strace on the firefox process and found that it attempted to  load in order libavcodec56, libavcodec55, libavcodec54, libavcodec53 to process the video.  Ubuntu 14.04 has libavcodec54 but 12.04 only has libavcodec53 and libavcodec52.  Unfortunately, there is no backport of libavcodec54 for 12.04 so I downloaded the 14.04 source package and built it on the 12.04 system.  When I installed it, the audio of the Facebook videos came out normally.  It would be nice if there were an official backport for this package.

---

### Post by Bucky Ball on 2015-12-25
*Thread moved to **Ubuntu, Linux and OS Chat**.*

Not a support request but thanks for sharing.

If you are hoping to convey your feedback to Canonical devs, better to contact them directly. This is not the place to do that. :)

---

### Post by kevdog on 2015-12-27
Well honestly its great you were able to do this.  I've had to do this a few times with whatever projects and learning how to compile from source is a great skill to pick up.  I'm not sure how to exactlly make ppa images and such however this perhaps is one of those times you could contribute.

---

