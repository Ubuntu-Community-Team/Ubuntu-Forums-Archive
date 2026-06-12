---
title: "Video editing programs that hadle mpeg2-TS files"
date: 2009-08-28
forum: Ubuntu Studio
---

### Post by epi 1:10,000 on 2009-08-28
Are there any video editing software that handles mpeg2 transport streams from mythtv.  I have a dedicated backend but would like to use my main computer for video editing/cutting the commercials because it has much more prossesing power.  I'm looking for something that might have an easy interface for cutting out segments/commercials.

---

### Post by kiddo on 2009-08-31
Yes, what you probably want is [PiTiVi]("http://pitivi.org") ([from the PPA]("https://launchpad.net/~gstreamer-developers/+archive/ppa"), for Jaunty or Karmic only). As far as I know, gstreamer has had TS and PS demuxers for a while, and a PS muxer was merged not long ago. But anyway, I presume you want to encode into something different from mpeg2?

If, instead, you just want to cut without re-encoding, maybe you want to look into avidemux.

---

