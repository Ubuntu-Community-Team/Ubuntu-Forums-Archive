---
title: "Is HTML5 Open ?"
date: 2010-10-15
forum: The Cafe
---

### Post by inobe on 2010-10-15
how does this affect all the other proprietary players, is HTML5 another proprietary player ?


youtube has a beta html5 video player, how will this work for them or anyone, what is it's purpose ?

---

### Post by Ctrl-Alt-F1 on 2010-10-15
HTML5 is just an HTML specification which allows video.  Video is not the only upgrade to HTML5.  The codecs that are used to decode the video are what make it work.  Currently there are several different video formats including open source and closed source.  As far as I'm aware there isn't a unanimous decision on what codec should be used, so the answer to your question is:

HTML5 video is both open/proprietary.

---

### Post by inobe on 2010-10-15
what i see is that the web content is being taken over, some content requires silverlight as other require flash, it's depressing when companies use the web at their advantage, for example to view silverlight content it needs to be done on windows.

or flash for example and it's security flaws.

---

### Post by samalex on 2010-10-15
As Ctrl-Alt-F1 mentioned, HTML5 is just the latest version of the HTML standards maintained by W3C, and it adds some neat functionality that wasn't easily done with just HTML.  What's neat is it could replace Flash and Silverlight, but with such a market behind both I doubt HTML5 will ever surpass either, contrary to what Steve Jobs keeps saying.

As for open vs closed source in regards to Video, the way I understand it to be the new [Video tag]("http://www.w3.org/TR/html5/video.html") has a codec parameter that allows the website author to use mostly any codec he prefers, but it has to be available on the client side for the video to work.  Most open source fanatics would love to see an open source codec becoming the standard, but I could see Apple and Microsoft using proprietary codec that would only work on their respective platforms.

I don't know if there is a 'standard' or 'default' video codec yet for HTML5 , but lots of companies are pushing [VP8]("http://openvideoalliance.org/2010/05/google-frees-vp8-codec-for-html5-the-webm-project/?l=en") which is an open source codec that's supposed to be amazing.  But of course Apple and Microsoft haven't said whether they'll support it or not.  I think even without their help VP8 could become a defacto standard, but it would suck having to install the codec on every new Mac or Win box.  

I'm curious to see when HTML5 will finally be fully ratified and pushed into mainstream. It'll be a fine day when that happens.

Sam

---

### Post by Canis familiaris on 2010-10-15
HTML 5 along with ECMAScript, CSS 3 is an Open Standard, and it can be used an implemented anywhere as desired to make great web applications.

However images, audio, and video don't have any specification binded by HTML 5 standards (AFAIK), and so basically it depends on the format or the codec being used. Image format like PNG/SVG are Open and virtually supported everywhere, GIF or JPEG were/are covered by patents (any clarification on this?) but are widely used, etc. In <audio> tag basically the Vorbis format is expected to be the standard as it is good on performace, size, and most of all free of patents.

Video is slightly tricky affair, W3C was initially expected to make Theora the standard codec for <video> however that wasn't to be, and we came to a free market in video codecs with two major players: Theora, and H.264 which was supported by Apple and Microsoft. H.264 being covered by patents was tricky to implement in spite of enhanced compression and performance.
Later Google released VP8 in open source license paving a way for a third codec for <video> tag to be used, and bundled VP8 video codec with Xiph.org's Vorbis codec for audio in a Matroska container in a package called WebM. WebM has now support from Google, Opera, and Mozilla, however not from Apple, while I am not sure of Microsoft's stance in this.

In a nutshell HTML5 is free, no doubt, but in implementation in videos, and plugins, the entire web cannot be guaranteed to be a total Open Experience.

---

### Post by samalex on 2010-10-15
> **Canis familiaris said:**
> 
Later Google released VP8 in open source license paving a way for a third codec for <video> tag to be used, and bundled VP8 video codec with Xiph.org's Vorbis codec for audio in a Matroska container in a package called WebM. WebM has now support from Google, Opera, and Mozilla, however not from Apple, while I am not sure of Microsoft's stance in this.

My vote is that VP8 win, which given AndroidOS based phones now outnumber IPhones and Firefox has closed the gap behind IE on all platforms, it'll be hard for Apple and/or Microsoft to not support it if the industry as a hole outside of their walls does.

---

### Post by endotherm on 2010-10-15
> **samalex said:**
> My vote is that VP8 win, which given AndroidOS based phones now outnumber IPhones and Firefox has closed the gap behind IE on all platforms, it'll be hard for Apple and/or Microsoft to not support it if the industry as a hole outside of their walls does.
depends on how the patent war works out. Apple et al (all the MPEGLA licensees) are collecting a patent porfolio to go after open codecs, and the analysises of VP8 that i have seen indicate that it borrows patented ideas from x264. 
this will likely get ugly, as the courts always seem to favor for-profit business over almost any other consideration.

---

### Post by samalex on 2010-10-15
> **endotherm said:**
> depends on how the patent war works out. Apple et al (all the MPEGLA licensees) are collecting a patent porfolio to go after open codecs, and the analysises of VP8 that i have seen indicate that it borrows patented ideas from x264. 
this will likely get ugly, as the courts always seem to favor for-profit business over almost any other consideration.

