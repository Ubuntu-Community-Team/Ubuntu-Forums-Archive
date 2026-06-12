---
title: "rt kernel fail to resume"
date: 2009-06-27
forum: Ubuntu Studio
---

### Post by Rog-Mahal on 2009-06-27
I recently upgraded to Ubuntu Studio 9.04 on my Macbook 2,1. Everything is working great so far, except for the rt kernel.

I guess my first question is: do I need the rt kernel? I've read some things about multicore processors and things like ext4 (which I'm using) that cut down on latency anyway.

Anyway, to the actual problem: My computer goes to sleep without a problem, but when I try to resume I get a few errors, the last of which is "USB 5-1 failed to initialize" or something like that. If it's referring to the same designation as lsusb, that means my whole usb hub isn't reinitializing.

I know the rt kernel is notorious for issues, but does anyone have a fix for this?

Thanks a lot!

---

### Post by kayosiii on 2009-06-28
The stock kernel from 2.6.28 onwards is pretty descent latency wise. You will of course get better latencies from the realtime kernel but as you can see there are trade-offs. 

For a dedicated audio rig rt is generally worth it. In your case it might not be.

---

### Post by raboofje on 2009-06-28
> **Rog-Mahal said:**
> My computer goes to sleep without a problem, but when I try to resume I get a few errors, the last of which is "USB 5-1 failed to initialize" or something like that. I know the rt kernel is notorious for issues, but does anyone have a fix for this?

I'm also having trouble with suspending with the -rt kernel.

For now, I just reboot for audio/rt work and shutdown afterwards, but a good method for debugging suspend issues would be quite welcome.

I believe for me the screen remains blank when resuming.

---

### Post by Rog-Mahal on 2009-06-28
Ok, I guess rebooting into rt works for now. Has anyone custom compiled a more recent kernel with rt patches? I wonder if that might be a way to get around some of these compatibility issues. I guess another question would be: is it worth it to use an rt kernel every day?

---

### Post by raboofje on 2009-06-29
> **Rog-Mahal said:**
> is it worth it to use an rt kernel every day?

It can't hurt (except when you're experiencing issues like suspend not working), but the only real advantage is you don't need to reboot when you want to perform timing-critical tasks.

---

