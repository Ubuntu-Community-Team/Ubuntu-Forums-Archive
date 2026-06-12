---
title: "[SOLVED] Encoding an mp3 into an avi"
date: 2008-07-19
forum: Ubuntu Studio
---

### Post by abuakel on 2008-07-19
I took a video of my desktop with gtk-recordmydesktop, converted it to avi using mencoder.. but now, I've had trouble getting an mp3 song embedded into the avi file. 
Any ideas?

---

### Post by BLTicklemonster on 2008-07-20
Avidemux.

sudo aptitude install avidemux

Open the file with avidemux, then go to Audio (top of avidemux browser) then choose Main Track. In the window that opens, in the first section, choose Audio Source: External MP3, then in Extrenal file, choose the path to the mp3 you want to use.

...probably. I never did this, but that looks like what you should do. 

Let me know either if it works, or how horribly it messes everything up so I'll know if I ever want to add audio to a video!

:)

*edit: just added all your base,mp3 to a video of a ufo flying overhead, and it worked fine. Have fun!!!

---

### Post by abuakel on 2008-07-20
> **BLTicklemonster said:**
> Avidemux.

sudo aptitude install avidemux

Open the file with avidemux, then go to Audio (top of avidemux browser) then choose Main Track. In the window that opens, in the first section, choose Audio Source: External MP3, then in Extrenal file, choose the path to the mp3 you want to use.

...probably. I never did this, but that looks like what you should do. 

Let me know either if it works, or how horribly it messes everything up so I'll know if I ever want to add audio to a video!

:)

*edit: just added all your base,mp3 to a video of a ufo flying overhead, and it worked fine. Have fun!!!

hmm. well, after I added the External MP3.. how do I save the file so that it embeds it.. when I clicked save, it didn't do anything.

---

### Post by BLTicklemonster on 2008-07-20
On the right, under video, choose mpeg-4 asp (xvid4) then under video, choose mp3 (lame) now go to file> save> save video, and save it as videoname.mpeg.

(took me a while to get the audio to settle down and not skip, but that worked for me. play around once you get this and see what other settings work for you)

---

### Post by BLTicklemonster on 2008-07-20
Okay, just did it as an avi file. Same setup as in the prior post, but this time you can just change the audio, and leave the other stuff alone, then save video as filemane.avi.

Hope all this helps.

---

### Post by abuakel on 2008-07-20
> **BLTicklemonster said:**
> Okay, just did it as an avi file. Same setup as in the prior post, but this time you can just change the audio, and leave the other stuff alone, then save video as filemane.avi.

Hope all this helps.

Thanks, I'm curently in bed replying with my iPhone, so when I wake up tomorrow, I'll edit this post with results :)

Edit: yes, it worked perfectly thanks!!

---

