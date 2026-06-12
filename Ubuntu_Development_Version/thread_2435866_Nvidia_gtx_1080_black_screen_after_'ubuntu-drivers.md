---
title: "Nvidia gtx 1080 black screen after 'ubuntu-drivers install'?"
date: 2020-01-27
forum: Ubuntu Development Version
---

### Post by dankegel on 2020-01-27
Hi all!
Installing [http://www.cdimage.ubuntu.com/daily-live/current](http://www.cdimage.ubuntu.com/daily-live/current) from today (timestamp 2020-01-24 07:49)
on an i9-9900K with a gtx 1080 graphics card went just fine.
However, 'sudo ubuntu-drivers install' to install the proprietary nvidia driver (440.44-0ubuntu2)
didn't seem to have the desired result; I get a black screen.  (Can still log in on other VTs,
but can't startx.)
I know the hardware is good, as it's been happily running ubuntu 18.04 with the proprietary driver for months.
(I also have windows on the box in case that's of interest.)

At first glance
[https://launchpad.net/ubuntu/+source/nvidia-graphics-drivers-440/440.44-0ubuntu2](https://launchpad.net/ubuntu/+source/nvidia-graphics-drivers-440/440.44-0ubuntu2)
seems to lack what looks like a fix for a similar or identical problem,
[https://devtalk.nvidia.com/default/topic/1068332/linux/nvidia-driver-does-not-build-on-linux-v5-5-release-candidate-kernel/](https://devtalk.nvidia.com/default/topic/1068332/linux/nvidia-driver-does-not-build-on-linux-v5-5-release-candidate-kernel/)

Has anybody run into this and found a solution?

I'm not blocked just yet, since I don't need graphics at the moment on this box, but I thought it might be worth mentioning.

---

### Post by CelticWarrior on 2020-01-27
How is your Secure Boot status?

---

