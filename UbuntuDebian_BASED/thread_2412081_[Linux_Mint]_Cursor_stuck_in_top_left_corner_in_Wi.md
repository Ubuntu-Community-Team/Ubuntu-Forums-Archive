---
title: "[Linux Mint] Cursor stuck in top left corner in Wine applications"
date: 2019-02-07
forum: Ubuntu/Debian BASED
---

### Post by mikasu on 2019-02-07
Hi,
I switched to Linux Mint 19.1 to see what it's all about and like it so far except this issue that prevents me from playing some of my favorite games. On any Wine applications, when I hold right click, my cursor sticks to the top left corner for some reason. On Astroneer, this causes the camera to be quite totally unusable and on League of Legends this prevents me from using "Smart Pings". Is there any fix for this?

Hardware:
CPU: Intel Core i5-5200U
RAM: 16GB DDR3-1600
GPU: NVIDIA GeForce 840M 2GB ( proprietary 415 driver from graphics drivers ppa)

---

### Post by mikasu on 2019-02-07
Found the issue. Wine doesn't behave well with Coordinate Matrix Conversion modifications.

---

