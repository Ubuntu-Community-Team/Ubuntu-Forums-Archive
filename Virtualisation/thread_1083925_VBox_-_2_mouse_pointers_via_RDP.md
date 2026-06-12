---
title: "VBox - 2 mouse pointers via RDP"
date: 2009-03-01
forum: Virtualisation
---

### Post by tebbens on 2009-03-01
I have VirtualBox 2.1.4 installed on Ubuntu 8.04 64-bit
When I RemoteDesktop into one of the Windows Guest OSs I'm getting 2 mouse pointers.
Does anyone know a fix for this ?

Thanks !

---

### Post by SpecialAgent on 2009-03-14
Hi, yes try to install the Guest Additions (should be the same version as VirtualBox Version on the host) and update your /etc/X11/xorg.file.

Here is an example of my xorg.conf:

```

Section "Device"
        Identifier      "Configured Video Device"
        Driver          "vboxvideo"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "InputDevice"
        Identifier      "Keyboard0"
        Driver          "kbd"
        Option          "XkbModel" "pc105"
        Option          "XkbLayout" "de"
        Option          "XkbVariant" "nodeadkeys"
EndSection

Section "InputDevice"
        Identifier      "mouse"
        Driver          "vboxmouse"
        Option          "CorePointer"
EndSection

Section "Screen"
        Identifier      "Screen0"
        DefaultDepth    16
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

```

The only thing Im running into, is that the mouse is pretty unprecise.

Hope this helped.

---

