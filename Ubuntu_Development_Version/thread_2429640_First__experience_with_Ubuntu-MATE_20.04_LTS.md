---
title: "First  experience with Ubuntu-MATE 20.04 LTS"
date: 2019-10-21
forum: Ubuntu Development Version
---

### Post by #&amp;thj^% on 2019-10-21
First experience with Ubuntu-MATE 20.04 LTS _Focal Fossa_ - Alpha amd64,
Live session would not load without a Parameter on kernel, never had to before this.
Brisk Menu Crashed  a few times: "brisk-menu crashed with SIGSEGV in gtk_list_box_insert"
I added the old style (Custom) menu back. (I prefer this anyway)

Not sure how I feel about the Munity panel Toggle with Global Menus.
```
System:
  Host: ubuntu-mate Kernel: 5.3.0-18-generic x86_64 bits: 64 
  Desktop: MATE 1.22.2 Distro: Ubuntu 20.04 LTS (Focal Fossa) 
ubuntu-mate@ubuntu-mate:~$ inxi -F
System:
  Host: ubuntu-mate Kernel: 5.3.0-18-generic x86_64 bits: 64 
  Desktop: MATE 1.22.2 Distro: Ubuntu 20.04 LTS (Focal Fossa) 
Machine:
  Type: Laptop System: LENOVO product: 2349M88 v: ThinkPad T430 
  serial: <root required> 
  Mobo: LENOVO model: 2349M88 serial: <root required> UEFI [Legacy]: LENOVO 
  v: G1ETB8WW (2.78 ) date: 09/19/2018 
Battery:
  ID-1: BAT0 charge: 50.0 Wh condition: 52.2/56.2 Wh (93%) 
CPU:
  Topology: Dual Core model: Intel Core i5-3320M bits: 64 type: MT MCP 
  L2 cache: 3072 KiB 
  Speed: 1198 MHz min/max: 1200/3300 MHz Core speeds (MHz): 1: 1197 2: 1197 
  3: 1198 4: 1197 
Graphics:
  Device-1: Intel 3rd Gen Core processor Graphics driver: i915 v: kernel 
  Display: x11 server: X.Org 1.20.5 driver: modesetting unloaded: fbdev,vesa 
  resolution: 1600x900~60Hz 
  OpenGL: renderer: Mesa DRI Intel Ivybridge Mobile v: 4.2 Mesa 19.2.1 
Audio:
  Device-1: Intel 7 Series/C216 Family High Definition Audio 
  driver: snd_hda_intel 
  Sound Server: ALSA v: k5.3.0-18-generic 

```

