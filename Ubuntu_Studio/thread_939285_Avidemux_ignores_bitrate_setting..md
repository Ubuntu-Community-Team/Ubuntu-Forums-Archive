---
title: "Avidemux ignores bitrate setting."
date: 2008-10-05
forum: Ubuntu Studio
---

### Post by Naguz on 2008-10-05
Hi,
Hope this is the right forum for this topic.
I am converting some videos from .avi (divx) to mp4 (x264) to put them on my psp I am following [this]("http://www.yogarine.net/2007/12/converting-video-for-psp-on-linux.html") guide. The problem is that avidemux seimply ignores the bitrate I enter. Tried two-pass - Bitrate (Average), and two pass video size, but i doesn't make any difference at all. The final vieo files are about five MBs bigger than the originals, hich isn't really what I wanted. I just can't understand why Avidemux behaves this way. Any help would be greatly appreciated.

---

### Post by eye208 on 2008-10-06
Avidemux has separate bitrate settings for video and audio. You have to take the audio stream size into account when calculating the video bitrate for a particular file size target.

---

### Post by Naguz on 2008-10-06
The problem is, it deos not matter what i enter into the bitrate field. Average bitrate 200kbs, 500kbs, and video size 200MB all result in the same output file, which is more than 350MB and has a video bitrate of more than 1000kbs... Seems like avidemux just doesn't give sh*t about what bitrate I tell it to use, and either uses the same bitrate as the riginal video, or uses one it comes up with vy itself for fun. I don't find it particulary funny, though. :confused:

---

