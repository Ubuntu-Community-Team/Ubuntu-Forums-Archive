---
title: "Why can't html5 video simply be in any video format?"
date: 2010-07-10
forum: The Cafe
---

### Post by Dustin2128 on 2010-07-10
Even though I put my support behind Ogg Theora, I think it's wrong to tie web developers to a single format, even if an open one. For instance, say I've got a video in avi format, why should I have to swap it to ogg to embed it via html? Imagine if, when embedding a photo with html, you could only use a single format. Why should this be any different?

---

### Post by Warpnow on 2010-07-10
Because users won't install a codec to watch a web video. They'll probably just close the box and go to a site that uses the one they have.

---

### Post by Paqman on 2010-07-10
> **Warpnow said:**
> Because users won't install a codec to watch a web video. They'll probably just close the box and go to a site that uses the one they have.

They currently have to install Flash to use that the first time, and they're highly likely to already have the codecs anyway.

---

### Post by neoargon on 2010-07-10
Avi or mp4 are containers . Not codecs .

---

### Post by Warpnow on 2010-07-10
> **Paqman said:**
> They currently have to install Flash to use that the first time, and they're highly likely to already have the codecs anyway.

Flash. One program. There are dozens of different codecs out there. I don't think the average user has them all installed. Go check thepiratebay comments on any video and you'll see dozens of people without the codec complaining about the file being "broken".

---

### Post by Paqman on 2010-07-10
> **Warpnow said:**
> Flash. One program. There are dozens of different codecs out there. I don't think the average user has them all installed. Go check thepiratebay comments on any video and you'll see dozens of people without the codec complaining about the file being "broken".

True, but I don't think it's any more of a usability issue than it is for non-embedded video. Even if the standard specified a particular codec, people would still have to install it.

Picking one codec and sticking with it would give the browser vendors the option of bundling the codec with the browser though, which I imagine is why Mozilla were pushing for Theora, and why Google open sourced VP8.

---

### Post by Bachstelze on 2010-07-10
*sigh*

HTML5 videos *can* be in any format, and Ogg is not even the "standard" one anymore.

