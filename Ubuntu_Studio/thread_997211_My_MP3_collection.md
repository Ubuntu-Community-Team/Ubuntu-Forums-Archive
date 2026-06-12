---
title: "My MP3 collection"
date: 2008-11-29
forum: Ubuntu Studio
---

### Post by yoman82 on 2008-11-29
I've got several gigs of 256 kb/s .wav music. I want to downscale this to perhaps 32or 64 kb/s music for playing on my music player (A Nintendo DS). The final product must be a .mp3. Is there an automated command I could just let run? Doing this manually would be a huge pain, as there are several hundred files. I would like to keep the original .wav file for playback, also. Thanks in advance!

---

### Post by ajgreeny on 2008-11-29
Soundconverter will do that for you, I think, though I'm not certain about how it will handle lots of folders full of wav files.  I can't remember if it will work recursively or not.

Just tried it and it will work well if you add all the folders you need before starting the conversion.  You can choose the output file type and destination from the edit menu, and it will not delete the original file unless you tell it to do so.

---

### Post by yoman82 on 2008-11-29
So... just sudo apt-get install soundconverter?

---

### Post by ajgreeny on 2008-11-29
That's right!  Just make sure you have all you will need for mp3 encoding as well, of course.

---

### Post by yoman82 on 2008-11-29
Thank you so much, you're a lifesaver.

---

