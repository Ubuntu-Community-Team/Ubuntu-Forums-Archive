---
title: "Do I Need Studio?"
date: 2016-07-29
forum: Ubuntu Studio
---

### Post by mcmulvaney on 2016-07-29
I am a brand new Ubuntu user. After some explorations running Ubuntu on a USB stick, recognition of the advanced age of my laptop (7 years), and tired of Microsoft's increasingly intrusive business practices I took the plunge and purchased a System76 Meerkat (2.3Ghz Intel I3, 8GB RAM, 250GB SSD) running Ubuntu 16.04. My creative needs are not large:
[LIST]
[*]I do multi-track audio recording, but only record 2 tracks at a time, although I have mixed projects with up to 32 tracks of audio and typically use 1-3 plugins on some of the tracks and a couple of mastering plugins on the stereo bus.
[*]I do some video production, typically with clips and stills that I've uploaded from my camera, audio from the captured video plus a music or narration track. For me an ambitious project might have 3 video tracks and 3 audio tracks at most. Distribution via DVD or upload to YouTube or similar.
[/LIST]

Studio has an incredible wealth of tools along with a higher performing kernel. I just find myself wondering if I really need all of that to do what I've described above. I think my tool needs boil down to:
[LIST]
[*]A decent DAW (Ardour, Audacity, Reaper ?)
[*]A fairly simple video editor
[*]DVD authoring tool
[/LIST]

So - what do you think - should I just download and install the tools that I need or go all the way and install Studio?

Thanks in advance for any advice you'd care to give!

---

### Post by yoshii on 2016-07-29
Personally, my needs and uses are very similar to yours.  I use 32-bit Ubuntu Studio v16.04 with 32-bit Windows REAPER v5.x
I had to implement some tweaks of PulseAudio and a few other things like disabling unneeded resources, but after that, it's been smooth sailing.  

[https://ubuntuforums.org/showthread.php?t=2309922](https://ubuntuforums.org/showthread.php?t=2309922)

That's my main thread describing what I do to get my system ready for audio use.  
It gets easier every time I do it.  

Personally, I don't yet use the Linux DAWs because I need easy access to my Windows 32-bit VST instruments and effects, both paid for and freewares.  
I do use OpenShot and KDEnLive for video editing, and I like those alot.  Also I installed xine and it's reccommended libraries which helps the 32-bit Windows version of AVIdeMux work better too.  I also use that.  I don't use xine for video playback though, I use VLC Media Player since it simplifies codec usage.  

I'm not sure about DVD authoring, but I think Ubuntu Studio comes with DeVeDe or something like that.  

I forgot to mention, I also use OcenAudio and Audacity for offline edits of WAV files instead of using REAPER for those.  REAPER would work, but I'm used to the old fashioned ways.  OcenAudio got a bit more difficult to install in recent months/versions, but I posted info here on how to get the needed dependencies to make it a bit easier.  

[https://ubuntuforums.org/showthread.php?t=2327225&highlight=OcenAudio](https://ubuntuforums.org/showthread.php?t=2327225&highlight=OcenAudio)

I hope this is all helpful.  

I am just now in the process of starting to make a music video.  
But if I need more video editing power, I make dual boot install into AV Linux to have access to Cinelerra (video editor).  
I tried AV Linux earlier this year.  It's Debian style but mostly the same as using Ubuntu and a lot of the .deb packages install just fine.  

The downside is that AV Linux is made and maintained by really just one guy and he can't do a whole lot alone to support everyone.  
But I'm still thankful for what he's done.  Also, I don't trust the idea of installing the KXstudio repos as is, because some of the PPA's link to really old stuff for before Trusty Tahr (v14.04 LTS).  But it is nice that KXstudio and AV Linux have joined each other.  Otherwise.  

I hope this helps.  Peace

---

