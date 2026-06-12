---
title: "aplay not independent of pulseaudio"
date: 2019-11-11
forum: Ubuntu, Linux and OS Chat
---

### Post by AdirondackJim on 2019-11-11
Hi,

I just got done diagnosing a sound issue on my (ubuntu) htpc.  I usually use hdmi or spdif to send audio to my receiver.  But, for Halloween, I wanted audio from the front headphone or rear audio jack .  But it didn't work.  I researched alsa & pulseaudio to get an idea of how things worked and it seemed to be layered--alsa was below pulseaudio & serves as an abstraction layer talking to the drivers..  Wanting to reduce the variables, I decided to test alsa first,  and then work my way up to pulseaudio.  I found a nice diagram that said speaker-test went through pulseaudio (and aplay did not).  So, I stopped using speaker-test & used aplay (and alsamixer to make sure nothing was muted).  I was about to give up (spent more time than it was worth) and decided to do a "Hail Mary" and run pvaudiocontrol and unmuted the main speakers.  Low & behold it worked.

I don't think pulseaudio should control if aplay works or not.  Otherwise, aplay is not a diagnostic tool for alsa--it's a tool that tests part of pulseaudio AND alsa.  In my experience, diagnosing a problem quickly involves testing one thing at a time.  I think aplay should be modified, or a new tool developed.

(I went to the alsa website and couldn't find a way to post a feature request, so I'm putting my thoughts here--as a warning to people troubleshooting audio and maybe I'm planting a seed for an improvement).

Thanks,


Jim

---

### Post by CatKiller on 2019-11-15
> **AdirondackJim said:**
> I researched alsa & pulseaudio to get an idea of how things worked and it seemed to be layered--alsa was below pulseaudio & serves as an abstraction layer talking to the drivers..  

Not exactly. 

In the before time, the drivers were in the kernel and exposed through ALSA, and there was a software stack for mixing and manipulating streams, which was also called ALSA and had some significant limitations. PulseAudio replaces that second part but still uses the first part.

To aid compatibility, PulseAudio can also act like the second part: some application can try to use the old ALSA software mixer and PulseAudio will let them, but it's still really going through PulseAudio. Otherwise, you wouldn't be able to move audio streams from one device to another, or simultaneously play streams of differing bitrates, or play things on multiple devices, or all the other things that PulseAudio does better than the old ALSA mixer.

---

