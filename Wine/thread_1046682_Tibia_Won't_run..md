---
title: "Tibia: Won't run."
date: 2009-01-21
forum: Wine
---

### Post by lordpoee on 2009-01-21
Hiya folks. Been having an issue with my Averatec 3250

OS Version: Ubuntu 8.10 (All updates installed)
Processor 1.6 Ghz
RAM 512

Now, I have ran Tibia under wine on some serious junk boxes...for some reason that's not happening on this machine.

But WINE I will leave for another day.

What I would LIKE to do is get the LINUX version of Tibia running.

When I run ./StartTibia.sh

I get the following error.

BadDrawable (Invalid Pixmap or Window Parameter)
Major opcode of failed request: 128 (XFree86-DRI)


glx is installed, I also have the VIA Technologies VT8378 openchrome drive installed.

I have added the line;

section "Modules"
        Load       "glx"
        Load       "dri"
EndSection

to /etc/X11/xorg.conf

None of that is working. 
THERE IS A SOLUTION. Help me find it, thank you.

I found the solution!
[https://help.ubuntu.com/community/OpenChrome#openChrome%20and%203D](https://help.ubuntu.com/community/OpenChrome#openChrome%20and%203D)
[MODS MAY CLOSE THREAD]

---

