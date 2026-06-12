---
title: "What do you think about Mozilla supporting h.264?"
date: 2012-03-20
forum: The Cafe
---

### Post by lovinglinux on 2012-03-20
There has been a lot of talk this week, about the fact that Mozilla decided to support h.264. The move is mostly because of the mobile market and Mozilla will initially target the mobile Firefox version and Boot2Gecko. However porting  such support for desktop is on the table as well.

The blog post from Mitchell Baker, Chair of the Mozilla Foundation:

[http://blog.lizardwrangler.com/2012/03/18/video-user-experience-and-our-mission/1234/](http://blog.lizardwrangler.com/2012/03/18/video-user-experience-and-our-mission/1234/)

A couple of articles discussing the issues of such move:

[http://arstechnica.com/gadgets/news/2012/03/idealism-vs-pragmatism-mozilla-debates-supporting-h264-video-playback.ars](http://arstechnica.com/gadgets/news/2012/03/idealism-vs-pragmatism-mozilla-debates-supporting-h264-video-playback.ars)

[http://arstechnica.com/business/news/2012/03/mozilla-firefox-needs-h264-support-to-survive-shift-to-mobile.ars?utm_source=rss&utm_medium=rss&utm_campaign=rss](http://arstechnica.com/business/news/2012/03/mozilla-firefox-needs-h264-support-to-survive-shift-to-mobile.ars?utm_source=rss&utm_medium=rss&utm_campaign=rss)

---

### Post by vasa1 on 2012-03-20
It seems they aren't too happy about the decision but felt forced to do so because of "market" forces and Google not its bit.

---

### Post by chipbuster on 2012-03-20
I don't like it at all, but there's really not much else to be done. Google seems to have abandoned WebM for market share on Chrome (have you seen how many HTML5 videos have WebM versions? Answer is basically none).

---

### Post by rg4w on 2012-03-20
Too bad they have to spend their money on those licensing fees, but I can understand the decision.

How much will they be paying?

---

### Post by kaldor on 2012-03-20
Shame that WebM never took off. I guess this was inevitable anyway. 

I didn't do much reading into it, so could someone nutshell what this will mean for the licensing of Firefox?

---

### Post by gradinaruvasile on 2012-03-20
> **kaldor said:**
> Shame that WebM never took off. I guess this was inevitable anyway. 

I didn't do much reading into it, so could someone nutshell what this will mean for the licensing of Firefox?

Probably it wont change as the support wont be built into the browser, it will be supported through external codecs.

---

### Post by screaminj3sus on 2012-03-20
Webm just didn't take off. Google simply bluffed, saying they'd remove it from chrome, and never did, leaving firefox in the cold. h.264 support is pretty inevitable or they will just be left behind.

Seems simple enough to me to just use the system decoders for this. Win7 and OSX can do h.264 fine out of the box, and they could use gstreamer on linux if the appropriate gstreamer plugin is detected.

---

### Post by kaldor on 2012-03-20
Ah, if this is the case then that's pretty good. Weird that it didn't happen sooner.

---

### Post by Lucradia on 2012-03-20
> **screaminj3sus said:**
> Webm just didn't take off. Google simply bluffed, saying they'd remove it from chrome, and never did, leaving firefox in the cold. h.264 support is pretty inevitable or they will just be left behind.

Seems simple enough to me to just use the system decoders for this. Win7 and OSX can do h.264 fine out of the box, and they could use gstreamer on linux if the appropriate gstreamer plugin is detected.

x264? >_> That's not a gstreamer plugin. (Nor does it give linux chrome h264 support.)

---

### Post by Npl on 2012-03-20
common sense to use the available OS codecs, thats what they are there for. Not doing it is rather poor propaganda, especially since WebM was little more than a PR Stunt for google.

---

### Post by Lucradia on 2012-03-20
> **Npl said:**
> common sense to use the available OS codecs, thats what they are there for. Not doing it is rather poor propaganda, especially since WebM was little more than a PR Stunt for google.

By default, Linux doesn't come with h264 support. However, even after installing the necessary h264 codecs, chrome will still not adhere and play h264 content. I'm not sure why this is though.

Also, doesn't h.264 use YUV? If so, I've had nothing but trouble with that.

---

