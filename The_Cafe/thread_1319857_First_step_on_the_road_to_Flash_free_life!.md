---
title: "First step on the road to Flash free life!"
date: 2009-11-08
forum: The Cafe
---

### Post by hobo14 on 2009-11-08
Here's an HTML5 viewer for youtube: [http://neosmart.net/blog/2009/watch-youtube-videos-in-html5/]("http://neosmart.net/blog/2009/watch-youtube-videos-in-html5/")

And youtube has their own: [here]("http://www.youtube.com/html5")

Bad news is: won't work in FF because of some mp4 streaming licensing problem??  What are they talking about?

---

### Post by Frak on 2009-11-08
Firefox won't play MP4 because of license and patent restrictions. Safari will play it just fine, though.

This is why HTML5 <video> isn't ready for prime time. There's no agreed-upon standard format yet.

---

### Post by SunnyRabbiera on 2009-11-08
yeh for rthe time being it wont woprk in firefox, but therer will be a back hack.
I think its all for dhrome anyway so google can force it on the market

---

### Post by gnomeuser on 2009-11-08
> **hobo14 said:**
> 
Bad news is: won't work in FF because of some mp4 streaming licensing problem??  What are they talking about?

Patented technology which requires a license, as Open Source needs to be redistributable to everyone that would require a patent grant which we are not getting (the patent holders want money for such licenses). Buying such a license would be impossible as license price times infinite is a quite substantial sum.

This is why advocating patent free technologies such as Ogg Theora or Dirac for video is important.

---

### Post by ZankerH on 2009-11-08
youtube-dl, ffmpeg, mplayer

flash-free enough yet?

---

### Post by Tipped OuT on 2009-11-08
How do I get it to work in Windows? What do I need? It never works for me.

EDIT: Nevermind, only works in Google Chrome.

---

