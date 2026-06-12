---
title: "DirectDraw Renderer Not Installed in Registry"
date: 2009-06-05
forum: Wine
---

### Post by lewys93 on 2009-06-05
Hello,
I've been trying to run the Windows game "Stronghold Crusader" through Wine.
Although it runs, The screen is black and I can't do anything.
Upon doing a bit of research, I found that I needed to set "DirectDraw Renderer" to OpenGL=False, or a value to that effect.
However, upon running regedit through Wine, I've found that I don't have DirectDrawRenderer in the Direct3D folder of my registry. Is there any way to install it?

---

### Post by hikaricore on 2009-06-05
Right click?  New?  String value?

I'm sure this is probably mention in the instructions you read but as you've not linked them I can't confirm.

---

### Post by lewys93 on 2009-06-05
> **hikaricore said:**
> Right click?  New?  String value?

I'm sure this is probably mention in the instructions you read but as you've not linked them I can't confirm.

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=3906&iTestingId=14081](http://appdb.winehq.org/objectManager.php?sClass=version&iId=3906&iTestingId=14081)

I've added a string now, and when I run Stronghold Crusader, in the terminal I get the following message:

```

fixme:mixer:ALSA_MixerInit No master control found on SAA7134, disabling mixer
fixme:win:EnumDisplayDevicesW ((null),0,0x32f92c,0x00000000), stub!
fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 16

```

The game still runs, but I still can't see anything and it is still unplayable

---

