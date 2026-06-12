---
title: "Full Screen Audio/Video Recording and Editing"
date: 2009-10-18
forum: Ubuntu Studio
---

### Post by Airyairy on 2009-10-18
Hi I want to record me playing fullscreen games under Ubuntu with sound and then edit them later. I notice there are quite a few programs that do similar things. Which ones are the best for what I'm planning?

---

### Post by Vadi on 2009-10-19
[glc]("http://nullkey.ath.cx/projects/glc") for recording and [pitivi]("http://www.pitivi.org/wiki/Main_Page") or openshot for editing.

I've found glc to be the best in terms of not reducing your fps while recording, but it's command-line only.

You can use this command to start a game with glc:

> glc-capture -o game.glc <full path to the game>

though I use this - it records at half resolution, but makes the filesize smaller and cpu usage okay on my computer:

> glc-capture -o game4.glc -z none -r 0.5 <full path to the game>

That will start the game with glc for you. To start recording, press Shift+F8, to stop, toggle that again.

Then after you're done playing, you want to encode your .glc file to a video and audio files for editing... you can do it with this:

> glc-play game.glc -a 2 -o audio.wav
glc-play game.glc -y 1 -o test.y4m
gst-launch-0.10 filesrc location=test.y4m ! decodebin ! avimux ! filesink location=video.avi

You will get an audio.wav file, video.avi and a test.y4m file out of that. You can delete the test.y4m file, as it's temporary and not needed anymore.

Now just import video.avi and audio.wav into your favourite linux video editor and attempt to do some magic... I've been using pitivi or openshot lately, depending on which actually works at the time.

---

