---
title: "96Khz Audio reproduction"
date: 2016-01-12
forum: Ubuntu Studio
---

### Post by drumanart on 2016-01-12
Hello.
My new USB Sound Card ROLAND DUO CAPTURE EX can record audio with maximum of 48KHz/24bit.

I can't understand why audio-fiels recorded (using an external recorder) with 96Khz/24bit are reproduced correctly using Audacity but not with Ardour3.

In Ardour3 the files run slow (48Khz).


Thanks Martin

---

### Post by marseille2 on 2016-01-12
Set the sample/bit rate in Jackd first... then Ardour should automatically start according to that. (Audacity doesn't have this step).

---

