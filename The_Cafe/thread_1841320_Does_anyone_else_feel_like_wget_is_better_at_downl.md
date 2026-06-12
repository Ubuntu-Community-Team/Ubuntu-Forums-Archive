---
title: "Does anyone else feel like wget is better at downloading stuff than curl?"
date: 2011-09-09
forum: The Cafe
---

### Post by ninjaaron on 2011-09-09
Ok ok, I realized tha wget is designed specifically as a download tool, and curl is a general tool for doing all kinds of stuff with (and to) URLs.

In any event, they both have the faculty to handle simple downloads.

I just feel like wget tends to do better, like when there is an unstable connection, or the host is weird...  When stuff times out, wget just keeps chugging.  It seems like curl gets messed up more easily.

Is this true, or am I on crack?

---

### Post by hakermania on 2011-09-09
Well, I once had a problem with 'wget', specifically it couldn't download a particular image while curl could.
In general, I haven't noticed that curl is more unstable...
I'd say that wget is more easy-to-use!

---

### Post by alexan on 2011-09-09
I found that the easier way to find out is take a look to the changelog file of both.
last release date (more updated)  and number of development version (more activity).
Yes, it is not a flawless way to dig out the truth...but it can give you more empirical idea

---

### Post by TeoBigusGeekus on 2011-09-09
I've noticed that as well.
I used to use curl in my conky scripts, but curl seemed to get stuck resulting in a lot of never terminating instances of it.
When I replaced it with wget, all problems disappeared.

---

### Post by ninjaaron on 2011-09-09
> **TeoBigusGeekus said:**
> I've noticed that as well.
I used to use curl in my conky scripts, but curl seemed to get stuck resulting in a lot of never terminating instances of it.
When I replaced it with wget, all problem disappeared.

This is EXACTLY what I meant.

---

