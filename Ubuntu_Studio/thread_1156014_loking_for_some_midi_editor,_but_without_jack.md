---
title: "loking for some midi editor, but without jack"
date: 2009-05-11
forum: Ubuntu Studio
---

### Post by yuki86 on 2009-05-11
hi im looking for some midi editing software but i cant setup and run jack, is anything without it?????????

---

### Post by thorgal on 2009-05-11
Rosegarden can ignore jack. The first time you run it without jack, it will warn you about what it has to disable in terms of functionality but you can ignore this message. This way, you can purely edit MIDI segments (piano roll, etc).

---

### Post by yuki86 on 2009-05-11
and will it play sound without jack? Im playing flute, and i need melody track from mid, better whet i hear someting.. thx

---

### Post by thorgal on 2009-05-11
well, that's the funny thing:

if you have a soft synth that is ALSA compatible for MIDI input and audio ouput (like qsynth) or a h/w instrument that can take MIDI input and play its own audio (like a digital piano with MIDI in), rosegarden can be patched up via the ALSA MIDI layer. When you connect the MIDI track to the MIDI soft synth or h/w, you wll hear sound as you create notes in the piano roll. However, playing back the MIDI track in rosegarden won't produce any sound in the soft synth or MIDI h/w. I just tried it, that's what I observed (I usually use jack for MIDI and audio). So from my little experiment, it does not sound like you will have playback through ALSA only. But you can also try for yourself and confirm or infirm what I saw.

---

### Post by yuki86 on 2009-05-14
ok i start qsync and choose alsa driver, control button blinking green when midi in rosgarden is playing but i hear no sound 

I NEED HELP!

---

### Post by yuki86 on 2009-05-16
OK I'm on different machine jack seems to work fine, but i cannot hear anything when i start rosegarden....

tell me what are the stepps to hear something?

---

