---
title: "Microphone with Virtualbox host and Win7 guest?"
date: 2016-08-25
forum: Virtualisation
---

### Post by asearle on 2016-08-25
Hallo Everyone,

I have a VirtualBox (5.1.4) host with Win7 guest. All current updates installed.

Everything works fine including audio out. And the microphone seems to be detected and working (on the guest). But no sound is received which seems to be very strange. I have looked all over for a potential "mute" setting (which might be stopping it) but can't seem to find anything.

Can anyone help me with this: I need to create some demo screen-recordings and it is pretty critical that I get it working.

I hope it is just a setting/switch which I have missed.

Many, many thanks,
Alan

---

### Post by &amp;KyT$0P# on 2016-08-25
How are you determining that it's detected and working in the guest?

---

### Post by asearle on 2016-08-26
When I go into audio settings in Windows I see everything recognised and allocated drivers.

Here the audio (out) works but the microphone does not.

I opened up the microphone set-up tool (in Windows) and could click through but no sound appeared (i.e. the bar didn't move).

Many thanks for any tips you have.

Yours,
Alan

---

### Post by &amp;KyT$0P# on 2016-08-26
Does the mic work on the host?
Do you have PulseAudio and pavucontrol installed on your host?
What host audio is the VM set to use?

---

### Post by asearle on 2016-11-23
Many thanks Halogen2, yes, I got it working by doing the following ...

I installed Pavu (pulse audio control) and could then see which devices were available.

Under record I could see "VirtualBox: PulseAudio (In)" which was set to "Monitor of Internal Audio Analagoue Stereo" and found that, when I changed this to "Internal Audio Analogue Stereo" then the microphone became available within the guest system (Windows 7). Excellent!

Many thanks for the tip.

Yours,
Alan

PS: One of the reasons for me needing this is that some of my contacts on Skype need to show me their screens and/or have conference calling. Neither of these seem to work (properly) with the Linux version of Skype (conference doesn't work and screen-sharing is too low resolution to be useful). I believe that Microsoft has simply pulled or withheld these features from the Linux version of Skype. Is this true?  Are they using a partial "denial of services" to try to pull people away from Linux?

Anyway, now I can use Skype on Windows through VirtualBox so have managed to bypass the problem. But it is still highly irritating.

---

