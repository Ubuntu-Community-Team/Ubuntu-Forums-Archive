---
title: "Midi problem!!"
date: 2009-01-10
forum: Ubuntu Studio
---

### Post by The-IRS on 2009-01-10
hi all.
I have downloaded rosegarden and an external midi mapper but neither of them play sound! Is there a midi driver or something that i have to install?

-IRS

---

### Post by mcduck on 2009-01-12
It really isn't a surprise, since this is a Linux forum and both programs you mentioned are for Windows. While Ubuntu certainly is a modern OS, it definitely isn't NT-based.. ;)

Besides, they are tools for internal routing of MIDI data, when in this case the question would be about getting something that would actually play the MIDI data as sound.

The-IRS, do you have timidity installed? You should probably start by testing if it can play your MIDI files. After that the next step would be to get the MIDI data to play with some software synth (try Fluidsynth!).

I assume you are using Jack to route the MIDI and audio between different programs?

---

