---
title: "Fluendo is selling legal codecs!"
date: 2007-01-16
forum: The Cafe
---

### Post by ago on 2007-01-16
[http://arstechnica.com/news.ars/post/20070115-8624.html](http://arstechnica.com/news.ars/post/20070115-8624.html)

IMO this is good news for Linux. It will now be easy to transform free distros (as beer and freedom)  into "practical" ones, for the users that so wish. Which also means that there is less incentive to start with a non-free distro to begin with...

DVD support is still absent but it will be added soon. Installation seems also slightly complex but that is also expected to change. It will also be interesting to see how the fluendo business model will perform. I personally think it is a great idea.

---

### Post by PuleX on 2007-01-16
I took a quick look. They [offer a plugin pack]("https://shop.fluendo.com/product_info.php?products_id=42&osCsid=dvvqv9knnegn2a48hmu6b498i2") for $28, which sounds reasonable: 

> This package contains all of Fluendo's GStreamer plugins which are:

Windows Media Audio Decoder
Windows Media Video Decoder
Windows Media ASF Demuxer
Windows Media MMS Networking

MPEG2 Video Decoder
MPEG4 Video Decoder
MPEG2 Program Stream and Transport Stream demuxer
MPEG4 ISO Demuxer
MP3 Audio Decoder
AC3 Audio Decoder

I'd like to support them (so they can further develop Elisa...?), but they need to provide a good argument for me to buy these. Are they better, faster, more stable then the "free" alternatives we now use? Has anyone been able to review them? And where are the installation notes for the different distros. 

I'll wait for a bit...

---

### Post by mushroom on 2007-01-16
Meh, FFMpeg supplies (mostly if libdvdcss is included) legal, free, Free alternatives. No real point.

---

### Post by saulgoode on 2007-01-16
> This package contains all of Fluendo's GStreamer plugins which are:

Windows Media Audio Decoder
Windows Media Video Decoder
Windows Media ASF Demuxer
Windows Media MMS Networking

MPEG2 Video Decoder
MPEG4 Video Decoder
MPEG2 Program Stream and Transport Stream demuxer
MPEG4 ISO Demuxer
MP3 Audio Decoder
AC3 Audio Decoder

To my knowledge, other than for MP3 there are no patent restrictions or licensing fees associated with *decoding* of the MPEG formats. Neither does *encoding* in MPEG format inherently require any licensing fees -- programs *which use patented technologies* to encode would require proper licensing but, other than MP3 audio, MPEG encoders can be written without resorting to patented methods and MPEG only demand royalties based on the distribution of MPEG encoded content (at least, this is the business model that they encourage their members to employ).

Microsoft does not seem to address the issue of licensing any patents for their Windows Media components. They do provide for licensing of their software (C source code) for implementing but this would fall under the category of 'copyrights' for their software; i.e., it does not address the issue of an indepently-written decoder. The Microsoft business model seems focused on exacting royalties for encoding software and content-streaming services which use their technology. Note that I am not saying that Windows Media content has no applicable patents, just that I have not found mention of them. 

I am not an expert on this but I have spent some time researching these things over the years. Based on the above analysis, Fluendo seems to mainly be offering a properly licensed MP3 decoder and protection against the eventuality that Microsoft would start enforcing some as yet unspecified patent claim. If the quoted list is complete, I would say I should expect more for my money.

Personally, I am not opposed to proprietary software being made available for Linux. I am, however, very opposed to closed, patent-encumbered formats for data files which are intended for archival and publication purposes. My objection here has nothing to do with Linux or open source software; closed file formats are just as undesirable to me whether they are supported on Linux or not.

---

### Post by satbunny on 2007-01-16
I think it is a great idea. It is also too expensive. Ten euros or dollars seems about right.
I would buy then to support them and hopefully a model for helping newbies setup legal Linux installs would be good.
I also support the idea of using open source rather than closed source formats but Microsoft and Apple have won that for the mp3 and mp4 generations.

---

### Post by shining on 2007-01-16
It's already said in the article:

> 
Additionally, Fluendo's codec release is bound to stir up controversy and generate criticism within certain segments of the open-source community. A small but vocal minority of Linux users vehemently oppose the commercial sale of proprietary codecs for the Linux platform since such codecs limit user freedom and impede open redistribution. Critics are likely to perceive the sale of codecs as validation of proprietary software business models and a tacit rejection of open-source ideals.


Now I believe ogg is a suitable, if not better, alternative for audio streaming, but for video, I'm not sure. 
How good is theora for video streamings compared to the other codecs?

---

### Post by kuja on 2007-01-16
> **shining said:**
> It's already said in the article:



Now I believe ogg is a suitable, if not better, alternative for audio streaming, but for video, I'm not sure. 
How good is theora for video streamings compared to the other codecs?

I've not tried it myself, but I hear Theora isn't as high quality as other things like xvid, divx, or h264(or whatever that one is).

---

### Post by JackSlammer on 2007-01-16
Some links for proper information:

[http://www.mp3licensing.com/](http://www.mp3licensing.com/)
[http://www.mpegla.com/index1.cfm](http://www.mpegla.com/index1.cfm)
[http://www.m4if.org/patents/](http://www.m4if.org/patents/)

Basicly it's not about software patents and mpeg codecs are not closed formats. You might have to buy the specs but they are not closed. Only usage and distribution is restricted.

---

### Post by ago on 2007-01-16
Whether the current set of codecs provided are available without legal restrictions or not is not that important and I guess it depends on the country. The novel (1L) idea is that it is now possible to separate the distro from the royalties and allow for different combinations of free/non-free, while always starting from a free platform and paying for extra-non-free capabilities on top of it. So the trade-off (at least in terms of price) is transparent, and freedom is the default. In the past, if you wanted legal access to multimedia capabilities your only shot was a commercial distro. Far too often I have read "if you want a multimedia-capable distro go with XYZ=commercial". No reason to go that route anymore. That is one tick less for distros like Linspire or Xandros and one tick more for community distros like Ubuntu or Debian.

---

### Post by Johnsie on 2007-01-16
With regard to open source video streaming.... That's something Linux isn't very good for at the moment.  At least in my opinion anyway. With Windows it's really easy to do with Windows Media Encoder. With WME you can point and click your way to starting  a good stream in minutes. I was running a webcam and was able to use it so people could watch the cam with audio from a webpage with an embeded media player box(wmp on windows, mplayer on linux). For live audio streaming I used winamp and shoutcast together which was really easy and worked gread. WME would've worked for that too. With Linux I have to use a long howto to do audio streaming with home pretty tacky looking software that isn't very user friendly and I still haven't worked out how to do video. Linux needs better streaming tools with good GUI.

---

### Post by Shay Stephens on 2007-01-16
Does this include DVD playback?  I can't tell, and that usually means no, but I just want to make sure.

---

### Post by PuleX on 2007-01-17
It doesn't include DVD playback, as far as I can tell. 

After reading the comments on the LWN article, I now understand the reason for selling these codecs: 
> I see a lot of people confused about why we are releasing these codecs when there are things like the open source ffmpeg codecs etc.
Our goal is not to provide the community with codecs which there is absolutly no support for already as
that would be foolish. Our goal is to provide a 100% legal option which I know a lot of companies who have or
want to deploy linux desktops have been looking for. These companies like open source, but they also have policies in place
which hinders them from deploying solutions which have clear patent issues hanging over them in their country of operations. This is unfortunatly
the case with most multimedia codecs and even though we have spent a lot on resources on Xiph codecs here at Fluendo and are now working with BBC
on Dirac there is still some way to go before the need for non-free codecs are gone.

So for those in a situation where they can freely use gst-ffmpeg and similar options, more power to you! For those who the lack of licensed codecs
has been a hinderance or problem for adopting Linux (or Solaris) desktops at your company or institution or even private use, then we hope our plugins will be a good solution.

Christian Schaller
Fluendo
Source: [http://lwn.net/Articles/217721/](http://lwn.net/Articles/217721/)

---

### Post by saultpastor on 2007-01-17
Is it not enough to buy the media, but we have to pay to decode it??  Have we lost our minds?
Maybe someday (when we become mindless enough) we can let them scramble the images and charge us for the glasses to see it, yeah I can't wait till that day.

Boy I sure am glad that FOSS is learning how to become proprietary like the other OS's.:o 

Sorry, Y'no if we just refused to buy the crap for 1 day, this would end.

This is pretty strong and opinionated, I know. I have no desire to debate or get in a fight, or be antagonistic.:)

---

### Post by banjobacon on 2007-01-17
> **saultpastor said:**
> Is it not enough to buy the media, but we have to pay to decode it??  Have we lost our minds?

Don't you have to buy a CD player in order to play CDs? Don't you have to buy a tape player in order to play tapes? A record player in order to play records?

Not that I'm saying we should pay for these codecs, but paying for them isn't as crazy an idea as you make it seem. If you purchased Windows, the price of the MP3 license is included in the box price. If you but a DVD player, the cost of the relevant patent license is attached to that, too.

---

### Post by ago on 2007-01-17
> **saultpastor said:**
> Is it not enough to buy the media, but we have to pay to decode it??  Have we lost our minds?

You have always been paying for decoding, but before the price was hidden within other items. This way the cost is transparent and people will see why free codecs are the way to go.

> Boy I sure am glad that FOSS is learning how to become proprietary like the other OS's.:o

In fact I am convinced that this new development will help free community distros (by giving people the option to add extra functionality) and it will help dissuade from using closed codecs (by transparently showing the costs incurred, while providing free alternatives as in beer and as in freedom).

---

### Post by jbus on 2007-01-18
This may be a good temporary solution for businesses, but in the long run it is just feeding the problem.

Money and effort would be better spent by Linux users lobbying Congress to pass fair internet laws. Laws that would tax companies that choose to distribute their content in proprietary formats without offering an open alternative. Offer your content in open codecs/standards and you pay no taxes. Offer your content in both proprietary and open codecs/standards and you pay no taxes. Offer your content in proprietary codecs/standards exclusively and you pay taxes on a sliding scale based on the amount of content you are distributing. This would be a sure way to cure the problem and would encourage open standards on the web while not preventing those that want to use proprietary formats from using them altogether.

---

### Post by tikal26 on 2007-01-19
anyone tried installing this on ubuntu 64. I would like to try them, but I would like to know if anyone tried them

---

