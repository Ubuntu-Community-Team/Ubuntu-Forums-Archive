---
title: "ubuntu 8.10 + Wine + DoD Problem"
date: 2009-04-08
forum: Wine
---

### Post by mrm48 on 2009-04-08
Hi all,

I just downloaded Wine through the intrepid repositories and installed steam, Day of Defeat 1.3 and Deathmatch Classic. DMC runs great, just like it does on my windows partition.

However, DoD 1.3 freezes after just a few seconds of gameplay. I'm using fglrx for my radeon, I don't have any desktop effects enabled, and I'm using ALSA for sound. I've also set the video settings to OpenGL, 800x600 resolution, and running in windowed mode. I've tried D3D, which came up with the same error.

Has anyone found a fix for this issue? Any help will be greatly appreciated (as I will blow away my windows partition if DoD 1.3 will work for me ):P).

Thanks in advance, 
Matt

---

### Post by mrm48 on 2009-04-08
I found that the issue was the sound. I've tried alsa and OSS, both gave me problems and adding -nosound to the launch options helped. 

Has anyone tried any of the other options for sound with Wine?

---

### Post by mrm48 on 2009-04-10
Still can't figure this one out and having to do a hard reboot each time, anyone have any suggestions?

It seems to freeze after a longer period of time (5 seconds instead of 2, every time) when I bump the resolution up, but considering this is most likely a sound issue, I wouldn't know why this is the case.

---

