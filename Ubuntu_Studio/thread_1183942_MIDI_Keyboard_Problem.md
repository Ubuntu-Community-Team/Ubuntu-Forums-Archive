---
title: "MIDI Keyboard Problem"
date: 2009-06-10
forum: Ubuntu Studio
---

### Post by ChrisB111 on 2009-06-10
I have Jack set up with QSynth and my midi keyboard (Yamaha PSR-550) using a usb to midi cable, it works but the sounds sound the wrong pitch and not all nots played are captured and played back by the computer. I have also used kmidimon to confirm this. Does anyone know what is causing this, I would have tried searching the internet first but I don't know what my problem is?

Thanks,

Chris

---

### Post by kayosiii on 2009-06-10
The difference in pitch sounds like qsynth (fluid-synth) is trying to operate at a different frequency rate to what the soundcard is using.

The missing notes I don't have any good answers for

---

### Post by ChrisB111 on 2009-06-13
I have fixed the frequency problem (thanks kayosiii) but I have a feeling the other problem is hardware based. This is my [midi/usb cable]("http://www.logilink.eu/cmsfiles/modules/i-sell2u/showproduct.htm?isu_zeigeartikel=UA0037&seticlanguage=en") and this is the [problem]("http://www.yamahaforums.co.uk/modules.php?name=Forums&file=viewtopic&t=3275") I think I have.
> Logilink support replied to my query stating that their usb/midi cable only supports single events at a time, so that is the problem. 
Does anyone else have another solution or have this cable working?

Thanks,

Chris

---

### Post by raboofje on 2009-06-13
> **ChrisB111 said:**
> I have a feeling the other problem is hardware based. This is my [midi/usb cable]("http://www.logilink.eu/cmsfiles/modules/i-sell2u/showproduct.htm?isu_zeigeartikel=UA0037&seticlanguage=en") and this is the [problem]("http://www.yamahaforums.co.uk/modules.php?name=Forums&file=viewtopic&t=3275") I think I have.

If that is true, that's a truly shitty usb midi interface.

The M-Audio MidiSport devices support this fine, but I'd say most cheaper offerings should be able to handle this, too...

---

### Post by ChrisB111 on 2009-06-15
Can anyone else advise a good midi cable that works with ubuntu? I dont want to by a rubbish one again.

Chris

---

