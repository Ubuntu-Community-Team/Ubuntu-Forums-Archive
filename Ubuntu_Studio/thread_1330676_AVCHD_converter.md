---
title: "AVCHD converter"
date: 2009-11-18
forum: Ubuntu Studio
---

### Post by trose on 2009-11-18
I'm trying to use ubuntu-studio and I need to convert my AVCHD Panasonic HDC Camcorder files to something that studio can handle.  I suppose MPEG.  Panasonic includes software for windoze but I don't use windoze.

Does anyone know a decent OSS converter for linux?  I've been searching the web for a couple hours.  I tried to see if the latest ubuntu studio has converters included.  From what I can tell they don't.
Thanks in advance, Tom

---

### Post by metol on 2009-11-18
ffmpeg is king here.  I would assume it is included with the studio flavor of Ubuntu, if not you will find it in the repos.  I just converted a 1080i AVCHD file yesterday with...

```
ffmpeg -i input.MTS -f mpeg -b 16M -deinterlace output.mpeg
```

If you have a 1080p recording, leave out the '-deinterlace' option.  There is also a GUI interface for ffmpeg called 'WinFF'.

Regards,
Metol

---

### Post by cotcot on 2009-11-19
This is what I use:


mencoder (mplayer):
```
mencoder -oac copy -ovc lavc -of mpeg -mpegopts format=dvd -vf scale=1920:1080,harddup -lavcopts vcodec=mpeg2video:vrc_buf_size=1835:vrc_maxrate=9800:vbitrate=8000:keyint=15:aspect=16/9:threads=4 00126.MTS -vf lavcdeint -ofps 25 -fps 50 -o 00126.mpg
```

Here is one for ffmpeg

```
 ffmpeg -i 00106.MTS -vcodec libxvid -b 18000k -acodec libmp3lame -ac 2 -ab 320k -deinterlace -s 1920x1080 00106.avi
```

And to batch convert a set of avchd files I use this :

```
find ~/encode -name '*.MTS' -type f -exec mencoder '{}' -oac copy -ovc lavc -of mpeg -mpegopts format=dvd -vf scale=1920:1080,harddup -lavcopts vcodec=mpeg2video:vrc_buf_size=1835:vrc_maxrate=9800:vbitrate=8000:keyint=15:aspect=16/9:threads=4 -vf lavcdeint -ofps 25 -fps 50 -o '{}'.mpg \;
```

---

### Post by ilil on 2009-11-19
I recommend Winff as nice GUI for FFmpeg. No spell with ffmpeg & mencoder now :)

---

