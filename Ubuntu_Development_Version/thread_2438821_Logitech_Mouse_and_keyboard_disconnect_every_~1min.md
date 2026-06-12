---
title: "Logitech Mouse and keyboard disconnect every ~1min on 20.04 Beta"
date: 2020-03-18
forum: Ubuntu Development Version
---

### Post by jkwiatkoski on 2020-03-18
Every minute or so on 20.04 beta my logitech keyboard and mouse disconnect which lasts 2-3s then reconnects. the mouse will also then lose scrolling sensitivity. By this i mean that it takes many many rotations of the scroll wheel to go a very little distance on the page. 

Checking dmesg the following lines are output several times:

[ 1125.627041] logitech-hidpp-device 0003:046D:4069.0005: multiplier = 8
[ 1185.338661] logitech-hidpp-device 0003:046D:4069.0005: multiplier = 8
[ 1190.334863] logitech-hidpp-device 0003:046D:4069.0005: multiplier = 8
[ 1200.322858] logitech-hidpp-device 0003:046D:4069.0005: multiplier = 8



Keyboard: Logitech K800
Mouse: Logitech MX Master 2S

Any tips on how to go about troubleshooting this?

---

