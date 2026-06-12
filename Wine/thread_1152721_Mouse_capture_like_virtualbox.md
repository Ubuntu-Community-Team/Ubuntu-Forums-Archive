---
title: "Mouse capture like virtualbox"
date: 2009-05-08
forum: Wine
---

### Post by kevinwinner on 2009-05-08
Hi, I'm trying to run some games through Wine but I'm having lots of problems with the way Wine interacts with the rest of Ubuntu.  If I run Wine and tell it not to let the window manager control the window, I lose the window permanently the first time I minimize it.  If I don't run it that way, I keep triggering things like alt-ctrl-d which eventually ends up losing the window the same way (it's gone from my taskbar and I can't maximize it in any way I know of).

I had tried using VirtualBox for a while before realizing it couldn't handle directx at all.  I really liked it's ability to capture all keyboard/mouse events and was hoping there was a way to do this with Wine.  Any ideas?

---

### Post by cogadh on 2009-05-08
The only functionality like that in Wine is the "Allow DirectX apps to stop the mouse leaving their window" option (right above the window manager option), which doesn't always work right. Wine is not designed to work like a separate environment as virtual machines like VBox are. It is supposed to allow Windows applications to be integrated into the Linux environment, so I don't think a function that allows a Wine-run app to "steal" mouse control away from the rest of the OS is considered a required or even desirable option. Wine's handling of mouse control, especially with games, does need some improvement, but I doubt you will ever see it do what you want.

---

