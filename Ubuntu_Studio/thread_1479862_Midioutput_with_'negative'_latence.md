---
title: "Midioutput with 'negative' latence"
date: 2010-05-11
forum: Ubuntu Studio
---

### Post by maliStfn on 2010-05-11
Dear Ubuntucomunity,

while trying to get my ultimate linux driven studio I found a problem and I need help:

My Midioutput comes to early. Has somebody the same Problem and/or do you know where the problem may come from?

What I did:

- Ardour with 120bpm an click switched on recorded on one track (sound card in to out)
- Seq24/Muse synchronised with Jack, over Midi out (esi Romi/o) to an Alesis DM5 on the other track

what happens:

- Ardour klick comes a little late, so far ok
- The Alesis DM5 signal is to early?!? it comes before the tick itself

Most of the time I thought it is a Problem of seq24 and so I tried Muse. Same Problem.

Seq24/muse have no possibility to correct this as far as I can see. in Jack-control I tried all three MidiDriver options: seq, raw and none. No difference. Ardour it self should also be ok, I tried this also with an external Midisequencer (Akai mpc) and the signal arrived at nearly the same time like that from the Ardour click.

Hope somebody could help me some further.

greetings, ..stfn

---

### Post by mango42 on 2010-05-11
Did you change the default MIDI 'delay' setting in **QJackCtl**?

If not, maybe check to see if you get the same problem by using a combination of QTractor + Hydrogen + Ardour. I'm running that combination with an ESI 8x8 MIDI interface and even doing drum'n'bass the whole issue stays very tight on timing.

---

### Post by maliStfn on 2010-05-11
No, I didn't. But I can't find this option in my jack-cntrl. There is a option: input latence and one output latence, but I guess that this is for audio, isn't it? Maybe you use the newer Jack2?

---

