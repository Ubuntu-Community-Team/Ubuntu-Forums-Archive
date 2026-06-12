---
title: "popping sound when playing back videos using new webcam"
date: 2020-06-25
forum: Ubuntu/Debian BASED
---

### Post by kevinstevens on 2020-06-25
Hello all,
 
 
 I had just purchased a new web cam and plugged it in to my Linux machine which is running Pop! OS 20.04 (based on the latest Ubuntu OS). I recorded some videos for testing, some using Cheese that was preinstalled and some using OBS Studio for Linux. When playing back the video, there is this continuous popping sound. I tried researching this and found a few items I tried.  
 
 
 1. sudo apt install alsa-tools
    Created and save a script in /usr/local/bin:
 ---------------------------------
 #!/bin/bash  
 hda-verb /dev/snd/hwC0D0 0x20 SET_COEF_INDEX 0x67
 hda-verb /dev/snd/hwC0D0 0x20 SET_PROC_COEF 0x3000`
 ------------------------------------
 Ran the script as root in a terminal.
 
 
 2. /etc/modprobe.d/alsa-base.conf
 Added the below line
 options snd-hda-intel power_save=0 power_save_controller=N
 
 
 3. Emailed the Video to someone else and the same thing happens. to me, this suggests it happens on creation of the video – perhaps I’m wrong but it’s what makes sense to me at least.
 
 
 4. Unplugged the headset/microphone and only used speakers.
 
 
 5. Unplugged speakers and only used headset.
 
 
 6. Changed 1 to 0 in /sys/module/snd_hda_intel/parameters/power_save
     Changed Y to N in /sys/module/snd_hda_intel/parameters/power_save_controller
 
 
 7.  in /etc/pulse/default.pa
 changed load-module module-udev-detect
 to load-module module-udev-detect tsched=0
 
 
 8. pulseaudio -k && sudo alsa force-reload
 It sounds like horses galloping after this
 
 
 9. Using the same webcam, created a video on a windows laptop. This worked fine so the webcam and integrated microphone seems to be fine.
 
 
 10. Note that I am able to listen to anything else with no issues. It is only when playing back my own video recordings on my Linux desktop.
 
 
 
 
 lspci | grep -i audio
 0a:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Raven/Raven2/Fenghuang HDMI/DP Audio Controller
 0a:00.6 Audio device: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 10h-1fh) HD Audio Controller
 
 
 cat /proc/asound/card0/codec* | grep Codec
 Codec: [COLOR=#c9211e]ATI R6xx HDMI[/COLOR]
 
 
 hostnamectl
 Operating System: [COLOR=#c9211e]Pop!_OS 20.04 LTS[/COLOR]
 Kernel: [COLOR=#c9211e]Linux 5.4.0-7634-generic[/COLOR]
 
 
 lsusb
 Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
 Bus 005 Device 002: ID 18f8:0f99 [Maxxter] Optical gaming mouse
 Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
 Bus 004 Device 002: ID 0bda:0411 Realtek Semiconductor Corp. 4-Port USB 3.0 Hub
 Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
 Bus 003 Device 003: ID 0bda:5411 Realtek Semiconductor Corp. 4-Port USB 2.0 Hub
 [COLOR=#c9211e]**Bus 003 Device 004: ID 0c45:6366 Microdia USB Color Camera**[/COLOR]
 Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
 Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
 Bus 001 Device 003: ID 1209:1776 Generic Io
 Bus 001 Device 004: ID 8087:0025 Intel Corp.  
 Bus 001 Device 002: ID 0e6a:02c0 Megawin Technology Co., Ltd PS/2+USB Keyboard
 Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by ajgreeny on 2020-06-25
*Thread moved to **Ubuntu/Debian BASED**.* which is more appropriate and a better fit.

---

