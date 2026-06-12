---
title: "AMD Driver problems - Pop OS lags if connected to the gpu"
date: 2022-02-16
forum: Ubuntu/Debian BASED
---

### Post by ediperazim on 2022-02-16
I am having problems with PopOS when I connect my monitor to the graphics card. When I connect to the display port from my motherboard, everything works smoothly.

What happens if I'm connected via GPU? Everything except the mouse cursor is very slow. And I guess that a very slow refresh rate is the reason. I also already checked the display settings, the display refresh rate is correct and is set to 59.97Hz.

What I tried:

[LIST=1]
[*]My theory was that it must be the driver. Therefore I watched this [video on youtube]("https://www.youtube.com/watch?v=boOXG_iX7Qo&ab_channel=MattsCreative") and made the same steps; installing "[Open Graphics Drivers]("https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers")" by Oibaf and the [XanMod-Kernel]("https://xanmod.org/"). But this did not fix my problem.
[*]So I undid everything and tried to install the [driver from AMD]("https://www.amd.com/en/support/kb/release-notes/rn-amdgpu-unified-linux-21-10"). I did it using this [guide]("https://devtalk.blender.org/t/guide-install-amd-opencl-on-pop-os-some-ubuntu-derivates-linux-amdgpu-amdgpu-pro-rocm-rocr/13458") and ran amdgpu-installer. I did not install amdgpu-pro-installer. But this also did not fix my problem.
[/LIST]

My System Specs:

[LIST]
[*]8GB DDR3
[*]Intel Core i5- 46900
[*]RX 580 4GB
[/LIST]

How can I use PopOS with my AMD GPU? Is that even possible? I also read that if someone is using a AMD GPU he does not have to install anything because it has to work out of the box... :/

---

### Post by Tadaen_Sylvermane on 2022-03-10
I'm using a 4gb  RX570 with no difficulty right now on a plain jane Ubuntu 20.04. No ppa drivers or anything. Just what Ubuntu provides. Get 90+ fps in games and everything @ 1080p for the most part. 

post output of ```
sudo lshw -c video
``` while plugged in and loaded on the video card.

For reference I'm using an i5-3470 cpu with 16gb of ram.

---

