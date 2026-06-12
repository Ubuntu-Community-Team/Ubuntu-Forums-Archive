---
title: "Intermitent screen dimming after Gusty upgrade on Daru2"
date: 2007-10-22
forum: System76 Support
---

### Post by GregCwx1 on 2007-10-22
This is annoying and appears to be related to flaky power management. The battery is fully charged and I'm on AC but then the battery icon looks empty and the LCD screen dims to lowest setting! Argh! After a moment, the screen brightens
up again.  Here's the output from /var/log/messages:

Oct 22 17:07:33 ubuntu kernel: [ 3440.424000] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
Oct 22 17:07:33 ubuntu kernel: [ 3440.424000] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
Oct 22 17:07:33 ubuntu kernel: [ 3440.424000] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
Oct 22 17:07:33 ubuntu kernel: [ 3440.424000] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
Oct 22 17:07:33 ubuntu kernel: [ 3440.444000] atkbd.c: Unknown key pressed (translated set 2, code 0xf8 on isa0060/serio0).
Oct 22 17:07:33 ubuntu kernel: [ 3440.444000] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
Oct 22 17:07:33 ubuntu kernel: [ 3440.444000] atkbd.c: Unknown key released (translated set 2, code 0xf8 on isa0060/serio0).
Oct 22 17:07:33 ubuntu kernel: [ 3440.444000] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.

This is listed over and over again every few moments when the screen dims and then brightens again.

Any ideas/fixes out there?

Thanks!

-Greg

---

### Post by agisfox on 2007-10-22
The brightness/dimming is a reaction to the flaky power management (at least for me) - it dims when it suddenly decides it's on battery power, and then brightens when it decides it's back on AC Power.  If you change the brightness settings in power management to not dim the screen on battery power, it won't flicker / dim.  (Annoying workaround, but ok if you're on AC power anyway).

I haven't seen any fixes for the flaky power management itself, though.

---

### Post by thomasaaron on 2007-10-23
Carl is working on this one today.

---

### Post by GregCwx1 on 2007-10-23
I was able to change the settings in power mangement so that the screen remains undimmed when low battery is sensed. That appears to be a workaround for the moment.

Good luck, Carl. I hope the fix is easy.

---

### Post by poetbeware on 2007-10-23
Hi,

I followed your suggestion to change the Power Management options as a workaround for the random screen dimming/undimming -- but it doesn't seem to work for me. Could you maybe post specific, idiot-proof instructions? It's hard to get anything done like this...

-Paul

---

### Post by palintheus on 2007-10-23
> **poetbeware said:**
> Hi,

I followed your suggestion to change the Power Management options as a workaround for the random screen dimming/undimming -- but it doesn't seem to work for me. Could you maybe post specific, idiot-proof instructions? It's hard to get anything done like this...

-Paul

Be sure that you read the options carefully, I made the mistake of assuming that the sliders for the screen dimming would be the same (IMHO they should be), but the one under the AC tab needs to be set to 100%, and the one under the battery tab needs to be set to 0%.

Also uncheck the "Dim display when idle" box

I also changed all the options from "Blank Screen" to "Do Nothing" even on the laptop lid option, that seems to have stopped all screen dimming/blanking and the screen still blanks when the lid is closed.

**Screen Shots Attached**

---

### Post by Rowan187 on 2007-10-24
Hey. Just thought I'd mention that the same thing happens on the Panv2, When i temporarily change the brightness with the FN + F4/F5 keys it will go back to 100%  in a while, and I don't have the options set to dim, etc. You get my point. Maybe. From what i've seen the Brightness Applet (for Gnome Panels) makes it stop changing.

---

### Post by thomasaaron on 2007-10-24
Rowan187, 

I don't think it is the same problem that the DarU2 has. The DarU2 has a dsdt table compilation issue, apparently. It's the only computer we've ever seen this on.

With the PanV2, it is probably a setting issue.
I'd start a new thread for it and post screenshots of all the tabs on your power management utility.

---

### Post by zaleski on 2007-10-28
I hope there's progress on this....I did the power management setting work around but when the event occurs, the screen still goes black for about a second.  Yeah, it's random and annoying; can't wait till there's a fix, but man do I love this laptop.

---

### Post by thomasaaron on 2007-10-29
Actually, Carl has made some good progress on this. He's still working out a few kinks, but it's getting better.

You should not have momentary screen-blanks though. There's probably something your missing in the power management settings.

---

### Post by zaleski on 2007-11-12
Hi there, any updates on this issue?

---

### Post by palintheus on 2007-11-12
> **zaleski said:**
> Hi there, any updates on this issue?


[http://ubuntuforums.org/showthread.php?t=609722](http://ubuntuforums.org/showthread.php?t=609722)

Bottom of the page.

---

### Post by zaleski on 2007-11-14
sweet, thanks!

---

