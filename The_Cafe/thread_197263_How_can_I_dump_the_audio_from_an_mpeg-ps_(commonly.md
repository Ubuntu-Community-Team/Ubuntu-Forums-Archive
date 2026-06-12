---
title: "How can I dump the audio from an mpeg-ps (commonly known as vob) file??"
date: 2006-06-15
forum: The Cafe
---

### Post by CyberAngel on 2006-06-15
Exactly what the topic header says :)

I have an mpeg-ps file and I want to extract only the audio from it.
How is that possible?

Don`t tell me to use avidemux cause it has a bug and it crashes when you are trying to open a vob file :(

---

### Post by wmcbrine on 2006-06-15
I do it thusly:

mplayer -dumpaudio -dumpfile filename.ac3 filename.vob

Now, maybe an .ac3 file isn't what you want. In that case, try this:

mplayer -ao pcm -vo null -vc dummy filename.vob

which will give you "audiodump.wav".

---

### Post by CyberAngel on 2006-06-15
[QUOTE=wmcbrine]I do it thusly:

mplayer -dumpaudio -dumpfile filename.ac3 filename.vob

Now, maybe an .ac3 file isn't what you want. In that case, try this:

mplayer -ao pcm -vo null -vc dummy filename.vob

which will give you "audiodump.wav".[/QUOTE]


Thanks! I tried the second option but it takes too long to extract the audio...

The first it extracts something but it does not work :)

Anyway the second option did the job ;)

---

### Post by GarethMB on 2006-06-15
I'd use VLC's streaming wizard but my install keeps crashing so i can't tell you anymore.

Edit I've fixed it but it will be obvious. :)

---

