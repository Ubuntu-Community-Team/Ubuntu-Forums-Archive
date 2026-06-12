---
title: "Cluster Idea"
date: 2008-06-02
forum: Server Platforms
---

### Post by greg73654 on 2008-06-02
Well, the Opteron might be a better choice, but the phenoms are cheaper! ^_^

But really this thing is more for s's and giggles. I'd really like to build a stable one to start and then work towards a goal that I could use it for. I'd really like to have some ideas on what it could be used for (besides scientific calculations and multi-media, cause I've heard those. ^_^)

---

### Post by mlapaglia on 2008-06-03
people make "rendering clusters," primarily for compiling movies made digitally on a computer, using different flavors of Linux. The thing you need to remember is most programs can't natively support the ability to use more than one computer for processing. Open source programs need to have MPI, or another kind of interface for the cluster and the specific program you want to run.

I am currently in the development phase of making a cluster for some scientific research. From what I've learned there are actual distributions of Linux geared towards distributed computer (in my case, I'll be using MPI and Parallel Knoppix.

Although it would be possible to use Ubuntu, it's not designed to behave as such, and you'll get better performance looking elsewhere.

Here's a few sites you can look at:
[http://helmer.sfe.se/](http://helmer.sfe.se/)
[http://pareto.uab.es/mcreel/ParallelKnoppix/Tutorial/Tutorial.htm](http://pareto.uab.es/mcreel/ParallelKnoppix/Tutorial/Tutorial.htm)
[http://www.linux.com/feature/58379](http://www.linux.com/feature/58379)
[http://students.haverford.edu/aohara/clustering.html](http://students.haverford.edu/aohara/clustering.html)

---

