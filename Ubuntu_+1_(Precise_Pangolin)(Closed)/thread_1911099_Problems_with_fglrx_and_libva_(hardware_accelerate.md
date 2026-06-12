---
title: "Problems with fglrx and libva (hardware accelerated video)? Try this."
date: 2012-01-18
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by jfernyhough on 2012-01-18
VLC started crashing on me with hardware acceleration enabled. I'd also found XBMC to crash with libva enabled, but I just thought that was XBMC.

Firstly I installed vdpau-va-driver and xvba-va-driver. I'm not sure if I needed both, but hey.

VLC was segfaulting with something along these lines:
```
libva: libva version 0.32.0
Xlib:  extension "XFree86-DRI" missing on display ":0".
libva: va_getDriverName() returns 0
```Getting  it to work I had to:

$ export  LIBVA_DRIVER_NAME=xvba
$ vlc

Works around the problem without the need for a patched VLC.

Added bonus to stream the snooker to VLC:
```
get_iplayer --type=livetv --url="http://news.bbc.co.uk/sport1/hi/snooker/15973141.stm" --stream --player='vlc -' --force
```Note the 'vlc **-**' which is needed to get it to stream from stdin.

XBMC also segfaulted at the same point, and again this works:

$ export  LIBVA_DRIVER_NAME=xvba
$ xbmc

Whoathunkit?

---

