---
title: "[SOLVED] Capslock led when switched through the keyboard preferences"
date: 2008-05-28
forum: System76 Support
---

### Post by Zxaos on 2008-05-28
I recently swapped the position of the caps lock and the escape key (I use vim and derivatives a lot) using the System->Preferences->Keyboard option in GNOME.  However, pressing the caps lock key still toggles the caps lock LED, even though its behaviour is that of the esc key, and the esc key does not toggle the caps lock led.

How can I fix this so that it matches up?

---

### Post by thomasaaron on 2008-05-28
This is a known bug in Hardy Heron.

There is a work-around here:
[https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/173350](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/173350)

I've not studied it in depth, but if the fix has to be re-done every time you reboot, perhaps we could make a start-up script to put in sessions that would implement the fix.

Let me know how it goes.

---

### Post by Zxaos on 2008-06-05
Ok, it's fixed. I disabled the option in the GNOME keyboard prefs window and created the following script in /etc/SwapCapsEsc.kmap

```
!
! Swap Caps_Lock and Escape
!
remove Lock = Caps_Lock
keysym Escape = Caps_Lock
keysym Caps_Lock = Escape
```

I then added the following line to /etc/rc.local
sudo xmodmap /etc/SwapCapsEsc.kmap

Works perfectly now.

---

