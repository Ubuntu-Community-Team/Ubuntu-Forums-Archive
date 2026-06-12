---
title: "S-video capture in Linux using August or Diamond cx23102 A/V decoder capture units"
date: 2023-01-17
forum: Ubuntu, Linux and OS Chat
---

### Post by Mr Pestle on 2023-01-17
Task: analog to digital capture/convertion of Hi8 tapes via S-video in Linux
System: Dell OptiPlex 7080, Intel i5 processor OS:Ubuntu 22.04.1 LTS  Gnome version:42.5 Windowing system: x11

Plugged in August VGB-100 capture unit into a UBS Hub. Linjux recognises it...
videodev: Linux video capture interface: v2.00
cx231xx 1-9.1.1:1.1: New device Geniatech Inc. Video Capture @ 480 Mbps (1f4d:0102) with 6 interfaces
cx231xx 1-9.1.1:1.1: Identified as Geniatech OTG102 (card=17)
i2c i2c-10: Added multiplexed i2c bus 12
i2c i2c-10: Added multiplexed i2c bus 13
cx25840 9-0044: cx23102 A/V decoder found @ 0x88 (cx231xx #0-0)
cx25840 9-0044: loaded v4l-cx231xx-avcore-01.fw firmware (16382 bytes)
cx231xx 1-9.1.1:1.1: v4l2 driver version 0.0.3
cx231xx 1-9.1.1:1.1: Registered video device video0 [v4l2]
cx231xx 1-9.1.1:1.1: Registered VBI device vbi0
cx231xx 1-9.1.1:1.1: video EndPoint Addr 0x84, Alternate settings: 5
cx231xx 1-9.1.1:1.1: VBI EndPoint Addr 0x85, Alternate settings: 2
cx231xx 1-9.1.1:1.1: sliced CC EndPoint Addr 0x86, Alternate settings: 2
usbcore: registered new interface driver cx231xx
cx231xx 1-9.1.1:1.1: audio EndPoint Addr 0x83, Alternate settings: 3
cx231xx 1-9.1.1:1.1: Cx231xx Audio Extension initialized

Tried to use VLC -  Media - Convert/save - capture device - capture mode Video Camera, Video device name: /dev/video0,  Audio device name: Hw:3,0, Video standard PAL
Result - sound only - blue screen - no video - tried tweaking numerous settings but never successful.

Tried to use OBS - Sources - Video Capture device (V4L2) + Mic/Aux. Device shows as Geniatech OTG102  Input: S-video Video format: YUYV 4:2:2  Colour range: Full
Result- sound plus black and white video

Work-around to get colour video with sound.
Boot up Windows 10 (dual boot system with Linux) or run Windows VM under Linux. Install and Open the Windows Capture software program supplied with your capture unit. (E.g EzGrabber) 
Check it shows colour video. (With VM - You will need to redirect usb video capture unit to VM) - Close the app and shutdown VM or reboot back into Linux.
Now OBS shows colour video with sound :-)

I hope this helps some of you and that it gives some pointers to someone to tweak the linux drivers to achieve colour output from S-video with Cx231xx firmware?

---

