---
title: "recording problems with audacity, ardour, jack..."
date: 2009-05-06
forum: Ubuntu Studio
---

### Post by cornsay on 2009-05-06
Hello everyone, 

I don't really know where to start with this, so I'll list everything and see where it gets me...

I'm running Ubuntu 8.10 on a dell inspiron 1501 laptop. I want to record an input (from a pair of turntables via an amp). I have an external USB soundcard -- a creative xmod -- because the line input on the onboard soundcard is awful quality.

The xmod works fine with ALSA. I can also record from it fine into the bog-standard sound recorder, but I'd like to record into one of these more sophisticated bits of software...

I first tried to record with audacity. The problem there was that it consistently stopped recording and crashed at no more than 15 minutes, often just five, or less. I have plenty of hard disk space and memory.

I then tried ardour. For this, I first had to try and configure jack. No matter what I put the settings to, I get a huge and continual series of xruns.

Even so, I tried recording in ardour. That crashed immediately I hit the record button. I guess this problem goes back to the jack thing, but perhaps not? So, in summary, can anyone help me:

1) avoid crashes in audacity; or
2) configure jack to avoid xruns; or
3) get ardour working (which might depend on 2); or
4) recommend some other recording software?

I know this is quite messy, but I can't separate out my problems, and they might have a common root. Grateful for any help.

---

### Post by OneMixDJ on 2009-05-07
:-\"

I've never worked with ardour, but I have with audacity.

Can you post your audacity settings for starters (Edit>Preferences)

Thanks!

---

### Post by kayosiii on 2009-05-07
Ok if you are getting xruns with jack try pushing the Frames/Period up to the maximum of 4096 also try pushing Periods/Buffer to 3.... 
Check to see what sample rates the device supports natively and make sure that jack is set to one of those (some cards only support 48000 natively and use software conversion for say 44100).

If you are still getting xruns at this setting then something is terribly wrong. (Maybe try the Alsa or jack people at that point or the Linux-Audio-Users mailing list)...

At this point your latency will be dreadful but working in Ardour this should be fine since it will automatically compensate. Try bringing down the frames/period and seeing what setting you can actually work with...

If this is not enough then you will want to get Jack running in realtime mode. To do this you need to give your audio Applications permission run at a higher priority than an application is normally allowed. There are instructions on how to do this on Ubuntu everywhere so I won't bother repeating it here.

---

### Post by thorgal on 2009-05-07
using the jack server on a random laptop with a stock ubuntu distro on it may lead to some frustration ...

jack is meant for DAWs and as such, it requires that the h/w and OS (read kernel) play cool for audio. There are tons of information on the matter, so before getting frustrated over jack, ardour, etc, read a lot about it :)

---

### Post by cornsay on 2009-05-07
Thanks for all your replies!

Thorgal: Hmm, I see... that's not obvious from any of the stuff I've read, but OK. It might be nice if Ardour (and other stuff that relies on Jack) said explicitly what you just said... but that's not a point/whinge to make here.

Kayosii: I think I've tried all those settings, but I'll have another fiddle later and report back. Thanks.

OneMixDJ: here's what I take to be the relevant settings from audacity:

---

### Post by rayj on 2009-05-07
Making sure you are running a real-time kernel will help. If you aren't, it isn't difficult to add RT functionality. In theory it isn't necessary, but in my experience it definitely helps...

---

