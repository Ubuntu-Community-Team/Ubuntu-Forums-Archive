---
title: "Best Virtualization Solution"
date: 2010-12-02
forum: Virtualisation
---

### Post by mark_smith111 on 2010-12-02
I am in process of putting a virtualization plan in place.  Wondering, from pure virtualization perspective, which hardware vendor provides the best virtualization solution.  Will like to know if any have had any experiences using virtualization on DELL hardware, SUN, HP or IBM. Also wondering, if any of you were able to get a decent discount from any of these hardware or vitualization software vendors.  Appreciate your help

---

### Post by thatguruguy on 2010-12-02
Why did you post this thread twice?

---

### Post by mciverza on 2010-12-03
Best hardware virtualization: IBM system Z or system P, possibly SUN sparc systems that support hardware partitioning.

... but I'm guessing that isn't what you're after.

x86 virtualization platforms are IMHO 6-of-one, half a dozen of the other. In terms of hardware, IBM's x3950 supports around 512 Gig of RAM, so that might be nice.

In terms of virtualization solutions, looking forward Red Hat RHEV is a good way to go, but you'd need to look at "what you want to get done"/achieve by virtualizing.

Is it High Availability or hardware vendor independence, is it performance, is it cost saving by consolidating several physical machines onto a single VM host?

I hope those questions will help you decide.

---

