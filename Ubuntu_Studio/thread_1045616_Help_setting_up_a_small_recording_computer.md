---
title: "Help setting up a small recording computer"
date: 2009-01-20
forum: Ubuntu Studio
---

### Post by hinesdeal102 on 2009-01-20
Hi everyone, I play bass and I was wondering what I need to do in order to get a good high quality recording.  I will be using Ubuntu Studio and I plan to just do some recording and editing.  I need close to zero latency (thats where linux is good) and I basically have this idea of using my computer's speakers as an amplifier.  I tried to do such a thing in windows with audacity and the latency was terrible.  I couldn't find a better free program for windows that may have supported lower latencies.  I need to be able to record my bass while playing it through the speakers.  I am just using an onboard sound card (realtech) just some simple sound thats an a 780g motherboard.  Will that integrated sound be able to record decently?  I'm not a idiot when it comes to computers but I am completely new to recording and all the little things that come with recording music.  I know close to nothing about sample rates or anything of that nature.  Basically I just want the best sound quality while recording and I don't want to spend any money.  One more thing, I heard that a lot of, if not all integrated sound cards are sample rate locked? Is this done through hardware or drivers?  I would greatly appreciate any help the Linux community could offer me.  I love Linux and open source... I plan on staying to open source for all my needs and right now I need a home recording machine/bass amp lol.  Thank you all for your help. :D

---

### Post by Jormeliini on 2009-01-21
> **hinesdeal102 said:**
> I tried to do such a thing in windows with audacity and the latency was terrible.  I couldn't find a better free program for windows that may have supported lower latencies.

There are ASIO4All drivers for low-latency operation in the Windows world. I think that they don't work with Audacity but there is plenty of software with ASIO support.

> **hinesdeal102 said:**
> Will that integrated sound be able to record decently?

Well, it depends. You will not get studio quality sound but it may be good enough for you. You'll know when you try it.

> **hinesdeal102 said:**
> Basically I just want the best sound quality while recording and I don't want to spend any money.

Sorry, that will never happen. The BEST sound quality is always expensive.

> **hinesdeal102 said:**
> I would greatly appreciate any help the Linux community could offer me.  I love Linux and open source... I plan on staying to open source for all my needs and right now I need a home recording machine/bass amp lol.  Thank you all for your help. :D

I think you'll do fine with Ubuntu Studio. You should, however, consider buying a decent sound card for better sound quality. Remember to check that the card is supported from [http://www.alsa-project.org]("http://www.alsa-project.org").

I have recorded music with Ardour on Ubuntu using an integrated sound card. No problems with about 50ms latency because the sound was routed directly from input to output. I think Ardour does latency compensation on the recorded audio because the recorded tracks were synchronized. It is possible that a lower latency would have worked but I had no need to try it. This way you can't use any real time effects from Ardour while recording.

On my recording computer I have Ubuntu Studio and Emu 1820 sound card. It works nicely with low latency.

---

### Post by Phil Urich on 2009-01-21
Another good list for supported stuff is [http://www.linuxstudiopro.com/](http://www.linuxstudiopro.com/).  Again though it tends to be a little bit expensive.

For my own Linux recording usage, which I've only just been dabling in so far, I've got two main cards.  One is an [M-Audio Transit](http://www.m-audio.com/products/en_us/Transit.html), which is a nice USB audio card although I don't have that much first-hand experience of its latency since I just use my cheap soundboard to listen to the mix while recording.  

Something more in line with your situation would probably be M-Audio's [FastTrack USB](http://www.m-audio.com/products/en_us/FastTrackUSB.html), which I've heard  very good things about in regards to using it with Ubuntu for guitars and vocals (hell, it's even got a [guitar input](http://www.m-audio.com/images/global/media_hqpics/FastTrack_back_RGB.jpg)).  I'm fairly certain that the latency is quite low on it, although you might want to check up on that beforehand, but it's quite a popular card so it shouldn't be hard to find that information with a bit of googling (hell, there's probably plenty of testimonials on this forum itself).

Of course, both those cost around $100; my second card that I've just started to use (as in, threw it in earlier today, heh) is a Creative Audigy Platinum.  These days Creative's Linux support is far from stellar, but the original Audigy is pretty much the height of Linux support (certainly for (K)Ubuntu) and I liberated this one from an aging free computer I acquired :)  So that's another option for you, there's lots of nearly decade-old cards out there to be salvaged that would likely do the trick for you better than the onboard (though again, for your purposes the onboard might be fine, you'd have to try it first).

The onboard card being sample-rate locked shouldn't be an issue, since it's certainly going to be either 44.1k or 48k, and either'd be fine. 

Get back to us when you're in the process of setting it all up! :)

---

