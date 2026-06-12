---
title: "Ubuntu Studio for daily use?"
date: 2015-06-15
forum: Ubuntu Studio
---

### Post by Grone1985 on 2015-06-15
Hi,
I'm a beginner web developer/programmer and I also make music as a hobby (mostly guitar recording and Hydrogen).
I've used Ubuntu and Ubuntu Studio for a fair amount of time and I've always dual booted between both but that's starting to get old.
I would like to get some advice about potential issues/limitations for programming if I moved to US full time. If anyone has any type of experience I would greatly appreciate your opinion.

Thanks in advance,

Jorge

---

### Post by jejeman on 2015-06-15
Lowlatency kernel can be a little bit heavy on CPU, but if you have at least C2D @ 2GHz, than you can go for US full time.

---

### Post by Grone1985 on 2015-06-15
Thanks jejeman! Good news for me!

---

### Post by MartyBuntu on 2015-06-17
I've been using the 14.04 LTS since it's release as my main workstation (with MATE Desktop).
Works well.

---

### Post by doc taz on 2015-06-30
I've used it for nearly 2 years as my main Ubuntu distro. I'm on 14.04.2 LTS 64 bit. I also have Windows 8.1 Pro and Debian 8.1 jessie on other partitions. The only thing I can't get to work is hibernation, but it may be a BIOS/hardware issue for me. Other than that, it runs great and I use the low latency kernel full time.

---

### Post by joseph-anthony-king on 2015-07-08
Hey doc taz, is your swap partition big enough to hold the contents in RAM?  If not that could be why hibernation isn't working.

---

### Post by Megadoomer on 2015-09-27
Hi everyone,

I would like to take Grone's question a little bit further. I am currently still using Windows 7, but with all the recent developments at Microsoft, I am highly considering to fully switch to GNU/Linux sooner or later (rather sooner). I have been using the "vanilla" Ubuntu on my laptop for quite a while already though.

Over the past weeks, I have been looking for ways to either use my programs on Ubuntu with Wine or to find free/open "substitutes" for them (I guess some people won't like this term, but I can't think of anything better right now). Since my interest is also in the music/video branch, I noticed the Ubuntu Studio derivative and it sounded absolutely fitting for what I was searching for, as I need low-latency performance for mulitrack recording, effects and software monitoring e.g. in Reaper with the Toontrack VSTs.

Now, I know that the graphics software with GIMP, Inkscape, Krita and Scribus is great. However, I'm still having doubts about the video editing and the "back-end" part of the audio software. I have read about such things as bugs Cinelerra, which prevent a frame-by-frame preview where the user must take illogical actions to get it to work properly or where some common files would not be loaded for unknown reasons. Also, Cockos states that while their DAW Reaper is fully compatible with Wine, it would probably perform a lot better in Windows.

I'm wondering now, if there are a lot of these little "flaws" in the daily use of these programs, small bugs that you have to know about to avoid them, such as having to press frame-back twice before being able to progress a frame forward in Cinelerra. Also, I'm curious if anyone is using Reaper, or maybe another DAW, with multiple tracks and VSTs ona regular basis and is able to tell how the stability and latency is holding up when under higher load.

Of course, I don't want a list of all the small bugs and crashes here, I just would love to read more opinions on how this distribution is working out for the people who have been using it for a while. Are there things to know/avoid? Or maybe even only positive experiences so far? Maybe even impressed after switching OSs, like I am planning to?

I'm a bit undecided yet and would be glad to get some more responses on this, as it is kind of an important decision for me. :)


Kind regards!

---

### Post by jejeman on 2015-09-27
It is best to use just Linux native software. Learn it.

If your sound card is supported, and JACK works, there are no significant flaws for audio production. I use MusE for DAW.

For video, situation is a bit less great. I use Kdenlive for editing, and while it worked fine for DV, for HD I'm not so impressed. Guess I need to except the workflow change. There are few more programs for video, but I have not used them that much.

Overall, UbuntuStudio has been a great experience since 2008.

---

### Post by Megadoomer on 2015-09-30
Hi jejeman,

that's great to hear! Thanks for your answer.

> **jejeman said:**
> It is best to use just Linux native software. Learn it.

I understand that, and I would like to use and support open and free software only, but unfortunately that's not really possible for me at the moment (well, of course it is, but at a high cost). I have gotten a Reaper license a while ago, which is still active, because Reaper is everything I have been looking for in a DAW. It's just so natural for me to work with it and and seems effortless compared to the other DAWs I have used, plus I think that they have an extremely fair business model. Granted, I have not tried Muse yet. Also, being a guitarist, I got myself the Toontrack EZMix VST and EZDrummer VSTi plugins and even if I wasn't happy with them, it would be a financial loss to just throw them away. So, it's really important to me that I can get this to work, but I just probably have to try it out.

> **jejeman said:**
> If your sound card is supported, and JACK works, there are no significant flaws for audio production.

As far as I can tell, my USB interface is supported and working out of the box. I haven't figured out how to control it yet, because there are no official drivers of course, but I guess I can find something out about that. At least, Reaper would also have options to control the device.

> **jejeman said:**
> For video, situation is a bit less great. I use Kdenlive for editing,  and while it worked fine for DV, for HD I'm not so impressed.

Oh okay, do you have an idea why the HD editing is not performing so well? Could that be hardware-related (don't know what system you're running on). From what I understand, Kdenlive has no GPU support for rendering video, so it's probably very CPU heavy?

---

### Post by jejeman on 2015-09-30
If your soundcard has some unique controls they are probably not supported.

My system has an i5 CPU which is not that bad. But still not fast enough for smooth HD editing in Kdenlive with long GOP codec. Basic editing is so-so, but with effects there is no chance for realtime playback. Kdenlive has ability to build proxies and transcoding to edit friendly codecs. Which is a legit workflow, that I don't like so much.

---

### Post by Megadoomer on 2015-10-04
> **jejeman said:**
> If your soundcard has some unique controls they are probably not supported.

Well, they are not really unique. Basically just quick settings for the sample rate and frequency, but embedded in the Windows driver window, so probably not available. However, Reaper also has a way to request a certain sample rate from the device, which I have also always set so that I definitely have the correct setting when I start Reaper, should I accidentally have changed it. Does someone know by any chance if this function is available and works under Ubuntu as well?

> **jejeman said:**
> My system has an i5 CPU which is not that bad. But still not fast enough for smooth HD editing in Kdenlive with long GOP codec. Basic editing is so-so, but with effects there is no chance for realtime playback. Kdenlive has ability to build proxies and transcoding to edit friendly codecs. Which is a legit workflow, that I don't like so much.

Well, there's many different types of Intel i5 processors. ;) As far as I can tell however, the biggest advantage when it comes to offline editing is gained from utilizing a dedicated gpu. For my study, I got an old workstation Quadro 5000. I wonder if there is a native video editing program on Ubuntu which supports CUDA or OpenCL for this?

---

### Post by MartyBuntu on 2015-10-04
> **Megadoomer said:**
>  Does someone know by any chance if this function is available and works under Ubuntu as well?


Reaper has always been hit-or-miss for me in the 2 years or so I've played with it under Ubuntu Studio.

> **Megadoomer said:**
> ...the biggest advantage when it comes to offline editing is gained from utilizing a dedicated gpu.

GPU assisted encoding isn't as big as people make it out to be. It's really over-sold...I mean, it helps...but...

---

