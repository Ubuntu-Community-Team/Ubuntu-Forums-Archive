---
title: "HTML5 a blessing for Linux?"
date: 2009-07-15
forum: The Cafe
---

### Post by Pasdar on 2009-07-15
With the coming of HTML5, there won't be any need for any of the proprietary plugins (e.g. Flash, Java, silverlight, etc)... Its the best thing that could happen for the internet experience of Linux really...  :guitar:

---

### Post by zekopeko on 2009-07-15
> **Pasdar said:**
> With the coming of HTML5, there won't be any need for any of the proprietary plugins (e.g. Flash, Java, silverlight, etc)... Its the best thing that could happen for the internet experience of Linux really...  :guitar:

you probably missed the part where you still need stuff like h.264 (patented technology). w3c dropped the ball. the whole thing is almost FUBAR.

---

### Post by keiichidono on 2009-07-15
Yeah, Runescape can switch from Java to O3D, and Youtube can switch from flash to Ogg Theora! Yeah! /sarcasm It doesn't matter if big sites don't switch, and Google has already said they won't. I'm waiting on thevideobay to be finished but that might take years. Flash/Java/Silverlight aren't going anywhere.

---

### Post by lovinglinux on 2009-07-15
htmlt5 video performance is worse than flash for me, which already sucks really bad.

See discussion at [http://ubuntuforums.org/showthread.php?t=1200496](http://ubuntuforums.org/showthread.php?t=1200496)

---

### Post by Pasdar on 2009-07-15
> **lovinglinux said:**
> htmlt5 video performance is worse than flash for me, which already sucks really bad.

See discussion at [http://ubuntuforums.org/showthread.php?t=1200496](http://ubuntuforums.org/showthread.php?t=1200496)
I've watched those videos before and it was great for me.. in fact i didn't know it was html5... cool :)

---

### Post by Vadi on 2009-07-15
Wrong. Apple (who many people for some reason here love) screwed over HTML5 video and it has been dropped.

Long story short: need to decide if to use Ogg Theora of H.264 for video.

Opera: Ogg!
Mozilla: Ogg!
Google: We'll use either
Apple: Ogg over my dead corpse!

---

### Post by lovinglinux on 2009-07-15
> **Pasdar said:**
> I've watched those videos before and it was great for me.. in fact i didn't know it was html5... cool :)

