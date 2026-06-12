---
title: "No audio after upgrade."
date: 2012-01-01
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Krovas on 2012-01-01
Just upgraded from 10.04 to 12.04. Went relatively smoothly for such a dramatic overhaul to an alpha release, but now I don't have sound at all. Audio players think they're playing, but nothing comes out. Not sure where to look. Any assistance appreciated.

---

### Post by cariboo on 2012-01-02
System Settings->Sound?

---

### Post by mgsfan on 2012-01-02
I've had that happen to me after a recent update don't know what broke it for me

---

### Post by Krovas on 2012-01-05
> **mgsfan said:**
> I've had that happen to me after a recent update don't know what broke it for me

Seems to have something to do with HDMI, but I haven't figured out what to do about it yet.

---

### Post by ventrical on 2012-01-05
Works great here on this card:

00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] SiS7012 AC'97 Sound Controller (rev a0)

---

### Post by Krovas on 2012-01-05
> **ventrical said:**
> Works great here on this card:

00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] SiS7012 AC'97 Sound Controller (rev a0)

I have a Pavilion 6 laptop. Lspci shows some sort of Radeon sound with HDMI in parens. In fact, with all the gui ways of manipulating sound settings that I know, the choices are HDMI or nuthin'. I have an HDMI port, but I never use it, and I see no compelling reason to.

---

### Post by baffle on 2012-01-06
> **Krovas said:**
> Just upgraded from 10.04 to 12.04. Went relatively smoothly for such a dramatic overhaul to an alpha release, but now I don't have sound at all. Audio players think they're playing, but nothing comes out. Not sure where to look. Any assistance appreciated.

I have the same issue. "aplay -L" lists the card correctly, and if I kill all of pulseaudio I'm able to play audio directly via ALSA.

The card does not show up in the "System Settings -> Sound" overview, but the microphone of my USB camera does actually show up. Very strange.

---

### Post by VMC on 2012-01-06
> **Krovas said:**
> Seems to have something to do with HDMI, but I haven't figured out what to do about it yet.

Are you sure the sound it isn't just muted?

---

### Post by baffle on 2012-01-06
I removed all pulseaudio configuration, and the problem still persists. It seems like soundcards I add via USB works, and comes up as a device in Sound settings. The HDA Intel [ALC888]*does not show up, however. I seem to have noticed a lot of people using the hda_intel card having the same issue.

---

### Post by Krovas on 2012-01-06
> **VMC said:**
> Are you sure the sound it isn't just muted?

Quite. I went through all that, believe me.

---

### Post by Krovas on 2012-01-09
This is my problem: my system now only recognizes one way to make noise, and that's though the unused HDMI. I have no option to use my internal analog stereo any more. How do I make Pangolin see and use my laptop's internal analog stereo?

---

### Post by Krovas on 2012-01-10
Okay, here's how I fixed my sound problem.

According to... ```
aplay -L 
```...there's a device called:

```
hw:CARD=HDMI,DEV=3
    HDA ATI HDMI, HDMI 0
    Direct hardware device without any conversions

```

...so I added ```
load-module module-alsa-sink device=hw
``` at the end of "/etc/pulse/default.pa"


..and had onboard sound again after a reboot. I'm not entirely certain why it works like that. I'm also wondering if...
```
plughw:CARD=HDMI,DEV=3
    HDA ATI HDMI, HDMI 0
    Hardware device with all software conversions

```

...would work as well, but I'll try it later. Hopefully, this will help someone.

---

### Post by mjpatey on 2012-02-04
@Krovas,

I just did a fresh install of 12.04 Alpha 2 on my laptop, and am experiencing the same problem: the only outputs available are digital (HDMI), no analog. Like you, I'm not interested in HDMI.

I tried editing the file you mentioned in your previous post, and neither of the example lines worked for me. I also tried a few of the lines from the output of aplay -L, and none of them worked, either.

Any insight into how to make Ubuntu see my good old analog outs?

Thanks in advance!

-Mark

---

### Post by james0658 on 2012-04-13
> **Krovas said:**
> Just upgraded from 10.04 to 12.04. Went relatively smoothly for such a dramatic overhaul to an alpha release, but now I don't have sound at all. Audio players think they're playing, but nothing comes out. Not sure where to look. Any assistance appreciated.

There seems to be mass confusion about the hdmi audio in Ubuntu 12.04. Well all you have to do is go to Dash Home type "Pulse Audio". Left click and drag the icon down to Unity task bar(so everytime you have to switch from HDMI to Computer Desktop, you don't have to go looking for it) Now once "Pulse Audio" is opened go to the configuration tab and click on it, once in there you have all the sexy audio outputs you want, things like Stereo Duplex and HDMI output and so on. I have no idea why they would not just put these selections into the sound preferences in system settings. It's very confusing to people that want to watch a film through HDMI and want surround sound audio also. It was an easy selection in 11.10 but not in 12.04. What a mess!

---

### Post by Krovas on 2012-04-13
> **mjpatey said:**
> @Krovas,

I just did a fresh install of 12.04 Alpha 2 on my laptop, and am experiencing the same problem: the only outputs available are digital (HDMI), no analog. Like you, I'm not interested in HDMI.

I tried editing the file you mentioned in your previous post, and neither of the example lines worked for me. I also tried a few of the lines from the output of aplay -L, and none of them worked, either.

Any insight into how to make Ubuntu see my good old analog outs?

Thanks in advance!

-Mark

Dunno. I just did a fresh install for the hell of it, and my sound now Just Works[SIZE="1"]™[/SIZE]. I'll have a look at my /etc/pulse/default.pa later to see if it will offer a hint.

---

