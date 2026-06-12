---
title: "export 192 khz 24 bit audio from video editor?"
date: 2017-01-04
forum: Ubuntu Studio
---

### Post by spiridonios on 2017-01-04
Hello,

I' ve been trying to export a video i edited, with audio resolution of 192 khz and 24 bit. I ve been editing in blender and made it till exporting with 192 khz but i cannot turn the 16 bit to 24 bit of the output.  (More explanation on my process with blender here ). Of course my original audio is 192 khz and 24 bit. After a lot of trial of exporting directly from blender, i tried to take my audio and video and try to import, synchronize and export from another video editing program. I tried Cinelerra, Kdenlive, Kino, Lives, Open Shot Video Editor and Pitivi with no success. None of them seem of having the capability of exporting at these audio resolution. Is there any known video editing program capable of exporting at 192 khz, 24 bit? [URL="https://blenderartists.org/forum/showthread.php?407042-video-speed-goes-faster-after-export-audio-loses-quality"]
[/URL]

---

### Post by marseille2 on 2017-01-04
Maybe try ffmpeg or Handbrake. [Lightworks]("https://www.lwks.com/index.php?option=com_kunena&func=view&catid=8&id=86488&Itemid=81") might be another option, but could be overkill if you don't want another pro NLE. If you go with the former... you could just export video with no sound from your editor, then couple the vid with sound in ffmpeg or (probably) [Handbrake]("https://handbrake.fr/").

---

### Post by spiridonios on 2017-01-05
Thank you marseille2!

ffmpeg did the job! It's funny to use a program with no Gui to work with video, but i must give it a big respect for actually doing what all of the other programs could not do. I couldn't find a way to import a separate audio track to compile with the video in handbrake. And although i downloaded and installed lightworks, i have the impression that the trial version does not let you export such big audio resolutions.The command i used in ffmpeg was: ffmpeg -i video.avi -i audio.wav -map 0:v -map 1:a -c copy output.avi
ffmpeg then it is!

---

