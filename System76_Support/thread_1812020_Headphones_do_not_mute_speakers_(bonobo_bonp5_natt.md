---
title: "Headphones do not mute speakers (bonobo bonp5 natty)"
date: 2011-07-25
forum: System76 Support
---

### Post by holdorph on 2011-07-25
I have a couple week old Bonobo bonp5 machine with Natty on it.  I have the version of Natty/Ubuntu that shipped with the laptop.

When I plug in headphones the computer speakers are not muted.  I have also installed and dual/boot windows.  In windows, this works correctly (plugging in headphones mutes computer speakers).

I would love for this to be automatic.  But if that's not possible, I'd settle for if I could set the volume for these two (built-in speakers vs headphones) separately.

Any help is appreciated.

- Cris

---

### Post by thomasaaron on 2011-07-29
This is called Jack Sensing. If it works in Windows, we can rule out a hardware failure. However, sometimes this doesn't work correctly in Ubuntu.

Can you look at your audio settings and see if you can mute the external speakers?

---

### Post by thomasaaron on 2011-07-29
Actually, please open your System76 driver, click the install tab and the install button. When the driver finishes running, reboot the computer. Does that fix the jack sensing?

---

