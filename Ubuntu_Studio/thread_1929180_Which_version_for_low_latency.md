---
title: "Which version for low latency?"
date: 2012-02-21
forum: Ubuntu Studio
---

### Post by Adski13 on 2012-02-21
I'm normally pretty good with searching the web and these forums to answer my questions but all I seem to be able to find on this subject is conflicting and mis-information so any help would be greatly appreciated.

I have an HP G70 laptop (Core2 Duo, 3GB RAM) and a Steinberg MI2 USB soundcard which I want to use as a home recording studio.  I have used Ubuntu Studio before on a different (lower spec) laptop but with the same soundcard and got on well with few (if any) xruns and relatively low latency.  With this new hardware however I can't seem to get my latency down to a reasonable level (below about 40 m/s) without unbearable x-runs (every 5-10 seconds or so).  

I think this may be down to using the Generic Kernel rather than the RT or lowlatency kernel but I can't seem to work out which versions of Ubuntu Studio ship with a low latency kernel or have them in the repos.

Am I being unrealistic in my expectations in terms of low latency or can anyone suggest what the best version of Ubuntu Studio would be to get the latency down?  As far as I can tell 10.10, 11.04 and 11.10 ship with the Generic kernel and all of these have so far given me problems.  How far back do I need to go to get a version of Ubuntu Studio that works?  Alternatively, any suggestions on how best to configure a more recent release to get the performance I'm after?

Cheers in advance for any help you can provide!

---

### Post by jejeman on 2012-02-21
Ubuntu studio 10.04 is still the best. It ships with rt or preempt kernel.
I've manage to get low latency on 11.04 by switching to jack1 and with lowlatency kernel from Abogani's ppa.

---

### Post by madeinfamous on 2012-02-22
allo Adski13!

here's my reminder on my multiple install, mine, friends and clients!

you seem to be on Intel, lucky you and me! 

if you are passably good with a terminal... then...

[https://docs.google.com/document/d/1_wpXjj5FkYC3aOGobhRfOPpKQiqmrDcAxLLhCNTm33c/edit](https://docs.google.com/document/d/1_wpXjj5FkYC3aOGobhRfOPpKQiqmrDcAxLLhCNTm33c/edit)

credits to all the people, here and there, for all this tips and tricks! enjoy!

---

