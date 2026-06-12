---
title: "What is w32codecs for?"
date: 2007-06-05
forum: The Cafe
---

### Post by aysiu on 2007-06-05
The general consensus is that w32codecs is illegal by any definition.

Okay.

Can I ask what w32codecs is needed for exactly? I'm just curious.

With MPlayer, Flash, and the GStreamer ugly codecs metapackage, I'm able to play pretty much everything I come across--YouTube, Apple Trailers, MP3s, etc.

Is there something I'm not playing that I'd need w32codecs for? Or does MPlayer use w32codecs? I've never heard of MPlayer being illegal--is it illegal? Are the ugly metapackages illegal?

By the way, I live in the United States.

---

### Post by visionaire on 2007-06-05
maybe avi and wma and wmv files?

---

### Post by shijirou on 2007-06-05
They're video codecs, some propietary, some open source,  usually used to play the numerous types of videos for Windows (ie MP4, XVID/DIVX, Real Media, Quicktime, AVI, WMV, etc...)

---

### Post by reacocard on 2007-06-05
> **shijirou said:**
> They're video codecs, some propietary, some open source,  usually used to play the numerous types of videos for Windows (ie MP4, XVID/DIVX, Real Media, Quicktime, AVI, WMV, etc...)

But with the various gstreamer and xine packages installed, all those play back fine. I have yet to encounter a video that can't be played without w32codecs.

---

### Post by shijirou on 2007-06-05
> **reacocard said:**
> But with the various gstreamer and xine packages installed, all those play back fine. I have yet to encounter a video that can't be played without w32codecs.

Yeah, which is why I don't use them either, w32codecs I mean :p

---

### Post by aysiu on 2007-06-05
So what I'm hearing is that you *don't* need w32codecs to play multimedia. That's what I suspected.

---

### Post by FuturePilot on 2007-06-05
You mainly need them for .avi .wmv stuff like that. I've run into a few streaming videos that won't give me the video, only the sound, without the W32codecs



> **aysiu said:**
> The general consensus is that w32codecs is illegal by any definition.
:-\"

---

### Post by saulgoode on 2007-06-05
> **aysiu said:**
> So what I'm hearing is that you *don't* need w32codecs to play multimedia. That's what I suspected.

That is my understanding. The FFMPEG project has produced open source (LGPLed) equivalents for practically everything W32CODECS could handle (see [libavcodec]("http://en.wikipedia.org/wiki/Libavcodec") for specifics).

---

### Post by aysiu on 2007-06-05
[quote=FuturePilot]You mainly need them for .avi .wmv stuff like that. I've run into a few streaming videos that won't give me the video, only the sound, without the W32codecs
[/quote] Can you post a link to a website that doesn't work without *w32codecs* so I can try it and see what happens?

---

### Post by laxmanb on 2007-06-05
They're the Windows DLL files used for playing various codecs. They're used for Windows Media, Real Player, mp3, etc. etc. support with a xine based media player like Totem-xine (Totem with xine backend), Amarok (KDE), etc., etc....

I think they support more formats than gstreamer-ugly....

And they're illegal because they're a direct copy of the Windows codecs. so they violate copyright laws...

**Atleast that's what I think... **

---

### Post by mips on 2007-06-05
> **aysiu said:**
> Can you post a link to a website that doesn't work without *w32codecs* so I can try it and see what happens?

lol, you just asked for one of those very hard to find things :D

---

### Post by Aranel on 2007-06-05
There is the occasional WMV file that doesn't play without the w32codecs. Even so, those files aren't very common - at least, not anymore.

But consider this: what players provide a frontend to GStreamer? There's Totem, and optionally Kaffiene (I think), but that's pretty much it. I myself am dual-booting on a 28GB hard disk, and that doesn't leave me with a whole lot of space to install all the GNOME/KDE dependencies required for those players. So the lack of available GStreamer-based players is a factor for people without a whole lot of disk space.

Still, I generally agree with you. The w32codecs really aren't absolutely necessary anymore.

---

### Post by mips on 2007-06-05
> **laxmanb said:**
> 
And they're illegal because they're a direct copy of the Windows codecs. so they violate copyright laws...

**Atleast that's what I think... **

You think correctly. In Linux they just repackage those very same codecs. Although illegal it was always encouraged on these forums strangely enough.

---

### Post by FuturePilot on 2007-06-05
> **aysiu said:**
> Can you post a link to a website that doesn't work without *w32codecs* so I can try it and see what happens?

