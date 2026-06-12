---
title: "Blender - Video sequence editor audio problem"
date: 2009-08-08
forum: Ubuntu Studio
---

### Post by Jim_in_Omaha on 2009-08-08
I am trying to use Blender's video sequence editor to work on some video projects. I'm new to Blender.

The problem I'm working on is I load a large MOV or AVI {movie + audio HD} into the sequence editor. The audio and video strips are different lengths and are out of sync. On one video that was 1h 55min it only loaded about 85% of the audio track. Had another that the audio was longer than the video.

I have been working with Kdenlive, Kino, Cinelerra. Most of the time they all crash at some point or another. Kdenlive I actually was getting pretty good but it will quit. So far Blender has not crashed yet with all the huge videos I've tried loading into it.

Any suggestions are appreciated. Running Jaunty 64 with 4g. Blender 2.49a

---

### Post by Jim_in_Omaha on 2009-08-08
I think I figured it out myself. I had to set the Anime/Playback to FPS: 30 and a timebase of 1.001 to get the NTSC of 29.97. This timing issue is probably common knowledge to the video editing crowd. Once that is set with both the AVI and the MOV the length of the audio and video strips match. 

And so far, no crashes. We'll see as I progress.

---

### Post by lexxore on 2010-01-21
Not sure if this will help anyone but you will need to set your output format before you load the video into the sequencer. If you are like me and set it after you loaded your video you will need to go to the sequencer buttons and under the input section press the reload button.

---

### Post by peet76 on 2012-08-25
Hi,

I have another solution: before add movie strip in the VSE check the frame rate of the movie (VLC player CTRL+J)  and then set the render frame rate in blender Render tab.

[http://my.opera.com/chaitanyak/blog/2012/02/15/common-problems-beginners-have-with-blender-vse](http://my.opera.com/chaitanyak/blog/2012/02/15/common-problems-beginners-have-with-blender-vse)

My English is bad :(

PeeT76

---

### Post by nothingspecial on 2012-08-25
Thank you for the extra information.

But this thread is very old and getting rather mouldy.

Closed.

---

