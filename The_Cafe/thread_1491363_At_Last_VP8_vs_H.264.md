---
title: "At Last VP8 vs H.264"
date: 2010-05-23
forum: The Cafe
---

### Post by ssj6akshat on 2010-05-23
[http://www.streamingmedia.com/Articles/Editorial/Featured-Articles/First-Look-H.264-and-VP8-Compared-67266.aspx](http://www.streamingmedia.com/Articles/Editorial/Featured-Articles/First-Look-H.264-and-VP8-Compared-67266.aspx)

looks like to me VP8 is okay but H.264 is slightly better(bah!who cares?)

---

### Post by pwnst*r on 2010-05-23
> **ssj6akshat said:**
> (bah!who cares?)

You do.

---

### Post by gnomeuser on 2010-05-23
Just for fun I tried playing back the sunflower reference video (SD content) both in H264 and WebM on my ATOM powered netbook. In both cases GStreamer was used via Totem, for H264 I was using the hardware optimized Fluendo codec and for WebM the newly published WebM gstreamer plugin as present in the GStreamer Developer PPA.

Needless to say both played back in slideshow format. I believe there is room for improvement in that experience, I am especially surprised that the highly tuned proprietary H264 decoder from Fluendo was unable to keep up on the netbook, WebM is still early in development I had expected it to do poorly but to have both fail so utterly was a surprise.

---

### Post by ssj6akshat on 2010-05-23
> **pwnst*r said:**
> You do.

No.I don't,as long it is free(free as in freedom) but comparable,I don't give a damn about whatever it is.

---

### Post by madjr on 2010-05-23
VP8/web is going open source and getting support by everyone so, it should become the best option soon

anyway it WILL BE the ONLY option as youtube will make it default you like it or not

---

### Post by Madspyman on 2010-05-23
[http://www.quavlive.com/video_codec_comparison]("http://www.quavlive.com/video_codec_comparison")

How about this comparison? VP8 seems to hold up pretty well if you ask me.

---

### Post by zekopeko on 2010-05-23
That is a bad, bad comparison. The exact parameters that were passed to the encoder are non-existent. The frames aren't aligned. Not to mention that the video is encoded in 360p which is the lowest quality Youtube offers.
This isn't a good comparison by any stretch of imagination.

---

### Post by pwnst*r on 2010-05-23
> **ssj6akshat said:**
> No.I don't,as long it is free(free as in freedom) but comparable,I don't give a damn about whatever it is.

You cared enough to research and post a topic.  So, yes, you do.

---

### Post by weezerBo on 2010-05-23
> **pwnst*r said:**
> You cared enough to research and post a topic.  So, yes, you do.
Or he could care about other people think since "other people" make up the open web. I'm in a similar position. I don't care about the quality myself but it's in my interest (since my interest is in not being sodomized by the MPEG-LA) to allay others fears about the quality.

---

### Post by pwnst*r on 2010-05-23
I guess if all you're ever going to watch it on is a small monitor or laptop.

---

### Post by jerenept on 2010-05-23
> **weezerBo said:**
> Or he could care about other people think since "other people" make up the open web. I'm in a similar position. I don't care about the quality myself but it's in my interest (since my interest is in not being sodomized by the MPEG-LA) to allay others fears about the quality.

Roger that.
The MPEG Group have played into the hands of the MAFIAA too long. Meanwhile, it is in Google's interest to keep the Web open, just like the Apache Project and Linux.
I think......

---

### Post by nrs on 2010-05-23
> **pwnst*r said:**
> I guess if all you're ever going to watch it on is a small monitor or laptop.
 Personally, I'm using my PhenomII desktop w/ 30" SyncMaster. Quality may be_*** *everything****_ to you, and you're entitled to your opinion and all that. But it isn't for me. Quality must be considered along with legal / financial / ethical aspects for me, and I'm sure they do for most people -- at least for every other aspect of life. It kind of drops off when it comes to computers for some reason. 

And really, it's not like VP8/WebM is a steaming pile. It's roughly as good as -- or maybe even better -- than H.264 baseline, which is pretty much all that matters for <video>. It's not intended to compete against super optimized profiles used for HD movies or w/e. It exists for <video>.

Edit: that weezerBo comment was written by me. I forgot to log out of my brothers account.

---

### Post by formaldehyde_spoon on 2010-05-23
> **pwnst*r said:**
> I guess if all you're ever going to watch it on is a small monitor or laptop.

All we're going to be using it for is html5, so we should be comparing it against H.264 baseline profile. 

> **zekopeko said:**
> That is a bad, bad comparison. The exact parameters that were passed to the encoder are non-existent. The frames aren't aligned. Not to mention that the video is encoded in 360p which is the lowest quality Youtube offers.
This isn't a good comparison by any stretch of imagination.

Then look at the second link posted.  It's vs H.264 high profile, not baseline.  The bee on the flower looks marginally better in VP8, but the people under the trees is better in H.264.

That said, the first comparison isn't really that bad: it compares VP8 and H.264 in the role that VP8 will most often be used.

---

### Post by andrewabc on 2010-05-23
> **madjr said:**
> anyway it WILL BE the ONLY option as youtube will make it default you like it or not

Source for youtube using only VP8?
Last I heard couple months ago they were converting everything to h.264.
So now they are dumping that conversion and switching to VP8?

---

### Post by Merk42 on 2010-05-23
> **andrewabc said:**
> Source for youtube using only VP8?
Last I heard couple months ago they were converting everything to h.264.
So now they are dumping that conversion and switching to VP8?

It's currently in H.264
as for converting to VP8 you can see it in the HTML5 opt in for Youtube
[http://www.youtube.com/html5](http://www.youtube.com/html5)

Once Flash supports VP8 (Adobe is on board to do so) then Google can make all Youtube videos VP8.  They'd either display directly in the browser via HTML5, or through Flash on other browsers.

---

### Post by Shining Arcanine on 2010-05-23
> **Merk42 said:**
> It's currently in H.264
as for converting to VP8 you can see it in the HTML5 opt in for Youtube
[http://www.youtube.com/html5](http://www.youtube.com/html5)

Once Flash supports VP8 (Adobe is on board to do so) then Google can make all Youtube videos VP8.  They'd either display directly in the browser via HTML5, or through Flash on other browsers.
Would this not result in a loss of quality?

---

### Post by chris200x9 on 2010-05-23
I'm pro vp8 but, why not use x264? It's widely accepted as the best h.264 encoder.

---

### Post by formaldehyde_spoon on 2010-05-23
> **Shining Arcanine said:**
> Would this not result in a loss of quality?
I'm sure they're not taking an H.264 video and converting to VP8, they go from the original to VP8.

> **chris200x9 said:**
> I'm pro vp8 but, why not use x264? It's widely accepted as the best h.264 encoder.
They already use x264.  The point is they don't want to be stuck with H.264 because in 5 years the "free" runs out...

---

### Post by zekopeko on 2010-05-24
> **Shining Arcanine said:**
> Would this not result in a loss of quality?

No. Youtube keeps original files that were uploaded so they can transcode them to anything they like.

---

### Post by ssj6akshat on 2010-05-24
> **chris200x9 said:**
> I'm pro vp8 but, why not use x264? It's widely accepted as the best h.264 encoder.

x264 is an encoder only while VP8 is a codec and H.264 might not as free as it is today in 5 years.

---

