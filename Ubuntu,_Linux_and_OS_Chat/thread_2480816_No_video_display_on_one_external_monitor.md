---
title: "No video display on one external monitor"
date: 2022-11-11
forum: Ubuntu, Linux and OS Chat
---

### Post by michaellongtoolstation on 2022-11-11
[COLOR=#333333][FONT=&amp]Good morning,

Apologies if this is not the correct forum.


I am wondering if someone is able to help; an issue has appeared with my work laptop very suddenly. I left my laptop for an hours break, came back & there was no display on the external monitor.


The system did upgrade from 20.04 LTS to 22.04 recently but the display seemed to work.


**Objective:** output display on HDMI
**Problem:** Cannot display on external monitor; note hooking up to a TV using the same cable on HDMI works. The monitor in question itself is working just fine as it works with my other linux distro & Windows PC that I have.
**Attempts:** Re-install kernel & headers & nvidia drivers
**Kernel: 5.17.0-1003-oem**
[B]Driver ver: 520.56.06
[/B]
I am not able to upload the nvidia bug report file so I can paste parts if needed?

Fri Nov 11 09:28:54 2022
±----------------------------------------------------------------------------+
| NVIDIA-SMI 520.56.06 Driver Version: 520.56.06 CUDA Version: 11.8 |
|-------------------------------±---------------------±---------------------+
| GPU Name Persistence-M| Bus-Id Disp.A | Volatile Uncorr. ECC |
| Fan Temp Perf Pwr:Usage/Cap| Memory-Usage | GPU-Util Compute M. |
| | | MIG M. |
|===============================+======================+======================|
| 0 NVIDIA T600 Lap&#8230; Off | 00000000:01:00.0 Off | N/A |
| N/A 49C P0 N/A / N/A | 4MiB / 4096MiB | 0% Default |
| | | N/A |
±------------------------------±---------------------±---------------------+
±----------------------------------------------------------------------------+
| Processes: |
| GPU GI CI PID Type Process name GPU Memory |
| ID ID Usage |
|=============================================================================|
| 0 N/A N/A 2909 G /usr/lib/xorg/Xorg 4MiB |
±----------------------------------------------------------------------------+
Screen 0: minimum 320 x 200, current 1920 x 1080, maximum 16384 x 16384
eDP-1 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 344mm x 194mm
1920x1080 60.05*+ 60.01 59.97 59.96 59.93
1680x1050 59.95 59.88
1600x1024 60.17
1400x1050 59.98
1600x900 59.99 59.94 59.95 59.82
1280x1024 60.02
1440x900 59.89
1400x900 59.96 59.88
1280x960 60.00
1440x810 60.00 59.97
1368x768 59.88 59.85
1360x768 59.80 59.96
1280x800 59.99 59.97 59.81 59.91
1152x864 60.00
1280x720 60.00 59.99 59.86 59.74
1024x768 60.04 60.00
960x720 60.00
928x696 60.05
896x672 60.01
1024x576 59.95 59.96 59.90 59.82
960x600 59.93 60.00
960x540 59.96 59.99 59.63 59.82
800x600 60.00 60.32 56.25
840x525 60.01 59.88
864x486 59.92 59.57
800x512 60.17
700x525 59.98
800x450 59.95 59.82
640x512 60.02
720x450 59.89
700x450 59.96 59.88
640x480 60.00 59.94
720x405 59.51 58.99
684x384 59.88 59.85
680x384 59.80 59.96
640x400 59.88 59.98
576x432 60.06
640x360 59.86 59.83 59.84 59.32
512x384 60.00
512x288 60.00 59.92
480x270 59.63 59.82
400x300 60.32 56.34
432x243 59.92 59.57
320x240 60.05
360x202 59.51 59.13
320x180 59.84 59.32
HDMI-1 disconnected (normal left inverted right x axis y axis)
DP-1 disconnected (normal left inverted right x axis y axis)
DP-2 disconnected (normal left inverted right x axis y axis)

Many thanks in advance.[/FONT][/COLOR]

---