The original video page has changed. The link is this [http://www.mozilla.com/en-US/firefox/video/](http://www.mozilla.com/en-US/firefox/video/)

---

### Post by CharmyBee on 2009-07-15
I think it's a funny double-standard that these new web standards are practically anti-standards. Going by the w3c, this seems standard.

---

### Post by azangru on 2009-07-15
> **Vadi said:**
> Apple: Ogg over my dead corpse!

And why did everybody care all of a sudden?

---

### Post by Grant A. on 2009-07-15
> **Vadi said:**
> Wrong. Apple (who many people for some reason here love) screwed over HTML5 video and it has been dropped.

Long story short: need to decide if to use Ogg Theora of H.264 for video.

Opera: Ogg!
Mozilla: Ogg!
Google: We'll use either
Apple: Ogg over my dead corpse!

Everyone has their price, and apparently, the guys at the w3c are pretty cheap.

---

### Post by Pasdar on 2009-07-15
> **lovinglinux said:**
> The original video page has changed. The link is this [http://www.mozilla.com/en-US/firefox/video/](http://www.mozilla.com/en-US/firefox/video/)

Yeah I watched that when it was released, and I checked it again now. It works better than youtube for me... so light and without issues... i like it a lot... i just didnt know it was html5 before.

---

### Post by cb951303 on 2009-07-15
does html video works with a streaming server? if not why is it considered as an alternative to flash or java?

---

### Post by lovinglinux on 2009-07-15
> **Pasdar said:**
> Yeah I watched that when it was released, and I checked it again now. It works better than youtube for me... so light and without issues... i like it a lot... i just didnt know it was html5 before.

Yep, it's working better than YouTube for me too. Surprisingly good.

I don't know if some recent Ubuntu updates did the trick or if this is the result of compiling Firefox with PGO. When I compiled just using processor optimization it improved a lot, but now it's better than flash. Great news.

The html5 video is using 10-20% less CPU than flash.

---

### Post by Pasdar on 2009-07-15
> **cb951303 said:**
> does html video works with a streaming server? if not why is it considered as an alternative to flash or java?

Yeah, live streaming tv channels and such.. thats what you mean right? I read something about Akamai wanting to use it to stream channels to Ipod with html5 with use VBR audio too.

---

### Post by geoken on 2009-07-15
> **Vadi said:**
> Wrong. Apple (who many people for some reason here love) screwed over HTML5 video and it has been dropped.

Long story short: need to decide if to use Ogg Theora of H.264 for video.

Opera: Ogg!
Mozilla: Ogg!
Google: We'll use either
Apple: Ogg over my dead corpse!

It was more like 

Google: We'll support ogg in the browser but we wont actually use it. They famously said that if they converted YouTube to ogg and maintained the same quality level it would consume all the worlds bandwidth. I don't necessarily agree with that claim, but it does serve as a strong indication of Google's position on ogg.


Apple: Use the OS's native media framework to play back video. As far as I know the h.264 decoder their using is part of the systems media playback framework and not the browser's rendering engine.

---

### Post by lovinglinux on 2009-07-15
I'm experiencing something weird. Watch [this video](http://www.mozilla.com/en-US/firefox/video/?video=fastest-sport-stacker) till the end and don't stop it or close the tab. Leave it there and check after a few seconds if your CPU usage starts to increase, a lot, until you close the tab.

Additionally, watch the same video from [http://www.mozilla.com/en-US/firefox/fastest/](http://www.mozilla.com/en-US/firefox/fastest/)

The page above includes a javascript overlay player. I guess that is the culprit of high CPU usage, not the video itself. Do you also experience huge differences in CPU usage between both videos?


Note: Comments about the video content [here](http://ubuntuforums.org/showthread.php?t=1214387).

---

### Post by DeadSuperHero on 2009-07-15
I'd really like for OGG to be officially adopted for HTML5. Maybe if the entire FOSS community gets behind it, keeps support for it in Webkit, KHTML, and Gecko, etc. It'd at least have a fighting chance of being supported by default on the Free Software desktop.

Alternatively, I don't see why anyone hasn't offered to write a framework similar to Flash, but with only OGG codecs.  Animated SVG, embeddable in web pages, etc. It wouldn't get into HTML code, but at least it'd be a GPL'ed alternative framework for media. I'd learn programming just to pursue this.

---

### Post by keiichidono on 2009-07-15
> **Mr. Psychopath said:**
> I'd really like for OGG to be officially adopted for HTML5. Maybe if the entire FOSS community gets behind it, keeps support for it in Webkit, KHTML, and Gecko, etc. It'd at least have a fighting chance of being supported by default on the Free Software desktop.

Alternatively, I don't see why anyone hasn't offered to write a framework similar to Flash, but with only OGG codecs.  Animated SVG, embeddable in web pages, etc. It wouldn't get into HTML code, but at least it'd be a GPL'ed alternative framework for media. I'd learn programming just to pursue this.

Like flash but open source? I like this idea.

---

### Post by DeadSuperHero on 2009-07-15
> **CalvinB said:**
> Like flash but open source? I like this idea.

Yeah, except it's not Gnash. No reverse-engineered .swf playback, something totally different.

---

### Post by keiichidono on 2009-07-15
> **Mr. Psychopath said:**
> Yeah, except it's not Gnash. No reverse-engineered .swf playback, something totally different.

Flash is very complex, if you can make a toolkit as powerful as flash but fully opensource then you have a very good project. I hope you get a good team of programmers to help you with that.

---

### Post by DeadSuperHero on 2009-07-15
It's really just a pipe dream at this point.

---

### Post by Viva on 2009-07-15
There are a few cheap/free flash creators for windows. I wonder why nobody ever created one for linux.

---

### Post by Pogeymanz on 2009-07-16
I would love to see HTML5 video have a big impact. I would also obviously prefer the ogg codec as well.

---

### Post by Sashin on 2009-07-16
Those videos on the firefox website are .ogg files. Both Firefox and Chrome seem to be able to play them.

But for some reason google seems to think that ogg files would take up the whole internet's bandwidth.

---

### Post by CharmyBee on 2009-07-16
> **Sashin said:**
> But for some reason google seems to think that ogg files would take up the whole internet's bandwidth.

It's mostly embedophobia. Have people really learned from Myspace and (RIP) Geocities?

---

### Post by toupeiro on 2009-07-16
I really .. REALLY hate to say this, but silverlight is the superior format.  Silverlight 3, the way its written, actually does GPU offloading, whereas Flash and company do not.  Too bad its Microsoft, which basically means something else good will be killed by bureaucracy and poor ethics.

---

### Post by vinutux on 2009-07-16
okey ,,, but some sites like **Dailymotion** start a pre-beta site for ogg
[B][COLOR="DarkGreen"]
[http://openvideo.dailymotion.com/](http://openvideo.dailymotion.com/)[/COLOR][/B]



.

---

### Post by mihai.ile on 2009-07-16
in my opinion the only thing html5 video is still missing is full screen (of course the browser is more responsible about this). And about ogg format, is it so inferior to flash in terms of bandwidth? I think that if it begins to be widely used it will improve a lot as it will get into the attention of many more developers...

---

### Post by GeneralZod on 2009-07-16
> **mihai007 said:**
> And about ogg format, is it so inferior to flash in terms of bandwidth? I think that if it begins to be widely used it will improve a lot as it will get into the attention of many more developers...

Wikipedia has a fairly nice summary of how it fairs against other codecs:

[http://en.wikipedia.org/wiki/Theora#Performance](http://en.wikipedia.org/wiki/Theora#Performance)

---

### Post by Vadi on 2009-07-16
Theres a firefox plugin that makes videos go fullscreen.

---

### Post by lovinglinux on 2009-07-16
> **Vadi said:**
> Theres a firefox plugin that makes videos go fullscreen.

[url=https://addons.mozilla.org/en-US/firefox/addon/12576]Full Screen Video 0.6
[/url]

---

### Post by Sublime Porte on 2009-07-16
> Wrong. Apple (who many people for some reason here love) screwed over HTML5 video and it has been dropped.

Long story short: need to decide if to use Ogg Theora of H.264 for video.

Opera: Ogg!
Mozilla: Ogg!
Google: We'll use either
Apple: Ogg over my dead corpse!

Since most Mac users use Firefox and not Safari, I really don't see why Apple has much of a say in it...

As Firefox becomes the more dominant browser, what Apple or Microsoft wanna do regarding web standards is going to become less relevant.

---

### Post by Vadi on 2009-07-16
Apparently the bickering they raised was relevant enough for W3C to give up on it.

*clap clap*

---

### Post by TBOL3 on 2009-07-16
> **lovinglinux said:**
> [url=https://addons.mozilla.org/en-US/firefox/addon/12576]Full Screen Video 0.6
[/url]

lol, so much for not having to install a plugin to watch videos in the web browser. :lolflag:

---

### Post by ghindo on 2009-07-16
> **Vadi said:**
> Apple: Ogg over my dead corpse!Well, sort of.  From what I can tell, Apple isn't exactly pleased with the situation, either; without specific codecs for audio and video, the browser market is really divided and it doesn't do **anybody** any good.  As a result, Apple is apparently rethinking their stance on Theora, but needs to do [some research first]("http://lists.xiph.org/pipermail/theora/2009-July/002415.html").  If Apple finds Theora suitable to their needs, then I would imagine Theora's case for inclusion into the HTML5 spec would be much stronger.> **Grant A. said:**
> Everyone has their price, and apparently, the guys at the w3c are pretty cheap.That's exactly the kind of FUD that will continue to hold us back.

---

### Post by Npl on 2009-07-16
So, whats the reason to dogmatically choose Theora and keep H264 out?

H264 is technically alot better than Theora, many encoders are available and delivering great quality.
Hardware support is everywhere, from Desktops down to Handhelds and mobilephones, Theora is just running in software on "Desktop OSes"

Now this all shoud be given up because Theora *claims* it miraculously avoided every patent on earth? It can just as easily be targeted by submarine-patents.

---

### Post by zekopeko on 2009-07-16
> **Vadi said:**
> Wrong. Apple (who many people for some reason here love) screwed over HTML5 video and it has been dropped.

Long story short: need to decide if to use Ogg Theora of H.264 for video.

Opera: Ogg!
Mozilla: Ogg!
Google: We'll use either
Apple: Ogg over my dead corpse!

Apple: No hardware decoder for ogg. sorry! FTFY

---

### Post by lovinglinux on 2009-07-16
> **TBOL3 said:**
> lol, so much for not having to install a plugin to watch videos in the web browser. :lolflag:

Full Screen Video 0.6 it's not a plugin, it's an extension. They are completely different things. Plugins are required to display content from web sites that otherwise wouldn't be displayed at all, while extensions are designed to enhance user experience, customize the interface, provide additional features and mash-ups. You don't need any extensions if you don't want to, but you can't simply disable flash without compromising your browsing experience. Besides, flash is proprietary, while the majority of extensions are open source.

I doubt most users would be able to write a flash plugin, but anyone can write a simple extension to display the video in fullscreen.

---

### Post by ghindo on 2009-07-16
> **Npl said:**
> So, whats the reason to dogmatically choose Theora and keep H264 out?

H264 is technically alot better than Theora, many encoders are available and delivering great quality.
Hardware support is everywhere, from Desktops down to Handhelds and mobilephones, Theora is just running in software on "Desktop OSes"

Now this all shoud be given up because Theora *claims* it miraculously avoided every patent on earth? It can just as easily be targeted by submarine-patents.It's not really an issue of ideology here, it's more an issue of practicality.  With H.264, browser vendors would have to pay a fee to MPEG to (legally) ship support in the browser.  For FOSS browsers like Firefox, that is completely impractical.  Not only that, but I think the W3C doesn't allow proprietary codecs in their recommendations.

I don't know why you would suspect that Theora is so susceptible to "submarine patents."  The whole point of the Xiph.org foundation is to provide free codecs.  The Xiph people are *very* patent-aware.  They have their own legal counsel.  If you hang out in #theora for any length of time, you regularly see links to the US patent office.  I see the promise of Theora being encumbered with submarine patents as a red herring until proven otherwise.

---

### Post by benj1 on 2009-07-16
> **Npl said:**
> 
Now this all shoud be given up because Theora *claims* it miraculously avoided every patent on earth? It can just as easily be targeted by submarine-patents.

thats true of any standard, or any piece of software for that matter, theres more chance of ubuntu infringing a patent (especially as microsoft has already stated that the linux kernel infringes their patents ;-) )

anyway if theres to be a standard, wouldn't you rather it be open source?

i really hope this gets sorted, its really silly that most of the web is built on open standards, except for things like sound and video.
i don't buy the arguments about ogg being inferior, yes at the moment it might be marginally worse but once everyone starts using and improving it, it will improve much faster than any closed source format could (thats the beauty of open source i suppose).

---

### Post by Npl on 2009-07-16
> **ghindo said:**
> It's not really an issue of ideology here, it's more an issue of practicality.  With H.264, browser vendors would have to pay a fee to MPEG to (legally) ship support in the browser.  For FOSS browsers like Firefox, that is completely impractical.  Not only that, but I think the W3C doesn't allow proprietary codecs in their recommendations.well if the license doesnt allow selling a license-enabled browser then I wouldnt call it free.
And even if there would be no reason against Theora in the standards, why is there a reason against H264. The license is already paid for if you buy a phone which enables H264 playback, it could aswell be paid as part of the GFX-Card or an option for browsers.
Sure I would prefer 1 standard, but Id also prefer if this would not be Theora. I dont see why I should settle for something worse.

> **ghindo said:**
> I don't know why you would suspect that Theora is so susceptible to "submarine patents."Not any more or less than H264 would be.> **ghindo said:**
> The whole point of the Xiph.org foundation is to provide free codecs.  The Xiph people are *very* patent-aware.  They have their own legal counsel.  If you hang out in #theora for any length of time, you regularly see links to the US patent office.  I see the promise of Theora being encumbered with submarine patents as a red herring until proven otherwise.I call anyone that claims his code is 100% patentfree a liar. Patents get granted for the most obvious and stupid crap, I dont think its possible to write a couple hundreds lines of code without violating some of them.
Well, and "until proven" - you know why they are "submarine patents", right? Its because the owner stays quiet for a long time and sues only if the "violations" are widespread. Whats the point in suing Theora now?

---

### Post by Npl on 2009-07-16
> **benj1 said:**
> thats true of any standard, or any piece of software for that matter, theres more chance of ubuntu infringing a patent (especially as microsoft has already stated that the linux kernel infringes their patents ;-) )

anyway if theres to be a standard, wouldn't you rather it be open source?There are opensource-decoders for H264.
Sure I would prefer a cost- and patentfree codec, but not if it comes with several penalties like lesser quality and no existing hardware-support. Some of these problems *might* be fixed in time, but on the other hand H264 is already tried and proven in every branch of CE.
> **benj1 said:**
> i really hope this gets sorted, its really silly that most of the web is built on open standards, except for things like sound and video.
i don't buy the arguments about ogg being inferior, yes at the moment it might be marginally worse but once everyone starts using and improving it, it will improve much faster than any closed source format could (thats the beauty of open source i suppose).Thats your opinion. If opensource means faster progress then why are codecs behind **now**?
And if it has to stay patentfree then that means it cant use some smart algorithms that companies spent alot time developing (some patents are word their name)

---

### Post by Vadi on 2009-07-16
Heh, wow. Without facts or knowledge, people will even go about doubting the open-ness of a certified free and open codec.

Amazing trolling going on.

---

### Post by Jimleko211 on 2009-07-16
> **Vadi said:**
> Heh, wow. Without facts or knowledge, people will even go about doubting the open-ness of a certified free and open codec.

Amazing trolling going on.
It's not trolling, he's offering an argument for the other side.  I laud him for doing so.  I haven't researched the codecs enough to have an opinion, but if he wants H.246, what's the problem with him saying that?

---

### Post by benj1 on 2009-07-16
> **Npl said:**
> well if the license doesnt allow selling a license-enabled browser then I wouldnt call it free.

why does it not allow you to sell a browser? as far as im aware its basically distributed under a bsd license see [here]("http://www.theora.org/faq/#14").
you can sell open source software you know. i could sell ubuntu if i wanted to, they don't even have to give away the source, as its a bsd license.

---

### Post by Npl on 2009-07-16
> **Vadi said:**
> Amazing trolling going on.try not to fall on your face while patting your own back

---

### Post by Npl on 2009-07-16
> **benj1 said:**
> why does it not allow you to sell a browser? as far as im aware its basically distributed under a bsd license see [here]("http://www.theora.org/faq/#14").
you can sell open source software you know. i could sell ubuntu if i wanted to, they don't even have to give away the source, as its a bsd license.Exactly my point... I dont know which license Firefox is under, but I doubt it would stop them from selling h264-licenses.

IMHO, the best would be to look at how GStreamer handles such license-issues... heck, even better just use GStreamer and notify the user to get a h264-component if the browser encounters such a file and the codec is missing

---

### Post by benj1 on 2009-07-16
> **Npl said:**
> 
Thats your opinion. If opensource means faster progress then why are codecs behind **now**?

open source projects have an amazing ability to step up to the plate when needed, look at rythmbox v banshee at the moment.
if ogg was announced as a definite html standard tomorrow, you would have a lot of people looking at the code and would be able to contribute changes.

my understanding was at the moment, although ogg isn't the best, it isn't the worst either.

heres an [interesting comparison]("http://people.xiph.org/~greg/video/ytcompare/comparison.html") (its from the xiph foundation but seems to be fairly balanced (or at least includes methodology))

---

### Post by Closed_Port on 2009-07-16
> **Npl said:**
> Exactly my point... I dont know which license Firefox is under, 

I don't want to come off as rude, but wouldn't spending 30 seconds on some research be a good idea before engaging in a discussion?
> Core Mozilla project source code is licensed under a disjunctive tri-license giving you the choice of one of the three following sets of free software/open source licensing terms:

    * Mozilla Public License, version 1.1 or later
    * GNU General Public License, version 2.0 or later
    * GNU Lesser General Public License, version 2.1 or later

[http://www.mozilla.org/MPL/](http://www.mozilla.org/MPL/)

> **Npl said:**
> 
but I doubt it would stop them from selling h264-licenses.

Selling a license is not the issue but incorporating the code in firefox. It is my understanding that this wouldn't be possible with the GPL but would be possible with the LGPL and the MPL.

> **Npl said:**
> 
IMHO, the best would be to look at how GStreamer handles such license-issues... heck, even better just use GStreamer and notify the user to get a h264-component if the browser encounters such a file and the codec is missing
I think that will eventually be the way that it is handled. However, this somehow defeats the purpose of the video-element which was meant to free browsers from plugins and external requirements.

It also would pose the same legal problems we (as in users of ubuntu) face now. You can get h.264 playback pretty easily, but the legality of it is in question.

---

### Post by Closed_Port on 2009-07-16
> **Npl said:**
> 
And if it has to stay patentfree then that means it cant use some smart algorithms that companies spent alot time developing (some patents are word their name)
Hey, you answered your own question. ;-D

---

### Post by ghindo on 2009-07-16
> **Npl said:**
> well if the license doesnt allow selling a license-enabled browser then I wouldnt call it free.I'm not sure I understand your argument.  When you say "the license," are you referring to the Theora license?  Because Theora is under a permissive BSD license, which allows commercial use.> **Npl said:**
> I call anyone that claims his code is 100% patentfree a liar. Patents get granted for the most obvious and stupid crap, I dont think its possible to write a couple hundreds lines of code without violating some of them.
Well, and "until proven" - you know why they are "submarine patents", right? Its because the owner stays quiet for a long time and sues only if the "violations" are widespread. Whats the point in suing Theora now?I realize why they're called "submarine patents," but I still think that it's a very poor argument against Theora.  The whole submarine patent argument is based on a lot of "What ifs."  What if somebody holds a patent which Theora is infringing upon?  Well, we don't really know if that's the case and won't really know until that person steps forward.  What if that patent holder decides to sue?  Well, sue who?  Xiph.org?  Mozilla?  Opera?

I just think that the "submarine patents" argument is kind of a silly one because it's one without any real support; the entire argument is built upon hypothetical situations and to me, that's not a very strong argument.

---

### Post by Closed_Port on 2009-07-16
> **ghindo said:**
> 
I just think that the "submarine patents" argument is kind of a silly one because it's one without any real support; the entire argument is built upon hypothetical situations and to me, that's not a very strong argument.
I fully agree.

And as an aside, h.264 isn't secure from submarine patents either.

---

### Post by ghindo on 2009-07-16
> **Npl said:**
> Sure I would prefer 1 standard, but Id also prefer if this would not be Theora. I dont see why I should settle for something worse.Worse how?  At the bitrates we would see streaming video, there's almost no discernible difference between H.264 and Theora, using the 1.1 encoder.  The Theora encoder has seen incredible improvements over the last year or so, and we will continue to see improvements for a while to come.

Also, it's important to bear in mind that Theora is *clearly* superior to H.264 is in terms of licensing, and that is a very important factor when considering the HTML5 spec.

---

### Post by Firestem4 on 2009-07-16
I'm not sure if this was mentioned but dailymotion is converting their entire website to ogg-based video's. You can access them at [www.openvideo.dailymotion.com](www.openvideo.dailymotion.com)

Dailymotion is pretty damn popular too so don't think that HTML5 Ogg<video> support doesn't have any traction.

---

### Post by geoken on 2009-07-16
> **Npl said:**
> 

IMHO, the best would be to look at how GStreamer handles such license-issues... heck, even better just use GStreamer and notify the user to get a h264-component if the browser encounters such a file and the codec is missing

In other words, completely replicate the existing situation which led to Flash becoming the defacto standard.

We already have that. Every major browser on every major platform has the ability to play back video by embedding one of the platform's native media players in the browser. It's the codec runaround which this situation produced that led people towards using the ubiquitous flash plugin for video playback.

---

### Post by Npl on 2009-07-16
> **Closed_Port said:**
> I don't want to come off as rude, but wouldn't spending 30 seconds on some research be a good idea before engaging in a discussion?reading through the whole license would take more than that. It was more a hypothetical question tough as I dint/dont believe selling a h264-enabled Firefox could be an issue.> **Closed_Port said:**
> Selling a license is not the issue but incorporating the code in firefox. It is my understanding that this wouldn't be possible with the GPL but would be possible with the LGPL and the MPL.AFAIK incorporating the code from eg. x264 wouldnt be an issue, providing binaries without paying for licenses would. Thats atleast how I understood it from the LAME project handled it. You see, this issue takes more than 30 seconds to research :D
> **Closed_Port said:**
> I think that will eventually be the way that it is handled. However, this somehow defeats the purpose of the video-element which was meant to free browsers from plugins and external requirements.clear format-specs are a huge step up from how its handled now, be it open or closed.> **Closed_Port said:**
> Hey, you answered your own question. ;-DWhy H264 is better than Ogg? Seriously, I dont know what you are refering to.
> **ghindo said:**
> I'm not sure I understand your argument.  When you say "the license," are you referring to the Theora license?  Because Theora is under a permissive BSD license, which allows commercial use.Was worded badly. I meant it should be possible to sell an (eventually optional) version of FF with h264-license.
> **Closed_Port said:**
> I just think that the "submarine patents" argument is kind of a silly one because it's one without any real support; the entire argument is built upon hypothetical situations and to me, that's not a very strong argument.Nope, but neither is the patent-freeness. Do you care about already paid license-fees if you buy an Phone? I dont and thus the only argument left would be submarine patents.
AFAIK neither Opera or Mozilla even negotiated about license-fees but flatout said "NAY".
Id have no prob paying for licenses directly or indirectly (for example through a GFX-Card). (You are already paying Theora and Firefox developers through advertising and thus price-markups even if you never touch a computer so dont tell me it must be gratis)
> **ghindo said:**
> Worse how?  At the bitrates we would see streaming video, there's almost no discernible difference between H.264 and Theora, using the 1.1 encoder.  The Theora encoder has seen incredible improvements over the last year or so, and we will continue to see improvements for a while to come.I havent seen indepth comparisons for a while, but as said... H264 is already proven and optimised from poststamp size to hi-def, was designed to be parallelizable and efficiently implementable in hardware. On top of that I already have a phone, a PSP and a gfx-card that natively support it.> **ghindo said:**
> Also, it's important to bear in mind that Theora is *clearly* superior to H.264 is in terms of licensing, and that is a very important factor when considering the HTML5 spec.Which seems to be a bigger issue on this forum than everywhere else in the world :smile: (There are tons of people already using their (licensed) h264-enabled hardware without even thinking about how a licensefree codec would brighten up their life)
I understand the issues, but I`d rate the proven versatility and hardwaresupport way higher than that.

---

### Post by Closed_Port on 2009-07-16
> **Npl said:**
> reading through the whole license would take more than that. It was more a hypothetical question tough as I dint/dont believe selling a h264-enabled Firefox could be an issue.

I was referring to you not knowing the licenses firefox uses.

> **Npl said:**
> 
AFAIK incorporating the code from eg. x264 wouldnt be an issue, providing binaries without paying for licenses would.

It would be an issue, as firefox is (also) under the GPL. AFAIK including h.264 would break the GPL

> **Npl said:**
> 
Thats atleast how I understood it from the LAME project handled it. You see, this issue takes more than 30 seconds to research :D

But the problem is that mozilla provides binaries and has to provide binaries and if it's not mozilla itself providing binaries, it would be for example Ubuntu. 

> **Npl said:**
> 
clear format-specs are a huge step up from how its handled now, be it open or closed.

I'll have to disagree here. Having a spec that many players in the market can't implement is useless at best. But that's exactly the situation we would find ourselves in if h.264 became part of the standard.

> **Npl said:**
> 
Why H264 is better than Ogg? Seriously, I dont know what you are refering to.

Oh, it was meant as a joke, but just to clear up the issue: In your first sentence you were bemoaning that Theora was behind h.264 when it comes to quality and asking how this could have happened. And in your second sentence you give a good reason that at least partially explains why it is the case: Having to code around patents.

> **Npl said:**
> 
Nope, but neither is the patent-freeness.

But then how are submarine patents an argument against Theora if h.264 suffers from the same problem?

> **Npl said:**
> 
Do you care about already paid license-fees if you buy an Phone? I dont and thus the only argument left would be submarine patents.

Sorry, but I can't follow you here. How are submarine patents the only argument left? How are they even an argument if both are not immune from them?

> **Npl said:**
> 
AFAIK neither Opera or Mozilla even negotiated about license-fees but flatout said "NAY".

Well, there is a further issue with h.264 that hasn't come up. The licensing terms will change in 2011 and it's at least possible that MPEG LA will charge royalties even for free streaming. 
[http://www.streaminglearningcenter.com/articles/46/1/H264-Royalties-what-you-need-to-know/Page1.html](http://www.streaminglearningcenter.com/articles/46/1/H264-Royalties-what-you-need-to-know/Page1.html)

---

### Post by ghindo on 2009-07-16
I wanted to clarify some points, so I popped into #theora and asked a question.  The answer I received makes me think we have been perhaps misunderstanding this issue entirely:> [12:48] <ghindo> This is probably a silly question, but H.264 can never make it into the HTML5 recommendation, right?  I seem to recall the W3C having a policy against proprietary codecs
[12:50] <xiphmont_> basically correct, yes.
[12:50] == sirlemonhead [n=bduncan2@86-45-8-64-dynamic.b-ras2.prp.dublin.eircom.net] has left #theora []
[12:51] <gmaxwell> ghindo: There have been some people outside of the whatwg discussions who have mistakenly misunderstood the issue as being H.264 vs Theora. Thats never been the case.
[12:51] <xiphmont_> derf: do you consider it a better idea to drop the frame that busted the budget, or to drop the next frame after?
[12:51] <ghindo> gmaxwell: How would you frame the issue?
[12:51] <gmaxwell> ghindo: The question has always ever been Baseline (which would be theora) or no baseline. In both cases vendors would be free to ship whatever they wanted.
[12:53] <gmaxwell> I don't think anyone has imagined that apple would stop shipping their own preferred formats. But it sure would be good for the internet if they'd also ship some freely available formats too.

---

### Post by Methuselah on 2009-07-16
Wow, ghindo thanks.
I never understood how proprietary codecs could even be considered as part of a web standard.
It would result in a situation where anyone could not implement a standard conforming browser.

---

### Post by Judo on 2009-07-16
At one point, xiphmont had stated that Theora was never meant to be long-term.  It was a temporary solution.  I can't remember the exact quote, but I'm pretty sure he also acknowledged that its compression is significantly lower than that of today's popular standards.  It wouldn't exactly be an improvement over Flash in the eyes of businesses, in most cases.

On the other hand, should Theora become part of the web standard, it will finally get people to work on a better free standard.  Perhaps OMS?

I'd love for it to become more common.  I've had enough with Flash.  I wouldn't have much of a problem with it if swfdec or Gnash were completely usable, but neither project is good enough for me.  So far, I haven't had any issues with Firefox's playback of <video> tags.  I already like it. :)

---

### Post by ghindo on 2009-07-17
> **Judo said:**
> At one point, xiphmont had stated that Theora was never meant to be long-term.  It was a temporary solution.  I can't remember the exact quote, but I'm pretty sure he also acknowledged that its compression is significantly lower than that of today's popular standards.  It wouldn't exactly be an improvement over Flash in the eyes of businesses, in most cases.I suppose Dirac will probably offer a more long-term solution, once it matures further.

---

### Post by Judo on 2009-07-17
> **ghindo said:**
> I suppose Dirac will probably offer a more long-term solution, once it matures further.

Unlikely.  I think Dark_Shikari, x264's developer, explains it all pretty well: [http://forum.doom9.org/showthread.php?p=1290935](http://forum.doom9.org/showthread.php?p=1290935).

It seems like none of the royalty-free video formats are any good (Theora, Dirac, MPEG-1), but they certainly are well-supported by the FOSS community.  For anyone interested in compression, it's a nightmare.  For regular users, though, it means no more crashes or memory leaks.

There's a good comparison of open-source encoders at [http://saintdevelopment.com/media/](http://saintdevelopment.com/media/) for anyone interested.

---

