---
title: "convert sound file to midi?"
date: 2011-10-01
forum: Ubuntu Studio
---

### Post by puzzled one on 2011-10-01
I have just loaded ubuntu studio and tux guitar on my computer and would like to use tuxguitar to produce tabs for a mandolin  witch it will do with manual inputs i.e. typing or mouse      so far so good    i would like to import a sound file into tux but tux will only import MIDI or Tef files.
does anyone know of any software to convert a recorded sound from a microphone to a midi file or any other work around if i could do this it would save a lot of typing 
many thanks

---

### Post by JayPeeJay on 2011-10-01
The only thing that comes to mind is using Rakarrak's midi option.  You can play your guitar or routed sound file and have it send the midi notes into a sequencer like Rosegarden.  Rosegarden can then print a score or piano roll.  The only problem with this is you cannot do chords, it messes with the midi out.  You would still have to somehow pencil in the harmonizing notes (maybe copying the notes and pasting them in intervals above the original?).  This may not save you anytime at all.

---

### Post by capicoso on 2011-10-01
Hi.
You cant convert a sound file to MIDI. Well, there are some programs that do "convert" sound to MIDI, but the results won't be what you expect. Sound is very complex. MIDI can't understand sound, but sound can understand MIDI. MIDI doesn't even generate sound. MIDI files are just messages, instructions that tells the synthesizer to play a note, with a determined velocity, aftertouch, etc. MIDI without a synthesizer will be silence. That's what you do with tuxguitar, thats why you can import MIDI into tuxguitar, to tell him what to play. So, you'll have to type!

---

