---
title: "touchpad"
date: 2008-03-31
forum: System76 Support
---

### Post by brook adams on 2008-03-31
hi there,

I have a new sytems76 Gazelle Value running ubuntu 7.10 and I have a problem setting up the touchpad. According to the "practical guide to ubuntu linux" by Mark Sobell the mouse preferences window should have three tabs; Buttons, Motion and Touchpad (on laptops). Mine has no tab for touchpad.

I'm guessing the answer is somewhere in /etc/x11 but I don't know where or what to look for.

Thanks in advance

---

### Post by prshah on 2008-03-31
> **brook adams said:**
> 
I'm guessing the answer is somewhere in /etc/x11 but I don't know where or what to look for.
Thanks in advance

You can either fiddle with the /etc/X11/xorg.conf or use ```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by thomasaaron on 2008-03-31
The new Gazelles have an ElanTech touchpad. As far as I know, there is still not a suitable driver for them in the Linux world.

The only adjustments you will be able to get are via System > Preferences > Mouse.

To completely disable it, you can run this command from a terminal:
sudo modprobe -r psmouse

To re-enable it, you can run this command:
sudo modprobe psmouse

---

### Post by brook adams on 2008-03-31
Thanks for the help prshah and thomas...
namaste

brook adams

---

