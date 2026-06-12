---
title: "shutdown WM back to server"
date: 2006-09-20
forum: Server Platforms
---

### Post by knuth_ on 2006-09-20
gives me following: ```
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom No such file or directory
FreeFontPath: FPE "/usr/share/X11/fonts/misc" refcount is 2, should be 1; fixing
.
Waiting for X Server to shut down
```

tried to fix that in /etc/X11/xorg.conf: ```
Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"              "/dev/wacom"    # Change to
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY 
```

deleted the whole Section "InputDevices" but then i had to reconfigure the X Server:( . Tried to delete only the wacom-entries but without success too.

I have only a server-installation (xserver-xorg, x-window-system-core and xterm with openbox, fbpanel, rox-filer). i had installed another WM - the same.

---

### Post by spp on 2006-09-22
Comment out the  the devices, remove the lines in the ServerLayout section (there will be Input "stylus" near the bottom), and you should be golden. 

SP

---

