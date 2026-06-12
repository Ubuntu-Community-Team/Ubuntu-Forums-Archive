---
title: "Is this possible? Pre-Rendered Real-Time Streamed 3D Games."
date: 2007-03-05
forum: The Cafe
---

### Post by PrimoTurbo on 2007-03-05
Okay imagine this, you have a laptop with a crappy video card. You cannot play any decent 3D Games, however at home you have an awesome gaming system.

You install a virtual server on your computer at home and a client on your laptop, the server allows you to launch any game on your home computer. It renders the game information, sends it back to the client in the form of compressed real-time streamed video, the client sends commands to the server which in effect change the game world. This is all done very fast and you are able to enjoy a 3d game with out a fast video card.

I don't think this might be possible yet, but I think it's an interesting idea. You could even have companies offer you to play various games independent of your video card or even your os/platform.

---

### Post by maniacmusician on 2007-03-05
With the current restrictions of broadband, networking, etc, no it's not possible. Developers have a hard enough time with getting servers to keep up with the workload even when the client is doing all the video work :)

---

### Post by ZylGadis on 2007-03-05
It should be theoretically possible with AIGLX. The old XFree/Xorg do have the extremely useful capability to have remote clients, but unfortunately any OpenGL rendering (when at all possible) happens on the client side. With AIGLX, rendering on the server side and then sending the frames over the network should be possible.

In terms of network bandwidth, suppose the client has a monitor running at 60Hz, and having a 1280x1024 screen at 24bpp. The required bandwidth is exactly 225 Mbytes per second. After compression, I suppose Gigabit ethernet will be able to handle that, if not the usual 100Mbit.

---

