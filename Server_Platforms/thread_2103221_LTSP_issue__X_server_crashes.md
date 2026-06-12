---
title: "LTSP issue:  X server crashes"
date: 2013-01-09
forum: Server Platforms
---

### Post by lykwydchykyn on 2013-01-09
I have an LTSP system built on Ubuntu 10.04 which has been running for a couple of years now.  During that time, I've had this issue crop up from time to time.  I haven't had much luck getting LTSP assistance here, but I thought I'd throw it out just to see if anyone has ideas.

The LTSP serves up our library's OPAC site to terminals around the library building.  The site has a few simple forms for doing things like applying for a library card, putting a hold on a book, etc.

I keep getting reports that while patrons are filling out the forms, the screen goes black and sends them back to the beginning.  It's not reproducible, and maybe happens once every few weeks when it happens.

The terminals run a custom browser written in Python (browser.py).  The problem also happened initially when we used other browsers (Midori and epiphany).

Here is a snippet of the log files from when the error occurs.  The LTSP server is "davros", the client is "ltsp100".
```

Jan  9 10:41:16 ltsp100 init: tty1 main process ended, respawning
Jan  9 10:41:16 davros ltsp100: browser.py: cannot connect to X server 192.168.175.100:1
Jan  9 10:41:17 davros ltsp100: last message repeated 3 times
Jan  9 10:41:17 davros ltsp100: Invalid MIT-MAGIC-COOKIE-1 keybrowser.py: cannot connect to X server 192.168.175.100:1
Jan  9 10:41:18 davros ltsp100: Invalid MIT-MAGIC-COOKIE-1 keybrowser.py: cannot connect to X server 192.168.175.100:1
Jan  9 10:41:17 ltsp100 init: tty1 main process ended, respawning
Jan  9 10:41:18 ltsp100 ldm[1630]: LDM2 running on ip address 192.168.175.100
Jan  9 10:41:18 ltsp100 ldm[1630]: rc_files: /bin/sh /usr/share/ldm/ldm-script init
Jan  9 10:41:18 ltsp100 ldm[1630]: ldm_spawn: pid = 1644
Jan  9 10:41:18 ltsp100 ldm[1630]: Waiting for process 1644
Jan  9 10:41:18 ltsp100 kernel: [27923.654971]  nbd9: unknown partition table
Jan  9 10:41:18 ltsp100 kernel: [27923.661912] nbd9: NBD_DISCONNECT
Jan  9 10:41:18 ltsp100 kernel: [27923.662347] nbd9: Receive control failed (result -32)
Jan  9 10:41:18 ltsp100 kernel: [27923.662413] nbd9: queue cleared

```

My best guess is that the client is losing connection with the network block device, causing X to crash.  Not sure why this happens when patrons fill out forms though...

So, fellow detectives and mystery-probers, any thoughts?

---

### Post by lykwydchykyn on 2013-01-15
bump... hoping against hope...

---

### Post by lykwydchykyn on 2013-02-19
Wanted to bump this again; users are telling me that certain keystrokes trigger the crash, though not consistently.  Hyphens, at-signs, or sometimes just the left shift key have all been reported.

This is truly frustrating.

---

### Post by lykwydchykyn on 2013-02-22
I know I'm talking to myself here, but I have more information, in case anyone reading this has an idea.

I have been able to reproduce the problem on a second system set up in my office.

Whenever I go to this page: ([https://library.williamson-tn.org/selfreg](https://library.williamson-tn.org/selfreg)), scroll down to either of the phone number fields, and start typing in symbols (SHIFT + number keys), it will eventually crash X11 (or maybe ldm?).  There's no one key it does it on consistently, nor any consistent number of keys.  It just randomly seems to crash if I type symbols in those fields.

This bug happens whether I use firefox, midori, or my own qtwebkit-based browser.  It's also not dependent on which window manager I use.

---

### Post by lykwydchykyn on 2013-04-09
Well, I upgraded to Precise, because on my test system this seemed to fix the problem.  Unfortunately in production, it doesn't.  In fact, it's worse because X crashes and doesn't respawn, leaving the users at a text login.

Here's what's in the Xorg log from the client when it crashes (previous output is from hours before):
```

[ 17055.573] (II) evdev: Vigor-Tech Generic USB-PS2: Close
[ 17055.573] (II) UnloadModule: "evdev"
[ 17055.573] (II) Unloading evdev
[ 17055.573] (II) evdev: Vigor-Tech Generic USB-PS2: Close
[ 17055.574] (II) UnloadModule: "evdev"
[ 17055.574] (II) Unloading evdev
[ 17055.574] (II) evdev: ES1978: Close
[ 17055.574] (II) UnloadModule: "evdev"
[ 17055.574] (II) Unloading evdev
[ 17055.574] (II) evdev: AT Translated Set 2 keyboard: Close
[ 17055.574] (II) UnloadModule: "evdev"
[ 17055.574] (II) Unloading evdev
[ 17055.575] (II) evdev: PS/2 Mouse: Close
[ 17055.575] (II) UnloadModule: "evdev"
[ 17055.575] (II) Unloading evdev
[ 17055.575] (II) UnloadModule: "synaptics"
[ 17055.575] (II) Unloading synaptics
[ 17055.595]  ddxSigGiveUp: Closing log
[ 17055.595] Server terminated successfully (0). Closing log file.

```

Here's the output of "setxkbmap -print" from the server (suggested by someone in #ltsp):
```

xkb_keymap {
        xkb_keycodes  { include "evdev+aliases(qwerty)" };
        xkb_types     { include "complete"      };
        xkb_compat    { include "complete"      };
        xkb_symbols   { include "pc+us+inet(evdev)+compose(ralt)"       };
        xkb_geometry  { include "pc(pc105)"     };
};


```

---

### Post by WattoDaToydarian on 2014-01-24
I have been having the same problem, after I login on the client X will crash and come back to the login screen.
The server is Ubuntu-Server 13.10 64bit and the LTSP client is XUbuntu-Desktop 32bit.
This is my .xsession-errors:
> Xsession: X session started for agent at Fri Jan 24 16:47:15 CST 2014
No protocol specified
xrdb: Resource temporarily unavailable xrdb: Can&#8217;t open display &#8216;:7&#8217;
No protocol specified
xhost: unable to open display &#8220;:7&#8221; No protocol specified
xhost: unable to open display &#8220;:7&#8221;
openConnection: connect: No such file or directory
cannot connect to brltty at :0
Script for cjkv started at run_im.
Script for default started at run_im.
No protocol specified
Script for cjkv started at run_im.
Script for default started at run_im.
No protocol specified
xfce4&#8212;session: Cannot open display:
Type &#8216;xfce4&#8212;session &#8212;&#8212;help&#8217; for usage.
Here are some errors from my dmesg:
> init: cryptdisks&#8212;enable main process (1130) killed by TERM signal
 nbd9: unknown partition table
block nbd9: NBD_DISCONNECT
block nbd9: Receive control failed (result &#8212;32)
block nbd9: queue cleared
 nbd9: unknown partition table
block nbd9: NBD_DISCONNECT
block nbd9: Receive control failed (result &#8212;32)
block nbd9: queue cleared
 nbd9: unknown partition table
block nbd9: NBD_DISCONNECT
block nbd9: Receive control tailed (result &#8212;32)
block nbd9: queue cleared

---

