---
title: "Ardour+Hydrogen: tempo change restarts hydrogen song"
date: 2010-08-12
forum: Ubuntu Studio
---

### Post by decomp on 2010-08-12
Hello,

I've recorded a guitar tune in Ardour and I am now composing drums to it in hydrogen.. but for some reason hydrogen keeps jumping back to the beginning of the song. It always happens at the same place and it coincides with a tempo change in Ardour. 

Ardour is set as transport master, and jack transport is turned on in Hydrogen. If i remove the tempo change in Ardour, hydrogen stops jumping back to the beginning. Hydrogen also stops jumping back if I just play hydrogen by itself (without ardour running.) any ideas?

---

### Post by decomp on 2010-08-14
update: 

I downloaded downloaded the hydrogen 0.9.5 beta package, which supports tempo changes. IF I define all tempo changes in hydrogen, and remove all tempo changes from ardour, everything works. But I would like to be able to define tempo changes in ardour for ease of editing.

So, found a work around, but still looking for a solution. :popcorn:

---

### Post by decomp on 2010-08-14
Simple: use hydrogen as time master instead of ardour. now that 0.9.5 can do tempo changes, it's all good. I've had one crash so far so I'll be sure to save often, run in a terminal and report reproducible bugs.

---

### Post by AutoStatic on 2010-08-14
Yeah Hydrogen is a bit unpredictable when it comes to syncing. Apparently it prefers being a JACK master. I've ran into similar problems and communicated it with the current devs, I think it boiled down to JACK transport issues.

---

