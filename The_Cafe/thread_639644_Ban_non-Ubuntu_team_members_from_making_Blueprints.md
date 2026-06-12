---
title: "Ban non-Ubuntu team members from making Blueprints"
date: 2007-12-13
forum: The Cafe
---

### Post by bruce89 on 2007-12-13
The [Launchpad Blueprints]("https://blueprints.edge.launchpad.net/ubuntu/") system has far too many blueprints (1842). Most of them are silly, such as removing the FHS or things that should be bugs.

I think only Ubuntu team members should be able to write blueprints.

---

### Post by aysiu on 2007-12-13
Can you explain a bit more about what the ideal process would look like?

---

### Post by 23meg on 2007-12-13
Who are "Ubuntu team members"? ubuntu-dev? I don't think a sensible group to restrict it to can be agreed upon; there will always be people capable of writing good blueprints that you'll be excluding, and excluding people that way isn't good PR. 

You need to define the problem well. The problem is that there are too many blueprint entries (not blueprints) that are devoid of any substance. Why? Because people seem to treat the blueprint system as a feature request mechanism. Why? Probably because they're led to think so by external sources, and because the fact that it's not a feature request mechanism isn't emphasized well enough anywhere.

Another thing: some projects do use the blueprint module as a feature request mechanism; it's entirely usable that way. The point is that Ubuntu doesn't.

---

### Post by bruce89 on 2007-12-13
> **aysiu said:**
> Can you explain a bit more about what the ideal process would look like?

I don't know, but I know not to have the system in use currently.

> **23meg said:**
> You need to define the problem well. The problem is that there are too many blueprint entries (not blueprints) that are devoid of any substance. Why? Because people seem to treat the blueprint system as a feature request mechanism. Why? Probably because they're led to think so by external sources, and because the fact that it's not a feature request mechanism isn't emphasized well enough anywhere.

This sounds right.

---

### Post by aysiu on 2007-12-13
Well, forgive my ignorance, but I thought blueprints were a legitimate venue for feature requests.

Can I then ask what blueprints are for?

And is there another legitimate venue for feature requests?

---

### Post by bruce89 on 2007-12-13
> **aysiu said:**
> Well, forgive my ignorance, but I thought blueprints were a legitimate venue for feature requests.

Can I then ask what blueprints are for?

And is there another legitimate venue for feature requests?

They should be bug reports IMHO.

---

### Post by 23meg on 2007-12-13
[QUOTE=aysiu]Well, forgive my ignorance, but I thought blueprints were a legitimate venue for feature requests.

Can I then ask what blueprints are for?[/QUOTE]

[https://wiki.ubuntu.com/FeatureSpecifications](https://wiki.ubuntu.com/FeatureSpecifications)

[QUOTE=aysiu]And is there another legitimate venue for feature requests?[/QUOTE]

Feature requests mostly work at the upstream level, and not so well at the distro level, partly because what makes up "features" is actually programmed upstream. Distro-level features are best decided upon with consensus rather than hit-and-run requests; with major ones, it's best to discuss them at a development mailing list and/or forum with the people involved, and try to reach a consensus on what should be done. With trivial ones, filing bugs will be enough.

---