### Post by phrostbyte on 2009-11-08
Gnash seems to (sort-of) work for YouTube and important SWF movies like [http://pinochan.net/flash/etc/babby.swf](http://pinochan.net/flash/etc/babby.swf) run flawlessly

---

### Post by hobo14 on 2009-11-08
> **gnomeuser said:**
> Patented technology which requires a license, as Open Source needs to be redistributable to everyone that would require a patent grant which we are not getting (the patent holders want money for such licenses). Buying such a license would be impossible as license price times infinite is a quite substantial sum.

This is why advocating patent free technologies such as Ogg Theora or Dirac for video is important.

So mp4 is patented, and FF can't use it without paying?
How does safari manage it?  Have they coughed up cash?
What are the legal issues for someone writing a codec for mp4 with a FOSS licence of some sort, and FF using that?


> **ZankerH said:**
> youtube-dl, ffmpeg, mplayer

flash-free enough yet?
I meant a replacement, not a work-around.

---

### Post by Frak on 2009-11-08
> **hobo14 said:**
> How does safari manage it?  Have they coughed up cash?

Apple owns the patents, they can do whatever they want with it.

---

### Post by gnomeuser on 2009-11-08
> **hobo14 said:**
> So mp4 is patented, and FF can't use it without paying?


yes

> 
How does safari manage it?  Have they coughed up cash?


Apple buys a bulk license from the patent holder or has a similar deal. This is for any patents they do not own, also they are probably able to enter patent covenants with other holders. Google does the same for Google Chrome btw.

> 
What are the legal issues for someone writing a codec for mp4 with a FOSS licence of some sort, and FF using that?


The technology is patented, any implementation that is compatible will be in violation and thus subject to litigation for patent infringement or be forced to pay a license for what is practically infinite redistributed copies.

> 
I meant a replacement, not a work-around.

We have replacements, namely Dirac and Ogg Theora, both are patent free and freely distributable they are however not compatible and industry adoption is nearly non-existent. What isn't lacking is industry opposition to adoption of such open and patent free formats.

---

### Post by qazwsx on 2009-11-08
I think no one would mind if mp4 container contained theora and vorbis (non standard). Actually you can even wrap patent free MPEG-1 stream in mp4. But patents concerning about AVC and AAC is the real issue. Vorbis is good but theora sucks very very much as quality wise / used bitrate. I mean I was able to get MPEG-2 more transparent (lossless source) than theora using ffmpeg/ffmpeg2theora. Of course at lower bitrates theora is usually better.

Google chrome comes with aac+avc capabilities (ffmpeg). Well, Google has some money...

---

### Post by whoop on 2009-11-08
> **Frak said:**
> Apple owns the patents, they can do whatever they want with it.

Curse those apples!:mad: :lolflag:

---

### Post by Exodist on 2009-11-08
I dont understand what FFMpeg and Apples use MP4 format has to do with any patent issues. If I am not mistaken FFMpeg was around before Apple started using MP4 video. Dont confuse MP4 with Quicktime. They are seperate beast all together.

I could be wrong here. But IDK..

---

### Post by Frak on 2009-11-08
> **Exodist said:**
> I dont understand what FFMpeg and Apples use MP4 format has to do with any patent issues. If I am not mistaken FFMpeg was around before Apple started using MP4 video. Dont confuse MP4 with Quicktime. They are seperate beast all together.

I could be wrong here. But IDK..
1. You have to have permission to use it from the Patent holders
2. FFMpeg is a way to access and manipulate MPEG files
3. Using FFMpeg without permission for commercial or public use is a violation of the patent. Private, non-commercial use is ok.

---

### Post by Chronon on 2009-11-08
> **hobo14 said:**
> So mp4 is patented, and FF can't use it without paying?
How does safari manage it?  Have they coughed up cash?
What are the legal issues for someone writing a codec for mp4 with a FOSS licence of some sort, and FF using that?



I meant a replacement, not a work-around.

MP4 is just a container.  It can contain various data streams that use various codecs.  I believe that h264 is the codec relevant to this discussion.  FF 3.5 works with the video tags if the media is encoded using Ogg Theora, AFAIK. I think Apple is merely one company that licenses the rights to implement a codec.  MPEG LA is the patent holder, I believe.

---

### Post by ceramicm on 2009-11-08
I recently (this week) found a different way to rid myself of Flash. I embed Totem in Firefox in the place of Adobe Flashplayer to view YouTube videos. Here's a short HowTo, in case anyone is interested:

1. Install the [Greasemonkey]("https://addons.mozilla.org/en-US/firefox/addon/748") Firefox addon.

2. Install [this script]("http://userscripts.org/scripts/show/50771") to replace Flashplayer on the YouTube site. (Click the green "Install" button in the upper right of the page.)

3. Install [this script]("http://userscripts.org/scripts/show/60977") to replace Flashplayer on other sites that embed YouTube videos.

4. Restart Firefox.

You can uninstall Flashplayer if you wish (but you may still want it to view non-YouTube content). When you visit YouTube, Totem should appear embedded, the same size and place as the old Flashplayer.

The scripts also give you the option to download the video files or view video in a different quality. One caveat is that Totem-Mozilla does not allow you to seek (fast-forward/rewind/jump) to specific places in Flash content.

Now if I could only get this to work in Epiphany...

---

### Post by Frak on 2009-11-08
> **Chronon said:**
> MP4 is just a container.  It can contain various data streams that use various codecs.  I believe that h264 is the codec relevant to this discussion.  FF 3.5 works with the video tags if the media is encoded using Ogg Theora, AFAIK. I think Apple is merely one company that licenses the rights to implement a codec.  MPEG LA is the patent holder, I believe.
Correct.

---

### Post by MaxIBoy on 2009-11-08
I think (could be wrong) that <video> was dropped from the HTML 5 standard due to all the aforementioned bickering over the file formats. In other words, web browsers which implement it are creating a nonstandard add-on to HTML, which is precisely the biggest problem with Internet Explorer. 

I'm all for standards compliance, but in this case, I think the <video> tag is still the Right Thing to do. And Theora is also the best format to use. 

At the very least, a significant minority of people at youtube are lazy/cheap jerks. They already have the MP4 and FLV streams for each video and they don't feel like converting to another format. So they made up some fake technical reasons not to support Theora.

---

### Post by samj on 2009-11-11
<video> is alive and well, but there is no reference to specific codecs.

Sam

---

### Post by MasterNetra on 2009-11-11
> **Frak said:**
> Apple owns the patents, they can do whatever they want with it.

Actually it seems AT&T owns the patent.

[http://en.wikipedia.org/wiki/MPEG-4#Licensing](http://en.wikipedia.org/wiki/MPEG-4#Licensing)

---

### Post by Frak on 2009-11-12
> **MasterNetra said:**
> Actually it seems AT&T owns the patent.

[http://en.wikipedia.org/wiki/MPEG-4#Licensing](http://en.wikipedia.org/wiki/MPEG-4#Licensing)
They own a patent that is used in the MP4 technology (compression). They don't own many of the patents that make up MP4 itself. Those belong to various companies, but mostly Apple.

---

### Post by etnlIcarus on 2009-11-12
> **qazwsx said:**
> I think no one would mind if mp4 container contained theora and vorbis (non standard). Actually you can even wrap patent free MPEG-1 stream in mp4. But patents concerning about AVC and AAC is the real issue. Vorbis is good but theora sucks very very much as quality wise / used bitrate. I mean I was able to get MPEG-2 more transparent (lossless source) than theora using ffmpeg/ffmpeg2theora. Of course at lower bitrates theora is usually better.

They rather recently did some fine-tuning of theora, due to this very issue. If you were to get the latest bleeding-edge code from xiph's git/svn/whatever repos, you'll find that theora practically has h.264 parity.

---

