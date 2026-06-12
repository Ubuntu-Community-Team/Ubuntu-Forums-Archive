---
title: "How to Import a wav file into an MPEG and create a new improved MPEG"
date: 2009-04-15
forum: Ubuntu Studio
---

### Post by taronski on 2009-04-15
Katanga,

I have created a MPEG movie using KINO but I now would like to add my own commentary which I created as a WAV file.  What software should I use to mix these two media into a new "improved" MPEG file.

Thanks a lot

Taron

---

### Post by FakeOutdoorsman on 2009-04-15
Convert WAV to MP2:
```
ffmpeg -i newcommentary.wav newcommentary.mp2
```
Now combine the two sources and ignore audio from original video:
```
ffmpeg -i video.mpg -i newcommentary.mp2 -acodec copy -vcodec copy -map 0:0 -map 1:0 newvideo.mpg
```
The *map* option tells FFmpeg what to grab from each input.  Works well because there is no re-encoding.  You're just copying streams so there is no quality loss and it's fast too.

---

### Post by taronski on 2009-04-15
Thanks a lot FakeOutdoorsman,

Here is another sign of my ignorance, how do I change the dir to execute the command in the correct folder?

Thanks again

Taron

---

### Post by FakeOutdoorsman on 2009-04-15
Example: my newcommentary.wav is in /home/frinkahedron/Desktop/audio/new.  When you open Terminal, the command prompt will already be set to your home folder.  Now I just:
```
cd Desktop/audio/new
```
You can use the tab button on your keyboard to autocomplete the path to your target directory.  For example, I can just type *D*, hit tab, and autocomplete will either fill it out for me, or list all files and directories that start with *D*.  Or you can just tell FFmpeg where everything is.  Assuming you are in your home folder (the command *cd* will take you to your home folder no matter where you are):
```
ffmpeg -i Desktop/video.mpg -i Desktop/audio/new/newcommentary.mp2 -acodec copy -vcodec copy -map 0:0 -map 1:0 newvideo.mpg
```

---

### Post by taronski on 2009-04-15
Thanks a lot will try it tonight and let you know.

Thanks again

Taron

---

