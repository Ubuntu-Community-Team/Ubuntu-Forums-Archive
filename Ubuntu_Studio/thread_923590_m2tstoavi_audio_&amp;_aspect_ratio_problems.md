---
title: "m2tstoavi: audio &amp; aspect ratio problems"
date: 2008-09-18
forum: Ubuntu Studio
---

### Post by jtappin on 2008-09-18
Having recently bought a Sony HDR-SR11 (one of the very few hard disk or flash-memory camcorders with a viewfinder), I installed m2tstoavi, and it looks to be mainly working but there are 2 significant problems.

1) When I play back the resulting AVI file, there is no sound although playing back on the camera does have sound. According to the konqueror properties window the file has an audio codec of DVM (and video codec of FMP4). I have tried the files on two different computers, both of which do give sound on other AVI files with MP3 sound codecs. Is anyone aware of a problem with this camera/codec or of a setting that might fix the problem. By disabling the deletion of the intermediate .ac3 audio file, I can confirm that the sound is being extracted correctly so the problem has to be in the re-encoding stage.

2) When played back with xine or mplayer the video defaults to a square aspect ratio. Actually the whole resolution question is a bit odd as the camera is 1080i which should be 1920 columns but setting the x-size to 1920 rather than 1440 in the m2tstoavi script generates garbage. Again any clues about where to look for fixes would be much appreciated. (FWIW the screen I'm using for playback is 1920x1200 resolution).

---

### Post by jtappin on 2008-09-18
I think I've found at least **a** solution to both problems if not **the best** solution.

1) I was able to get sound by changing "-acodec copy" to "-acodec mp3" in the ffmpeg call. 

2) a) Turns out that it's necessary to specify an aspect ratio in the ffmpeg call.
b) The 1920 vs 1440 issue isn't very clearly described in the manual, but only the highest quality mode is 1920 all the others are 1440.

---

### Post by Erlander on 2008-09-19
Hi,

I have a HDR-SR11E which is the PAL version.  I'm still not very successful with M2TStoAVI but thought I ought to mention that the settings for the camera include 1920x1080 and 1440x1080.  Mine came set on 1440x1080 so it would be worth checking.

Rob

---

### Post by cotcot on 2008-09-19
I have sound and size OK. Look to post 15 in [[COLOR="Red"]this[/COLOR]]("http://ubuntuforums.org/showthread.php?t=898235&page=2") thread.
Hope this will help you.
Be aware that opening some apps with sound locks the sound server for other apps. Have you tested the video with a fresh boot (no other sound apps in use) ?
I experience this with blender and vlc.

---

