---
title: "AES Security w/ Multiple Files"
date: 2009-03-18
forum: Security
---

### Post by Catatonic Turtle on 2009-03-18
I've been wondering... is AES any less secure if I have multiple volumes all containing different encrypted data but with the same password?  So say for example I had 50 TrueCrypt volumes, all of which use the same password... could a hacker use this to somehow reconstruct the password?

Thanks in advance!

---

### Post by snova on 2009-03-18
> **Catatonic Turtle said:**
> I've been wondering... is AES any less secure if I have multiple volumes all containing different encrypted data but with the same password?

Yes, but so is any cipher. The more the better for an attacker.

> So say for example I had 50 TrueCrypt volumes, all of which use the same password... could a hacker use this to somehow reconstruct the password?

Possibly, but I doubt it.

Assuming there is no attack more efficient than brute force, there's no hope, see: [Brute force attack]("http://en.wikipedia.org/wiki/Brute_force_attack")

> The amount of time required to break a 128-bit key is also daunting. Each of the 2^128 (340,282,366,920,938,463,463,374,607,431,768,211,456) possibilities must be checked. A device that could check a billion billion keys (10^18 ) per second would still require about 10^13 years to exhaust the key space. This is a thousand times longer than the age of the universe, which is about 13,000,000,000 (1.3 x 10^10) years.

As AES is quite secure (see: [Wikipedia]("http://en.wikipedia.org/wiki/Advanced_Encryption_Standard#Security")), I'd be inclined to believe you're pretty safe.

That doesn't mean you should depend on it, though...

---

### Post by Catatonic Turtle on 2009-03-18
Ok thanks snova, that makes sense.

---

