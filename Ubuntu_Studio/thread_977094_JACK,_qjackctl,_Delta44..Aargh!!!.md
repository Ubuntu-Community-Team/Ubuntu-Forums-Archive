---
title: "JACK, qjackctl, Delta44..Aargh!!!"
date: 2008-11-09
forum: Ubuntu Studio
---

### Post by 98springer on 2008-11-09
Okay, I usually consider myself to be pretty good at searching for info on unfamiliar subjects but the whole Linux Audio thing is whipping my butt. Sometimes things work and sometimes they don't. What I need is a "This needs to be setup this way" guide for the fundamentals. If I get directed to [http://jackaudio.org/](http://jackaudio.org/) one more time I swear I'm gonna just go back to porn or, God forbid, XP. Thanks in advance for any help.
My setup:
M-Audio Delta 44 Soundcard
M-Audio Audio Buddy Preamp
Pocket POD
Ubuntu Studio 8.04
jackd version 0.109.2
JACK Audio Connection Kit - Qt GUI Interface
Version: 0.3.2
Hydrogen
Ardour
Qsynth (love it)
M-Audio Key Rig 49 (recognized right out of the box)
At one point I was able to record Synth and Drum Tracks in Ardour but was not able to (CONSISTENTLY) record a Guitar track although I could hear it in Ardour. This is as good as it got. Guitar path was Electric Guitar>POD>Audio Buddy>Delta44 breakout box>Delta44 card. I was also able to playback using a stereo. Most of my issues are with JACK and qjackctl.
Questions:
1.In qjackctl setup, should I select Delta44 or ICE1712 as my input and output devices?
2. In JACK, what is the difference between the Connections and Patchbay configurations? Do I even need to use the Patchbay?
3. What are the TIMidity ports for? I see ports 0-3. Does this have anything to do with the connections on the breakout box?
4. I want to be able to record Drums, Synth and Electric Guitar. If anyone is using this setup for this purpose, please post screenshots, links, etc of what I need to do so I can have a baseline of the fundamentals to get running and something to go back to when I blow it up.:)
5. Once it's up and running, do I have to save the config somehow?

Alright, that's it. Thanks for letting me rant. By the way, Ubustu was down last time I checked so that's one of the reasons I'm boring you folks with this.:)

---

### Post by duffrecords on 2008-11-10
1. I'm not sure why QjackCtl's Setup lists both Delta 44 and ICE1712.  ICE1712 is the name of the chip on the Delta 44 card.  I have a Roland RPC-1, which uses the same chip, but I only have these options:

ICEnsemble ICE1712
ICE1712 multi

Either one works for me.  Can you tell me exactly what options are available in the drop-down lists for Interface, Input Device and Output Device?

2. [The difference between QjackCtl Connections and Patchbay]("http://ccrma-mail.stanford.edu/pipermail/planetccrma/2005-December/010923.html")

3. To record something, whether it's a guitar through your Delta 44 or drums tracks from Hydrogen, it's more or less the same:[LIST]
[*]Check in QjackCtl if Ardour's master/out ports are connected to your system's playback ports (it usually connects automatically).
[*]Add a new track in Ardour
[*]Using QjackCtl's Connections or Patchbay, connect your source to the new Ardour track
[*]Open Ardour's mixer window (Alt-M)
[*]FYI, you could have also connected your source using the Input button at the top of the track strip (instead of using QjackCtl)
[*]Click the Output button at the bottom of the track strip and select Master Out
[*]Click the record enable button at the top of the track strip in the mixer
[*]Press Record+Play in Ardour's editor window
[/LIST]

4. QjackCtl's Patchbay can save your routing configuration (that's one of the main differences between it and the Connections box).  As for the settings on your other applications, you need [LASH (Linux Audio Session Handler]("http://lash.nongnu.org/").  Basically, you start LASH, then start your audio apps, and you save the LASH session when you're done.  Unfortunately, there are still a lot of apps that don't have LASH support yet, so make your voice heard on their forums.  We want LASH support!

If you've made it this far, you're in good shape.  Next you should set up realtime processing so you don't get xruns (audio dropouts).

---

### Post by 98springer on 2008-11-10
Thanks for the reply. I changed the input and output device settings and I think I see more options(an extra tab) when Ardour starts. I'll experiment later and see if I can record all of the instruments that I need. I'm using the realtime kernel in Ubuntu Studio already but I'm sure I'll need to do some tweaking but I guess I won't know for sure until I'm actually recording more than a couple of minutes worth of material.

---

### Post by duffrecords on 2008-11-10
If you're already using the realtime kernel, the only settings you should double-check are that the following lines appear in your /etc/security/limits.conf:```
@audio          -       rtprio          99
@audio		-	nice		-10
```and that you are a member of the audio group:```
cat /etc/group | grep audio
```

---

### Post by duffrecords on 2008-11-12
Oh, also make sure you check the "Realtime" checkbox in the QjackCtl settings.

---

### Post by 98springer on 2008-11-16
Thanks a bunch! Just using the "Connections" in JACK made everything so much easier. I totally ignore the Patchbay. It helps to have somebody say "this should work" so I know where to begin troubleshooting. I'm able to consistently record a guitar track now. Just need to get my levels right. Do you know of a really good mixer app. Right now I have to click one tab to see the levels and another to adjust them.

---

### Post by cek on 2008-11-18
> **98springer said:**
> Thanks a bunch! Just using the "Connections" in JACK made everything so much easier. I totally ignore the Patchbay. It helps to have somebody say "this should work" so I know where to begin troubleshooting. I'm able to consistently record a guitar track now. Just need to get my levels right. Do you know of a really good mixer app. Right now I have to click one tab to see the levels and another to adjust them.

You can use meterbridge for watching the input levels, it's relatively straight forward.

In this situation I usually run patchbay/connections like so:

in1->jack-rack1->meterbridge1->ArdourIn1
in2->jack-rack2->meterbridge2->ArdourIn2

ArdourMaster1->system_playback_1
ArdourMaster2->system_playback_2

Though you can leave Ardour our (go straight from meter bridge to output) if you just want to adjust settings (not record).

---

