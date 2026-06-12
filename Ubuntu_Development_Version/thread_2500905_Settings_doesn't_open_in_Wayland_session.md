---
title: "Settings doesn't open in Wayland session"
date: 2024-09-15
forum: Ubuntu Development Version
---

### Post by Shishimaru on 2024-09-15
Hi there.

I've noticed that the Gnome Settings app opens in Xorg session (and crashes sometimes, especially when dealing with fractional scaling), but not in the default Wayland session. Anybody else experienced the same?

I don't see any error appearing or anything else. Just the cursor loading something when hovering on the right part of the upper panel.



edit: laptop with Intel iGPU and Nvidia RTX 4080 dGPU, Nvidia drivers version 560 from the PPA.

---

### Post by Claus7 on 2024-09-15
Hello,

settings are working fine under wayland: ubuntu 24.10 under vb.

Regards!

---

### Post by jbicha on 2024-09-15
Do you have Nvidia graphics?

---

### Post by Shishimaru on 2024-09-16
> **jbicha said:**
> Do you have Nvidia graphics?

Yes, I do.

It's a laptop with Intel iGPU and Nvidia RTX dGPU.

I used the Launchpad PPA to install Nvidia drivers (version 560).

---

### Post by jbicha on 2024-09-16
Please file a bug using

```

ubuntu-bug gnome-control-center

```

Mention your graphics card.

---

### Post by Shishimaru on 2024-09-18
I've tried, but the commands doesn't produce any .crash file, so whoever is running Launchpad is closing my bug report. They suggest to open Nautilus and reach a specific directory, which probably doesn't contain this .crash file since no crash happened.

Anyways, today I can't even open Nautilus since I get a similar error. What a disaster.

$ nautilus
** Message: 21:54:52.949: Connecting to org.freedesktop.Tracker3.Miner.Files
MESA-INTEL: warning: ../src/intel/vulkan/anv_formats.c:763: FINISHME: support YUV colorspace with DRM format modifiers
MESA-INTEL: warning: ../src/intel/vulkan/anv_formats.c:794: FINISHME: support more multi-planar formats with DRM modifiers
Gdk-Message: 21:54:53.193: Error 71 (Errore di protocollo) dispatching to Wayland display.

---

### Post by jbicha on 2024-09-18
Well, it's probably because GTK4 has switched to new renderers in GNOME 46 and GNOME 47. See [https://gitlab.gnome.org/GNOME/gtk/-/issues/6574]("https://gitlab.gnome.org/GNOME/gtk/-/issues/6574#note_2225470")

---

### Post by Shishimaru on 2024-09-19
> **jbicha said:**
> Well, it's probably because GTK4 has switched to new renderers in GNOME 46 and GNOME 47. See [https://gitlab.gnome.org/GNOME/gtk/-/issues/6574]("https://gitlab.gnome.org/GNOME/gtk/-/issues/6574#note_2225470")

GNOME 46 is working good with any distro. I was hoping to keep Ubuntu 24.10 separate and eventually bug report something, but it's impossible. ubuntu-bug doesn't collect anything and no crash happens, so I can't manually select any file. Without any file, the bug report gets closed. If the bug report is closed, the malfunction just stays there.

I'm not hoping in any improvement. I know Ubuntu 24.10 is in development, bug Gnome 47 has been released as stable, so that's it.

Welp.

---

