---
title: "What's the angle here?"
date: 2010-01-25
forum: The Cafe
---

### Post by BuffaloX on 2010-01-25
I just read a couple of articles on YouTube choosing h.264 over OGG Theora for their HTML 5 experiment.

This is one of them:
[http://www.techcrunch.com/2009/07/06/html-5-ogg-theora-vs-h264-in-the-battle-for-a-web-video-standard/]("http://www.techcrunch.com/2009/07/06/html-5-ogg-theora-vs-h264-in-the-battle-for-a-web-video-standard/")

The experiment uses the embedded video tag in HTML5 so videos can be watched without the need to install extensions like FLASH or Silver-light, provided your browser support H.264.

But the problem is that H.264 is patented, and requires a license.
Some argue that H.264 is superior to OGG Theora, but this test shows the opposite.

From what I can find OGG Theora is less CPU intensive, making it better for smart-phones/books and netbooks, and more powerfull computers eat a little less battery/power.
OGG Theora offer better image quality on low bitrates, making it better for mobile devices with limited bandwidth. On higher bitrates the difference is indiscernible.
OGG Theora is completely free, H.264 is patented and owned by MPEG-LA.

[http://people.xiph.org/~greg/video/ytcompare/comparison.html]("http://people.xiph.org/~greg/video/ytcompare/comparison.html")

Apple is against OGG Theora becomming standard for HTML5.
The Google/YouTube move is a strong push for H.264 and against OGG Theora.
Microsoft has licensed H.264 for Win7, so they probably support it too.

It seems only Mozilla is left supporting OGG Theora, guaranteeing that everybody can use video on any site, without some patent owner controlling it and requiring (steep) license fees.

So why is Google pushing H.264?
One paranoid theory is that it would make it harder for others to compete with YouTube.

Why pay for something when we can have a better alternative for free?
Can we influence W3C so they choose OGG Theora?

---

### Post by user1397 on 2010-01-25
The way I think of this issue is I compare it to the Citizens United v. FEC supreme court ruling in the US which just passed recently.  All of the progress in law-making that was done over the past several decades concerning the subject was completely lost at a whim.

Progress that was made over the last few years concerning open formats/protocols seems like is going to be lost at a whim (at least concerning online video formats), due to the power of the few wealthy parties who can do as they please.

Then again, as long as they provide ogg theora as an alternative format for the video tag, then at least it won't be so bad.

---

### Post by LowSky on 2010-01-25
H.264 might be better at supporting DRM or encoding, it might be why google has pick H.264 over OGG. Youtube wants to make money and using a standard that movie and TV companies like might help their bottom line.

---

### Post by JDShu on 2010-01-25
Well, the paranoid theory is that it forces Firefox users to move to Chrome. They're leaving the possibility of support Theora open though.

---

### Post by Xbehave on 2010-01-25
**point 0:**Open web standards out-weigh any technical advantage h.254 may or may not have.

h.264 is what apple will back because the iPhone has a hw decoder, and google may support it for similar reasons, but at the end of the day see point 0 as it trumps everything. If websites go with theora, there are hw decoders for theora and software implemetations are less CPU intensive so an option on most devices.

> **LowSky said:**
> H.264 might be better at supporting DRM or encoding, it might be why google has pick H.264 over OGG. Youtube wants to make money and using a standard that movie and TV companies like might help their bottom line.
flash videos are already h.264 encoded, youtube switched to h.264 because it was easy

---

### Post by BuffaloX on 2010-01-25
> **JDShu said:**
> Well, the paranoid theory is that it forces Firefox users to move to Chrome. They're leaving the possibility of support Theora open though.

I agree this could unfortunately be a huge problem for Firefox.

AFAIK Chrome already supports OGG Theora, and for You Tube they have explicitly said no way we can convert billions of movies.
So I'm not quite sure what you mean.

Seems there is something called X.264 which is compatible with H.264, but I'm not sure if it's legal...

Apple says Firefox users can just install QuickTime?

---

### Post by Nephersir7 on 2010-01-25
> **BuffaloX said:**
> I just read a couple of articles on YouTube choosing h.264 over OGG Theora for their HTML 5 experiment.

So why is Google pushing H.264?

Google is not really "pushing H.264", nor did they "choose" H.264 over Theora.

In my opinion, I think that the fact that Google only enabled H.264 HTML5 video on youtube has more to do with the fact that all their videos were already encoded in that format (at at least 3 different resolutions. Therefore, it was relatively easy to just turn on the switch for beta HTML5 embedding. Back in 2007, prior to the iPhone's launch, all Youtube videos were in FLV. It then took MONTHS to convert all of these videos to h.264 MP4s. Youtube had way less videos than it has now. And it had no 720p or 1080p HD videos yet.

Transcoding all those videos to Ogg Theora (with multiple copies for SD, HQ and HD) would require a major computing effort (convert 320p, 480p, 720p and 1080p MP4s) and storage space increase : that'd double the whole website's data storage, which is already one of the biggest of the world. 

I think we can all agree that, sadly, it just isn&#8217;t worth it at this point. HTML5's video tag specification is far from being finalized and Theora's popularity is just not there yet. 

Also, Apple should be blamed for being the only browser vendor refusing to feature Theora support for its tag support. That, IMHO is the biggest obstacle in the road to ogg theora adoption.

To conclude, i think it's hard to blame Youtube for not (yet?) supporting Theora, and that even if it's through a proprietary codec, turning on HTML5 video support is still a positive thing: a proprietary video codec without flash is better than a proprietary codec through Flash.

edit: one more thing:
> **BuffaloX said:**
> I agree this could unfortunately be a huge problem for Firefox.

Much worse. It's a problem for the free and open Web.

> **BuffaloX said:**
> Seems there is something called X.264 which is compatible with H.264, but I'm not sure if it's legal...
X.264 is an encoder, not a decoder(player).

---

### Post by BuffaloX on 2010-01-25
> **Xbehave said:**
> **point 0:**Open web standards out-weigh any technical advantage h.254 may or may not have.

h.264 is what apple will back because the iPhone has a hw decoder, and google may support it for similar reasons, but at the end of the day see point 0 as it trumps everything. If websites go with theora, there are hw decoders for theora and software implemetations are less CPU intensive so an option on most devices.


flash videos are already h.264 encoded, youtube switched to h.264 because it was easy

Yes we want open standards. :D

HW decoder could have been made even easier for OGG Theora, why did they choose not to?
In theory H.264 should be superior, but actual results does not seem to support that. :P
Yes FLASH supports it, but part of the point of HTML5 was to get away from proprietary standards such as FLASH, wasn't it?

Just checked Wiki it says Patent is valid till 2028.:!:

---

### Post by Nephersir7 on 2010-01-26
> **BuffaloX said:**
> Yes we want open standards. :D
HW decoder could have been made even easier for OGG Theora, why did they choose not to?


Even if there were hardware-accelerated OGG theora decoding, Youtube will always need to have H.264 support: it's here to stay, notably for legacy suport. That doesn't exclude upcoming Theora support, but at best, it'll support both.

---

### Post by BuffaloX on 2010-01-26
> **Nephersir7 said:**
> Google is not really "pushing H.264", nor did they "choose" H.264 over Theora.

In my opinion, I think that the fact that Google only enabled H.264 HTML5 video on youtube has more to do with the fact that all their videos were already encoded in that format (at at least 3 different resolutions. Therefore, it was relatively easy to just turn on the switch for beta HTML5 embedding. Back in 2007, prior to the iPhone's launch, all Youtube videos were in FLV. It then took MONTHS to convert all of these videos to h.264 MP4s. Youtube had way less videos than it has now. And it had no 720p or 1080p HD videos yet.

Transcoding all those videos to Ogg Theora (with multiple copies for SD, HQ and HD) would require a major computing effort (convert 320p, 480p, 720p and 1080p MP4s) and storage space increase : that'd double the whole website's data storage, which is already one of the biggest of the world. 

I think we can all agree that, sadly, it just isn&#8217;t worth it at this point. HTML5's video tag specification is far from being finalized and Theora's popularity is just not there yet. 

Also, Apple should be blamed for being the only browser vendor refusing to feature Theora support for its tag support. That, IMHO is the biggest obstacle in the road to ogg theora adoption.

To conclude, i think it's hard to blame Youtube for not (yet?) supporting Theora, and that even if it's through a proprietary codec, turning on HTML5 video support is still a positive thing: a proprietary video codec without flash is better than a proprietary codec through Flash.

edit: one more thing:

Much worse. It's a problem for the free and open Web.


X.264 is an encoder, not a decoder(player).

Oh yes they are pushing it, by making it available as HTML5 before a standard has been determined.

When YouTube chose to encode everything with H.264, they chose it, didn't they. :P
Usually encoders have more legal trouble than decoders, H.264 may be different. But we need both encoder and decoder to have a working ecosystem on the internet IMO. There are lots of players that can play back H.264, both VLC and mplayer can do it.
Anyways free options are available, but are they legal particularly for USA?

---

### Post by Nephersir7 on 2010-01-26
> **BuffaloX said:**
> Oh yes they are pushing it, by making it available as HTML5 before a standard has been determined. 

YouTube chose to encode everything with H.264, they chose it, didn't they. :P

Spending MASSIVE resources in something with an uncertain future is just plain stupid, especially whenyou aren't really profitable yet. 

Back in 2007, HTML5 was non-existent. Therefore, video could only be played through Flash players, which don't support free codecs such as Theora.

---

### Post by BuffaloX on 2010-01-26
> **Nephersir7 said:**
> Back in 2007, HTML5 was non-existent. Therefore, video could only be played through Flash players, which don't support free codecs such as Theora.

No it wasn't, but still H.264 cost money and OGG Theora doesn't.
So maybe FLASH was the only way, ohh now I get it...
Flash was supported by Microsoft...

[http://www.appleinsider.com/articles/09/07/06/ogg_theora_h_264_and_the_html_5_browser_squabble.html]("http://www.appleinsider.com/articles/09/07/06/ogg_theora_h_264_and_the_html_5_browser_squabble.html")

---

### Post by user1397 on 2010-01-26
what I want to know is IS flash going to eventually die out (for videos, games are another story)?

even if proprietary codecs are the norm for the html5 video tag, flash would no longer be needed...

---

### Post by samjh on 2010-01-26
> **ubuntuman001 said:**
> what I want to know is IS flash going to eventually die out (for videos, games are another story)?

even if proprietary codecs are the norm for the html5 video tag, flash would no longer be needed...

It depends on how much multimedia capability will be included in HTML5.

If HTML5 can do everything Flash does, then Flash will die a natural death, but it will be very slow.  HTML4 was published in 1997, but it took several years for developers to taken advantage of CSS instead of frames and tables, and even longer for Web 2.0 to really influence ordinary web users.  IMHO, it will be at least 2015 for Flash to start to die out, unless competing technologies like MS Silverlight and Sun JavaFX oust it before then.

---

### Post by user1397 on 2010-01-26
> **samjh said:**
> It depends on how much multimedia capability will be included in HTML5.

If HTML5 can do everything Flash does, then Flash will die a natural death, but it will be very slow.  HTML4 was published in 1997, but it took several years for developers to taken advantage of CSS instead of frames and tables, and even longer for Web 2.0 to really influence ordinary web users.  IMHO, it will be at least 2015 for Flash to start to die out, unless competing technologies like MS Silverlight and Sun JavaFX oust it before then.and then Adobe will fall into despair! :D

Although they would still hae the monopoly on raster graphics editing and web design wisywig editing... :(

---

### Post by samjh on 2010-01-26
I don't think Adobe will be despairing when Flash dies. ;)  Instead, they will try to strengthen their market share in media authoring software such as Photoshop, Illustrator, Dream Weaver, FrameMaker, etc.

I think it's food for thought that Microsoft and Sun have both launched "rich internet applications" platforms like Silverlight and JavaFX to compete against Flash, despite the pending adoption of HTML5.  I don't think HTML5 will simply kill off multimedia platforms on the web. :)

---

### Post by squilookle on 2010-01-26
I believe it is Mozilla and Opera that are supporting the free codec. As users, I reckon the only thing we can do is use one of these browsers over Chrome or. Safari. 

When Apple and Google see the market shares of their browsers slump they'll introduce support (google in youtube, apple in safari) pretty quickly. 

Of course, Google haven't written off the idea of supporting theora, and it would be very difficult for them, and daft of them, to jump in and start encoding all those videos in a new format.

---

### Post by Merk42 on 2010-01-27
> **squilookle said:**
> When Apple and Google see the market shares of their browsers slump they'll introduce support (google in youtube, apple in safari) pretty quickly. 

(the majority of) Firefox and Opera users won't stop going to youtube, they'll just use a browser that works with h.264

If you want to tell Google to use OGG, [vote for it](http://productideas.appspot.com/#9/e=3d60a&t=ogg).

In the typical open source way there are hundreds of polls that do the same thing, so rather than have 1 with a lot of votes, there are hundreds with less votes...

---

### Post by LightB on 2010-01-27
There might be some argument to make for theora better for browser playback over h264, but it's definitely not a better codec overall. It is less cpu intensive, but that doesn't matter that much when it beats it in quality so much. Besides that, h264 settings can be reduced to ease cpu usage, and I'm guessing well into theora levels while still compressing better quality at the same size.

> **Nephersir7 said:**
> I think that the fact that Google only enabled H.264 HTML5 video on youtube has more to do with the fact that all their videos were already encoded in that format

That's what it looks like. And with google owning youtube and pushing chrome, they will not support something that will compete with some non-existent competitor to youtube. Unless there's a big video site out there that is already matching youtube in functionality with firefox-theora videos.

---

### Post by squilookle on 2010-01-27
E> **Merk42 said:**
> (the majority of) Firefox and Opera users won't stop going to youtube, they'll just use a browser that works with h.264

I know that. I'm just saying that sticking to those browsers would be the best way of getting the message across (in theory). I know it won't happenn in practice.

---

### Post by LightB on 2010-01-27
I had been using chrome for a while and ignoring firefox. I have to say that the more I see it the more it looks bad to force h264 as part of html5. For one thing, the betas on youtube and vimeo don't work right, they just don't, at least not on google chrome; yes, I know they are in beta. But the theora player in current firefox is already working great and has been for a while. It even uses less cpu than the flash player. I know there's a few video sites that have been experimenting with this already, but to be honest, they stink. Why can't there be some real competition to youtube? Vimeo is stuck as a niche forever by following youtube.

Btw, I said theora is not better than h264 and it's true. Let's not lie. It's not the video version of vorbis, which is definitely a superior lossy format with audio.

---

### Post by Gallahhad on 2010-01-28
> **LowSky said:**
> H.264 might be better at supporting DRM or encoding, it might be why google has pick H.264 over OGG. Youtube wants to make money and using a standard that movie and TV companies like might help their bottom line.
This^ is likely.
I have not looked into the issue, but my gut response was similar to this post. DRM is likely at the root of the matter. If I felt compelled that would be something I would consider when putting together a search term, or support inquiry, or any other questions.

---