Try this one.
[http://media.putfile.com/White-Van-Wit]("http://media.putfile.com/White-Van-Wit")

---

### Post by reacocard on 2007-06-05
> **FuturePilot said:**
> Try this one.
[http://media.putfile.com/White-Van-Wit]("http://media.putfile.com/White-Van-Wit")

Works fine for me in totem-xine.

---

### Post by saulgoode on 2007-06-05
> **laxmanb said:**
> And they're illegal because they're a direct copy of the Windows codecs. so they violate copyright laws...

**Atleast that's what I think... **

If you obtain your DLLs from a copy of Windows which you have purchased (and are otherwise not using) then are you violating copyright if you use it with your Linux box? That's rather like saying you are in violation if you play a Sony MG audio CD on a Marantz stereo. I don't see how it could violate copyrights if you are only using a single copy of the DLL for which you have purchased the licensing.

It **might** be a violation of the Windows licensing agreement (not a copyright violation) but I was unable to find anything within the Windows licensing agreements which restricted you from using DLLs on non-Windows machine - although I admit I may have missed it.

---

### Post by FuturePilot on 2007-06-05
> **reacocard said:**
> Works fine for me in totem-xine.Maybe it was because I was using the MPlayer plugin?

---

### Post by jclmusic on 2007-06-05
> **saulgoode said:**
> If you obtain your DLLs from a copy of Windows which you have purchased (and are otherwise not using) then are you violating copyright if you use it with your Linux box? That's rather like saying you are in violation if you play a Sony MG audio CD on a Marantz stereo. I don't see how it could violate copyrights if you are only using a single copy of the DLL for which you have purchased the licensing.

It **might** be a violation of the Windows licensing agreement (not a copyright violation) but I was unable to find anything within the Windows licensing agreements which restricted you from using DLLs on non-Windows machine - although I admit I may have missed it.

i heard that if u own a legal copy of windows it's fine. although it wouldn't surprise me if microsoft has put something in the vista eula to change this.

---

### Post by hanzomon4 on 2007-06-05
You can't play rmvb files (.rm or .ram video files) and xine screws up some wmv files(regression from the edgy version). You have to give the w32s a higher priority in the xine config files of the various players to get working wmv(wmv 8 I believe). Gst is great but some websites don't stream right, like the non-flash videos on gamespot. I fully expect gst to rule in a sort while.

---

### Post by stimpack on 2007-06-05
Not everyone lives in the US, they are quite legal for me thanks. I'm sure a crippled version for US users may be possible, but hands off the international please.

---

### Post by aysiu on 2007-06-05
> **stimpack said:**
> Not everyone lives in the US, they are quite legal for me thanks. I'm sure a crippled version for US users may be possible, but hands off the international please.
I don't know all the details or Spanish law, but from everything I've read, it appears to be illegal regardless of country (whether you country *enforces* those laws or not is another question).

This isn't like *libdvdcss2*, which has questionable legality in the US but is legal pretty much everywhere else.

Read more here:
[http://ubuntucat.wordpress.com/2007/05/28/the-legality-or-illegality-of-w32codecs-and-libdvdcss2/](http://ubuntucat.wordpress.com/2007/05/28/the-legality-or-illegality-of-w32codecs-and-libdvdcss2/)

---

### Post by SishGupta on 2007-06-05
Without w32codecs about 90% of my wmv collection doesn't play properly. It plays, but I can't seek with the slider or it will become very distorted and crash.

Might be illegal, but I like it that way.

---

### Post by klerfayt on 2007-06-05
> There are a few formats such as **certain Windows formats**, **Real**, and **Apple Quicktime** which do not have native codecs under Linux. To work around this issue, **external binary codecs** are used instead to play these formats. **MPlayer** and **xine** use such external codecs and these codecs are stored in the MPlayer website in their codecs directory located at [http://www.mplayerhq.hu/MPlayer/releases/codecs/](http://www.mplayerhq.hu/MPlayer/releases/codecs/).

Medibuntu distributes a package which contains these codecs. The codecs are under the non-free component of the repository.
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by Andrewie on 2007-06-05
I haven't came across anything that needs w32codecs but most of my stuff is xvid anyway

---

### Post by samjh on 2007-06-05
I've come across some Quicktime files that won't play properly with Gstreamer and Xine.  w32codecs are OK.

For legalities, it depends on the jurisdiction and its treatment of the EULA.

There are many websites that freely distribute Windows DLLs, but have not suffered any legal action from Microsoft.  Just search WIndows DLL in a search engine.  It's strange that Microsoft hasn't shut these sites down.

---

### Post by jiminycricket on 2007-06-05
> **saulgoode said:**
> That is my understanding. The FFMPEG project has produced open source (LGPLed) equivalents for practically everything W32CODECS could handle (see [libavcodec]("http://en.wikipedia.org/wiki/Libavcodec") for specifics).

Yes, you USED to need w32codecs since ffmpeg hadn't reverse engineered all the formats yet, and it used to be that you had to install totem-xine instead of totem-gstreamer, until Feisty Fawn at least, because now gstreamer is "good enough".

---

### Post by BrokeBody on 2007-06-05
> **aysiu said:**
> Can you post a link to a website that doesn't work without *w32codecs* so I can try it and see what happens?

It's very hard to find a website with some multimedia content which will not work or not work properly without w32codecs. However, I ran on some movies (.avi) and they didn't have picture or they didn't work at all. After installing w32codecs everything is fine now. Btw, I also have gstreamer, ffmpeg, xvid, libdvd...

---

