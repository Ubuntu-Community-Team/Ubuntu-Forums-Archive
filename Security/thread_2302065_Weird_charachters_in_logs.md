---
title: "Weird charachters in logs"
date: 2015-11-07
forum: Security
---

### Post by cogset on 2015-11-07
After having some hardware issue in Ubuntu 15 (a temporary failure of the video card, cured by contact cleaner) I've had to brutally shut down the system using the power button (since there was no display at all) .

Right after that, on the next reboot I've seen weird strings in my logs (syslog, kern.log and auth.log) consisting in long sequences of these characters```
 ^@^@^@^@^@^@
``` 
is that perhaps a consequence of that issue above? 

One thing to mention is that after having halted the system and then restored the video card functionality, I've run a filesystem check from another OS and it did something along the lines of "recovering the journal" , and then the very first reboot didn't go smoothly at all: grub threw an error about "reading outside the partition" or something like that, and I had to use the REISUB trick to restart the system.

After that, everything looks back to normal, aside of that anomaly in the logs (which I think more or less  matches the time of the forced shutdown) .
What do you think?

---

### Post by cogset on 2015-11-10
Any hints here? Has anyone ever run into this before? Is that possibly just some rummage left behind by the forced shutdown/fsck that I've explained earlier ?

---

### Post by matt_symes on 2015-11-12
Hi

No idea about the strange characters in your log file (never seen that before) but....

> brutally shut down the system using the power button ... REISUB trick

Use REISU**O** to switch the machine off instead of rebooting. 

It should work as long as there is no serious kernel panic and the machine has not totally locked up.

Kind regards

---

### Post by Habitual on 2015-11-12
> **cogset said:**
> Any hints here? Has anyone ever run into this before? Is that possibly just some rummage left behind by the forced shutdown/fsck that I've explained earlier ?
Actually, I have seen this, but it has been *years*.
I do not recall the cause, but it may have been a b0rked video driver issue that forced a reset/reboot.

I'd say, note the entry and the time and keep it for the "next time" something like this happens.

---

