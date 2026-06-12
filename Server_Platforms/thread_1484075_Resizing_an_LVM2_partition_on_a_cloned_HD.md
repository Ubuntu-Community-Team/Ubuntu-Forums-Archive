---
title: "Resizing an LVM2 partition on a cloned HD"
date: 2010-05-15
forum: Server Platforms
---

### Post by schmappel on 2010-05-15
I have an Ubuntu Server install that's been running for months without any problems, except that the original 80GB drive is nearly full. I had a 500GB drive lying around and managed to successfully clone the 80GB drive to the 500GB drive with an Ubuntu 10.04 live CD and gddrescue.

All went well, and I am able to boot from my new drive. But now I am stuck at the part i thought would be the easiest: resizing my freshly cloned partition from 80GB so it utilizes its full capacity. The resize/move option is not available for sda1. I resized sda2 instead, hoping that would somehow make it available to sda1, but that didn't work.

Here's a screenshot from my current setup in gparted.
[ATTACH]157011[/ATTACH]

Hope there's a brave soul out there that can help me.

---

