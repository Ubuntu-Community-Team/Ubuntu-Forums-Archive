---
title: "Screen problem in wine with compositing &amp; open source ati driver"
date: 2009-05-09
forum: Wine
---

### Post by barisurum on 2009-05-09
Hi there folks;

I try to run a 2d game: dune2000 with metacity's compositing or compiz but it fails to set the fullscreen display. I only see my destop in 640x480 (the game's resolution) and I hear the sound, but no game display. Also Return to Castle Wolfenstein doesn't work, I only see some flickering graphics of the game menu (game menu is not 2d but 3d in a 2d fashion). 

When I run them with no compositing, no problems, but I need awm dock. Is there a way to solve this? Thank you all.

---

### Post by cogadh on 2009-05-10
Wine and Compiz do not get along at all. From Wine's perspective, Compiz breaks OpenGL functionality and almost anything that might make use of your graphics hardware will not work correctly. From the Wine [FAQ]("http://wiki.winehq.org/FAQ#head-db2fa150a8b8f906508959b92beb00768ec6ec47"):
> [B]6.24. I'm using Desktop Effects with Compiz, Fusion, or XGL and get poor performance/odd messages/broken applications
[/B]
Using composite display managers in Linux tends to cripple OpenGL performance or break OpenGL entirely. We recommend that you disable them entirely before trying to use Wine. If you are using one and experiencing slow performance then please do not file bugs in Wine, as these are bugs in your window manager or your video drivers. Also, disabling the Composite extension within /etc/X11/xorg.conf will most certainly prevent any compositing from affecting Wine.

---

### Post by barisurum on 2009-05-10
Thanks codagh. I will try with composite extension removed then. If I experience performance loss I will report here. Cheers!

---

### Post by barisurum on 2009-05-10
Nope, removing composite extension from xorg.conf didn't help with the problem. Any suggestions for a fix? I really love to work with awm dock and its the only thing that needs compositing in my desktop.

---

