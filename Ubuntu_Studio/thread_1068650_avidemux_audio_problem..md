---
title: "avidemux audio problem."
date: 2009-02-13
forum: Ubuntu Studio
---

### Post by Bigneil on 2009-02-13
when opening avi files shot on my digital camera, a message appears telling me there is no audio codec for this sound file, and save audio will work. 

I tried this and it does work, except, the audio always cuts off at the same moment in time, leaving the last one and half minutes with no audio.

Is there a time limit on 'save audio' or a maximum amount of data allowed.?

could anybody point me in the correct direction?

---

### Post by cotcot on 2009-02-15
There is no limit on the audio file.
I do not have a solution; only a couple of suggestions/guesses :

Save the clip from your cam in another format as .avi (MPEG P V+A for instance) (I have seen some problems with avidemux saving to .avi)

Could have something to do with importing NTCS video and saving it as PAL or sound being 44.1 or 48 kHz.

Check sound in another video editor. Blender VSE, kino, kdenlive, cinelerra.

Convert the clip with ffmpeg or mencoder. WinFF is a GUI for ffmpeg.

---

