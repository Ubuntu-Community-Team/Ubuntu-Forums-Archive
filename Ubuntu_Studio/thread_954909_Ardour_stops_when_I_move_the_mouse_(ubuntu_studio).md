---
title: "Ardour stops when I move the mouse (ubuntu studio)"
date: 2008-10-21
forum: Ubuntu Studio
---

### Post by Simon S on 2008-10-21
More correctly, it is when I move the touchpad, as I have a laptop (Dell D400). It is only when the touchpad or keyboard has not been touched for several seconds that, if it is moved again, Ardour stops recording with the message "the system could not keep up" I have it set to stop recording on xruns.

I have tried many jack settings, including high latency settings as I use a Behringer UCA202 usb interface which has external monitoring. I have enabled memlock via studio controls and upped the priority setting and added the expression nohz=off in /boot/grub/menu.lst as recommended elsewhere in te forums.

I tried looking in power management tools as it seems that the keyboard and touchpad go to sleep and then wake up with a start when touched again. I can hear this as a noise in the headphones even when Ardour isn't running.

I am at my wit's end. Any help would be greatly appreciated.

Thanks,

Simon.

---

