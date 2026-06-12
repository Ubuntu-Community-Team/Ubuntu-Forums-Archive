---
title: "Few questions about JACK and audio on Ubuntu Studio"
date: 2012-07-22
forum: Ubuntu Studio
---

### Post by Alecossy on 2012-07-22
Hello there, 
I'm planning on using my laptop as a mobile amplifier for a bass guitar using the default microphone input and connecting the guitar through a mono jack cable, still I have no idea where to start from.
I tried playing around with JACK settings only to be able to connect manually input-1 to output1.
Last time I tried it automatically connected the whole thing using this scheme: 
[http://i45.tinypic.com/rjfh21.png](http://i45.tinypic.com/rjfh21.png)
but all i'm getting is some crunchy sounds with a lot of statics behind.
What am I doing wrong?

---

### Post by jejeman on 2012-07-22
I've uninstalled pulse-jack-sink, on my system it just bugged JACK.

You can try that, or turn off pulseaudio. And go from there.

Guitarix and Rakarrack are good for effects.

---

### Post by Alecossy on 2012-07-22
Beside the fact that I would like not to mess with the audio softwares, not activating the JACK server means that there will be no sound at all.
Plus, i'm looking for something that can keep latency low, since I would like to use the system as an amplifier and as a multitrack recorder for speed and tecnique exercises (fast moving exercises around 250 bpm).
What would you suggest, then?

---

### Post by jejeman on 2012-07-23
Well, I understood that you want to use laptop as bass effect processsor while playing in a band.

For practice and casual playing, you don't need JACK.

You can use Traverso as multi track recorder, it works without JACK, and for monitoring you can set playback in alsamixer of jack that you use (mic in your case). When you monitor like this there is no latency, because signal is routed in audio card.

---

### Post by Alecossy on 2012-07-23
Here comes an obvious question, then: what's JACK and what's its full potential?

---

### Post by jejeman on 2012-07-23
Jack Audio Connection Kit is a sound server.

Better to read from the source
[http://jackaudio.org/](http://jackaudio.org/)

---

### Post by sgx on 2012-07-24
> **Alecossy said:**
> Here comes an obvious question, then: what's JACK and what's its full potential?

used to connect -->supported<-- hardware and software, where the
cpu and ram are the main limits.

In a session, one can run standalone Amplitube 3 exe, reaper DAW as  vst host, loaded with Guitar Rig 5 plugin, and route their output to
rakarrack or wherever else, with other linux instruments for
drums, keys etc.  Using asio in a windows session, would not easily allow for this type of free-range flexibility.

There are social concerns around the world, where linux
and jackd might enable musicians in dire situations, to wonderfully
utilize gear that musicians in free and prosperous situations,
might consider obsolete, or unwittingly deem inadequate.

Cheers

---

### Post by Sylos on 2012-07-25
> **Alecossy said:**
> Hello there, 
I'm planning on using my laptop as a mobile amplifier for a bass guitar using the default microphone input and connecting the guitar through a mono jack cable, still I have no idea where to start from.
I tried playing around with JACK settings only to be able to connect manually input-1 to output1.
Last time I tried it automatically connected the whole thing using this scheme: 
[http://i45.tinypic.com/rjfh21.png](http://i45.tinypic.com/rjfh21.png)
but all i'm getting is some crunchy sounds with a lot of statics behind.
What am I doing wrong?


Hello there. Just thought it worth a mention that connecting a line level device (such as your bass) into a microphone input is likely to give you clipping and distortion (and possibly damage the input). You may be able to suitably attenuate the level through alsamixer or some such software control but you may need some attenuation device between instrument and laptop. That or see if you have a line input on your laptop and use that.

Cheers

---

### Post by Alecossy on 2012-07-25
> **Sylos said:**
> Hello there. Just thought it worth a mention that connecting a line level device (such as your bass) into a microphone input is likely to give you clipping and distortion (and possibly damage the input). You may be able to suitably attenuate the level through alsamixer or some such software control but you may need some attenuation device between instrument and laptop. That or see if you have a line input on your laptop and use that.

Cheers
Thanks for the info!
Sadly, I don't have any line-in on my laptop (it's an Acer 5742ZG).
Is there any tool or device i might use to reduce such distortion?

---

### Post by Sylos on 2012-07-25
Well, first things first - plug in and connect your guitar. Then run "alsamixer" in a terminal. This should give you a mixer showing inputs/outputs etc. Try playing and see if the level shown for the input is in the red. If it is that is bad. Try reducing the mixer level and stop it from peaking into the red. If you cant get it to stop peaking then you need something between the guitar and laptop.

As for what to use - Im not sure really. I would think some kind of DI (direct input) box would be the sort of thing you want for the job.

See how you get on with existing equipment first (once you get jack etc running).

Cheers

---

### Post by Alecossy on 2012-07-25
Simply playing with alsa levels doesn't seem to work... reducing mic boost and / or mic volume levels simply gets the sound to disappear but statics remain.
The only way to remove statics is to set the volume levels to almost 0 (which is useless)

What we would need is something different.
I think, by using jack, we could connect the input to an application able to clean it up (provided that such apps exist) and then digitally amplify it and redirect it to the speakers/headphones

This would slightly increase delay but solve the problem without having to buy a DI Box.
Another question is: would 4GB DDR 3 ram suffice for the job? 
I would want to spend money on a box and then end up with memory problems.

What I'm asking you guys is this: can the first solution be applied?

---

### Post by sgx on 2012-07-25
> **Alecossy said:**
> Thanks for the info!
Sadly, I don't have any line-in on my laptop (it's an Acer 5742ZG).
Is there any tool or device i might use to reduce such distortion?

definitions of the signal levels:
[http://www.bedroom-recording.com/audio-signal.html](http://www.bedroom-recording.com/audio-signal.html)

[http://www.guitar.com/articles/recording-guitars-get-signal](http://www.guitar.com/articles/recording-guitars-get-signal)

The mic input maybe a combo mic/line.

Often a cheap usb interface works to provide the needed
signals. The Mustang amp would do this, and so much more.

You can get ART or Presonus preamps, Behringer usb
guitar interfaces, or a variety of mAudio usb soundcards.

Lots of good options.
Cheers

---

### Post by jejeman on 2012-07-25
> **Alecossy said:**
> Another question is: would 4GB DDR 3 ram suffice for the job? 
I would want to spend money on a box and then end up with memory problems4GB is plenty. You will not have any problems memory wise.

---

### Post by Sylos on 2012-07-26
> **sgx said:**
> definitions of the signal levels:
[http://www.bedroom-recording.com/audio-signal.html](http://www.bedroom-recording.com/audio-signal.html)

[http://www.guitar.com/articles/recording-guitars-get-signal](http://www.guitar.com/articles/recording-guitars-get-signal)

The mic input maybe a combo mic/line.

Often a cheap usb interface works to provide the needed
signals. The Mustang amp would do this, and so much more.

You can get ART or Presonus preamps, Behringer usb
guitar interfaces, or a variety of mAudio usb soundcards.

Lots of good options.
Cheers


Cheers for that sgx - I stand corrected.

Not the level but the impedance that causes the issue. 

Sorry for the confusion OP - I live and learn.

Cheers

---

