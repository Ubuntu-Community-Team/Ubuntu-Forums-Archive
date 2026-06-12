---
title: "Rendering / output recommendations from Pitivi / ffmpeg combo"
date: 2010-06-06
forum: Ubuntu Studio
---

### Post by cdaringe on 2010-06-06
Hi all:

Currently I'm using ffmpeg command line for screen capture & Pitivi for easy cutting.

My screen capture command is as follows, and gets me beautiful video:
```

ffmpeg -f alsa -ac 2 -i hw:0,0 -f x11grab -r 20 -s 1360x768+0+0 -i :0.0 -acodec pcm_s16le -vcodec libx264 -vpre lossless_ultrafast -threads 0 -y TITLE_OF_VIDEO.mkv

```

After splicing and adding new audio, I'd like to know some of the best setups for getting clear audio/video out, as close to the native recordings' quality.  I'm messing with the parameters, and compression is making things ugly.  How should I retain good, grain-free quality after changes in Pitivi?  I intend to upload some videos on the yewtubes, and don't want recompression into their flv to make things any less clear.

---

### Post by cdaringe on 2010-06-08
posted to wrong forum :x

---

