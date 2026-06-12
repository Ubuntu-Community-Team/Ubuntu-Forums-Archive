---
title: "mplayer args to write a file that gopchop can read."
date: 2009-01-30
forum: Ubuntu Studio
---

### Post by Cracauer on 2009-01-30
I want to convert a file from an obscure format to something that gopchop can deal with.

I know that I need two components here:
[list]
[*] mpeg video
[*] mpeg file format
[/list]

But when I do the following, with the "-of mpeg", mplayer just hangs
```

[...]
ew_Face failed. Maybe the font path is wrong.
Please supply the text font file (~/.mplayer/subfont.ttf).
subtitle font: load_sub_face failed.
Writing header...
^C^C^C^C^Z

```

Have to kill-9 it.

```

mencoder -ovc lavc -lavcopts vcodec=mpeg2video \
        -oac pcm \
        -demuxer lavf -aid 1  \
        -of mpeg \
        -o /var/tmp/l.mpg \
        foo.evo
 
```

Is "-of mpeg" broken?

Pilot errors?

What are my options?

I know mplayer can be naughty with file format correctness and all that. But This is a HD-DVD file and I'm glad I can read it in mplayer. The built-in ffmpeg in mplayer plays it but I don't think I have a standalone ffmpeg which plays this file.  Maybe I have to do a two-step, first in avi format with mpeg format and then use ffmpeg to copy the video stream but change the container?

---

