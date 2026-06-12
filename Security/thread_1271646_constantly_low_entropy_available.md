---
title: "constantly low entropy available"
date: 2009-09-21
forum: Security
---

### Post by dreamingdarkness on 2009-09-21
Hopefully I have the right forum for this -
I'm going to be generating a few encryption keys in the near future, and research shows that entropy available is a key component in ensuring there is enough randomness to make the keys harder to determine.

In /proc/sys/kernel/random, I've been checking entropy_avail and it seems consistently low - mouse and keyboard usage manage to keep it up over 100, with occasional spikes as high as 250, or intensive mouse-movement running possibly up to 400 or so. 

When I first added entropy_aval monitoring to my .conkyrc for conky, the entropy_avail would drive as high as 2000-3500 with constant mouse and keyboard use. 

I am not certain what package I have since installed may be creating a constant drain on the entropy pool, which has a max size of 4096. 
Is there any way to tell what is pulling all the entropy out of my system, so that I can ensure these keys are as secure as possible in terms of the quality of the random number generation? 

Any thoughts would be appreciated.

---

### Post by Lars Noodén on 2009-09-21
Some motherboards have devices specifically added for random number generation, get one.

Or, 

It might be possible to kludge something from audio, video, wifi or bluetooth. e.g.

[http://www.freewebs.com/pmutaf/iwrandom.html](http://www.freewebs.com/pmutaf/iwrandom.html)

---

### Post by __p1n__ on 2009-09-21
OpenPGP has you type random crap until a sufficiently high level of entropy is achieved and maintained and the target keypair generated.  You may care to imitate this as a counter-measure.

---

### Post by dreamingdarkness on 2009-09-21
Hmm, sadly that seems like the only batch of options. I'll have to look into the video/audio entropy, since my available entropy remains pretty much spoken for. 
The machine I was testing/setting this up on is a laptop, so motherboard replacement's not in the cards.

Thanks for the feedback Lars, p1n. Kludge may be the answer. Amusingly, firefox seems to suck down a lot of the entropy. I may have to set up some tests with successively fewer processes starting on the machine until I find  the ones that're entropy-hogs.
Back to experimentation! Thanks again :)

---

