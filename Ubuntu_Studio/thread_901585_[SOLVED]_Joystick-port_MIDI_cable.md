---
title: "[SOLVED] Joystick-port MIDI cable"
date: 2008-08-26
forum: Ubuntu Studio
---

### Post by klange on 2008-08-26
Alright, so I have this fairly old joystick-port-based (is there a more techy name for that thing that I've missed?) MIDI cable that I can't for the life of me get working.

If I can't get it to work at all, I'll probably just get a USB one, but anyway, any help is appreciated.

There's nothing really defining about the cable itself (couldn't say who made it, but I know the cable itself isn't faulty), maybe it's my hardware that's the problem.

Any ideas?

---

### Post by Stochastic on 2008-08-27
what have you tried so far?  how far have you gotten?

I assume you're plugging this into a soundcard that is equipped with a joystick port.  Have you started jack on that soundcard?  then looked in the MIDI tab?

---

### Post by klange on 2008-08-31
> **Stochastic said:**
> what have you tried so far?  how far have you gotten?

**I assume you're plugging this into a soundcard that is equipped with a joystick port**.  Have you started jack on that soundcard?  then looked in the MIDI tab?

Not sure. It's built-in to my motherboard, which has an nForce 2 (so it could be attached through that). Now, I'm not crazy, this thing worked on Windows with an old Midi program (I'd give it a crack in Wine, but I have my doubts), so there should be some way, even if it takes writing drivers myself (not that I'd do that, I'm not hardware guy), to get this working.

I've plugged it in, rebooted, checked logs, looked everywhere in the Jack controls, but nothing seems to even report its existence (it's attached to a working Midi-capable keyboard if it makes any difference). I have some form of integrated Midi control on the board, and that shows up, but using it produces nothing (I know my Jack set up is functional, I've routed through Timidity and such to check that). I'll go take another look and see what I can find.

---

### Post by klange on 2008-09-01
After screwing around for a few hours I got the thing working. Quite happy with the results :)

---

### Post by Sydnisaurus on 2008-09-12
Hi, I'm having this same problem, on an nforce motherboard.
Typing "aplaymidi -l" in the console only finds a "Midi Through", should this list any hardware midi ports?
I've got nothing showing up in the MIDI tab of JACK Control and just this Midi Through in the ALSA tab.
Would love to know how you got this working.

Have an ensoniq esq-1 sitting here looking forlorn and a roland D-50 which needs some kind of factory reset.
I've never used MIDI before but I'm sure what I have done should make it work.

---

