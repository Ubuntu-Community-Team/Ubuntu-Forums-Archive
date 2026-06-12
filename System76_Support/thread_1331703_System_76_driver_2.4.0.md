---
title: "System 76 driver 2.4.0"
date: 2009-11-19
forum: System76 Support
---

### Post by awoade on 2009-11-19
So the only way that the System 76 driver is working for me is if it's 2.3.9 . But my computer keeps wanting to upgrade it to 2.4.0 - which doesn't help in the restoration of my sound or touchpad in 9.10 .  Are other people having a problem with 2.4.0?  Is it just me?  Is there a way to take 2.4.0 out of the repositories so that it's not bothering people if this is a problem?

Thanks!  You guys are always so great whenever I have an issue!

---

### Post by marshmallow1304 on 2009-11-19
Edit:  Just noticed you're on Kubuntu.  In that case, I haven't a clue how to lock versions.


Open up Synaptic and find the system76-driver package.  Select it, then do Package->Lock Version.

However, I wasn't aware that updating the driver actually does anything unless you run it.  Perhaps someone else will be able to clarify.

---

### Post by awoade on 2009-11-19
Synaptic is installed on my Kubuntu, (probably because I went through my original Ubuntu to add the Kubuntu to my machine) so that fix should work!  Thanks!

---

### Post by thomasaaron on 2009-11-20
If not, you can remove System76's repo from your Software Sources. Then it won't search our repos for updates.

---

