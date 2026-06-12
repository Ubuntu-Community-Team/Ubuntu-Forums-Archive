---
title: "Having problems installing the rt kernel in 9.10"
date: 2009-11-16
forum: Ubuntu Studio
---

### Post by pkslot on 2009-11-16
As the headline says, i'm having a bit of trouble installing the rt kernel in ubuntu 9.10.

Iv'e used the 8.04 release since it came out. Tried with both 8.10 and 9.04, but installing the tr kernel on the last two has only resulted in major chrashed no matter what i did. So i decided to stick to the 8.04 lts release for obvious reasons.

So the 9.10 release came out and i thought that i'd give it a go, again. But i still have trouble installing the rt kernel properly. So can anyone tell me if i'm doing anything wrong. When installing, i fire up the synaptic and search for linux rt. I'll get the results:

linux-image-2.6.31-9-rt
linux-rt
linux-rt-headers-2.6.31-9
linux-headers-2.6.31-9-rt
linux-headers-rt
linux-image-rt

I'll mark the linux-rt package for installation, and the rest will automatically be added and installed.

When starting up in rt mode, there is really no rt mode, but just the ordinary kernel, installed by default.

This method worked fine under the lts 8.04 release, but not with 9.10, so what am i doing wrong?

---

### Post by luctor on 2009-11-16
You can select which kernel to boot using the arrow keys from the menu loader (grub).

---

### Post by pkslot on 2009-11-16
> **luctor said:**
> You can select which kernel to boot using the arrow keys from the menu loader (grub).

Yes i know, and i've loaded the right kernel, but it's not working properly. When recording audio it very laggy.

---

### Post by AutoStatic on 2009-11-16
> **pkslot said:**
> When starting up in rt mode, there is really no rt mode, but just the ordinary kernel, installed by default.What does **uname -a** say in a terminal when booted with the realtime kernel?

---

### Post by pkslot on 2009-11-16
> **AutoStatic said:**
> What does **uname -a** say in a terminal when booted with the realtime kernel?

It says:

```
Linux peter 2.6.31-9-rt #152-Ubuntu SMP PREEMPT RT Thu Oct 15 05:01:14 UTC 2009 i686 GNU/Linux
```

---

### Post by AutoStatic on 2009-11-16
Looks good, what's so laggy about it then? What is not working properly?

---

### Post by pkslot on 2009-11-16
> **AutoStatic said:**
> Looks good, what's so laggy about it then? What is not working properly?

Well, for an example, when recording audio through audacity, i just get something that most of all reminds me of static noise. But i can hear that it's small bits of what i was supposed to record.

Having tried recording without a rt kernel, i know that this is how it sounds when the rt kernel is not installed, or not properly installed.

Also playing wav and mp3 files, and even aup files made on 8.04 with rt kernel installed, through audacity just seem to lag a little. Mostly in the beginning of playback, but still enough to screw the audio work up.

---

### Post by pkslot on 2009-11-16
Also jack isn't running.

I'll post a screenshot:

---

### Post by AutoStatic on 2009-11-16
> **pkslot said:**
> Well, for an example, when recording audio through audacity, i just get something that most of all reminds me of static noise. But i can hear that it's small bits of what i was supposed to record.

Having tried recording without a rt kernel, i know that this is how it sounds when the rt kernel is not installed, or not properly installed.

Also playing wav and mp3 files, and even aup files made on 8.04 with rt kernel installed, through audacity just seem to lag a little. Mostly in the beginning of playback, but still enough to screw the audio work up.Those issues are all sound related and have nothing to do with the realtime kernel. What are your current settings in Audacity? What soundcard do you have? What does **lspci | grep -i audio && aplay -l && cat /proc/asound/card*/codec* | grep -i codec** in a terminal say? And concerning your JACK issue, did you install UbuntuStudio Controls and configure any permissions? Because now you're not allowed to do any realtime stuff. You could also untick the Realtime option in Qjackctl.

---

### Post by pkslot on 2009-11-16
> **AutoStatic said:**
> Those issues are all sound related and have nothing to do with the realtime kernel. What are your current settings in Audacity? What soundcard do you have? What does **lspci | grep -i audio && aplay -l && cat /proc/asound/card*/codec* | grep -i codec** in a terminal say? And concerning your JACK issue, did you install UbuntuStudio Controls and configure any permissions? Because now you're not allowed to do any realtime stuff. You could also untick the Realtime option in Qjackctl.

This is what i get from:

lspci | grep -i audio && aplay -l && cat /proc/asound/card*/codec* | grep -i codec

```

00:0a.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 07)
**** List of PLAYBACK Hardware Devices ****
card 0: Live [SB Live! 5.1], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdevices: 32/32
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
  Subdevice #8: subdevice #8
  Subdevice #9: subdevice #9
  Subdevice #10: subdevice #10
  Subdevice #11: subdevice #11
  Subdevice #12: subdevice #12
  Subdevice #13: subdevice #13
  Subdevice #14: subdevice #14
  Subdevice #15: subdevice #15
  Subdevice #16: subdevice #16
  Subdevice #17: subdevice #17
  Subdevice #18: subdevice #18
  Subdevice #19: subdevice #19
  Subdevice #20: subdevice #20
  Subdevice #21: subdevice #21
  Subdevice #22: subdevice #22
  Subdevice #23: subdevice #23
  Subdevice #24: subdevice #24
  Subdevice #25: subdevice #25
  Subdevice #26: subdevice #26
  Subdevice #27: subdevice #27
  Subdevice #28: subdevice #28
  Subdevice #29: subdevice #29
  Subdevice #30: subdevice #30
  Subdevice #31: subdevice #31
card 0: Live [SB Live! 5.1], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: Live [SB Live! 5.1], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
cat: /proc/asound/card0/codec97#0: Is a directory
```

I have a soundblaster live soundcard and no i didn't install any ubuntu studio controls. My current settings in audacity is the default settings.

If i might add, when installing rt in 8.04 i didn't set up audacity either, it just worked out of the box when i installed it, as was it with my sound card, it worked too, without altering any settings.

---

### Post by MiCK.ca on 2009-11-20
Audacity can run without realtime. Audacity has it's own "clock" so to speak. if what you hear is static...open your system monitor  system>administration>system monitor  and then click the resources tab. Run audacity. 

Does your CPU max out? does it spike back and forth 'tween 60-70% up to 89-95%? That flux in your CPU with cause static and "drop-outs" or if using Jack you will get x-runs. The "static" occurs when it is at 90% or more. ALL bad. In Jack it can be adjusted via buffers/latency but with audacity...hmmmm someone else might know. i use Ardour to record so can't help you with Audacity.

---

