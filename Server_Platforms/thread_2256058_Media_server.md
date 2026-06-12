---
title: "Media server"
date: 2014-12-09
forum: Server Platforms
---

### Post by Jason_Mulder on 2014-12-09
Hey,

Not sure if I am in the right place or wether this is even possible... I have a 5 year old pc that just can't handle 1080p. That pc is connected to my tv and I would like to play movies at it. Is it possible that the encoding(or how it's called) happens upstairs at my game pc and then is sent to the pc downstairs which displays it on the tv. The idea being that the quality doesn't matter as long as my game pc can handle it.
If possible, what software should I use?

Thanks,

Jason

---

### Post by TheFu on 2014-12-09
It is called "transcoding" and if you want the slow PC to handle 1080p content, you want a GPU that supports whatever codec using hardware and drivers, not the CPU.  Any $20 GPU can do this today as can any $150 netbook today - provided the video is h.264 or mpeg2 video and any supported audio (mp3/ac3/aac).  Without hardware video decoding using a GPU, the only solution is to force the resolution going to it to be DVD level or less. That is 480p.

For many people, the best answers for this stuff is:
* use Plex Media Server "somewhere" on the network - probably your gaming PC
* Get a cheap, video player for each remote location - a roku stick, chromecast, or any other DLNA client/renderer should work fine.

Plex will transcode, but my plex server just doesn't have the horsepower to do that, so I've never tried.

Oh - and if you go with a cheap chromecast device, be aware that it is **extremely** picking about both the video and audio codecs used.  It will not play normal FLV or AVI or MPEG2 files.  I hope all this makes sense. If not, ask.

---

### Post by Jason_Mulder on 2014-12-09
I happen to have Plex Media Server on my pc, I tried to stream to my tv but that didn't work so well with HD. If I could get it working on the old pc it would be great!

---

### Post by mörgæs on 2014-12-09
Which GPU are you using? Please post the results from ```
lspci -nnk | grep -iA2 vga
```

---

### Post by Jason_Mulder on 2014-12-10
Got it working. Couldn't get flash installed for Firefox so I installed Chrome. No lag at all when playing HD now from Plex :D

---

### Post by TheFu on 2014-12-10
> **Jason_Mulder said:**
> Got it working. Couldn't get flash installed for Firefox so I installed Chrome. No lag at all when playing HD now from Plex :D

So, you don't want help?  For me, running Chrome is not possible (political decision), so I know that running flash under Firefox can work, with the correct content streamed.

---

### Post by Jason_Mulder on 2014-12-11
Nah, it's just for watching movies at home. As long as it works I am happy. Thanks for the effort though! :)

---