Note: This is not a rant just pointing out early bugs on my end, and there will be plenty more before this ride is over.
But after install all hardware was installed OTB.
EDIT: This is the first time in many years I've done a Clean Install, instead of rolling to the Alpha.
EDIT2: Mouse and touchpad a bit sketchy:
```
 Outer window is 0x4600001, inner window is 0x4600002

EnterNotify event, serial 25, synthetic NO, window 0x4600001,
    root 0x152, subw 0x0, time 2869101, (107,164), root:(1507,248),
    mode NotifyNormal, detail NotifyAncestor, same_screen YES,
    focus NO, state 0

MotionNotify event, serial 25, synthetic NO, window 0x4600001,
    root 0x152, subw 0x0, time 2869101, (107,164), root:(1507,248),
    state 0x0, is_hint 0, same_screen YES

MotionNotify event, serial 25, synthetic NO, window 0x4600001,
    root 0x152, subw 0x0, time 2869113, (111,151), root:(1511,235),
    state 0x0, is_hint 0, same_screen YES

MotionNotify event, serial 25, synthetic NO, window 0x4600001,
    root 0x152, subw 0x0, time 2869126, (114,141), root:(1514,225),
    state 0x0, is_hint 0, same_screen YES

MotionNotify event, serial 25, synthetic NO, window 0x4600001,
    root 0x152, subw 0x0, time 2869138, (115,132), root:(1515,216),
    state 0x0, is_hint 0, same_screen YES

MotionNotify event, serial 25, synthetic NO, window 0x4600001,
    root 0x152, subw 0x0, time 2869150, (115,124), root:(1515,208),
    state 0x0, is_hint 0, same_screen YES

MotionNotify event, serial 25, synthetic NO, window 0x4600001,
    root 0x152, subw 0x0, time 2869162, (115,118), root:(1515,202),
    state 0x0, is_hint 0, same_screen YES

MotionNotify event, serial 25, synthetic NO, window 0x4600001,
    root 0x152, subw 0x0, time 2869174, (114,115), root:(1514,199),
    state 0x0, is_hint 0, same_screen YES

MotionNotify event, serial 25, synthetic NO, window 0x4600001,
    root 0x152, subw 0x0, time 2869185, (114,112), root:(1514,196),
    state 0x0, is_hint 0, same_screen YES

MotionNotify event, serial 25, synthetic NO, window 0x4600001,
    root 0x152, subw 0x0, time 2869198, (114,112), root:(1514,196),
    state 0x0, is_hint 0, same_screen YES

MotionNotify event, serial 25, synthetic NO, window 0x4600001,
    root 0x152, subw 0x0, time 2869210, (114,111), root:(1514,195),
    state 0x0, is_hint 0, same_screen YES

MotionNotify event, serial 25, synthetic NO, window 0x4600001,
    root 0x152, subw 0x0, time 2869222, (113,111), root:(1513,195),
    state 0x0, is_hint 0, same_screen YES

MotionNotify event, serial 25, synthetic NO, window 0x4600001,
    root 0x152, subw 0x0, time 2869234, (113,111), root:(1513,195),
    state 0x0, is_hint 0, same_screen YES

MotionNotify event, serial 25, synthetic NO, window 0x4600001,
    root 0x152, subw 0x0, time 2869259, (113,111), root:(1513,195),
    state 0x0, is_hint 0, same_screen YES

MotionNotify event, serial 25, synthetic NO, window 0x4600001,
    root 0x152, subw 0x0, time 2869283, (113,111), root:(1513,195),
    state 0x0, is_hint 0, same_screen YES

MotionNotify event, serial 25, synthetic NO, window 0x4600001,
    root 0x152, subw 0x0, time 2869295, (113,111), root:(1513,195),
    state 0x0, is_hint 0, same_screen YES

MotionNotify event, serial 25, synthetic NO, window 0x4600001,
    root 0x152, subw 0x0, time 2869356, (113,111), root:(1513,195),
    state 0x0, is_hint 0, same_screen YES

MotionNotify event, serial 25, synthetic NO, window 0x4600001,
    root 0x152, subw 0x0, time 2869367, (111,117), root:(1511,201),
    state 0x0, is_hint 0, same_screen YES

MotionNotify event, serial 25, synthetic NO, window 0x4600001,
    root 0x152, subw 0x0, time 2869380, (108,125), root:(1508,209),
    state 0x0, is_hint 0, same_screen YES

MotionNotify event, serial 25, synthetic NO, window 0x4600001,
    root 0x152, subw 0x0, time 2869392, (105,132), root:(1505,216),
    state 0x0, is_hint 0, same_screen YES

MotionNotify event, serial 25, synthetic NO, window 0x4600001,
    root 0x152, subw 0x0, time 2869404, (102,136), root:(1502,220),
    state 0x0, is_hint 0, same_screen YES

MotionNotify event, serial 25, synthetic NO, window 0x4600001,
    root 0x152, subw 0x0, time 2869416, (101,138), root:(1501,222),
    state 0x0, is_hint 0, same_screen YES

MotionNotify event, serial 25, synthetic NO, window 0x4600001,
    root 0x152, subw 0x0, time 2869427, (101,138), root:(1501,222),
    state 0x0, is_hint 0, same_screen YES

ButtonPress event, serial 25, synthetic NO, window 0x4600001,
    root 0x152, subw 0x0, time 2869696, (101,138), root:(1501,222),
    state 0x0, button 1, same_screen YES

ButtonRelease event, serial 25, synthetic NO, window 0x4600001,
    root 0x152, subw 0x0, time 2869755, (101,138), root:(1501,222),
    state 0x100, button 1, same_screen YES

MotionNotify event, serial 25, synthetic NO, window 0x4600001,
    root 0x152, subw 0x0, time 2870554, (94,137), root:(1494,221),
    state 0x0, is_hint 0, same_screen YES

MotionNotify event, serial 25, synthetic NO, window 0x4600001,
    root 0x152, subw 0x0, time 2870566, (86,133), root:(1486,217),
    state 0x0, is_hint 0, same_screen YES

MotionNotify event, serial 25, synthetic NO, window 0x4600001,
    root 0x152, subw 0x0, time 2870579, (77,128), root:(1477,212),
    state 0x0, is_hint 0, same_screen YES

MotionNotify event, serial 25, synthetic NO, window 0x4600001,
    root 0x152, subw 0x0, time 2870590, (67,121), root:(1467,205),
    state 0x0, is_hint 0, same_screen YES

MotionNotify event, serial 25, synthetic NO, window 0x4600001,
    root 0x152, subw 0x0, time 2870602, (58,114), root:(1458,198),
    state 0x0, is_hint 0, same_screen YES

MotionNotify event, serial 25, synthetic NO, window 0x4600001,
    root 0x152, subw 0x0, time 2870615, (50,107), root:(1450,191),
    state 0x0, is_hint 0, same_screen YES

MotionNotify event, serial 25, synthetic NO, window 0x4600001,
    root 0x152, subw 0x0, time 2870626, (44,102), root:(1444,186),
    state 0x0, is_hint 0, same_screen YES

MotionNotify event, serial 25, synthetic NO, window 0x4600001,
    root 0x152, subw 0x0, time 2870638, (40,98), root:(1440,182),
    state 0x0, is_hint 0, same_screen YES

MotionNotify event, serial 25, synthetic NO, window 0x4600001,
    root 0x152, subw 0x0, time 2870651, (36,94), root:(1436,178),
    state 0x0, is_hint 0, same_screen YES

MotionNotify event, serial 25, synthetic NO, window 0x4600001,
    root 0x152, subw 0x0, time 2870663, (34,90), root:(1434,174),
    state 0x0, is_hint 0, same_screen YES

MotionNotify event, serial 25, synthetic NO, window 0x4600001,
    root 0x152, subw 0x0, time 2870674, (31,84), root:(1431,168),
    state 0x0, is_hint 0, same_screen YES

MotionNotify event, serial 25, synthetic NO, window 0x4600001,
    root 0x152, subw 0x0, time 2870687, (29,77), root:(1429,161),
    state 0x0, is_hint 0, same_screen YES

MotionNotify event, serial 25, synthetic NO, window 0x4600001,
    root 0x152, subw 0x0, time 2870699, (27,68), root:(1427,152),
    state 0x0, is_hint 0, same_screen YES

LeaveNotify event, serial 25, synthetic NO, window 0x4600001,
    root 0x152, subw 0x0, time 2870711, (26,58), root:(1426,142),
    mode NotifyNormal, detail NotifyInferior, same_screen YES,
    focus YES, state 0

MotionNotify event, serial 25, synthetic NO, window 0x4600001,
    root 0x152, subw 0x4600002, time 2870711, (26,58), root:(1426,142),
    state 0x0, is_hint 0, same_screen YES

MotionNotify event, serial 25, synthetic NO, window 0x4600001,
    root 0x152, subw 0x4600002, time 2870723, (24,51), root:(1424,135),
    state 0x0, is_hint 0, same_screen YES

MotionNotify event, serial 25, synthetic NO, window 0x4600001,
    root 0x152, subw 0x4600002, time 2870734, (23,44), root:(1423,128),
    state 0x0, is_hint 0, same_screen YES

MotionNotify event, serial 25, synthetic NO, window 0x4600001,
    root 0x152, subw 0x4600002, time 2870748, (22,39), root:(1422,123),
    state 0x0, is_hint 0, same_screen YES

MotionNotify event, serial 25, synthetic NO, window 0x4600001,
    root 0x152, subw 0x4600002, time 2870759, (22,37), root:(1422,121),
    state 0x0, is_hint 0, same_screen YES

MotionNotify event, serial 25, synthetic NO, window 0x4600001,
    root 0x152, subw 0x4600002, time 2870771, (22,36), root:(1422,120),
    state 0x0, is_hint 0, same_screen YES

MotionNotify event, serial 25, synthetic NO, window 0x4600001,
    root 0x152, subw 0x4600002, time 2870784, (22,35), root:(1422,119),
    state 0x0, is_hint 0, same_screen YES

MotionNotify event, serial 25, synthetic NO, window 0x4600001,
    root 0x152, subw 0x4600002, time 2870796, (23,35), root:(1423,119),
    state 0x0, is_hint 0, same_screen YES

MotionNotify event, serial 25, synthetic NO, window 0x4600001,
    root 0x152, subw 0x4600002, time 2870808, (27,34), root:(1427,118),
    state 0x0, is_hint 0, same_screen YES

MotionNotify event, serial 25, synthetic NO, window 0x4600001,
    root 0x152, subw 0x4600002, time 2870820, (34,35), root:(1434,119),
    state 0x0, is_hint 0, same_screen YES

MotionNotify event, serial 25, synthetic NO, window 0x4600001,
    root 0x152, subw 0x4600002, time 2870832, (40,36), root:(1440,120),
    state 0x0, is_hint 0, same_screen YES

MotionNotify event, serial 25, synthetic NO, window 0x4600001,
    root 0x152, subw 0x4600002, time 2870844, (45,38), root:(1445,122),
    state 0x0, is_hint 0, same_screen YES

MotionNotify event, serial 25, synthetic NO, window 0x4600001,
    root 0x152, subw 0x4600002, time 2870856, (49,40), root:(1449,124),
    state 0x0, is_hint 0, same_screen YES

MotionNotify event, serial 25, synthetic NO, window 0x4600001,
    root 0x152, subw 0x4600002, time 2870869, (51,41), root:(1451,125),
    state 0x0, is_hint 0, same_screen YES

MotionNotify event, serial 25, synthetic NO, window 0x4600001,
    root 0x152, subw 0x4600002, time 2870880, (52,42), root:(1452,126),
    state 0x0, is_hint 0, same_screen YES

MotionNotify event, serial 25, synthetic NO, window 0x4600001,
    root 0x152, subw 0x4600002, time 2870904, (52,42), root:(1452,126),
    state 0x0, is_hint 0, same_screen YES

MotionNotify event, serial 25, synthetic NO, window 0x4600001,
    root 0x152, subw 0x4600002, time 2870916, (52,43), root:(1452,127),
    state 0x0, is_hint 0, same_screen YES

MotionNotify event, serial 25, synthetic NO, window 0x4600001,
    root 0x152, subw 0x4600002, time 2870928, (52,44), root:(1452,128),
    state 0x0, is_hint 0, same_screen YES

MotionNotify event, serial 25, synthetic NO, window 0x4600001,
    root 0x152, subw 0x4600002, time 2870941, (53,45), root:(1453,129),
    state 0x0, is_hint 0, same_screen YES

MotionNotify event, serial 25, synthetic NO, window 0x4600001,
    root 0x152, subw 0x4600002, time 2870953, (53,46), root:(1453,130),
    state 0x0, is_hint 0, same_screen YES

MotionNotify event, serial 25, synthetic NO, window 0x4600001,
    root 0x152, subw 0x4600002, time 2870977, (54,46), root:(1454,130),
    state 0x0, is_hint 0, same_screen YES

MotionNotify event, serial 25, synthetic NO, window 0x4600001,
    root 0x152, subw 0x4600002, time 2870989, (55,47), root:(1455,131),
    state 0x0, is_hint 0, same_screen YES

MotionNotify event, serial 25, synthetic NO, window 0x4600001,
    root 0x152, subw 0x4600002, time 2871001, (56,48), root:(1456,132),
    state 0x0, is_hint 0, same_screen YES

MotionNotify event, serial 25, synthetic NO, window 0x4600001,
    root 0x152, subw 0x4600002, time 2871014, (56,48), root:(1456,132),
    state 0x0, is_hint 0, same_screen YES

MotionNotify event, serial 25, synthetic NO, window 0x4600001,
    root 0x152, subw 0x4600002, time 2871037, (57,48), root:(1457,132),
    state 0x0, is_hint 0, same_screen YES

MotionNotify event, serial 25, synthetic NO, window 0x4600001,
    root 0x152, subw 0x4600002, time 2871050, (57,49), root:(1457,133),
    state 0x0, is_hint 0, same_screen YES

ButtonPress event, serial 25, synthetic NO, window 0x4600001,
    root 0x152, subw 0x4600002, time 2871281, (57,49), root:(1457,133),
    state 0x0, button 1, same_screen YES

EnterNotify event, serial 25, synthetic NO, window 0x4600001,
    root 0x152, subw 0x0, time 2871281, (57,49), root:(1457,133),
    mode NotifyGrab, detail NotifyInferior, same_screen YES,
    focus YES, state 256

ButtonRelease event, serial 25, synthetic NO, window 0x4600001,
    root 0x152, subw 0x4600002, time 2871339, (57,49), root:(1457,133),
    state 0x100, button 1, same_screen YES

LeaveNotify event, serial 25, synthetic NO, window 0x4600001,
    root 0x152, subw 0x0, time 2871339, (57,49), root:(1457,133),
    mode NotifyUngrab, detail NotifyInferior, same_screen YES,
    focus YES, state 0

ButtonPress event, serial 25, synthetic NO, window 0x4600001,
    root 0x152, subw 0x4600002, time 2871836, (57,49), root:(1457,133),
    state 0x0, button 1, same_screen YES

EnterNotify event, serial 25, synthetic NO, window 0x4600001,
    root 0x152, subw 0x0, time 2871836, (57,49), root:(1457,133),
    mode NotifyGrab, detail NotifyInferior, same_screen YES,
    focus YES, state 256

ButtonRelease event, serial 25, synthetic NO, window 0x4600001,
    root 0x152, subw 0x4600002, time 2872016, (57,49), root:(1457,133),
    state 0x100, button 1, same_screen YES

LeaveNotify event, serial 25, synthetic NO, window 0x4600001,
    root 0x152, subw 0x0, time 2872016, (57,49), root:(1457,133),
    mode NotifyUngrab, detail NotifyInferior, same_screen YES,
    focus YES, state 0

ButtonPress event, serial 25, synthetic NO, window 0x4600001,
    root 0x152, subw 0x4600002, time 2872417, (57,49), root:(1457,133),
    state 0x0, button 1, same_screen YES

EnterNotify event, serial 25, synthetic NO, window 0x4600001,
    root 0x152, subw 0x0, time 2872417, (57,49), root:(1457,133),
    mode NotifyGrab, detail NotifyInferior, same_screen YES,
    focus YES, state 256

MotionNotify event, serial 25, synthetic NO, window 0x4600001,
    root 0x152, subw 0x4600002, time 2872598, (56,56), root:(1456,140),
    state 0x100, is_hint 0, same_screen YES

MotionNotify event, serial 25, synthetic NO, window 0x4600001,
    root 0x152, subw 0x4600002, time 2872611, (54,63), root:(1454,147),
    state 0x100, is_hint 0, same_screen YES

EnterNotify event, serial 25, synthetic NO, window 0x4600001,
    root 0x152, subw 0x0, time 2872622, (51,73), root:(1451,157),
    mode NotifyNormal, detail NotifyInferior, same_screen YES,
    focus YES, state 256

MotionNotify event, serial 25, synthetic NO, window 0x4600001,
    root 0x152, subw 0x0, time 2872622, (51,73), root:(1451,157),
    state 0x100, is_hint 0, same_screen YES

MotionNotify event, serial 25, synthetic NO, window 0x4600001,
    root 0x152, subw 0x0, time 2872634, (45,83), root:(1445,167),
    state 0x100, is_hint 0, same_screen YES

MotionNotify event, serial 25, synthetic NO, window 0x4600001,
    root 0x152, subw 0x0, time 2872646, (38,93), root:(1438,177),
    state 0x100, is_hint 0, same_screen YES

MotionNotify event, serial 25, synthetic NO, window 0x4600001,
    root 0x152, subw 0x0, time 2872659, (33,100), root:(1433,184),
    state 0x100, is_hint 0, same_screen YES

MotionNotify event, serial 25, synthetic NO, window 0x4600001,
    root 0x152, subw 0x0, time 2872671, (30,105), root:(1430,189),
    state 0x100, is_hint 0, same_screen YES

MotionNotify event, serial 25, synthetic NO, window 0x4600001,
    root 0x152, subw 0x0, time 2872683, (28,107), root:(1428,191),
    state 0x100, is_hint 0, same_screen YES

MotionNotify event, serial 25, synthetic NO, window 0x4600001,
    root 0x152, subw 0x0, time 2872695, (27,108), root:(1427,192),
    state 0x100, is_hint 0, same_screen YES

MotionNotify event, serial 25, synthetic NO, window 0x4600001,
    root 0x152, subw 0x0, time 2872708, (27,109), root:(1427,193),
    state 0x100, is_hint 0, same_screen YES

MotionNotify event, serial 25, synthetic NO, window 0x4600001,
    root 0x152, subw 0x0, time 2872720, (27,109), root:(1427,193),
    state 0x100, is_hint 0, same_screen YES

MotionNotify event, serial 25, synthetic NO, window 0x4600001,
    root 0x152, subw 0x0, time 2872780, (26,113), root:(1426,197),
    state 0x100, is_hint 0, same_screen YES

MotionNotify event, serial 25, synthetic NO, window 0x4600001,
    root 0x152, subw 0x0, time 2872792, (25,119), root:(1425,203),
    state 0x100, is_hint 0, same_screen YES

MotionNotify event, serial 25, synthetic NO, window 0x4600001,
    root 0x152, subw 0x0, time 2872804, (25,125), root:(1425,209),
    state 0x100, is_hint 0, same_screen YES

MotionNotify event, serial 25, synthetic NO, window 0x4600001,
    root 0x152, subw 0x0, time 2872816, (24,129), root:(1424,213),
    state 0x100, is_hint 0, same_screen YES

ButtonRelease event, serial 25, synthetic NO, window 0x4600001,
    root 0x152, subw 0x0, time 2872827, (24,129), root:(1424,213),
    state 0x100, button 1, same_screen YES

MotionNotify event, serial 25, synthetic NO, window 0x4600001,
    root 0x152, subw 0x0, time 2873857, (14,132), root:(1414,216),
    state 0x0, is_hint 0, same_screen YES

MotionNotify event, serial 25, synthetic NO, window 0x4600001,
    root 0x152, subw 0x0, time 2873868, (2,136), root:(1402,220),
    state 0x0, is_hint 0, same_screen YES

LeaveNotify event, serial 25, synthetic NO, window 0x4600001,
    root 0x152, subw 0x0, time 2873881, (-12,141), root:(1388,225),
    mode NotifyNormal, detail NotifyNonlinear, same_screen YES,
    focus YES, state 0

EnterNotify event, serial 25, synthetic NO, window 0x4600001,
    root 0x152, subw 0x0, time 2877498, (2,10), root:(1402,94),
    mode NotifyNormal, detail NotifyAncestor, same_screen YES,
    focus YES, state 0

MotionNotify event, serial 25, synthetic NO, window 0x4600001,
    root 0x152, subw 0x0, time 2877498, (2,10), root:(1402,94),
    state 0x0, is_hint 0, same_screen YES

MotionNotify event, serial 25, synthetic NO, window 0x4600001,
    root 0x152, subw 0x0, time 2877510, (6,8), root:(1406,92),
    state 0x0, is_hint 0, same_screen YES

MotionNotify event, serial 25, synthetic NO, window 0x4600001,
    root 0x152, subw 0x0, time 2877522, (9,6), root:(1409,90),
    state 0x0, is_hint 0, same_screen YES

MotionNotify event, serial 25, synthetic NO, window 0x4600001,
    root 0x152, subw 0x0, time 2877535, (10,5), root:(1410,89),
    state 0x0, is_hint 0, same_screen YES

MotionNotify event, serial 25, synthetic NO, window 0x4600001,
    root 0x152, subw 0x0, time 2877546, (10,5), root:(1410,89),
    state 0x0, is_hint 0, same_screen YES

MotionNotify event, serial 25, synthetic NO, window 0x4600001,
    root 0x152, subw 0x0, time 2877571, (10,4), root:(1410,88),
    state 0x0, is_hint 0, same_screen YES

MotionNotify event, serial 25, synthetic NO, window 0x4600001,
    root 0x152, subw 0x0, time 2877583, (5,4), root:(1405,88),
    state 0x0, is_hint 0, same_screen YES

LeaveNotify event, serial 25, synthetic NO, window 0x4600001,
    root 0x152, subw 0x0, time 2877594, (-2,4), root:(1398,88),
    mode NotifyNormal, detail NotifyAncestor, same_screen YES,
    focus YES, state 0

ClientMessage event, serial 25, synthetic YES, window 0x4600001,
    message_type 0x14d (WM_PROTOCOLS), format 32, message 0x14b (WM_DELETE_WINDOW)

```
NOW Bring on the Breakage. :)

---

### Post by jbicha on 2019-10-22
By the way, it is so early in the release cycle that the archive is still closed except for some early [preparation work]("https://lists.ubuntu.com/archives/ubuntu-devel/2019-October/040817.html") (mostly involving perl and python3.8 updates).

That means that the Ubuntu MATE developers aren't able to directly make uploads to fix issues. Also, most developers are still using Ubuntu 19.10.

---

### Post by #&amp;thj^% on 2019-10-23
Just a first look is all. :D
Of course I know its still Very early.;)
Thanks for the info though.

---

### Post by #&amp;thj^% on 2019-10-29
Fixed a few things, I installed (compiled) compiz-reloaded had to maximize windows first to close it. (It was related to drawing the desktop background) (_Just Noting is all no need for reply's_ ;)) 
Now to find how to tweak the clock again. :( they hid it good this time. LOL
Both Mate and XFCE4 are starting to shape up nicely. (Conky-manager still installs here)
Some of my hacks need a bit of work though.
All in All so far I'm a little more impressed, and a long way to go yet.
If someone could answer why they want the Clock so "hard coded" I be Interested in hearing that reasoning. (Small thing for some, not here though)

---

