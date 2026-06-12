---
title: "Theora 1.0 released"
date: 2009-02-10
forum: The Cafe
---

### Post by glotz on 2009-02-10
[http://www.xiph.org/press/2008/theora-release-1.0/](http://www.xiph.org/press/2008/theora-release-1.0/)

A video codec that's

[LIST]
[*]Easy on CPU
[*]Free Software
[*]royalty free
[*]included in HTML5
[/LIST]

Yeehaw! \\:D/

---

### Post by eragon100 on 2009-02-10
> **glotz said:**
> [http://www.xiph.org/press/2008/theora-release-1.0/](http://www.xiph.org/press/2008/theora-release-1.0/)

A video codec that's

[LIST]
[*]Easy on CPU
[*]Free Software
[*]royalty free
[*]included in HTML5
[/LIST]

Yeehaw! \\:D/

Very nice, but since all the anime (and other videos) I download are only available in other formats, I won't be using it. I know it is possible to convert these files to theora with one mouse click in the program ogg-convert, but double lossy compression will degrade video quality, so no deal. I realize the fact that people like me don't use the codec keep more videos from being encoded with the codec, but since avi, mov, wmv etc. gstreamer plugins are installable with one mouse click (and no legal issues where I live either), I couldn't care less.

---

### Post by Polygon on 2009-02-10
my only problem with theora is that it uses keyframes, so while switching around in a movie, you get garbled video for a bit (or a long time depending on how they encoded it, more or less keyframes) until it reaches another keyframe and its fine.

---

### Post by Lostincyberspace on 2009-02-10
> **Polygon said:**
> my only problem with theora is that it uses keyframes, so while switching around in a movie, you get garbled video for a bit (or a long time depending on how they encoded it, more or less keyframes) until it reaches another keyframe and its fine.
I believe most others are like that too I have it happen all time with xvid and other avi codecs?

---

### Post by qazwsx on 2009-02-10
So codec which is VP3 successor and *belived* to be patent free.

For  quality DVD ripping theora is just horrible if you compare it x264 or xvid at same bitrate (both GPL). And even at 5000 kbps it looses much details according to my source material.

Not totally hopeless but if we want H.264 (which specs are standardized and available) killer this is not a soluton.

I'm way more intrested in dirac! Currently dirac is very CPU intensive currebtly. But no patent issues there.

---

### Post by qazwsx on 2009-02-10
> **Polygon said:**
> my only problem with theora is that it uses keyframes, so while switching around in a movie, you get garbled video for a bit (or a long time depending on how they encoded it, more or less keyframes) until it reaches another keyframe and its fine.
Probably just decoder, encoder or damaged data issue and not in theora itself.

---

### Post by Polygon on 2009-02-11
> **qazwsx said:**
> Probably just decoder, encoder or damaged data issue and not in theora itself.

no, its part of the format. I realized then when i was messing with ffmpeg2theora

it seems other formats use some sort of index, but whatever they use its much better then keframes i think, as no matter where you scroll to in the movie it starts playing instantly.

---

### Post by philliptweedie on 2009-02-11
> **eragon100 said:**
> (and no legal issues where I live either)

Is there anywhere you can go to check what the situation is regarding codecs and legality in your own country?

---

### Post by cl333r on 2009-02-11
That's not news, the page says November 3, 2008.
Despite h264 being (in some cases much) better than theora, theora is still better for HTML5 because it means there will be no need for binary blobs that make Firefox crash. Yesterday I experienced this like 5 times when watching the colbert report and some large you tube videos. I belive these issues would be knocked out if Firefox wouldn't have to use a closed source binary blob called Flash.

---

### Post by Colonel Kilkenny on 2009-02-11
Theora is not in HTML5 spec.
HTML5 doesn't specify any codec when it comes to video -element.

---

### Post by cl333r on 2009-02-11
> **Colonel Kilkenny said:**
> Theora is not in HTML5 spec.
HTML5 doesn't specify any codec when it comes to video -element.
I know, that's not what I mean, I was referring to Firefox's implementation and decision.

---

### Post by TenPlus1 on 2009-02-11
As far as I'm aware, Opera has included Theora also for html5 video formatting...

I've ripped a DVD and saved as Theora and the quality and size are really good, no problems so far...  I cant wait until it's implemented web-wide...

---

### Post by cl333r on 2009-02-11
Good to hear that, but I think Opera can't go its own way because its market share is too low to get people to adopt its decision.

---

### Post by Colonel Kilkenny on 2009-02-11
> **cl333r said:**
> I know, that's not what I mean, I was referring to Firefox's implementation and decision.

And I was actually referring to first post :)

Anyway, if Apple (+Nokia) and maybe Microsoft decide not to use Theora then using theora in FF or Opera is basically useless. Whole point of video-element was to have one way of doing things. Atm it looks like Opera and Mozilla are on their own and that doesn't fix the web. Actually is just causes more fragmentation.

And Opera doesn't have a need to go its own way as they have probably the most standard compliant browser and lots of people working with web specs (WHATWG, W3C, etc.).

---

### Post by Judo on 2009-02-11
> **Polygon said:**
> my only problem with theora is that it uses keyframes, so while switching around in a movie, you get garbled video for a bit (or a long time depending on how they encoded it, more or less keyframes) until it reaches another keyframe and its fine.
All standards use intra-frames/i-frames/keyframes.

Xiph is working on a new encoder called Thusnelda now that is much better than the original and is comparable to Xvid, but x264 is still on top.

I'm more interested in Dirac than Theora, though.

---

### Post by Polygon on 2009-02-11
> **Judo said:**
> All standards use intra-frames/i-frames/keyframes.

Xiph is working on a new encoder called Thusnelda now that is much better than the original and is comparable to Xvid, but x264 is still on top.

I'm more interested in Dirac than Theora, though.

then what makes it so other formats can seek to a certain spot in a video so much better then theora?

---

### Post by zekopeko on 2009-02-11
> **Polygon said:**
> then what makes it so other formats can seek to a certain spot in a video so much better then theora?

theora isn't the best of codecs but it's patent free. you should see some of the <video> stuff that you can do. way better then flash. and CPU negligible.

i also noticed this in VLC (diffrent format/codecs) so it may not be a theora problem.

---

### Post by TBOL3 on 2009-02-11
It's the quality.  In order to have the same quality, thoera must be massive in size.  Where as H264 can fit much more in a smaller space.  If you see a video in h264 that is of low quality, then you will really notice the artifacts.

---

### Post by qazwsx on 2009-02-12
> **Judo said:**
> 
Xiph is working on a new encoder called Thusnelda now that is much better than the original and is comparable to Xvid

Sounds intresting. How about encoding speed?


Yesterday I tried to rip DVD with theora. Oh my there are  blocks everywhere even at -v 8. -v 10 is not even transparent to a human eye and bitrate is just massive over 6000 kbps and with x264 at 2000-2500 kbps I couldn't see the difference in terms of which one is better the source or the rip. IMHO even mpeg-2 preserves more details but mpeg-2 is of course  worse when it comes lower bitrates.

> **Judo said:**
> 
I'm more interested in Dirac than Theora, though.
+1

---

