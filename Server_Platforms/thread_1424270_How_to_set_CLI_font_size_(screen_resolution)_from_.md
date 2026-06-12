---
title: "How to set CLI font size (screen resolution) from CLI"
date: 2010-03-07
forum: Server Platforms
---

### Post by qajaq on 2010-03-07
I've just installed Ubunter Server 9.04 (after having installed 9.10, having problems with it, and uninstalling it). Mostly, 9.04 is working well so far, but for one nuisance: the font is huge.

Well, okay, not huge, but big. On my other machine, running Ubuntu 9.04 desktop, same size monitor, I have the resolution set to 1440x900 which gives me 46 lines on the CLI (with the window maximized, but not full-screen). On the server machine, however, I'm getting only 25 lines -- and there's not even a window title-bar, menu bar, or panels taking up any of the landscape.

So my question is this: Not having a GUI nor any of the associated display-management software, how can I set the screen resolution or otherwise get my display font smaller, using the CLI?

---

### Post by adam814 on 2010-03-07
What you want to do is use a framebuffer console like "vesafb."

This should help:
[http://lab.frontseed.com/entry/enable-frambeuffer-ubuntu-karmic-koala-using-grub2](http://lab.frontseed.com/entry/enable-frambeuffer-ubuntu-karmic-koala-using-grub2)

---

### Post by qajaq on 2010-03-08
Thanks. As it turned out, it was even easier than that. When I read the page to which you pointed, I realized I'd had to edit my /boot/grub/menu.lst file to get the font-size I wanted on the desktop terminals. I did the same in the server's menu.lst and it worked a charm!

---

