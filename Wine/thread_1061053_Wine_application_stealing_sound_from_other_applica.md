---
title: "Wine application stealing sound from other applications"
date: 2009-02-05
forum: Wine
---

### Post by Kareeser on 2009-02-05
Hey guys,

So I installed Sibelius (a music notation and score playback program) onto my computer through WINE. Works great, and I get MIDI playback through the TiMidity package.

Problem is, while I can get playback working great on Sibelius, whenever the program is running, it hogs the sound output, so I can't use Rhythmbox at the same time (for example)

I'm not sure whether this is a problem with TiMidity hogging the output, or something through Wine...

Anyone have suggestions?

---

### Post by cogadh on 2009-02-05
It is probably due to the fact that you have a sound card that is not capable of hardware mixing. If that is the case, then it will only process one audio "stream" at a time, meaning only one app can have sound at any given time.

---

### Post by xzero1 on 2009-02-06
Hardware mixing is probably *not* the problem. See posts on setting up alsa or pulse audio correctly to solve this problem.

---

### Post by donkyhotay on 2009-02-06
It may be timidity, I can play sound in starcraft and other programs (such as skype) at the same time with no problems, but I have issues when playing music from NTED (a native linux sound composing program) which uses timidity. Try playing sound with wine from a program that isn't trying to use midi instead and see what happens. This will at least narrow down the possibilities.

//edit: BTW unless you have a specific reason to use sibelius (I never have) you might want to check out NTED which as I mentioned is linux native and available in the repos.

---

### Post by Kareeser on 2009-04-07
Thanks for the headsup, donkyhotay, but NTED doesn't seem robust enough for me. I've also done some heavy work on Sibelius, and I can arrange things faster on there than any other program :)

All that work, gone to waste? Not unless there's a good reason :)

Anyhow, I figured out my own problem:
TiMidity was loading itself before the Pulseaudio sound server, which led to some conflict issues when it came time for wavemapping to the output device.

Restarting the TiMidity sound server with

```
sudo /etc/init.d/timidity restart
```

... did the trick :)

[Bug report](https://bugs.launchpad.net/ubuntu/+source/timidity/+bug/210472)

---

