---
title: "How to change drumset bank in Timidity from 0 to 128 ?"
date: 2011-11-13
forum: Ubuntu Studio
---

### Post by SketchMan3 on 2011-11-13
I've looked at some tutorials, but they don't make sense to me.

Many of my midis use GS drumsets (808, Electronic, Orchestral, etc..), and they don't sound right without them. For some reason Timidity doesn't recognize that the drum channel should be played through bank 128 instead of bank 0, so everything sounds like the Standard Drumset.

Is there a way to replace bank 0 with bank 128 for the drumset in the timidity.cfg file?

Edit: Like, is there a way to tell it, "if channel = 10(the drum channel) then bank = 128"?

Edit2: Also, the soundfont I'm using is GeneralUserGS

---

### Post by SketchMan3 on 2011-11-14
And now, after fooling around with it, uninstalling/reinstalling timidity, and following the instructions on [this](https://help.ubuntu.com/community/Midi/SoftwareSynthesisHowTo#Automatically_starting_TiMidity.2B-.2B-_on_boot) page the silly server won't load upon boot, and I just noticed that when I shut-down it just shows a blank screen instead of the "killing processes" screen (although that may be unrelated).

Please help. Also, I'm editing midi with an old working version of Jazz++ in Wine. It works, although the timing/tracking is spotty, I can work with it.

Edit: And now, for some reason (I don't know what settings I was using before), the timing in Jazz++ is PERFECT.

???

---

### Post by SketchMan3 on 2011-11-15
Did I post this in the wrong section or something?

---

### Post by s.fox on 2011-11-17
Thread moved to [Ubuntu Studio]("http://ubuntuforums.org/forumdisplay.php?f=335") at OP request.

---

### Post by SketchMan3 on 2011-12-16
I'm still looking for a solution.

---

### Post by SketchMan3 on 2012-08-05
Am I the only person who has trouble with getting Timidity to play with a drumkit other than the Standard one, even when the sf2 file includes all of the GM kits?

---

