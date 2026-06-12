---
title: "Webcam Colours with Motion? - what's missing?"
date: 2011-08-07
forum: Server Platforms
---

### Post by Jose Catre-Vandis on 2011-08-07
Running server (10.04.3 LTS) - cli only
Have set up motion and connected an eyetoy webcam
Image colours are incorrect (blue is orange, red is blue)

Tested webcam against my Xubuntu 11.04 install and colours are correct using mplayer and ffplay, both through gui and console - e.g.:
```
mplayer tv:// device=/dev/video0
```

I tried viewing webcam with a connected monitor on the server in the same way, but just got a green and brown 8 colour image (probably incorrect settings for framebuffer?)

Tried the force_rgb=1 option but this doesn't seem to apply with the newer gspca module. Have googled but can't find any parameters/options for this module.

What is "missing" on the server install?

---