Ahh, I hadn't heard that.  

***I truly loath software patents ....***

---

### Post by inobe on 2010-10-15
is this a crucial time ?

---

### Post by endotherm on 2010-10-16
> **inobe said:**
> is this a crucial time ?
in terms of software patents? yes. there are some big cases just wrapped (bilsky and autodesk vs some dude) and some others on the horizon that will realy define the legal landsccape for patents and license enforcement. 

in terms of html, yes and no. much of the focus on htm 5 deals with competition between a small number of gargantuan corporations (MS + adobe vs apple, etc), so in many ways this is a manufactured dialog that we are having. I'm not sure we will see the substance behind the debate beneath the talking points our favorite companies and bloggers are feeding us. for instance html5 is not a panacea for all our flash ills, but certian sectors of the industry want us to believe it is.

personaly I really hope vp8 takes off and finds itself in an reasonably invulnerable legal position. Steve Jobs assertion that there can never be an open unencumbered video codec really bothers me. [http://hugoroy.eu/jobs-os.en.html](http://hugoroy.eu/jobs-os.en.html)

---

### Post by matthew.ball on 2010-10-16
> **inobe said:**
> what i see is that the web content is being taken over, some content requires silverlight as other require flash, it's depressing when companies use the web at their advantage, for example to view silverlight content it needs to be done on windows.
I haven't used it, don't know how well it works (if it works at all), but I noticed [this]("http://www.microsoft.com/getsilverlight/get-started/install/default.aspx") the other day. Might make some people happy.

---

### Post by inobe on 2010-10-16
> **matthew.ball said:**
> I haven't used it, don't know how well it works (if it works at all), but I noticed [this]("http://www.microsoft.com/getsilverlight/get-started/install/default.aspx") the other day. Might make some people happy.

unfortunately its just a hack from flash with a mixture of microsoft DRM.

but no thanks, you can enjoy the silverlight content till your hearts content :P

---

### Post by matthew.ball on 2010-10-16
I don't even know what silverlight is.

You said "... to view silverlight content it needs to be done on windows." and I just showed that this is not the case.

I'm not going to need it - I don't even use flash.

---

### Post by SeijiSensei on 2010-10-16
> **endotherm said:**
> personaly I really hope vp8 takes off and finds itself in an reasonably invulnerable legal position. Steve Jobs assertion that there can never be an open unencumbered video codec really bothers me. [http://hugoroy.eu/jobs-os.en.html](http://hugoroy.eu/jobs-os.en.html)

What precisely bothers you about it?  That Jobs said it, or that he may be right?  There's a very good chance that VP8 will be embroiled in some type of patent litigation probably coming from MPEG-LA.  VP8 is a refinement of the Ogg video standard.  No one bothered to sue *them*, but with Google a major player behind VP8 the stakes are now much higher.

> **matthew.ball said:**
> You said "... to view silverlight content it needs to be done on windows." and I just showed that this is not the case.

Silverlight includes various DRM hooks to protect the content it contains.  Open-source alternatives like Moonlight will never have these closed, proprietary extensions since exposing the algorithms would mean the content could then be copied and redistributed.

---

### Post by endotherm on 2010-10-18
> **SeijiSensei said:**
> What precisely bothers you about it?  That Jobs said it, or that he may be right?  There's a very good chance that VP8 will be embroiled in some type of patent litigation probably coming from MPEG-LA.  VP8 is a refinement of the Ogg video standard.  No one bothered to sue *them*, but with Google a major player behind VP8 the stakes are now much higher.


you hit on my meaning with that latter. My problem with software patents is that they are so abstract that they eliminate any alternate means to obtain an end goal mentioned or implied by a claim. with a hardware patent, you can obtain the ends by altering the means, but with software patents, since they don't extend to the implementation (copyright does that), the ends are what is restricted. I don't really care about who said it, if they have the influence to give it a go. 

the intelectual property protections were supposed to be there to promote innovation and ensure that valuable ideas were not lost, but were available to the society at large. how far we have strayed from the course...

---

### Post by alexan on 2010-10-18
> Is HTML5 Open ?


So long web browser will be unable to run compiled html5 source code... 

yes, html5 will be always open: it's distribution is _forced_ through source codes, you know :popcorn:

---

### Post by MasterNetra on 2010-10-18
html5's video may replace using flash to host video content but flash won't be completely replaced as it is still useful for interactive content. So no video tag is not a flash killer. But I do look forward to be able to use HTML5 for coding by default someday... Hopefully when IE9 is released and replaces IE8...and side note, screw IE6...evil creature not worth the effort anymore.

---

### Post by Merk42 on 2010-10-18
> **MasterNetra said:**
> html5's video may replace using flash to host video content but flash won't be completely replaced as it is still useful for interactive content. So no video tag is not a flash killer.Thank you so much for knowing HTML5 beyond a buzzword (see sig)


HTML5 is like Linux, at the core it's open, but it can run proprietary things.

---

