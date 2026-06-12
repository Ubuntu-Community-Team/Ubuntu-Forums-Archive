---
title: "Matching up audio and video with 13.10"
date: 2013-12-02
forum: Ubuntu Studio
---

### Post by brianmc on 2013-12-02
I've just done the sound for a charity gig, with the current 64-bit 13.10 build, using Ardour to manage/record/mix the live audio from an Akai EIE i/O (the USB 1.1, 44.1kHZ/16-bit red one). I'm fairly happy with how the sound went, would - ideally - like a 'proper' realtime kernel to kill the half-dozen xruns I had through ~3 hours of recording, but am currently more-concerned with the post-production work on the media I've snagged.

I don't expect any problems on the audio side, but I've a bunch of independently-filmed video clips of the gig. Those - obviously - have pretty dreadful audio from built-in microphones. I'm interested in what tools, the techniques, and - hopefully - a few tips on how other Ubuntu Studio users deal with marrying those up. I've no guarantee there's video for all the recorded audio, and I'd obviously like to concentrate my audio mixing efforts on where there is video.

Documentation? I'll read that when it's how-to wire stuff up, but it never tells you what machine you're actually building. Some insight into what other folks have *learned the hard way* is effectively what I'd really appreciate.

Anyone else who, like me, mics up everything, please note I enjoy laughing at amplifier-expressed sexual-inadequacy too. But, the only reason I keep having to say: "Eh? What?" to the guy using a 500 watt Marshall trouser-shaker head, is because I'm wearing earplugs. :D

For the curious, the mics in use were: 2x Beyer dynamic 201 N(C), 1x SM58, and 1xSuperlux R102 phantom-powered ribbon. After a 'turn it down!' moment when an amplifier was placed on stage, the SM58 was used to mic it up. On the back-end, using a Dell quad-core i5 laptop and running the live playback out of the line out from that into what the pub referred to as their 'vocal PA'. As a FYI, I'm really happy with the Akai EIE I/O box, and will be stepping up to the Pro version in the near-future. Unless, that is, someone can suggest an eight-channel 'step-up' that isn't an order of magnitude step-up in price.

---

### Post by qavfoto on 2013-12-03
Hi, brianmc:
I come from "the other side": I am a photographer beguinning with video, where I understand the pictures as something natural to me, the sound is something that I can not understand well.
I think that what you want is a way to get syncronized your well recorded sound with diferent videos, whose sound is poorly recorded with on-camera microphones. If this is the question, there are no good news. The usual way to sinchronize sound with video in cinema or video is to use a clapboard or make a loud clap with your hands in front of the camera, it is recorded in both media simultaneously, and both, sound and video, files have to be named to be recognised in post as "engaged". Then in post-production it is easy to "marry" them as the wave produced by the clap in the beguinning of the sound clip is easyly recognised, as it is the frame in the video clip where you can see that the clap is done.
I think that for you will be easy to recognise the characteristic wave of a chord, two drumsticks beating, etc. at the beguinning of each song. It must be easier than can be expected, since I could do it some times. The job is to find these frames-waves and "marry" them in the timeline. Every NLE (Non Linear -video- Editor) will show you a timeline in which you can put the video and audio channels that you want. You must add first your record and then you can go adding the video clips, cutting from them later the sound that they have attached. To finish: save and export in the video format that you prefer/need.
It is a hard job by its tedious procedure more than by its complication.
Ubuntu Studio comes with Kdenlive, a good NLE enough for what you want. If you want more, you can try with Lightworks.
I am sorry if I am telling something that could be obvious for you

---

