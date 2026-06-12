---
title: "No sound from Behringer UCA202"
date: 2010-02-10
forum: Ubuntu Studio
---

### Post by acidblue on 2010-02-10
I bought a Behringer UCS202 because every review I read said it works out of the box on linux.

Even though it is listed under the Hardware tab in sounds preferences, I can't get any sound from it.
Not sure what i  should do.
Can anyone give me a clue?
Using Karmic 9.10 64 bit

---

### Post by cchhrriiss121212 on 2010-02-11
If you are hoping to use this for music production you should perhaps look into Ubuntu Studio as it is easier to get up and running than a plain install.
Alsa mixer will give you best control of your levels. There is a nice GUI for it in synaptic. 
Have you tried starting up jack? Try that out and post what happens.

---

### Post by acidblue on 2010-02-11
Ubuntu studio won't run on my hardware.
The rt kernel is just too damn unstable.

Ive tried running Jack, but no dice.
Jack starts, but still no sound.

---

### Post by AutoStatic on 2010-02-11
> **acidblue said:**
> Ubuntu studio won't run on my hardware.
The rt kernel is just too damn unstable.I beg to differ, 2.6.31-9-rt is pretty solid. What is unstable about it? And what messages do you get when you start JACK? With which parameters do you start JACK?
And from the Behringer site: > Works with your PC or Mac computer&#8212;no setup or drivers required.
So it's most probably a class-compliant USB1.1 device that should work out of the box.
Could you post the outcome of **aplay -l** with the UCA202 attached?

---

### Post by acidblue on 2010-02-11
> **AutoStatic said:**
> I beg to differ, 2.6.31-9-rt is pretty solid. What is unstable about it? And what messages do you get when you start JACK? With which parameters do you start JACK?
And from the Behringer site: 
So it's most probably a class-compliant USB1.1 device that should work out of the box.
Could you post the outcome of **aplay -l** with the UCA202 attached?

rt kernel is unstable period.
Ubuntu studio refuses to run on my machine.
I get a whole list of error's when the rt kernel tries to load.
Can't remember what they were, but I tried several times to get it
running.
It always gives me a command prompt at the end, I have to do "startX"
But it loads the default kernel, not the rt kerel.

Any way here is the output of aplay -l:
**** List of PLAYBACK Hardware Devices ****
card 0: CK804 [NVidia CK804], device 0: Intel ICH [NVidia CK804]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CK804 [NVidia CK804], device 2: Intel ICH - IEC958 [NVidia CK804 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: default [USB Audio CODEC ], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by AutoStatic on 2010-02-12
> **acidblue said:**
> rt kernel is unstable period.
Ubuntu studio refuses to run on my machine.
I get a whole list of error's when the rt kernel tries to load.
Can't remember what they were, but I tried several times to get it
running.
It always gives me a command prompt at the end, I have to do "startX"
But it loads the default kernel, not the rt kerel.So the RT kernel tries to load, gives errors and in the end the default kernel gets loaded? Or am I misinterpreting the above? The generic Karmic kernel is pretty suited for multimedia stuff also so it shouldn't make any huge difference that the RT kernel doesn't want to run on your machine.


> **acidblue said:**
> card 2: default [USB Audio CODEC ], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0Thanks for the aplay info! The UCA2020 has hardware ID 2 and ALSA device name 'default' so in QjackCtl you should set Interfaces on 'hw:2' or 'hw:default' and then try starting JACK again.

---

### Post by acidblue on 2010-02-13
Thanks that worked.

---

