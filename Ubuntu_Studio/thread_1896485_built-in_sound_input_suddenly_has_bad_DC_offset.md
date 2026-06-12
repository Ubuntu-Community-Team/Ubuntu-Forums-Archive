---
title: "built-in sound input suddenly has bad DC offset?"
date: 2011-12-17
forum: Ubuntu Studio
---

### Post by dewdrop_world on 2011-12-17
This one seems quite odd -- I don't know how to explain it. (Note -- I'm talking a lot about voice recognition, but *this problem is not specific to voice recognition*. It's an audio problem that I can observe in other software -- posting under Ubuntu studio because I'm also using jack.)

I depend a lot on voice recognition (Dragon NaturallySpeaking) to write e-mails etc. In Linux, I run jack 1.9.6 with the kx-studio pulse-jack script to connect to pulse audio*, which allows me to run winxp inside virtual box NaturallySpeaking in that virtual machine. (I tried NaturallySpeaking under wine, but it was a disaster.) This setup worked really well for about a year and a half. Then, last week, recognition accuracy went from 95% to about 2%.

* I know pulseaudio sux for a pro-audio system, but virtualbox doesn't have good support for any other audio backend (according to some vbox forum threads stating that pulse is the only fully supported framework). So, sadly, I can't dump pulse.

So I tested a bunch of stuff related to audio:

- Try a shure sm57 --> m-audio fast track pro, instead of the headset mic I had been using (plugged into the laptop's built-in audio input). Near-perfect recognition -- so, definitely something wrong with the headset mic signal.

- Try the headset mic after booting into the Windows 7 partition. No problem.

- Record a few seconds of audio from the headset mic in windows and Linux. Image attached. In Linux, there is noticeable DC offset (which would mess up NaturallySpeaking's threshold detection if it doesn't rectify the signal first) and the signal-to-noise ratio is really dramatically lower. (In Linux, the recording comes from jack's system_capture --> SuperCollider in0 -- pulse was not involved in this recording at all. It's pure alsa --> jack --> sc --> disk file.)

- Switch the signal flow to have headset mic --> SuperCollider running *{ LeakDC.ar(SoundIn.ar(0)) ! 2 }.play(outbus: 0);* --> pulseaudio jack source. Dictation accuracy magically improved, though not to the level before the problem (because this only tweaked the DC offset, not the SNR).

Unfortunately, I don't have a recording from the headset mic in Linux before the problem started. But, dictation performance was comparable between the Linux and Windows partitions, so I suppose that somehow, the built-in input signal changed a lot in Linux and not in windows.

Any ideas how that could happen? Recent updates to alsa or lower-level audio handling? I suppose another theory could be that something broke in the built-in soundcard, and Windows has some DSP magic to compensate -- but that seems really far-fetched to me. (If the hardware signal really does suck as much as the second track in the image, it's hard to see how it could be corrected.)

Ubuntu 10.04 2.6.33-29-realtime, amd64, running on an MSI laptop, intel core i3.

Any ideas would be welcome. It's a viable temporary workaround to use the shure mic at home, but that solution doesn't travel well.

Thanks --
James

---

