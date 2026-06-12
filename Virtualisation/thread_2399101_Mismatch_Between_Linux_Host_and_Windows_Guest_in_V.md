---
title: "Mismatch Between Linux Host and Windows Guest in VirtualBox"
date: 2018-08-21
forum: Virtualisation
---

### Post by Spiralagnus on 2018-08-21
I run a Xubuntu 18.04 host with a Windows 7 guest. My setup includes three monitors:

* A 1080p monitor running on HDMI (my primary monitor)
* A 1680x1050 monitor running on VGA
* My laptop display

In Xubuntu, my monitor arrangement is fine. However, if I start up my Guest with more than one monitor, there's a mismatch on the second and third monitors. Essentially, the Windows seems to think that the second monitor (the 1680x1050) has the laptop display resolution and the third monitor (my laptop display) has the 1680x1050 resolution.

Let me illustrate in pictures. Here's the display configuration of my host:

[IMG]https://i.imgur.com/8Iqgkpz.jpg[/IMG]


And here's the display configuration on my guest:

[IMG]https://i.imgur.com/kEWaQAh.jpg[/IMG]


Now, with the guest in full-screen mode, here are what my three monitors look like:


Monitor 1:

[IMG]https://i.imgur.com/c528HJJ.jpg[/IMG]

Monitor 2:

[IMG]https://i.imgur.com/W4obQKB.jpg[/IMG]


Monitor 3:

[IMG]https://i.imgur.com/1b3EepG.jpg[/IMG]


As you can see, monitors 2 and 3 appear to have flipped resolutions. No amount of playing around with the monitor configurations in the display panel in either my host or my guest appear to be doing much good.

I'd appreciate any advice the community can provide on solving this problem.

---

### Post by TheFu on 2018-08-21
How much virtual video ram is assigned to the VM?  How much is necessary to support the resolutions and bit depth for all 3 monitors?

I'm just guessing here.

---

### Post by Spiralagnus on 2018-08-21
Here are my video settings in VirtualBox:

[IMG]https://i.imgur.com/7ONsqgc.png[/IMG]

I don't know the amount of memory required. How do I find out?

---

