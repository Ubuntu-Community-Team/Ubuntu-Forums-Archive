---
title: "M-Audio Radium-49 keyboard: troubleshooting"
date: 2010-05-06
forum: Ubuntu Studio
---

### Post by intuited on 2010-05-06
I've got a M-Audio Radium 49 keyboard.  This is a USB-based MIDI controller that works via the midisport-firmware package.  It used to work okay; now it doesn't seem to be picked up by linux at all.  I went a while without using it, so I'm not sure if this is maybe due to updates, or if there is a hardware issue with the keyboard.  I'm having identical symptoms on two different machines, one running Karmic and the other running Lucid.

  I've discovered that plugging the keyboard in and powering it up has no effect on the output of `lsusb`.  Is there a better way to check to see if the keyboard is sending anything at all over the USB interface?

  It seems to work okay otherwise: the sliders, keys, etc. all affect the keyboard's LED readout in the normal way.  This would seem to indicate that it's unlikely that it's a hardware problem with the keyboard.  The manual doesn't mention any way to reset the keyboard.

  I'd like to be able to dig a little deeper to find out where the problem is.  I'm also wondering if it's possible that a botched firmware upload (as performed by midisport-firmware) could have caused problems with the device, or if this is more likely an issue with some hardware component shorting out or such.

  The tests with $(lsusb) were performed a few times using various combinations of USB cables (including a brand new one) and USB ports on the aforementioned two machines.

---

### Post by cchhrriiss121212 on 2010-05-07
I am curious about one thing: The midisport is a midi to usb adapter, so why did you flash your keyboard with this firmware update?
Have you tried running lsusb in a live cd of whatever OS you were using when this worked?

---

