---
title: "Realtime-kernel and multiuser-environment"
date: 2010-05-01
forum: Ubuntu Studio
---

### Post by G-Sun on 2010-05-01
Hi!
What's the thing about realtime-kernel and multiuser-environment.
Is this why I get a black screen when switching user?
Do I have to run realtime-kernel for Jack?

(My system tells me I'm using "Kernel Linux 2.6.32-21-generic". So, I'm not running realtimekernel now?)

Thanks!

---

### Post by cub on 2010-05-01
> **G-Sun said:**
> Hi!
What's the thing about realtime-kernel and multiuser-environment.
Is this why I get a black screen when switching user?
Do I have to run realtime-kernel for Jack?

(My system tells me I'm using "Kernel Linux 2.6.32-21-generic". So, I'm not running realtimekernel now?)

Thanks!
Then you are using the standard kernel. As for Jack I'll the more expert people answer that.

---

### Post by sgx on 2010-05-01
Hi, a kernel with RT or PREEMPT in the name indicate it will perform
better in critical audio situations, when the system is configured to use it. jackd does not rquire them, but will benefit.

You can get an idea what your current limits will be with
a good old torture test:
load zynaddsubfx, and begin enabling its
16 multi-timbral parts. (look right above the 'Edit Instrument' button, the number 1 and a tick-marked 'enable'  change this to 2, and retick the enable box, and on the right of the screen, change the midi channels all to 1 as you go, to hear all the instruments, and keep loading more...Pick a sound you like, play a 6  or more finger chord, and hold the sustain pedal, add sound 2, and repeat the chord-sustain, before long, you'll see where things max out.

Another torture is to get the gscw drumkits for hydrogen, and build an extremely complex rythm to enjoy with the keyboard test

Add in Rakarrack for each, and you'll also add a little more cpu
stress.

Doing the same test with an RT kernel will let you go much deeper before
maximum sound is achieved, and I suspect the PREEMPT kernels are similar,
I've been using one for a week now, and have no complaints. 

Sometimes when a 3D driver is installed, and multiple kernels are  installed, and the video only works on the kernel available to it when it was installed. 

Multi-user, does that mean you and root, or you and root and a 3rd user account? A 3rd user might not be included in the audio group, or other needed groups, just a guess?

Cheers

---

### Post by G-Sun on 2010-05-02
> **sgx said:**
> 

Multi-user, does that mean you and root, or you and root and a 3rd user account? A 3rd user might not be included in the audio group, or other needed groups, just a guess?
Cheers
Thanks a lot!
Multi-user: Me, root and 3rd user.

PREEMPT: What's that? Is it for 10.04?

---

