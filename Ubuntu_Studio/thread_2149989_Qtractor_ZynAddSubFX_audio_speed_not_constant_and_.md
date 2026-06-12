---
title: "Qtractor ZynAddSubFX audio speed not constant and strange note cutoff"
date: 2013-05-30
forum: Ubuntu Studio
---

### Post by DoubleW on 2013-05-30
Hello everyone

I just installed Ubuntu Studio and played around for a while.
After getting Qtractor and ZynAddSubFX connected with jack and selecting an instrument in Zyn, I drew 4 notes in a row in Qtractor and looped them.

After two or three times looping the notes become shorter and shorter until I only a tick every time I should have heard a note.
Also I noticed that when I copied the notes instead of looping them the speed of the audio seems to randomly slow down.

I have no I idea what could be causing this, maybe I configured jack wrong?

---

### Post by zequence on 2013-05-30
Sounds like an application bug to me. Could be jack, qtractor, zynaddsubfx, a plugin you are using, or some library that is used with one of those apps. I'd write to LAU and ask about it [http://lists.linuxaudio.org/listinfo/linux-audio-user](http://lists.linuxaudio.org/listinfo/linux-audio-user)

---

