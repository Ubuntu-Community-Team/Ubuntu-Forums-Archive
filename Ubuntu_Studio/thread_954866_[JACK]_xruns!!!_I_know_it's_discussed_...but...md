---
title: "[JACK] xruns!!! I know it's discussed ...but.."
date: 2008-10-21
forum: Ubuntu Studio
---

### Post by kakyoism on 2008-10-21
I tried to run Jack for the first time by following this link
[http://www.ubustu.com/globe/2007/05/29/how-to-configure-jack-in-ubuntu-studio/]("http://www.ubustu.com/globe/2007/05/29/how-to-configure-jack-in-ubuntu-studio/")

But I just can't get rid of the xruns, no matter how I switch between 44.1khz and 48khz samplerate, raise priority to 70-80, tuning the buffer size, time-out.... switching between my USB SB Live! 24bit and my built-in Intel soundcard on my Sony Vaio. I'm running the latest -rt kernel of Hardy, i.e. kernel 2.6.24-21-rt

The xruns just flush out my jack and cause the qjackctl interface dead.

I read a lot of pages regarding this issue and they all claim that tuning the setup can solve the problem in favor of my own hardware. But so far I'm totally lost here after trying with numerous parameter combination here. 

Help!!!

---

### Post by thorgal on 2008-10-21
have you tried the number of periods per buffer ? Intel HDA is more stable with 3. But increasing this number of course increases your latency, if you're after low latency.

The other thing, if it's not a jack server tweaking, is your hardware. Are you sure you do select the right hardware ? I remember a year ago, I had my onboard chip alternatively hw:0 and hw:1 after reboots and I didn't know. Very annoying. I fixed the problem by assigning an explicit index to each sound card in /etc/modprobe.d/alsa-base or something like that, but after a few days, I just disabled my onboard chip in the bios, totally useless anyway.

Last thing I can think of : IRQ sharing or unfriendly mobo (e.g. VIA).

---

### Post by kakyoism on 2008-10-21
Thank you!!
Yeah, setting period to 3 does the trick!!
Now I think what stops xruns for me with my hardware is 


Frames/Period: 256
Periods/Buffer: 3

Other non-essential settings that I use for now:
Priority: 80
Sample rate: 44100 or 48000
Timeout: whatever
Realtime: checked
Monitor: checked

---

### Post by andrewkk on 2008-10-25
Wow, that fixed it. ThinkPad X60.

---

