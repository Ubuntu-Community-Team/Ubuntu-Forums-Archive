---
title: "Running Ubuntu under Win7"
date: 2012-11-11
forum: Virtualisation
---

### Post by andyross on 2012-11-11
For awhile, I had been playing around with Ubuntu on an old computer I had (P3-1000, 512M, dual-boot with Win2K!) I would pull it out every once in awhile and try it. It was a bit slow, as expected, and updating to 12.10 didn't go well and mangled it so bad I had to blow the partition away.

I decided to try running Unbuntu in a VM on my main system (Q6600, Win7-32bit, 4G [3G usable].) I knew running it in a VM would be a bit slow, but I'm surprised it seems to be slower than the old computer!! 

I'm using VirtualBox 4.2.4 (or whatever the latest is.) I have also installed the Guest additions and verified that the session info shows them as active. The host has an nVidia 8600GTS@1920x1080. I have Ubuntu running at 1280x960. I currently have it configured with 1G of RAM and 128M of video. The VM partition is 20G.

To me, the main issue seems to be the display speed. It's pathetic. Even something like typing in word processor can be 1-2 seconds behind what I'm actually typing. Trying to resize a window is frustrating as it's way behind. I used compiz manager to disable a few effects, like fading, but it's still very slow, worse than the ancient ATI in the old computer.

Is this the best it can do? Any options to try and make the display more usable?

---

### Post by 2F4U on 2012-11-11
I noticed the same with 12.10 in VirtualBox, while 12.04 runs well with the same VM settings. I guess it has to do with the increased graphics requirements in 12.10. So if you don't rely on a particular version, I would install 12.04.

---

### Post by andyross on 2012-11-17
I created a new VM using 12.04LTS. WOW! What a huge difference. Now it's actually fun and usable to play with!

---

### Post by rdp870 on 2012-11-17
Ubuntu 12.10 got rid of "Unity 2-D Mode" which supported lower power graphics and virtual environments. That's probably the reason.

---

