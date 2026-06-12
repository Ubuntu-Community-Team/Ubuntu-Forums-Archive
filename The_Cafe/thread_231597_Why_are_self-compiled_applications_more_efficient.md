---
title: "Why are self-compiled applications more efficient?"
date: 2006-08-07
forum: The Cafe
---

### Post by paulyche on 2006-08-07
I've just compiled a build of amarok from svn to fix an annoying (and short lived) "feature" in 1.41. 

I haven't done any fair comparisons but when amarok is running my CPU monitor certainly looks less full - which I presume is a benefit of amarok being a self-compiled version rather than a pre-built binary.

Why is this? Is it simply a case of my amarok being compiled to take advantage of 686 or k7 optimisations and the binary being compiled for a 386?

If I compliled something on my computer and ran the binary on an identical machine I presume it'd run identically. What if I ran it on a computer with an identical processor but different mobo, RAM etc?

Just curious and Google isn't being my friend.

---

### Post by TravisNewman on 2006-08-07
it could be updated code, but compiling from scratch can remove a lot of the stuff that's compiled in for maximum compatibility and tailor it to your own PC.

Depending on the optimizations you've compiled it with, you might be able to take it to a different pc and it would work fine. The ram and motherboard probably wouldn't matter much if at all, the CPU is the catch.

---

### Post by paulyche on 2006-08-07
Mmmmm. Didn't think about the compatibility issues. Sounds about right. 

It's interesting because at my work (CentOS) we have some apps compiled on intel machines that only run over the network on other intel machines of about the same generation (they have non-identical configurations including different CPUs)

amarok's a bit of a resource hog and the compilation worked okay I might try experimenting with compilations of other intensive apps.

Thanks panickedthumb.

---

### Post by TravisNewman on 2006-08-07
good luck, but be careful if you compile too much. You might try compiling from apt, that way you keep everything organized and in the system.

---

### Post by paulyche on 2006-08-07
I used makeinstall this time which I suppose offers the same functionality? Haven't ever heard of compiling from apt.

---

### Post by Anduu on 2006-08-07
Use checkinstall...

---

### Post by Michael_aust on 2006-08-07
Checkinstall sometimes bombs out when it tried to make the actual deb.  SO you sometimes have to resort to using make install.

---

### Post by paulyche on 2006-08-07
Oops. I actually meant checkinstall when I said makeinstall. Thanks though.

---

### Post by G Morgan on 2006-08-07
It all depends on what compile flags you use. If you've specified it to compile specifically for your architecture then it should be a reasonable amount more efficient (I found about 10%-20% on Gentoo but it does vary quite wildly). If you didn't set compile flags then it would have defaulted to 386. It may be the case that the repos version has all the options compiled in and the version you compiled from source only did what you needed.

---

