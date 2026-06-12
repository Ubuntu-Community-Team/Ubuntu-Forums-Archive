---
title: "[SOLVED] More RAM is bad?"
date: 2008-10-20
forum: Server Platforms
---

### Post by skathrein on 2008-10-20
I am running Ubuntu Server (8.04) with two 1 GB sticks of RAM for a total of 2GB.  Does anyone have a guess as to why it takes 30-40 minutes to load (literally) with 2GB of RAM, but if I pull one stick out leaving only 1GB, it loads within minutes?  Thanks for your help.

P.S.  I've tried running with each stick and it doesn't matter so I'm pretty sure the RAM isn't bad.

---

### Post by Dr Small on 2008-10-20
Have you tried the RAM in the *second* slot? It almost sounds like a bad slot, but who knows. I know for certain that the system should not boot slower with more RAM.

---

### Post by skathrein on 2008-10-20
Possibly a bad slot, except the computer registers 2 GB at the initial start (BIOS).

UPDATE:  Tried each stick in each slot and computer boots normally as long as I only have one in.  So slots and RAM seem ok.  It is just a problem if I have both in.

---

### Post by cariboo on 2008-10-20
You didn't mention what type of ram, but it looks like you have two mismatched ram modules.

Jim

---

### Post by skathrein on 2008-10-21
Turns out it wasn't the RAM, it was the BIOS.  I posted my solution [here]("http://ubuntuforums.org/showthread.php?t=953864").
Thanks everyone.

---

