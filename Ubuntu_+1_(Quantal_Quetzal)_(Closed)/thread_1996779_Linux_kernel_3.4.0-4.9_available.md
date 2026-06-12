---
title: "Linux kernel 3.4.0-4.9 available"
date: 2012-06-04
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by Harry33 on 2012-06-04
The newest version of the Linux kernel 3.4.0 is available for manual download and installation and will very soon hit the repos too.

Here:
[https://launchpad.net/ubuntu/quantal/+source/linux/3.4.0-4.9](https://launchpad.net/ubuntu/quantal/+source/linux/3.4.0-4.9)

---

### Post by Harry33 on 2012-06-05
There is 3.4.0-4.10 already.
Only minor checking changes though.

---

### Post by jerrylamos on 2012-06-06
Today's daily live is 3.4.0-5.11 whatever that means. I'm installing it now.

Jerry

---

### Post by zika on 2012-06-06
Is there anybody out there with knowledge about latest lowlatency and realtime kernel...?

---

### Post by fjgaude on 2012-06-06
Newest kernel working fine on Dell mini-10 and my main Intel box. No issues except with Prefs for Nautilus. That'll come I'm sure as time goes by.

Seems to be few errors msgs so far.

---

### Post by ventrical on 2012-06-06
Alpha1 install working great on this Dell Dimension 3100.

---

### Post by mildisaster on 2012-06-08
I thought kernel 3.4 was supposed to bring support for the AMD 7000 series graphics cards? I have a 7750 and am experiencing the same issues I was experiencing in Ubuntu 12.04.

---

### Post by jerrylamos on 2012-06-08
Also testing 3.4.0-4.? kernel back on precise as an LTS update candidate.  Working fine for what I've tried.

Jerry

---

### Post by fjgaude on 2012-06-08
On a fresh install of 12.04 LTS and then install the latest kernel:

```
Fri Jun  8 11:22:18 PDT 2012
Ubuntu 12.04 LTS
Linux 3.5.0-030500rc1-generic
unity 5.10.0

OpenGL vendor string:   Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) Sandybridge Desktop 
OpenGL version string:  3.0 Mesa 8.0.2

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes

Package: mesa-utils
Status: install ok installed
Priority: optional
Section: x11
Installed-Size: 148
Maintainer: Ubuntu X-SWAT <ubuntu-x@lists.ubuntu.com>
Architecture: amd64
Source: mesa-demos
Version: 8.0.1+git20110129+d8f7d6b-0ubuntu2
Replaces: xbase-clients (<< 6.8.2-38)
Depends: libc6 (>= 2.4), libgl1-mesa-glx | libgl1, libx11-6
Description: Miscellaneous Mesa GL utilities
 This package provides several basic GL utilities built by Mesa, including
 glxinfo and glxgears.
Homepage: http://mesa3d.sourceforge.net/
```

Then gtkperf:

```
GtkPerf 0.40 - Starting testing: Fri Jun  8 11:22:49 2012

GtkEntry - time:  0.02
GtkComboBox - time:  0.46
GtkComboBoxEntry - time:  0.30
GtkSpinButton - time:  0.06
GtkProgressBar - time:  0.05
GtkToggleButton - time:  0.40
GtkCheckButton - time:  0.06
GtkRadioButton - time:  0.11
GtkTextView - Add text - time:  0.48
GtkTextView - Scroll - time:  0.07
GtkDrawingArea - Lines - time:  0.63
GtkDrawingArea - Circles - time:  1.15
GtkDrawingArea - Text - time:  0.36
GtkDrawingArea - Pixbufs - time:  0.08
 --- 
Total time:  4.23
```

All that I've tried has worked correctly on my main box: Intel i5-2405S, using Z68 ASRock MB Model 68M-ITX/HT, booted using latest UEFI bios onto an SSD, linked to another SSD database.

---

