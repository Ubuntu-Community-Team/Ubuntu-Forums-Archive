---
title: "gstreamer pipeline to tanscode a video for ipod"
date: 2008-10-22
forum: Ubuntu Studio
---

### Post by yelo3 on 2008-10-22
Hello, I'm trying to write a patch to banshee to let video be transcoded by default when syncing to an ipod.

Unfortunately I still haven't found a correct gstreamer pipeline.

I tried with this

gst-launch-0.10 filesrc location="$input" ! decodebin name=decoder decoder. ! ffenc_mpeg4 bitrate=300000 ! queue ! ffmux_mp4 name=mux ! filesink location="$output".mp4 decoder. ! audioconvert ! faac bitrate=64000 ! mux.

but it does not work when transferred to my ipod
do you know a correct pipeline?
thanks

---

