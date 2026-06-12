---
title: "Firefox audio to Ardour"
date: 2014-03-04
forum: Ubuntu Studio
---

### Post by Tristan_Williams on 2014-03-04
How can I pipe the audio from Firefox into Ardour?
Every time I try this, jackd prevents all firefox audio from going anywhere, even to the speakers.

I can just issue 'killall jackd' and the audio works fine. 

Anyways, how can I pipe the Firefox audio to Ardour?

---

### Post by su:bhatta on 2014-03-05
If I understand correctly, you get no audio from Firefox with Jack on, right ?

Then you have to first get the Pulse-audio Jack sink to work. Once that is done Firefox audio will play with Jack running. 
Refer to this page to get the Pulse-audio sink working: [https://help.ubuntu.com/community/UbuntuStudio/ProAudioIntro/1204](https://help.ubuntu.com/community/UbuntuStudio/ProAudioIntro/1204)

How to 'pipe' the audio into Ardour I am unsure,, Patchage, maybe, but does it show the Firefox audio, I dont know. 

Sorry there.

---

### Post by jejeman on 2014-03-05
Firefox actually doesn't have audio output, I guess. Flashplayer does etc.
Any way "Firefox" isn't JACK aware application, so you need some helper to sink audio from "firefox" to JACK. This topic has already been discussed on this forum.

---

### Post by Tristan_Williams on 2014-03-05
Oh well it wasn't really that important.

---

### Post by Sylos on 2014-03-06
I think there is another option (if you dont want to use pulseaudio). There used to be a firefox plugin called flash replacer (i think) that allowed you to set VLC as the player for flash content (it worked with some site but not others). As VLC has a jack plugin tha can be installed you could then pipe that into any jack recording software. 

I havent tried it but it may be possible if you dont fancy the pulseaudio jack sink.

Cheers

---

### Post by brianmc on 2014-03-13
Assuming you get the PulseAudio sink installed, there's some setup required to make it work.

First, you should find it connecting - by default - to route output to speakers:
[ATTACH=CONFIG]251097[/ATTACH]

Assuming you see that, it is just a matter of routing output via PulseAudio through the sink:
[ATTACH=CONFIG]251098[/ATTACH][ATTACH=CONFIG]251099[/ATTACH]

Once you've started Ardour, or whatever other JACK-aware application you want to route 'regular' audio to, just rewire the "[FONT=fixedsys]*PulseAudio Jack Sink*[/FONT]" to the inputs of that.

---

