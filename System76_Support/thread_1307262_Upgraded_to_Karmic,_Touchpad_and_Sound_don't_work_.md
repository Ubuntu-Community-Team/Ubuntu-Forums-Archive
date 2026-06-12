---
title: "Upgraded to Karmic, Touchpad and Sound don't work on my PamP5"
date: 2009-10-31
forum: System76 Support
---

### Post by thefinn93 on 2009-10-31
Hello,
I was hoping you guys could help me out. I just updated to Karmic and my built in mouse (including scroll thingy, buttons and finger print reader) doesn't work, nor does the sound (haven't tested with headphones, but it doesn't see any sound device so I don't see why that would work). I went into the "Software Sources" settings and turned my old repositories (I found an official guide at one point, can't seem to find it again. That was the first step after the initial install) and updated. I then went in and updated the System76 Drivers, rebooted, etc. but no luck. Also, I'm using a USB mouse and it works fine.

Any help would be greatly appreciated.

---

### Post by ubuntu27 on 2009-10-31
Maybe You should do a fresh install of Ubuntu Karmic.

I don't know about touchpad, but for soud...

DId you install a restricted or propietary driver called "Modem Software" in Hardware Drivers [System/Administration/Hardware Drivers]?

If so, remove it. That proprietary driver has a nasty bug that removes or mutes all the sounds.

---

### Post by thomasaaron on 2009-10-31
If you run these commands...

sudo modprobe -r psmouse
sudo modprobe psmouse

...does your touchpad work?

---

### Post by thefinn93 on 2009-10-31
> **thomasaaron said:**
> If you run these commands...

sudo modprobe -r psmouse
sudo modprobe psmouse

...does your touchpad work?

no :(

---

### Post by thomasaaron on 2009-11-02
1. Did you have Ubuntu Tweak installed in Jaunty? If so, is it still in Karmic?
If it is, disable it.

2. Try running this command from a terminal...
sudo apt-get install xserver-xorg-input-synaptics
...and then reboot.

---

