---
title: "Encryption key-fil"
date: 2008-02-06
forum: Server Platforms
---

### Post by hyper_ch on 2008-02-06
Hiho

I just wonder if key-files for unlocking encrypted devices should have any specific properties. Like a minimal filesize or maximal one. Should it be a text document or binary file or an image....

So far I have not given much thought yet for using a key-file.

As I have currently 4 harddisks fully encrypted it would be nice if I only had to unlock the primary one during boot with entering the password. All others can then be unlocked through the key-file(s) subsequentially.

---

### Post by euler_fan on 2008-02-06
> **hyper_ch said:**
> Hiho

I just wonder if key-files for unlocking encrypted devices should have any specific properties. Like a minimal filesize or maximal one. Should it be a text document or binary file or an image....

So far I have not given much thought yet for using a key-file.

As I have currently 4 harddisks fully encrypted it would be nice if I only had to unlock the primary one during boot with entering the password. All others can then be unlocked through the key-file(s) subsequentially.

No matter how a keyfile works with your encryption system, it really needs to have two attributes:

1) hard to guess--otherwise what was the point?
2) replaceable--it would be really bad to lose access to all that data forever.

Size-wise, as large as your hd encryption software can handle. In terms of content, I'd say go grab a bunch of random noise somewhere reputable. Where exactly I'd leave to someone with more experience in PRN generation. As I understand it, so long as you know the seed and have the same implementation of the same algorithm (to be safe), you can recover the random digits. The point is high entropy.

Or just make a few copies to CD and stash them different places where no one will find them.

---

### Post by hyper_ch on 2008-02-07
well, with luks/dm_crypt you can add multiple passwords and key-files for unlocking.

I just thought I might be using a key-file on an encrypted drive to unlock the others.

---

