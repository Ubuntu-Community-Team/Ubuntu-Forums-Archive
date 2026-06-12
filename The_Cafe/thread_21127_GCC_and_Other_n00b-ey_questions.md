---
title: "GCC and Other n00b-ey questions"
date: 2005-03-20
forum: The Cafe
---

### Post by Leebobs on 2005-03-20
I'm very much a Linux n00b... but I'm enjoying it so far! Anyhow, I was reading over at Neowin how GCC4 is going to make Linux faster & smaller...

How is this possiable? Will GCC4 break code? Will the next version of ubuntu use GCC4 to compile everything?

Leebobs

---

### Post by DJ_Max on 2005-03-20
I'm not sure about smaller, but it's possible it could make it somewhat faster, even though I wouldn't depend on it. I haven't looked at GCC4, but depending on which application you're compiling, and how it's written, it may spit a few errors.

---

### Post by jdong on 2005-03-20
If it compiles under GCC 3.4, it _SHOULD_ compile under GCC 4.0.

However, 3.4 is not binary-compatible with 3.3. You're gonna have to recompile your WHOLE system under GCC 4.0...

I don't recommend you switch to GCC 4.0 on Ubuntu -- try Gentoo or Fedora if you want that kind of bleeding-edge setup, as you'll get better community/developer support for the new GCC.

---

