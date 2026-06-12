---
title: "Using your current swap in a VM"
date: 2008-12-01
forum: Virtualisation
---

### Post by Lostincyberspace on 2008-12-01
I have started doing work with VM's and one thing they are lacking is a way to use your existing swap. When ever I go in and make a new virtual i makes another swap. If they would just allocate from the swap I already have.

---

### Post by pp. on 2008-12-02
> **Lostincyberspace said:**
> I have started doing work with VM's and one thing they are lacking is a way to use your existing swap. When ever I go in and make a new virtual i makes another swap. If they would just allocate from the swap I already have.

If you mean by that that the guest machine will be using the same swap as the host machine does: don't.

---

### Post by sdennie on 2008-12-02
Moved to virtualization

---

### Post by bodhi.zazen on 2008-12-02
> **pp. said:**
> If you mean by that that the guest machine will be using the same swap as the host machine does: don't.

I agree you can not (should not) use a swap partition on the guest and host at the same time (or multiple guests).

What you could do is make an additional virtual HD and use it on multiple guests, one at at time.

---

### Post by Dedoimedo on 2008-12-02
Hello,

Accessing raw partition can be tricky in the first place.
Using the same swap might cause unpredicable behavior in many applications. You might even get a few unpleasant system crashes.

In general, using a swap partition for several OS can be ok, provided you run ONE at a time.

Dedoimedo

---

