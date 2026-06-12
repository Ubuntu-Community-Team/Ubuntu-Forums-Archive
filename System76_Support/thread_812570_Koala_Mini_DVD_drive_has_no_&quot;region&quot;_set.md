---
title: "Koala Mini DVD drive has no &quot;region&quot; set, DVD playback is rejected (solution)"
date: 2008-05-30
forum: System76 Support
---

### Post by buster8079 on 2008-05-30
To anyone struggling to get DVD playback working after installing libdvdcss2 onto your Koala Mini (and perhaps other system 76 machines), please see the following post of mine, which lead me to the ultimate solution. Long story short: the DVD drive as shipped from system 76 didn't have a "region" set to it, so discs were not recognized and thus not playable. I suppose this makes sense since the Koala Mini is an aopen mini PC that ships world wide bare bones and that system 76 builds with an Ubuntu installation, etc.

Any how, to anyone out there struggling, give the post below a whirl and good luck.

[http://ubuntuforums.org/showpost.php?p=5067999&postcount=363](http://ubuntuforums.org/showpost.php?p=5067999&postcount=363)

---

### Post by thomasaaron on 2008-05-30
That's interesting. We've never got that complaint before on the Koalas.
I wonder if yours was just a fluke.

I'll be checking with manufacturing to make sure the region is set to U.S.

Best,
Tom

---

### Post by perce on 2008-05-31
Doesn't libdvdcss2 ignore the region anyway?

---

### Post by buster8079 on 2008-06-05
> **perce said:**
> Doesn't libdvdcss2 ignore the region anyway?

I suppose the DVD still needs *some* region set before it ignores the others, and that "0" is no region at all. That the software can't masquerade as other regions (or its own region) if it can't even get into the dance?

---

