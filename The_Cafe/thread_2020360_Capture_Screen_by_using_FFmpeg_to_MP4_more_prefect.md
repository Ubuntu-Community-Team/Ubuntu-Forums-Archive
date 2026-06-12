---
title: "Capture Screen by using FFmpeg to MP4 more prefect way"
date: 2012-07-08
forum: The Cafe
---

### Post by beterhans on 2012-07-08
capture a mp4 for all devices could play

1. you will need ffmpeg x264 libfaac installed

2. use this command
ffmpeg -f x11grab -follow_mouse 200 -r 8 -s 800x600 -i :0.0 \
-f alsa -i hw:0 \
-vcodec libx264 -profile:v main -level 3.1 -qmax 20 -qmin 12 \
-acodec libfaac -ac 2 -ab 160k \
-threads 0 \
screen_capture.mp4

(If you are not using alsa the sound won't walk)

No sound? check this video
[http://www.youtube.com/watch?v=fJ7gSP4lKvo](http://www.youtube.com/watch?v=fJ7gSP4lKvo)

A/V NOT sync? don't let it ask you "do you wan't to overwrite?" delete the file and try again.

---

