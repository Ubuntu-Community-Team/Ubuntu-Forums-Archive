---
title: "FFmpeg audio sync"
date: 2009-02-22
forum: Ubuntu Studio
---

### Post by rylleman on 2009-02-22
When converting an avi (Microsoft DV) to x264 mov in FFmpeg audio/video gets out of sync.
The movie is 30 minutes and at the end of it the sync is off with about 1-2 seconds.

The command I'm running is;
ffmpeg  -qmax 9 -i input.avi -s 768x576 -r 25 -pass 2 -vcodec libx264 output.mov

I've tried to add different combinations of -async and -vsync without any difference at all.

So, how do I get ffmpeg to produce a synced movie?

---

### Post by FakeOutdoorsman on 2009-02-23
Are you using a FFmpeg from the repository, or did you compile it yourself?  One reason to compile FFmpeg is to gain access to the libx264 presets which makes high quality encoding much easier.  Try one of these presets and let me know if it is still out of sync.  More info:

[HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)

---

### Post by rylleman on 2009-02-23
I'm using the unstripped version from the medibuntu repos.

Starting out with your guide at the first step to purge the old version I get told that a whole range of apps depending on ffmpeg will be removed, something I'm not prepared to do in the middle of a production...

So, what to do?

---

### Post by scar1 on 2011-09-07
I had the same problem try the "-async 1" option. This stretches the audio to match video timestamps.

---

