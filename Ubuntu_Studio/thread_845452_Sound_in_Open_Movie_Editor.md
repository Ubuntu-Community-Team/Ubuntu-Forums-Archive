---
title: "Sound in Open Movie Editor"
date: 2008-06-30
forum: Ubuntu Studio
---

### Post by v4169sgr on 2008-06-30
Ubuntu 8.04, with restricted extras, and the medibuntu repository enabled.

I am using Open Movie Editor to string together AVI format movie clips for writing to video CDs.

The AVIs are of the form:

```
RIFF (little-endian) data, AVI, 640 x 480, 25.00 fps, video: XviD, audio: MPEG-1 Layer 3 (stereo, 48000 Hz)
```

and are actually .mod files pulled off a Panasonic SDC H40 camcorder and converted with mod2avi [found elsewhere on these forums].

I can arrange the clips on a common timeline, and export to a single file, without problem. My issue is that something happens to the sound on the video clips. Specifically, sound becomes a loud 'chirp' right at the beginning of the clip.

If I use avidemux with the same files, I have both video and audio on the same timeline [but haven't yet figured out a way of fading to black, and adding a secondary audio track].

So, how can I have audio on my Open Movie Editor movies?

---

### Post by allcazar on 2008-07-07
Hello, I have the same problem (I have a Panasonic SDR-S7)... but you don't even have to convert .mod to .avi.  Open Movie Editor just accepts .mod clips in my opinion.  Only the sounds "jerks".

I tried everything.  I installed the Pinnacle SD Motion application that came with the camera in a Virtualbox environment.  I works, and even rather fluently.  The only problem is that it needs to "import" the .MOD files into a Windows-directory and since my Virtual-box environment is only 9 Gb... I get stuck (or I have to remove the files manually).  So... if you wish to proceed this way make shure your Virtual-hard drive is dynamic and not static. 

So, this is after investigating all possibilities how I deal with the .MOD files.  Seems the .MOD files are actually MPEG-2 format. So you do not have to decode-recode them.  Only rename should do.   


1. I copy my SD-card to a "original" directory somewhere on the HD
2. I batch rename the .MOD files using Krename (in the repositories).   I make from "MOV001.MOD" for instance "200807130412.mpg". So I replace the filetype from .MOD to .mpg and rename the file according to the creation date and time.  In the same time  
3. The renamed files are copied (so I keep the originals for safety) into  one directory 
4. I finished with using KDenlive as video-editor because it is in my proper language, sound seems to work and it can write directly to DVD

---

### Post by Creative2 on 2008-07-08
well i used open movie editor , with avi files ... but when i have rendered i have lost sound.... -.-''
it seems has some problem with sound system o library i don't know now i ma using blender and kdenlive and i ma happy much more with blender..

---

### Post by v4169sgr on 2008-07-08
I am now using kino rather than Open Movie Editor. As far as I can see, it does everything that I need it to.

---

