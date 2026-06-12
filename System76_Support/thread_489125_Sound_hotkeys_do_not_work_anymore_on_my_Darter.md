---
title: "Sound hotkeys do not work anymore on my Darter"
date: 2007-07-01
forum: System76 Support
---

### Post by perce on 2007-07-01
Hi,

I've noticed that the sound-related hotkeys Fn-F10, Fn-F11, and Fn-F12 do not work anymore. I don't use them often, so I can't tell when they exactly stopped working, but I think it's a recent thing. The logs don't give any error message, as far as I know (I've checked dmesg and /var/log/acpid).

---

### Post by thomasaaron on 2007-07-02
They do not work with all applications, it seems.
Do they work with RythmBox? Mine do.

---

### Post by perce on 2007-07-05
> **thomasaaron said:**
> They do not work with all applications, it seems.
Do they work with RythmBox? Mine do.

Hi Tom,

I didn't try RythmBox: you´ll think I´m stupid, but I don´t understand how it works. However, when the hotkeys were working, they worked with Totem too. Even better, is seemed to me that they changed the master channel of Alsamixer, in the same way Gnome's volume applet does.

---

### Post by thomasaaron on 2007-07-05
I just double checked mine on Rhythmbox and they worked, so it doesn't look like an update hosed them.

Go to System > Preferences > Sound.
Under the "Devices" tab...
Make sure PCM (or maybe FRONT) is highlighted.
Then click OK.

Does that work?

---

### Post by perce on 2007-07-06
Thank you Tom,

the problem was exactly that one. Now they work again.

---

### Post by thomasaaron on 2007-07-06
No problem.

Hey, even a blind squirrel stumbles across a nut once in a while. :)

---

