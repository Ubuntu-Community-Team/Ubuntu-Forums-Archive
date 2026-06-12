---
title: "ffmpeg libmp3lame buffer size issue"
date: 2009-04-26
forum: Ubuntu Studio
---

### Post by rudygrabmore on 2009-04-26
i am trying to make video files usable for my portable player. i'm using ffmpeg to resize etc the files, and i'm running into a snag with libmp3lame conversion.


matt@matt-desktop:~$ ffmpeg -i /home/matt/Desktop/test.avi -aspect 1.7777 -t 00:05:00 -g 1 -b 256k -r 12 -s 160X128 -vtag xvid -vcodec libxvid -ac 2 -ar 44100 -ab 128k -acodec libmp3lame /home/matt/Desktop/test2.avi
FFmpeg version SVN-r18680, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-postproc --enable-pthreads --enable-libfaac --enable-libfaad --enable-libmp3lame --enable-libtheora --enable-libx264 --enable-libxvid
  libavutil     50. 3. 0 / 50. 3. 0
  libavcodec    52.27. 0 / 52.27. 0
  libavformat   52.32. 0 / 52.32. 0
  libavdevice   52. 2. 0 / 52. 2. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Apr 25 2009 00:32:55, gcc: 4.3.3
Input #0, avi, from '/home/matt/Desktop/test.avi':
  Duration: 00:22:15.40, start: 0.000000, bitrate: 1220 kb/s
    Stream #0.0: Video: msmpeg4v2, yuv420p, 480x360, 23.98 tbr, 23.98 tbn, 23.98 tbc
    Stream #0.1: Audio: mp3, 44100 Hz, stereo, s16, 192 kb/s
Output #0, avi, to '/home/matt/Desktop/test2.avi':
    Stream #0.0: Video: libxvid, yuv420p, 160x128 [PAR 64:45 DAR 16:9], q=2-31, 256 kb/s, 12 tbn, 12 tbc
    Stream #0.1: Audio: libmp3lame, 44100 Hz, stereo, s16, 128 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Press [q] to stop encoding
[libmp3lame @ 0xaaf18a0]lame: output buffer too small (buffer index: 9195, free bytes: 597)
Audio encoding failed



i tried setting the using "bufsize" to set the buffer to 9195 and 597 with the same result.  i really don't know anything about a/v files or codecs, i'm just reading what others have done and copy, pasting commands, so if someone could shed some light on what an output buffer is, and how i get it to not be too small it would be greatly appreciated.

---

### Post by andrew.46 on 2009-04-26
Hi rudygrabmore,

Unfortunately this is a 'known problem' with the newest version of Lame and the svn FFmpeg. There has been extensive discussion on the FFmpeg mailing lists about the best way to fix this but the best short term measure is what I eventually did in my own case: revert to lame 3.98. This will again give trouble free mp3 conversion with FFmpeg.

All the best,

Andrew

---

### Post by FakeOutdoorsman on 2009-04-27
I usually ignore this error.  The resulting files seem to work fine for me with no issues.  Probably not the best practice.

---

