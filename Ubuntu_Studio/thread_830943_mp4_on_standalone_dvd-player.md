---
title: "mp4 on standalone dvd-player"
date: 2008-06-16
forum: Ubuntu Studio
---

### Post by Mz33 on 2008-06-16
Hi all,

How can I burn a video-file (700mb)(x264 video, aac audio in an mp4 container) on a cd so that it can be played be a standalone dvd-player? 

Thx.
Mzee.

---

### Post by eye208 on 2008-06-18
It depends on the player. Most of them do not yet support H.264 and AAC in MP4 containers, but Xvid and MP3 in AVI containers should work fine.

First you have to make sure that the movie is standard DVD resolution (720x480 for NTSC, 720x576 for PAL) or lower. If it is not, you have to scale it down during the transcode stage.

Calculating the bitrate for a 700MB file size target can be tricky because the AVI frame headers cause a little overhead that has to be taken into account. If I remember correctly there is a bitrate calculator in Avidemux. Or you can use one of the online versions. Use Google to find them.

Note that if the movie is much longer than 90 minutes you may want to split it across two CDs. Otherwise the bitrate may be too low and cause block artifacts in high motion scenes. Xvid is not as efficient as x264 in this regard.

---

