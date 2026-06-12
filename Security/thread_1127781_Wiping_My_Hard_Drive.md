---
title: "Wiping My Hard Drive"
date: 2009-04-16
forum: Security
---

### Post by ki4jgt on 2009-04-16
I have Ibex/8.10 and I'm planning on selling my laptop. I wanted to wipe the hard drive first so my personal information wouldn't fall into the wrong hands.

---

### Post by ddrichardson on 2009-04-16
```
dd if=/dev/random of=/dev/sdX
```Where sdX is the drive you want. Need to do it from a LiveCD though.

I'm sure someone can quote a more secure method, or it could be done multiple times. In my work we destroy the drives.

---

### Post by slowth5 on 2009-04-16
The only way to be absolutely sure is to destroy it.  That scenario is impractical on occasion.  I'd say two random writes would be sufficient.

On the other hand, according to the 2006 NIST Special Publication 800-88 (p. 7): "Studies have shown that most of today&#8217;s media can be effectively cleared by one overwrite" and "for ATA disk drives manufactured after 2001 (over 15 GB) the terms clearing and purging have converged."  

NIST says one, but I'll take it one step further because that's the way I am.  The example ddrichardson provided should be very secure, but it might take a long time (>24h).

---

### Post by Windsurfer619 on 2009-04-16
I've done that before on a 260GB 5400 rpm drive. It took about 5 hours. It should be plenty.

---

### Post by HermanAB on 2009-04-16
Instead of /dev/random, you should use /dev/urandom (much faster), or /dev/zero (fastest).

---

### Post by Thelasko on 2009-04-17
I always use [DBAN]("http://www.dban.org/"), as it works regardless of operating system.

---

