---
title: "ubuntu server 18.04 connection problem"
date: 2020-09-03
forum: Server Platforms
---

### Post by math492m on 2020-09-03
hi i resently just moved my fully working physical ubuntu server 

it worked perfectly fine before i moved it (turned it off)

and not i dont have network connection and i cant ssh

any suggestions 

hardware:
hp Proliant SE326M1
8gb ecc ddr3
intel xeon l5640

---

### Post by LHammonds on 2020-09-03
If it worked before the move, it is likely not a software configuration problem.

#1 If you have 2 ethernet ports, make sure you plugged it into the same one.
#2 Check your ethernet cable and make sure both ends are plugged in.
#3 Try a different ethernet cable
#4 Make sure the wall outlet is hot (actually works)
#5 Trace the wall outlet to the switch and move it to a different port (to rule out a bad port on switch)

---

### Post by math492m on 2020-09-03
hi it was plugged directly in to a switch

it turned out to be a network config file error

---

