---
title: "Audio Signal Problems.  Guitarix Jack and Ardour.  Line 6 TonePort UX-1 working."
date: 2012-08-28
forum: Ubuntu Studio
---

### Post by MentatGhola on 2012-08-28
After an upgrade to precise, my toneport works almost out of the box.  I  just had to install QasMixer and check PCM Capture Source and select  instrument.  Thanks to [M1szcz]("http://ubuntuforums.org/member.php?u=1720904")  for the advice.  There is only system playback in the right ear which I  think is the default setting for a mono signal, not sure how to change  this.

My main problem is that I can't seem to get jack to route an audio  signal to any software (except audacity, which hears and records my mono  signal fine with great split playback).  This includes Ardour,  Rosegarden, Rakarrack and Guitarix.  I have tried what I believe to be  all relevant routing combinations in jack.

Guitarix only hears my laptop mic, the audio interface isn't listed in guitarix settings only system audio(though my system i/o are both set to my interface... so this may be part of the problem, since my system mic is working)

Ardour and rosegarden don't seem to have and selections to choose an input device.  I am perpelexed.

---

### Post by CrocoDuck on 2012-08-29
Hi. Have you tried to set up Input and Output devices in the setup tab in Qjackctl?

---

### Post by MentatGhola on 2012-08-29
yes, they are set to default.  I tried a few combinations that seemed sensible.  Maybe I should be selecting system i/o's in some combination rather than my hardware i/o's but I think I tried that.  I will play with it some more but I'm going out of town and I wont be able to reply for a week or so.

---

### Post by CrocoDuck on 2012-08-30
If you want to do a last try with input and output devices settings,  probe the plugged audio devices with:

```
cat /proc/asound/cards
```and then try to set the input and output devices  in Qjackctl as you need.

What about the connection tab in Qjackctl? Does it shows the right inputs and outputs?

---

