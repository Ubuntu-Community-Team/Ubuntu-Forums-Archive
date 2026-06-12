---
title: "Problem suspend when lid closed"
date: 2009-06-19
forum: System76 Support
---

### Post by jmwink on 2009-06-19
Just closed the lid on my gazu1 and got a weird screen full of errors, and the fan just ramped way up fast. Dunno what happened, or if it will happen again, but I'm going to post my logs file to see if anyone can troubleshoot this to see if it's a predictable problem, or a once-off.

---

### Post by thomasaaron on 2009-06-19
This error...

*ERROR* trying to get vblank count for disabled pipe 0

...shows that something glitched and X crashed. There are a couple of bug reports that show that error.

Make sure you're updated and see if it happens again before we start digging into it.

---

