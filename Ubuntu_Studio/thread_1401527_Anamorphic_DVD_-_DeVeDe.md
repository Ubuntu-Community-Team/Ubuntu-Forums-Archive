---
title: "Anamorphic DVD? - DeVeDe"
date: 2010-02-08
forum: Ubuntu Studio
---

### Post by rylleman on 2010-02-08
I need to create anamorphic DVDs, preferably using DeVeDe.

The source material is 1920x1080 avi.
Using options; final size - standard, 16:9 aspect ratio and scale image. Will this create a *proper* anamorphic DVD?

Browsing the net for anamorphic specs I found out that there should be a [Widescreen signaling]("http://en.wikipedia.org/wiki/Widescreen_signaling") code in the DVD that tells the DVD-player to show in correct aspect ratio. Is DeVeDe adding this to it's scaled output?

In short, is DeVeDe outputting true anamorphic DVDs that will playback with proper aspect ratio on both 4:3 and 16:9 screens?

(using DeVeDe 3.11)

---

### Post by VertexPusher on 2010-02-08
I haven't used DeVeDe yet, but widescreen signaling is such a basic feature in DVD authoring, DeVeDe would basically be broken without it. I don't think you need to worry about it. By the way, you can test your DVD before burning it, e.g. by pointing VLC at the .iso image file or the VIDEO_TS folder on your hard disk. If the aspect ratio flags are wrong, you'll notice it.

---

### Post by rylleman on 2010-02-08
Ok, thanks. I just wanted to make sure since I didn't find anything specific about DeVeDe and anamorphic DVDs.

---

