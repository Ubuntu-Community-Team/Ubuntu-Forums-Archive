---
title: "Installing xserver on ubuntu server (not desktop)"
date: 2007-08-21
forum: Server Platforms
---

### Post by endfx on 2007-08-21
I have an ubuntu server and would like to install Xserver on it so it.
The server won't need to run a window manager, I just need the X server running on it so I can use X11 forwarding to a windows machine.

Can somebody tell me what packages I need to install to get xserver running on Ubuntu Server (Note, that I don't want the whole desktop package).

I've installed xserver-xorg but I don't think that's everything I need.

Thanks!

---

### Post by endfx on 2007-08-21
Figured it out in case somebody wants to know:

1. Install xserver-xorg
2. Install xfonts-base xfonts-100dpi xfonts-75dpi

---

