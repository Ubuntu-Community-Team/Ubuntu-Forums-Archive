---
title: "Zoneminder Server"
date: 2010-09-02
forum: Server Platforms
---

### Post by Liam Larks on 2010-09-02
Hi,
i tried setting up an experimental Zoneminder server on Ubuntu 8.04 LTS.
My webcam (Labtec Webcam Pro) is recognized by the server and displayed as video0.
> 
 zmu -d /dev/video -q -v 
Video Capabilities
  Name: Labtec Webcam Pro
  Type: 1
    Can capture
  Video Channels: 1
  Audio Channels: 0
  Maximum Width: 640
  Maximum Height: 480
  Minimum Width: 160
  Minimum Height: 120
Window Attributes
  X Offset: 0
  Y Offset: 0
  Width: 320
  Height: 240
Picture Attributes
  Palette: 4 - 24bit RGB
  Colour Depth: 24
  Brightness: 32768
  Hue: 0
  Colour :0
  Contrast: 32768
  Whiteness: 0
Channel 0 Attributes
  Name: ZC301-2
  Channel: 0
  Flags: 0
  Type: 2 - Camera
  Format: 2055 - Unknown

By this i guess the cam is working?
When i try to set up a monitor in  ZM using video0 there is no picture displayed.
My thesis is build on the unknown format 2055, but thats just a guess.
I'm still an ubuntu beginner.
Greetings Liam

---

