---
title: "MD5 collision probability"
date: 2009-04-16
forum: Server Platforms
---

### Post by cdenley on 2009-04-16
What is the probability that the MD5 checksum of a file can match the checksum of a copy, even though the copy has been corrupted? I think the probability that any two different sets of random data compute to the same checksum would be 1 in 2^128. However, wouldn't it be much less likely that two data sets of the same size with minimal differences would compute to the same MD5 checksum?

---

### Post by PacSci on 2009-04-16
I'm not sure of the exact probabilities - I'm not an advanced mathematician, and it would depend on the file size and amount of corruption - but localized, major corruption would definitely hash differently. As a simple example, try this series of hexadecimal numbers: '0 F 3 B 8 7 A 1'. They have a sum of 37 in decimal. If one of the numbers got changed - say, to '0 E 3 B 8 7 A 1' - the sum would change to 36. It's a similar principle. If the damage was completely random, it is unlikely that the damage would balance out to 0 - especially with a complex algorithm like MD5.

If you want to be more sure, though, use SHA1 hashes if possible.

---

### Post by BkkBonanza on 2009-04-16
I don't know if it's more likely - that depends on the exact nature of the hash and how natural it's distribution is. The MD5 algorithm has been shown to have weaknesses. The Wikipedia article has some references to them and they could be followed up from there.

[http://en.wikipedia.org/wiki/MD5](http://en.wikipedia.org/wiki/MD5)

Some interesting info on probabilities of collisions is laid out in the article on Birthday Attacks - it isn't exactly what you're askign about but it is related. In particular near the end dealing with fraudulent contracts, ie. similar data sets.

[http://en.wikipedia.org/wiki/Birthday_attack](http://en.wikipedia.org/wiki/Birthday_attack)

---

