---
title: "How to voice over on a video file"
date: 2009-02-18
forum: Ubuntu Studio
---

### Post by philidox on 2009-02-18
I have a desktop recording that I would like to redo the voice recording.  I have never done a voice over on a video file does anyone know how or at least get me in the right direction

---

### Post by cotcot on 2009-02-18
I suppose you have the new audio track. So load a multitrack video editor (blender vse, cinelerra, ...), delete the old track and insert the new, finally render.

Avidemux is another possibility. Load the video. Select --> Audio --> Main track. This gives you the possibility to add a new track (external source).

Either you are not familiar with video editors or ffmpeg/mplayer or maybe I do not fully understand what you want. If it is the first then it is better to tell it, so that we can try to help you in a more dedicated way.

---

### Post by philidox on 2009-03-02
ok I'll try that. thx

---

### Post by KyleRickards on 2009-11-02
Hi

Realise this is a bit of an old thread but I am trying to do the same, i.e., shoot some footage on my camcorder, upload to PC and then add voiceover/narration to parts of the footage, similar to a documentary. I guess I would need the ability to add a further audio track over the existing one without replacing the master.

Which would be my best program, I have Ubuntu Studio installed on a spare HDD if there is anything there that will help?

Kyle

---

### Post by gordintoronto on 2009-11-28
> **KyleRickards said:**
> Hi

Realise this is a bit of an old thread but I am trying to do the same, i.e., shoot some footage on my camcorder, upload to PC and then add voiceover/narration to parts of the footage, similar to a documentary. I guess I would need the ability to add a further audio track over the existing one without replacing the master.

Which would be my best program, I have Ubuntu Studio installed on a spare HDD if there is anything there that will help?

Kyle

This is very simple with Cinelerra.

---

### Post by cotcot on 2009-11-29
Most multitrack editors are able to do this. If you have an editor with keyframing you can lower the sound level of the video track when the narration comes up and vv.

---

