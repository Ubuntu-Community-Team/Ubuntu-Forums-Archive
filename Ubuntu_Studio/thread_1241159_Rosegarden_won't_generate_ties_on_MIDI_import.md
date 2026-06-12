---
title: "Rosegarden won't generate ties on MIDI import"
date: 2009-08-15
forum: Ubuntu Studio
---

### Post by Sadistic Tribble on 2009-08-15
I have a MIDI file that was 'written' by a program my dad wrote, and we're trying to open it with Rosegarden. When we try to play it, the piece itself sounds fine; however, when we open it in the notation editor, there are no ties. That is, is a half note in measure A is tied to a half note in measure B, they will simply be turned into a whole note in measure A- yes, extending measure A to contain 6 beats instead of 4- and measure B will simply be 2 beats short, including the half note or two quarter notes that were after the tied half note.

[EDIT] Also, 'quantize' does nothing (I'm taking shots in teh dark to fix the problem since I can't find anything on Google about the problem). I'm sure it's some simple config option we missed or something.

ties and notation work perfectly in Finale 2002 using WINE, and the Rosegarden problem exists under all Ubuntu distros we've tried (my Kubuntu 9.04, his Ubuntu 8.04 and 9.04 and Ubuntu Studio 8.04).

---

### Post by Sadistic Tribble on 2009-08-15
NVM: got it working. "When recording MIDI, split and tie long notes at barlines" was disabled by default for some reason. :o

Feel free to delete this post

---

