---
title: "Programmatically enable built-in camera?"
date: 2008-10-28
forum: System76 Support
---

### Post by phyzome on 2008-10-28
On my Pangolin laptop (panp4i), I have to press [Fn]+[F10] to enable the built-in camera. Is there a way of doing it programmatically, e.g. from the command line?

---

### Post by thomasaaron on 2008-10-28
Not that I'm aware of.

There doesn't appear to be a script for it, and no new modules are loaded or unloaded when you press Fn-F10. Can't find any keybinding settings for it.

It appears to be toggled at the bios level.

---

### Post by compholio on 2008-10-28
It's possible there's an instruction you can send to the BIOS in order to tell it to enable the camera, you'd probably have to go through the BIOS documentation though.  For example, there are commands you can send the BIOS that tell the I8042 controller to disable and enable the keyboard and/or mouse.

---

