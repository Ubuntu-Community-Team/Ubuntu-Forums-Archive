---
title: "[SOLVED] Photoshop CS is really messed up. Can't uninstall"
date: 2008-12-23
forum: Wine
---

### Post by mahasmb on 2008-12-23
Okay, so I have a copy of Photoshop CS and I tried to use it on my fresh install of Intrepid Ibex. But every time I opened CS, it gave me an error message saying there was a hardware program or something. So I wanted to try to uninstall it. This is what I get:

```
 uninstaller
fixme:x11drv:X11DRV_SetWindowRgn not supported on other thread window 0x20040
err:ole:get_unmarshaler_from_stream Failed to read common OBJREF header, 0x00000000
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002

```

Even in the uninstaller window after the uninstallation I still see Photshop CS listed under the Wine programs. It's odd. It's like it does nothing.

I'm currently using the last stable version.

```
$ wine --version
wine-1.0.1

```

I could use some help in uninstalling the program and then some help in actually getting it to work after a reinstall.

The only other program I have running with Wine is mIRC with an Acidmax script.

---

### Post by wootah on 2008-12-23
All programs for wine are installed in ~/.wine/drive_c   (In *most* situations)

If an uninstaller fails, you could try removing the real folder from your installation. Or if everything is all bloaked up, you could just remove the .wine directory, and reinstall wine by synaptic ?

---

### Post by mahasmb on 2008-12-23
I tried that. No luck.

---

### Post by alex.rayu on 2008-12-23
How is it no luck? You removed the photoshop folder or the .wine folder, and the Photoshop still runs? You have a ghost in your computer =) The ghost of a photoshop. A silver bullet will do.

But it you removed the folder and the photoshop is still listed in the menu, then remove it with the menu editor. Wine is weak in removing things.

---

### Post by mahasmb on 2008-12-23
Well, I meant no luck in fixing the overall problem.

But this time I uninstalled everything and THEN I deleted .wine and it worked. Just removing the folder still caused me problems. But everything works nicely now. Thanks for the help.

---

