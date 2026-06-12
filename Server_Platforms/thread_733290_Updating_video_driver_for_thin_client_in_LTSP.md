---
title: "Updating video driver for thin client in LTSP"
date: 2008-03-23
forum: Server Platforms
---

### Post by cchoffman on 2008-03-23
I'm a linux noob, so please bear with me.  I know a little bit of my way around the system, but ltsp is a whole new environment for me.  I'e done some searching, but part of my problem is that I don't know exactly what to search for.  Here's the quick version of my story:

I've got Edubuntu server 7.10 installed on a Dell Inspiron 531 desktop, and diskless thin clients (one so far) running on an Intel D210GLY2 motherboard.  Everything seems to go well, expect the video drivers for the SIS Mirage 1 video chipset display vertical line "noise".  I've found an updated video driver for the video chipset thanks to Intel recently releasing one, but I here's where I'm stuck.

The files are "sis_drv.so" and "sis_drv.la".  Where do I put these so that the thin clients will use these drivers to display the video? and what other steps must I take?  I've got everything else running the way I want it.  (Haven't tested sound yet, though).

Thanks,

---

### Post by fausto@6comm.net on 2008-06-20
Hello, sorry for bothering you, but
Did you find a solution for this problem?
I am stuck on the very same situation
Thanks in advance for any comment
Regards, Fausto

---

### Post by salvador_luna on 2008-06-20
These drivers are for linux or windows? I'm not an expert but i think you get the updated drivers for video cards from the update manager, and i think there is no way to use windows drivers in GNU/Linux, but maybe i'm wrong.

---

### Post by fausto@6comm.net on 2008-06-20
It's Linux
D201GLY is a diskless PC booting through PXE from a Ubuntu LTSP server.
I got the drivers, but I don't know what to do for them to be used from the thinclient.
read the original post for more details
Thanks for your comments
F

---

### Post by cchoffman on 2008-06-21
These are linux drivers, available directly from Intel.  I'm too much of a linux noob (trying to change that, slowly), I just don't know how to get the thin client to use those drivers when it boots off of the server.  I prefer to keep these thin clients diskless, if at all possible, but the video isn't really usable in it's current state.

---