[http://en.wikipedia.org/wiki/HTML5_video#Supported_video_formats](http://en.wikipedia.org/wiki/HTML5_video#Supported_video_formats)

---

### Post by Penguin Guy on 2010-07-10
> **dustin2128 said:**
> why can't html5 video simply be in any video format?
> **bachstelze said:**
> html5 videos *can* be in any format.
Lol.

---

### Post by Paqman on 2010-07-10
> **Bachstelze said:**
> *sigh*

HTML5 videos *can* be in any format, and Ogg is not even the "standard" one anymore.

[http://en.wikipedia.org/wiki/HTML5_video#Supported_video_formats](http://en.wikipedia.org/wiki/HTML5_video#Supported_video_formats)

Indeed, but there has been plenty of discussion/argument/waffle about specifying a codec in the standard. HTML5 isn't even official yet, so various people were hoping to slip their pet codec into it.

---

### Post by Lucradia on 2010-07-10
> **Paqman said:**
> They currently have to install Flash to use that the first time, and they're highly likely to already have the codecs anyway.

Windows Vista and higher comes with flash I believe. (There even has been an update to flash in Microsoft update at least once, as well as JAVA.)

---

### Post by zekopeko on 2010-07-10
> **Bachstelze said:**
> *sigh*

HTML5 videos *can* be in any format, and Ogg is not even the "standard" one anymore.

[http://en.wikipedia.org/wiki/HTML5_video#Supported_video_formats](http://en.wikipedia.org/wiki/HTML5_video#Supported_video_formats)

The problem is that you still have to have a codec installed.
They should implement something similar to Silverlight's solution. Silverlight allows sites to provide the codec to the Silverlight runtime. That way the user doesn't have to install anything and can still play the video. That would be the best solution IMO.

---

### Post by Lucradia on 2010-07-10
> **zekopeko said:**
> The problem is that you still have to have a codec installed.
They should implement something similar to Silverlight's solution. Silverlight allows sites to provide the codec to the Silverlight runtime. That way the user doesn't have to install anything and can still play the video. That would be the best solution IMO.

You also have to have an MP3 codec to play flash audio, eh heh heh.

---

### Post by alexan on 2010-07-10
> **Dustin2128 said:**
> Even though I put my support behind Ogg Theora, I think it's wrong to tie web developers to a single format, even if an open one. For instance, say I've got a video in avi format, why should I have to swap it to ogg to embed it via html? Imagine if, when embedding a photo with html, you could only use a single format. Why should this be any different?

HTML5 is meant to bring "multimedia web" on everykind of device, and not all devices can (or have enough horsepower) to manage codecs.
Some kind of cheap devices (think about smartphones) have limited number of codec which can support, they are mainly optimized through hardware.
If you have a single, standard, codec.. these device can be optimized (hardware and software) for such codec (maybe a little gpu or something like that).
So these cheap smartphone can allow you watch video on youtube-like website without the horsepower (cpu) needed if the codec was mainly software.


This is just an example. We need a codec video standard for web.. and this need to be free/open to any idea.

---

### Post by kmsalex on 2010-07-10
> **Lucradia said:**
> Windows Vista and higher comes with flash I believe.
what world are you living in? 
Adobe would never allow that by default, unless Microsoft paid them or something. 
I got my laptop back in November and it came with vista, TUNS OF CRAPWARE, but no flash.

---

### Post by Lucradia on 2010-07-10
> **kmsalex said:**
> what world are you living in? 
Adobe would never allow that by default, unless Microsoft paid them or something. 
I got my laptop back in November and it came with vista, TUNS OF CRAPWARE, but no flash.

I guess my ASUS is special then.

---

### Post by Steve603z on 2010-07-10
> **kmsalex said:**
> what world are you living in? 
Adobe would never allow that by default, unless Microsoft paid them or something. 
I got my laptop back in November and it came with vista, TUNS OF CRAPWARE, but no flash.

I've usually push out Adobe Crash errr, I mean Flash out to desktops using Group Policy.  However, for Windows Desktops that arn't on a Windows Server domain (cringe) I've slipstreamed Adobe Crash into Windows install CD's before.

---

### Post by Paqman on 2010-07-11
> **alexan said:**
> HTML5 is meant to bring "multimedia web" on everykind of device, and not all devices can (or have enough horsepower) to manage codecs.

That actually makes a lot of sense. I hadn't really thought about it from the mobile angle.

---

### Post by YeOK on 2010-07-11
> **Dustin2128 said:**
> Even though I put my support behind Ogg Theora, I think it's wrong to tie web developers to a single format, even if an open one. For instance, say I've got a video in avi format, why should I have to swap it to ogg to embed it via html? Imagine if, when embedding a photo with html, you could only use a single format. Why should this be any different?

Opera on linux uses Gstreamer, so it will actually play any video file format you have codecs installed for. The issue is, codecs and the cost of having them codecs distributed with the browsers. 

One of the good things Google have done is to create WebM, its already available in Opera, Firefox 4 and chrome.

---

### Post by cprofitt on 2010-07-11
> **Lucradia said:**
> I guess my ASUS is special then.

Was it factory installed or did you install it from the Windows DVD?

---

### Post by Dustin2128 on 2010-07-11
so basically the 'format war' is over which codec will be standard and included in all browsers? Then the net news sites blew it COMPLETELY out of proportion.

---

### Post by Merk42 on 2010-07-11
> **Dustin2128 said:**
> so basically the 'format war' is over which codec will be standard and included in all browsers? Then the net news sites blew it COMPLETELY out of proportion.

I guess because it was leaning towards the technically superior, and already widely adapted, but closed source h.264 versus the technically inferior but open (maybe) ogg.

Then Google opened up the VP8 codec as WebM, which fueled the war all over again.


But hey, most net news sites seem to think that HTML5 is ONLY video and will be the death knell for Flash, so I take all that news with a grain of salt

---

### Post by Potters Son on 2010-07-12
One recurring bad memory from my Windows days is when I could watch an AVI video just fine on one PC, but when I tried to watch it on another, Windows Media Player would refuse to play it and send me to some generic troubleshooting website. Is that what you want to do to your users?

If you have any kind of video format you want, users will have to go codec hunting just to watch a video. It's easy for users to go and download Flash because it's well-known, free (with a lower-case 'f'), and supports everything. Codecs, on the other hand, are not well-understood by users. People don't know, for example, that AVI is just a container format which requires different codecs depending on how it was encoded.

Worse, if you open up html5 video to any codec you want, companies will push their own, proprietary codecs and make people go and download them. These downloads will be bundled with bloatware and/or malware, and, of greater consequence to those on this forum, they won't support less-popular OS's like Linux.

> **zekopeko said:**
> The problem is that you still have to have a codec installed.
They should implement something similar to Silverlight's solution. Silverlight allows sites to provide the codec to the Silverlight runtime. That way the user doesn't have to install anything and can still play the video. That would be the best solution IMO.

I agree that that's quite elegant, but that sort of solution requires that all users are on a similar platform, and the only way to accomplish that is through a plugin. I thought we were trying to do away with plugins. Besides, Moonlight doesn't support > .NET v.1 (and I don't think chances are good that it ever will).

---

