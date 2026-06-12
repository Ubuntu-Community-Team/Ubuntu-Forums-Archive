---
title: "LTSP Boot Results in Constant Audio Feedback"
date: 2009-11-03
forum: Server Platforms
---

### Post by yottabit on 2009-11-03
Hi Everyone,

I've just installed the LTSP edition of 9.10 Karmic in my ESXi HyperVisor. I finally managed to get the VM Tools installed for memory ballooning, enhance network, etc. Everything went smoothly.

Next I tried the first PXE boot of an LTSP client. I'm using my Lenovo T60 notebook (Intel T2500 Core Duo, 3 GB RAM, Intel GbE, Intel 945GMA chipset/graphics).

It boots fine and I'm actually posting this from the LTSP environment right now. But I have two problems:

1. As soon as the login screen appears I get the high-pitched audio feedback loop through the speakers. It's enough to crack my skull in two. I figured I would just have to adjust and/or mute the mic volume once I logged in, so I hit the hardware mute button and did just that. But When the mic is muted and even when I change the hardware profile to "Analog Stereo Output" instead of "Analog Stereo Duplex" (thereby disabling the mic control completely), it makes no difference. If I turn the volume down to the point where I can barely hear the audio anyway the feedback problem goes away. Any ideas on this one?

2. Video playback sucks and audio is choppy. I have tested this computer on LTSP with 9.04 or 8.10 (can't remember which now) and was quite impressed with the capability. I was able to playback 720p video successfully even on computers much lower spec than this notebook. Does anyone have any ideas on the video and sound choppiness?

I have STF and Google to no avail. :(

My end-game is to get this running suitably on the notebook and then to spring for the new dual-core Atom 330 with nVidia Ion chipset! But I'm not going to drop the cash on that until I'm confident this is going to work successfully!

Thanks in advance!

Edit: I have filed a bug related to the audio problem:
  [https://bugs.launchpad.net/ubuntu/+source/ltsp/+bug/472935](https://bugs.launchpad.net/ubuntu/+source/ltsp/+bug/472935)

---

