---
title: "Why static addresses for dynamically shared objects again?"
date: 2007-10-12
forum: Server Platforms
---

### Post by Adnarim on 2007-10-12
Well I can exactly remember that the first thing I noticed after the upgrade from edgy to feisty was that finally dynamically shared objects were not linked to a static/certain address and I thought wow that's a real increase in security because this makes attacks against non-daemon processes nearly impossible.

But today while playing around a bit I incidentally hit two times the ldd command and what did I see? linux-gate.so.1 is again statically bound to 0xffffe000 ?

When did this change again and why? Do you know with what kernel? I'm using 2.6.20-16-386.

---

