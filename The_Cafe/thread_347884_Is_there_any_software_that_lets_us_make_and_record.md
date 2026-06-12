---
title: "Is there any software that lets us make and record music and sound?"
date: 2007-01-27
forum: The Cafe
---

### Post by Coop on 2007-01-27
Hello
I'm not sure what exactly what I'm looking for,but is there any Linux software that lets us make and record music,sound etc without a musical instrument,by only using our keyboard and/or mouse?
For eg,a software that assigns sounds to the different keys on a keyboard and lets us make sound by pressing those keys and lets us record the sounds we make?

---

### Post by kevinlyfellow on 2007-01-27
try rosegarden

[http://www.rosegardenmusic.com/](http://www.rosegardenmusic.com/)

---

### Post by Artemis3 on 2007-01-28
[http://www.hydrogen-music.org/](http://www.hydrogen-music.org/)
[http://www.reduz.com.ar/cheesetronic/](http://www.reduz.com.ar/cheesetronic/)
[http://www-stud.fht-esslingen.de/~alex/tX/](http://www-stud.fht-esslingen.de/~alex/tX/)
[http://jazzplusplus.sourceforge.net/](http://jazzplusplus.sourceforge.net/)
[http://denemo.sourceforge.net/](http://denemo.sourceforge.net/)
[http://www.rosegardenmusic.com/](http://www.rosegardenmusic.com/)
[http://www.soundtracker.org/](http://www.soundtracker.org/)
[http://ardour.org/](http://ardour.org/)
[http://beast.gtk.org/](http://beast.gtk.org/)
[http://www.muse-sequencer.org/](http://www.muse-sequencer.org/)
[http://rezound.sourceforge.net/](http://rezound.sourceforge.net/)
[http://audacity.sourceforge.net/](http://audacity.sourceforge.net/)

:guitar:

---

### Post by jdhore on 2007-01-28
personally, i use Audacity and Jokosher

---

### Post by Patrick-Ruff on 2007-01-28
honestly there isn't much professional grade music recording software for linux, ubuntu-studio looks like it could go somewhere, but at the moment there is pretty much nothing really spectacular.

check out the guitarists thread, we had a discussion on it before.

---

### Post by PrinceArithon on 2007-01-28
Yeah, I was going to say there is nothing out there on the level of Cubase or Protools for Linux.

---

### Post by qamelian on 2007-01-28
> **Patrick-Ruff said:**
> honestly there isn't much professional grade music recording software for linux, ubuntu-studio looks like it could go somewhere, but at the moment there is pretty much nothing really spectacular.

check out the guitarists thread, we had a discussion on it before.

This surprises me to hear. I ditched all Windows and Mac audio production software about two years ago. I help support 2 different recording studios that are completely linux-based and have a 100% linux home studio myself. Although the initial setup of a linux audio production environment is a bit more complex than the equivalent in Windows or Mac, the linux environment is every bit as powerful and capable of providing professional results.

---

### Post by TLE on 2007-01-28
There's also [Jokosher]("http://www.jokosher.org/"). It's got our very own Jono Bacon as one of the developers.

---

### Post by kevinlyfellow on 2007-01-29
I don't think coop is looking for software to record music that is played on a physical instrument, but rather something that is synthesized on the computer, so jokosher and audacity are out

---

### Post by shining on 2007-01-29
I started reading this rosegarden tutorial :
[http://rosegarden.sourceforge.net/tutorial/en/chapter-0.html](http://rosegarden.sourceforge.net/tutorial/en/chapter-0.html)

but well, it looks far more complex than I hoped :)

I had a relative success by using qjackctl, rosegarden and qsynth. I opened one of rosegarden examples, then downloaded one soundfount file (.sf2) from the net and loaded it in qsynth. And then I had to manually associate each channel in qsynth to one instrument from the soundfont , to hear something. But the sound produced was awful. But there are several possible reasons:
1) I'm not using a realtime kernel
2) rosegarden complains about the 250hz kernel resolution, I guess it expects 1000hz
3) it's an intel integrated sound card. With a sound blaster card, it's apparently possible to directly load the soundfont in the card (and not using qsynth), which should probably lead to better result.

Anyway, it doesn't seem to be able to do what Coop asked, making music with the keyboard. You can edit the partitions though.

EDIT:
I tried on a less powerful pc, but with a sound blaster live. Boths way work nicely : loading the soundfont to the soundcard, or loading it in qsynth result in a clear sound. There is something wrong with my laptop, but I'm not sure what.

---

