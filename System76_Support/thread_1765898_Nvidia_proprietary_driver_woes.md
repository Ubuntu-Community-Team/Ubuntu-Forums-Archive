---
title: "Nvidia proprietary driver woes"
date: 2011-05-23
forum: System76 Support
---

### Post by macaholic on 2011-05-23
Hello all,
I was wondering if anyone else has been experiencing issues with their nvidia cards and 11.04? I have with my gtx 460m; I can't seem to get them to work properly for the life of me. Specifically, nothing I do will get rid of the tearing at the top of screen that occurs during videos/fullscreen games. Videos also just seem jerky overall, no matter what player I use and what output settings I try. This is quite frustrating since it's keeping me from using this awesome screen to its full capabilities. I've tried every combination of settings in compiz and the nvidia settings and I can't get the tearing/jerkiness to go away. Has anyone else been experiencing these issues or know of anything that helps? At this point I'm under the belief that there's something wrong with X in 11.04 that isn't agreeing with nvidia cards.

My problems seem to be akin to what's discussed here: [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/600178](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/600178)

---

### Post by isantop on 2011-05-24
There is an option that can help improve that in the Nvidia Control Center. I can't remember exactly where it's at, but it has to do with enabling vSync or Sync to vBlank for Video.

---

### Post by macaholic on 2011-05-24
Yeah, it's under "X Server X Video Settings" as "Sync to VBlank". I've had it enabled since I got the computer though it doesn't seem to resolve the issue.

---

