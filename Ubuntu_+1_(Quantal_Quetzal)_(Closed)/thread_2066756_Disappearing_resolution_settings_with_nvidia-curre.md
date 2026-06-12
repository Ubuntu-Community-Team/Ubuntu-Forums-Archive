---
title: "Disappearing resolution settings with nvidia-current"
date: 2012-10-05
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by Yahoé on 2012-10-05
Using nouveau, the display settings offer me 6 different 16-9 settings: 1920x1080, 1680x945, 1366x768, 1360x768, 1280x720, etc... but when installing the current nvidia-current I only have 1920x1080 and 1280x720, so on a 47' HD screen, display is either too small or too big . Any idea why I miss three intermediate settings?

---

### Post by GeForce 9500GT on 2012-10-05
open a terminal and type this command:
```
sudo nvidia-xconfig
```
Then reboot and see if that solved the problem

---

### Post by mips on 2012-10-05
Run the display at it's native resolution and adjust your icon & font sizes to suite you.

If you really want those other resolutions then use the nouveau drivers.

---

### Post by Yahoé on 2012-10-05
Thanks both for your input.

Running nvidia-xconfig doesn't change a thing. It's my comprehension that it is not necessary anymore in the latest versions of Ubuntu, installing nvidia-current surely doesn't create one, and nvidia-settings reports everything as it should without.

The option of increasing font and icons size just doesn't cut it for me either, and it only affect Ubuntu, not Firefox per exemple.

I'm still very curious to understand why these resolutions settings are not proposed anymore just because nvidia-current is used.

---

