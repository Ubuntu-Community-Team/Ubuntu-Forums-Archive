---
title: "Headless Server, x11vnc and resolution"
date: 2016-09-23
forum: Server Platforms
---

### Post by scambro on 2016-09-23
This is driving me nuts and every time I think I have it when the server reboots, it turns out I was wrong.  I have a headless server that I will access over SSH 95% of the time and the rest via VNC.  I believe I figured out how to connect using x11vnc without having a monitor attached, but after my latest reboot, the resolution I'm getting now via VNC is 640x480.  I'm trying all my usual tricks to set the resolution to something higher, but without a monitor it seems to be rejecting it.  

When I use xrandr inside the vnc session, I can add the mode I want, but when I set it I get "failed to get gamma size for output default" followed by "Configure crtc 0 failed."

Is there a quick way to setup a headless server that will have a desktop I can connect to over VNC in a 'normal' resolution?  Something at least 1024x768....  

Thanks!

---

