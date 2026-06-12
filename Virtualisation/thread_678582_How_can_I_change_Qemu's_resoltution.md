---
title: "How can I change Qemu's resoltution?"
date: 2008-01-26
forum: Virtualisation
---

### Post by Alucard-sama on 2008-01-26
Whenever I launch a virtual machine in QEMU it always displays at 1024x768 and seeing as this is my actual screen resolution this means parts of the screen are cut off completely.
Is there any way to change the default resolution for QEMU.
PS: I'm using QEMU launcher.

---

### Post by BrainwreckedTech on 2009-05-21
You'll have to mess with the /etc/X11/xorg.conf file.  There's a couple of things that go wrong with the auto configuration of X under QEMU.  The emulated Cirrus Logic card never supported EDID (came out after its release) and only supports 1024x768 and 1280x1024 at 16-bit color due to memory limitations.

When X goes to auto-configure, it falls back on a safe HSync refresh range which ends up excluding 1280x1024 and 1024x768.  If you specify a custom Hsync refresh range to get the higher resolutions, the X server ends up in a crash-and-restart cycle over the use of 24-bit color.

Now that you know more than you bargained for, the auto-config tool in use for Xorg isn't all that bad.  It allows us to get away with a minimum xorg.conf file like this to solve the problem:

```
Section "Monitor"
  Identifier  "Monitor0"
  HorizSync   20.0 - 50.0
  VertRefresh 40.0 - 80.0
End Section

Section "Device"
  Identifier "Device0"
  Driver     "vesa"
EndSection

Section "Screen"
  Identifier   "Screen0"
  Device       "Device0"
  Monitor      "Monitor0"
  DefaultDepth 16
  Subsection "Display"
    Depth 16
    Modes "1024x768"
  EndSubsection
EndSection
```

Compare *that* to some of the hairy-scary X11 config files of not-too-long-ago.  ;)

You can replace "1024x768" with "800x600" or "640x480" if you want a smaller res, but I take it that's not what you want as those are available by default without any xorg.conf tweaking.  You can also get rid of the entire SubSection if you like the 1280x1024 resolution it'll end up choosing.

---

### Post by BrainwreckedTech on 2009-05-21
Go me for completely mis-reading your post.  #-o

How the heck *did* you get QEMU to always start up in 1024x768?  QEMU always uses whatever resolution the operating system you're emulating is using. The only OS I know of that uses a constant resolution is Mac OS as Mac monitors were only capable of one resolution.  Both Windows and any Linux distro will "jump around" a bit as video resolutions change during the boot process.

What's your host OS and guest OS?

---

### Post by 98cwitr on 2010-04-05
back from the dead, if I'm using xubuntu and don't have an xorg.conf file, how would I still achieve this same goal?

Edit: I downloaded and installed Ubuntu 9.10 and still no xorg.conf in the X11 dir, I do have:

app-defaults
cursors
fonts
xinit
Xsession
Xsession.d
XvMCConfig
rgb.txt
xkb
Xwrapper.config
default-display-manager
X
Xresrouces
Xsession.options

---

