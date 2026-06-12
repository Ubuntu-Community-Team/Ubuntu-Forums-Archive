---
title: "Bluetooth and wireless keyboard not working"
date: 2012-01-01
forum: Ubuntu Studio
---

### Post by _Esc on 2012-01-01
I've just installed Ubuntu Studio 11.10 and my wireless apple keyboard and trackpad are not being discovered. I also don't see that the bluetooth dongle (Dlink 122) is active either.

I've installed 'bluez python-gobject and python-dbus. I'm new to ubuntu.. any help greatly appreciated :confused:

---

### Post by _Esc on 2012-02-10
I've found a fix in case anyone else is having problems with bluetooth. In synaptic I installed 'blueman' which is a gui for bluetooth. I used blueman to discover the keyboard first and the trackpad second, once the keyboard was installed.

Ubuntu will offer to use a random key for the trackpad but this will not work. You have to input 1111 - four ones.

The apple trackpad does not have full functionality under ubuntu, but 'touchegg' adds several other gestures... touchegg is not without bugs though, so you might prefer to do with less functionality to avoid grief.

---

