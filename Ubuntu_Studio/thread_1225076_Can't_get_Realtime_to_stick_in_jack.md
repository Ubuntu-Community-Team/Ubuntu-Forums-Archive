---
title: "Can't get Realtime to stick in jack"
date: 2009-07-28
forum: Ubuntu Studio
---

### Post by chuck_notorious on 2009-07-28
Hi guys,

I wonder if anybody has any suggestions of things I could try to get realtime working in jack.

First of all, the kernel in linux-rt won't boot on my system *at all*. It really doesn't work. 

So I installed Ubuntu Studio from a plain Jaunty install and have been messing around compiling kernels and trying other people's realtime kernels.

I have a realtime kernel that will boot but I haven't had any success getting jack to run in realtime mode. When I start jack from qjackctl the little "RT" light alternates between on and off and I get siginificant Xruns. So it's not working.

I've amended limits.conf, created an "audio" group and added my user to it.

Any suggestions? I've heard that the limits.conf file might not work but I don't know how to work around that.

My system is brand new: AMD Athlon 5050e on a Gigabyte MA78GM-US2H with 4GB RAM. For the sound card, I've tried the onboard audio as well as a USB Edirol UA-20 which both work under ALSA.

Thanks for any help!

--Charles.

---

### Post by trulan on 2009-07-28
Well, good news, the RT light is supposed to blink.  That part is working.

And of course you are not supposed to get xruns.  What are your settings in qjackctl, especially the buffering settings?

---

### Post by chuck_notorious on 2009-07-28
hey trulan,

Thank goodness the light is supposed to blink. At least *something* is working!

Jack Settings:
Realtime: Y
Everything else: N

Priority: (default)
Frames/Period: 128
Sample Rate: 44100
Periods/Buffer: 2

Port maximum: 256
Timeout: 500

I've tried with various frames/period settings and it is a bit more reliable with higher settings, but I'm really trying to keep the latency below 10ms. 

Thanks for your help!

--Charles.

---

### Post by Grishka on 2009-07-28
[look](https://help.ubuntu.com/community/UbuntuStudioPreparation#Real-Time%20Support).

---

### Post by sgx on 2009-07-28
Hi, Chuck_N, try not to worry too much about statistical latency, (a defacto fantasy in the world of windoze DAW maintainers) but rather, audible latency. If you can record multiple tracks without audible timing issues, the latency numbers are reduced in their 'buzz-value', to becoming indicators of possible good configuration, rather than predictors of a certain quality of recording. Keeping it simple, and recording something every day, is the best advice I can offer. Your new
computer should be an awesome powerhouse soon, so keep asking, as linux is a fast moving target, and we all learn continually, or get crushed by the juggernaut, then rising again like a Phoenix, to learn even more!
Cheers

---

### Post by trulan on 2009-07-28
I've never messed with any USB sound cards, but I've had little success with onboard sound cards and Jack.  I use a firewire device (presonus firepod) and can easily get my latency below 10ms (as low as 2.18 with a 32 frames 3 periods, but it's not very stable at that.  I usually record at 128 frames 2 periods.  Also, the firepod adds around 5-6ms to the latency shown in qjackctl, so my actual measured round trip latency when recording comes in at something like 11 ms.)  I expect USB will lag a bit more than firewire, as it doesn't have as direct of a channel to the processer.

Like sgx said, while recording,  latency is pretty much a non-issue, especially if you are using Ardour, because it will automatically compensate and align the waveforms properly.  For live sound processing, effects and such, it's a bigger deal because you could actually hear it.  But if you're recording you really can't afford to be having x-runs.  Stability is far more important than the latency numbers.

---

### Post by chuck_notorious on 2009-07-28
Thanks for your suggestions and advice guys, I really appreciate it.

Ok, for now, I can get stable performance from the onboard sound by setting a pretty high buffer. I'm going to give up on the Edirol card... it has really poor sounding outputs... very annoying. I often use a Presonus Firepod (borrowed from university) so I might give it a go with that soon and see what happens. It's a great piece of equipment!

BTW, Grishka - yes I've followed the advice from that wiki page. There's great material on the wiki, I always learn a lot!

--Charles.

---

