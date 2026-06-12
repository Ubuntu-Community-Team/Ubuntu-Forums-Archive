---
title: "Can I disable velocity settings for soundfonts?"
date: 2013-05-22
forum: Ubuntu Studio
---

### Post by trumpeteersman on 2013-05-22
I have a M-Audio Keystation 88es that DOES NOT support disabling of the built-in velocity curves. I am using qsynth to load my sf2 organ soundfonts, piping that through jackrack for the other plugins, and then to aurdour for the recording. Does anybody know how I would go about disabling the velocity settings? I know that ZynAddSubFX has an option, but it doesn't support sf2.

---

### Post by zequence on 2013-05-22
Try qmidiroute. Pretty straight forward to make all notes have the same velocity, once you understand the controls.

---

### Post by trumpeteersman on 2013-05-24
Thanks, I will try that.

---

### Post by trumpeteersman on 2013-06-02
Ok, I have an issue. In theory QMidiRoute can adjust the velocity settings for a range from a min of 0 to a max of 127. However you can only set the max sensitivity. Any value in the first box , or minimum sensitivity, causes qsynth downstream to ignore velocity off, which means all notes are, once pressed, sustained on until you turn the volume on qsynth to off which resets it. QMidiRoute has woefully inadequate documentation. Their manpage doesn't even contain the word "velocity" which is clearly in the application. Can anyone tell me of how to get this to work, or recommend another method for my original purpose?

---

