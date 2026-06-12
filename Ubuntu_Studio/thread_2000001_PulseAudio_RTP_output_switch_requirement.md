---
title: "PulseAudio RTP output switch requirement"
date: 2012-06-08
forum: Ubuntu Studio
---

### Post by Ozzman on 2012-06-08
hey guys, I'm having a rather odd issue.

Earlier this week I became obsessed with setting up a dedicated MPD server that could stream via Pulse RTP to my Ubuntu Studio 10.04 install and also via HTTP to my droid via mpdroid. I plan on setting up several independent MPD instances for each system in my home later (fun times I know).

I was able to get both those to work and it's marvelous! I can switch outputs via both my phone (through 3/4g through custom ports) and PC interchangeably. Then stream to my phone via it's 3/4g connection through HTTP.

HOWEVER for some stupid reason I need to switch my audio output option via sound preferences on my ubuntu studio install to anything other than my internal sound card then back before the audio kicks in. Also if I stop the MPD stream instead of pausing or switching songs then I need to do the quick switch via sound Pref again before audio kicks back in. 

It looks like every time my stream stops I need to do that switch before it kicks back in. Everything else is working fine.

What do you guys think is up? I'm at my wits end over this!!

---

### Post by Ozzman on 2012-06-09
for those that may run into it later:

First make sure you select create separate audio device for multicast/RTP is enabled in pulseaudio preferences under Multicast/RTP

Then I just wrote a script that loops the rtp.monitor source to my audio.. you can check what those are via paman under devices. The source is source and sink is output. here is the script:

```
pacat -r --latency-msec=500 -d [input] | pacat -p --latency-ms=500 -d [output]
``` (For these purposes 500ms is about perfect)

so mine looks like this:

```
pacat -r --latency-msec=500 -d rtp.monitor | pacat -p --latency-ms=500 -d alsa_output.pci-0000_00_0f.1.analog-stereo
```

save that as a script then add that script to your start under preferences/startup applications

---

