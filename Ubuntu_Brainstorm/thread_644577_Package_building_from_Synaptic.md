---
title: "Package building from Synaptic"
date: 2007-12-19
forum: Ubuntu Brainstorm
---

### Post by Megatog615 on 2007-12-19
Could this be possible? I'd love to tick a box in Synaptic called "prefer building packages" and Synaptic will download the source code to anything you select along with its dependencies and build them, if possible(some non-free packages might not have source code).
There could also be build optimizations available in an "Advanced..." menu.

Of course something would have to be done with how apt prefers packages in the repository rather than your already-built packages with the same version.

Menu options for a selected package could be "select repository package" and "build from source" if you want to force the package in he repository or if you want to explicitly build a package rather than download the binary package.

Any takers?

---

### Post by smartboyathome on 2007-12-19
I would like this, and since it STILL gets them from the repos, dependancies will be satisfied already. I would wonder if people would start wanting it to build all packages though (which wouldn't be possible as far as I know).

---

### Post by insane_alien on 2007-12-21
that would be cool. a bit like the flags you can set in yaourt in arch.

---

### Post by lexen on 2007-12-24
This may be a stupid question, but what advantage would you get  from compiling from source?

---

### Post by smartboyathome on 2007-12-24
It would be optimized for your kernel (instead of Ubuntu's kernel). This is only for if you recompile your kernel though.

---

### Post by Hobbsee on 2007-12-25
I thought it was reasonably well known that it hardly helped at all.

If you want this kind of stuff, you probably want gentoo.  I *really* doubt ubuntu will ever do this.

---

### Post by DizzyTech on 2007-12-26
This would allow Ubuntu to have more alternative kernels (e.g., special niche ones).  Compiling allows optimization towards your kernel (as previously said) and your hardware architecture.

---

### Post by puccaso on 2007-12-27
well a while ago there was something called apt-build,
now the ubuntu guys have something called prevu - 
if they were both put together somehow,
you could do a "rebuild world" (old gentoo user here) and recompile everything how you wanted it.

you want cups support? you want svg support..
yes it SOUNDS very much like a gentoo setup - but thats truely the benefit of having a system you can tune. dont install the things you want, dont install the features you dont want.. 

imagine building pidgin with the protocols you want - it could pull in plugins from the pidgin track and build then at buildtime - 

its a very carismatic.. 

it should be ubuntumatic! :D

---

### Post by Hobbsee on 2007-12-28
puccaso, that sounds very much why you'd go and run gentoo.  If that were to be done for ubuntu, there would be no guarentee that you could get support, or that dist upgrades would work, you couldn't file bugs, etc - because your system is different from everyone else's.

---

