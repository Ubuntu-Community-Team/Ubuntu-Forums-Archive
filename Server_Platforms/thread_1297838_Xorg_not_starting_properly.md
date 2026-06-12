---
title: "Xorg not starting properly"
date: 2009-10-22
forum: Server Platforms
---

### Post by Diubidone on 2009-10-22
Hi all,

I had to install an ubuntu server (I used 9.04), after the installation I installed a minimal gnome gdm interface (requested to me).

The graphical interface didn't came up at restart, so I had to do a dpkg-reconfigure xorg-xserver. I had all the questions asked and reconfigured the thing.

Now the graphical interface starts, but it takes serveral minutes because before coming to the screen...it starts some loop operation looking for the screen. I get some errors about a screen not found, but then, as I said, eventually gnome comes up and starts correctly. Attached to this thread the part of the log that contains the error description.

I have a [Fujitsu Siemens]("http://ts.fujitsu.com/products/standard_servers/rack/primergy_rx100s5.html") with Matrox GRAPHICS MGA G200e video card.

xserver-xorg-video-mga is correctly installed. Anyone can help?

---

### Post by cdenley on 2009-10-22
Try using this option in the "Device" section of xorg.conf.
```

Option "UseFBDev" "false"

```

---

### Post by Diubidone on 2009-10-26
Hi,

After the modification made to xorg.xonf gdm doesn't even starts. I had to recover the precedent configuration and again with many problems the graphics finally started.

Anyone?

---

