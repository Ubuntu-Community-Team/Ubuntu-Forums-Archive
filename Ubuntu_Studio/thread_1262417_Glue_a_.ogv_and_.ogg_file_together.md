---
title: "Glue a .ogv and .ogg file together?"
date: 2009-09-09
forum: Ubuntu Studio
---

### Post by hambone79 on 2009-09-09
Ok, I'm trying to make a screencast for work. I have recorded my screencast with gtk-recordmydesktop and Gnome Sound Recorder. I had to use Gnome Sound Recorder because no matter what I tried, I always ended up with awful sounding audio with gtk-recordmydesktop. Anyway, I now have an .ogv file from gtk-recordmydesktop and an .ogg file from Gnome Sound Recorder and I need to glue to two files together to make a single .ogv file.

I have tried using Kdenlive and a few other apps, but I always end up with sucky quality files that are 3-5x larger than the files I started with. Is there an easy way to this without blowing up the file size or losing quality?

---

### Post by DodgeV83 on 2009-09-09
One way:

Use sound converter to change the .ogg to a .wav

then

Use Avidemux, set the Video and Audio settings both to "copy" then open your video file.

Once open, click Audio -> Main Track -> Audio Source -> External WAV and Browser to the file.

Click OK and save the video.

---

### Post by hambone79 on 2009-09-15
For anyone still looking for a way to do this, just run this command:

```
apt-get install mkvtoolnix-gui
```

Then launch the **mmg** program.

This is a gui to mkvmerge and it will glue the two files together without changing the file size at all.

---

### Post by FakeOutdoorsman on 2009-09-15
Another alternative is FFmpeg:
```
ffmpeg -i input.ogv -i input.ogg -acodec copy -vcodec copy -f ogg output.ogv
```
This will copy the video and audio from each input and place them into *output.ogv*.  Because the video and audio are being copied there is no re-encoding and no loss in quality.

---

