---
title: "Improved WoW performance with NVIDIA override application settings"
date: 2009-01-04
forum: Wine
---

### Post by Elviswind on 2009-01-04
I was experiencing some issues in Northend where my FPS would drop down to below 5 in certain areas (seems to be related to full screen shaking effect such as experienced in Wintergarde Keep).  I could recover sometimes with: ```
/console gxRestart
```
Occasionally, this would result in a crash.  In general, in Northend, setting MS to 1x in WoW would avoid these problems, but my personal preference is to have some antialiasing for a more visually pleasing experience.

What I've found to help this issue, and also seems to result in an increase in FPS, is to use the NVIDIA X Server Settings to override the application control of antialiasing and anisotropic filtering.  For good measure, within WoW, I also set the MS to 1x and the Texture Filtering to low.

I also experimented with using the NVIDIA X Server Settings to force vertical sync and found that it did **not** work as well as forcing vertical sync in WoW.

From my experiments, I decided to leave Full-Screen Glow Effect (bloom?) off within WoW.

With these settings, I was able to eliminate (so far) the need to occasionally restart the graphics engine in WoW while in Northend and also have some antialiasing.

**Setup**

I am **not** using the registry tweak.

My Config.wtf includes: ```
SET gxApi "OpenGL"
```
but **not**: ```
SET SoundOutputSystem "1"
SET SoundBufferSize "150"
```

I am **not** loading WoW in its own session of X.

I have **not** disabled NVIDIA PowerMizer, nor do I have any reason to suspect that it is throttling my GPU performance while playing WoW.

My hardware is:
[LIST]
[*]Intel C2D E8400
[*](2) 1GiB DDR2 @ 800 MHz
[*]NVIDIA 9800GT
[/LIST]

My software is:
[LIST]
[*]Xubuntu Release 8.10 (intrepid)
[*]Kernel Linux 2.6.27-9-generic
[*]wine 1.1.12~winehq0~ubuntu~8.10-0ubuntu1 (intrepid)
[*]NVIDIA 180.18 (this is a beta driver and was manually installed)
[/LIST]

Screenshots of my NVIDIA and WoW settings are attached.  The key parameters are, within the NVIDIA control panel, set to override antialiasing and anisotropic filtering, and within WoW set to multisampling to 1x and texture filtering to Low.  All other settings can be set to whatever is your personal preference between performance and rendering quality at your resolution.

Hope this helps someone!  :D

---

