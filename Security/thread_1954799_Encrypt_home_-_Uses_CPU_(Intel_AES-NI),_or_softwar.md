---
title: "Encrypt /home - Uses CPU (Intel AES-NI), or software?"
date: 2012-04-08
forum: Security
---

### Post by lookitseman on 2012-04-08
I use a Core i7 which supports on-chip AES encryption.

When I installed Ubuntu, I chose to encrypt /home.

Is there any way to determine if Ubuntu is taking advantage of the hardware encryption, or using software-based encryption?

More important (possibly), if anyone has any experience in this area, about how much faster is hardware-based encryption vs software-based.  I saw some results from the Intel site, but I'm looking for something from someone who doesn't work at Intel.

---

### Post by Paddy Landau on 2012-04-09
At the moment (sorry, I've lost the reference), Ubuntu does not use hardware encryption because, surprisingly, it slows Ubuntu down.

I believe that the developers are looking into the issue.

---

### Post by lookitseman on 2012-04-11
Well that's good to know, actually

I'm looking to encrypt part of a drive on another computer whose CPU doesn't support AES-NI.  At least I know it can't be much slower than encrypting/decrypting on my current laptop.

---

### Post by Paddy Landau on 2012-04-11
> **lookitseman said:**
> I'm looking to encrypt part of a drive on  another computer whose CPU doesn't support AES-NI.  At least I know it  can't be much slower than encrypting/decrypting on my current  laptop.
Well, that depends on the CPU, of course. However, an older laptop that I  have appears to run just as fast on one (encrypted) user as on another  (unencrypted) one.

If this answers your question, please [mark it as solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads").

---

### Post by Hungry Man on 2012-04-11
The bottleneck for disk encryption is nearly always the disk and not the CPU. You won't see much difference between AES/ non-AES.

---

