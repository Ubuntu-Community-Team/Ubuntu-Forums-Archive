---
title: "realtime kernel?"
date: 2008-01-24
forum: System76 Support
---

### Post by darkbob9 on 2008-01-24
Has anybody tried installing a realtime kernel on a serval?  I installed one just fine, but then I had no sound.  What should I do to get the system76 driver installed in that new kernel?

---

### Post by thomasaaron on 2008-01-25
Can you give more information on the kernel you're using? I don't have much experience with realtime kernels.

You can crack open the System76 driver and look in the sound.py file to see what we do for your computer model.

Basically, though, it boils down to compiling ALSA 1.0.15rc3 against the kernel and then adding this line to the bottom of /etc/modprobe.d/alsa-base:

options snd-hda-intel model=toshiba

---

### Post by darkbob9 on 2008-01-25
> **thomasaaron said:**
> Can you give more information on the kernel you're using? I don't have much experience with realtime kernels.

You can crack open the System76 driver and look in the sound.py file to see what we do for your computer model.

Basically, though, it boils down to compiling ALSA 1.0.15rc3 against the kernel and then adding this line to the bottom of /etc/modprobe.d/alsa-base:

options snd-hda-intel model=toshiba

The kernel I'm using is the one that shows up when you do:

apt-get install linux-rt

It looks like it is 2.6.22-14-rt

I went to the system76 driver application, and asked it to install
the drivers, and now my sound works again (it looked like it
did some apt-getting and driver compilation and other such
things).

The wifi also works just fine under this -rt kernel.  Now it's
time to try playing with jack and hydrogen and some other
fun toys.

---

### Post by steveneddy on 2008-01-27
I've had mixed experiences with that kernel.

Let me know how your installation works.

I do like the sound and performance on that kernel.

---

### Post by darkbob9 on 2008-01-27
> **steveneddy said:**
> I've had mixed experiences with that kernel.

Let me know how your installation works.

I do like the sound and performance on that kernel.

I haven't had any issues yet (except for the wireless issue that
happens once in awhile and has been reported by others on 
this forum already).

If anybody who hasn't managed to get jackd working well yet
happens to find this thread, my settings in qjackctl are:

realtime checked
priority 70
frames/period 128
sample rate 44100

and the most important one for getting low xruns and decent
(although still not as great as I would like) latency:

Periods/buffer: 3

these seem to work well enough to play around with midi
on the serp3.

---

### Post by studiesinsound on 2008-02-08
thanks for this info.
however, i note you said priority is 70.
Is that the priority from with the setup window in jackcontrol?
or are you setting the priority in system-preferences-sessions, after launching jack control

---

### Post by darkbob9 on 2008-02-09
> **studiesinsound said:**
> thanks for this info.
however, i note you said priority is 70.
Is that the priority from with the setup window in jackcontrol?
or are you setting the priority in system-preferences-sessions, after launching jack control

That's with the priority set in qjackctl.

I've also managed to get this working with the M-AUDIO usb fast track pro external sound card.  I can read directly from the inputs from the maudio card, and set jack to output to the built-in soundcard.

---

