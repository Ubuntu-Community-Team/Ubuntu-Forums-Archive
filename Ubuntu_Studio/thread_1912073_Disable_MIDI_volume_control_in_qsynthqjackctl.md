---
title: "Disable MIDI volume control in qsynth/qjackctl"
date: 2012-01-19
forum: Ubuntu Studio
---

### Post by treacl on 2012-01-19
[Thanks to Sylos]("http://ubuntuforums.org/showthread.php?t=1911462"), I am now using a harpsichord soundfont with qsynth, controlled by an Axiom 61 USB/MIDI keyboard via jack.

The keyboard has volume control, such that the harder (or faster?) you press the keys the louder the volume. Problem is, that's not the way harpsichords work. So the question is: Is there a way of disabling that in qsynth or qjackctl (or on the keyboard)?

Many thanks,
treacl

---

### Post by jejeman on 2012-01-20
Thats called Velocity. So, you need to find the way to disable velocity. Some instruments have option to determine velocity data influence to sound. Sorry, I can say anything speciffic, but this is the way to go.

---

### Post by treacl on 2012-01-20
Thanks, jejeman. By "instrument," do you mean the physical keyboard or the instrument soundfont? I.e., is this strictly a hardware function, or can it also be controlled/disabled in the software?

---

### Post by treacl on 2012-01-20
Don't know whether there is a way to control this in jack or qsynth, but thanks to jejeman's suggestion I did figure out how to disable it on the M-Audio Axiom 61 keyboard:


[LIST=1]
[*]Press the "EDIT" button just below the LCD.
[*]Press the "Curve" key.
[*]Use the patch "^" and "v" keys to select F3 on the LCD.
[*]Press the "Store" key.
[*]Press the "EDIT" key again to exit.
[/LIST]
Full details in the manual, available [here]("http://www.m-audio.com/index.php?do=support&tab=manuals").

Thanks again, jejeman.

---

### Post by jejeman on 2012-01-20
It can be done on both, hardware, as you already find out, and software side.
For example in Zyn AddSubFx here is the slider fo that

---

