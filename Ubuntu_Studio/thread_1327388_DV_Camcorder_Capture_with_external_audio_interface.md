---
title: "DV Camcorder Capture with external audio interface?"
date: 2009-11-15
forum: Ubuntu Studio
---

### Post by Mike'sHardLinux on 2009-11-15
I am wanting to play around with video production using my miniDV camcorder along with an audio interface. I don't want to rely on the built-in microphone. I assume some people are already doing this and can give some advice.

I am running Karmic, 64-bit, but have no problem switching to something else if it'll make the job easier. I have been playing with Kino and KDEnlive and like both (I am using [and prefer] Gnome, not KDE). 

I wonder if there may be any issues running a firewire audio interface at the same time as doing capture with a DV(firewire) camcorder. ie, might I have any problems getting them to work together simultaneously...sync issues, or dropouts, or whatever.

Is anybody already doing video production this way and have any tips they want to share? ie, what problems you ran into, what equipment are you using, workflow suggestions, kernel optimizations, anything I should avoid, etc....

I would prefer to run a firewire audio interface. Second choice would be USB, only because I want portability. I only need 2 channels of input and I don't *need* mike preamps, although if the interface has them, that is OK. I want to be able to capture **live** from my camcorder while recording the audio through the audio interface.

I already have a Delta 1010 on another machine that I use strictly for music production, so I don't need another PCI audio interface. It just isn't very mobile.

Thanks

---

### Post by gordintoronto on 2009-11-28
I have no idea what you mean by "audio interface."  Does it record the audio, so that you can copy a file from the device to your computer?

I have found Cinelerra excellent for combining audio and video which were recorded separately.  (And for everything else I wanted to do...)

---

### Post by Mike'sHardLinux on 2009-11-29
Hey. Thanks for the reply!

Well, originally, the problem was that the audio recorded from the camcorder just plain sucked. Since I have tons of audio equipment (microphones, pre-amps, etc...), I thought I could just tell the capture software to grab the audio from my external audio interface. I have found that will not work because EVERY IEEE1394 capture software I have tried in Linux and Windows only captures the DV stream, and don't even give an option to grab multi-track audio, or at least pick a different audio input.

I did some more research and basically ended up doing what you suggested.....I capture the DV stream with DVGrab and using an audio software, capture the audio from my audio interface simultaneously. Then I use my editor to insert the extra audio track and manually synchronize them. I was concerned that it would be too difficult to synchronize the audio, but it was easy. 

The sad part of this story is that I could not get KDEnlive to work properly...lots of bugs on my systems. (I tried it on two completely different systems.) Perhaps, part of my problem is that I am running KDE apps in Gnome? I have had to resort to using Windows again, using Sony Vegas Movie Studio HD, since it is cheap and does the job OK.

I guess I can marked this as solved, though it sure isn't the ideal solution.

---

