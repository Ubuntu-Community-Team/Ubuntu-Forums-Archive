---
title: "To what degree do new Ubuntu releases build on the previous one(s)?"
date: 2008-07-25
forum: The Cafe
---

### Post by GOfree on 2008-07-25
I just want to ask this question before I shoot my mouth off.

(And maybe avoid shooting my mouth off altogether.)

:)

---

### Post by Canis familiaris on 2008-07-25
Quite a lot actually.

---

### Post by sdennie on 2008-07-25
A very, very large degree.  With a 6 month steady release cycle, changes necessarily happen incrementally rather than radically.

---

### Post by kko1 on 2008-07-25
Hi!

I thought you might find some of this page relevant. It doesn't directly answer your question, but it gives an idea of "what makes a distribution", or "what's Ubuntu made of (and why)". The central (IMO) sections, that is descriptions of *boot, minimal, standard* and *desktop* "seeds", give an idea about the criteria used to *select & maintain* the packages making up the different parts of the distribution. (Kubuntu etc. of course have different *desktop* seeds, because the desktop environment of choice is different.)

_[https://wiki.ubuntu.com/SeedManagement](https://wiki.ubuntu.com/SeedManagement)_

---

### Post by 23meg on 2008-07-25
The following are more relevant (read the parts about merges):

[https://wiki.ubuntu.com/UbuntuDevelopment/PackageArchive](https://wiki.ubuntu.com/UbuntuDevelopment/PackageArchive)
[https://wiki.ubuntu.com/UbuntuDevelopment/ReleaseProcess](https://wiki.ubuntu.com/UbuntuDevelopment/ReleaseProcess)

In a manner of speaking, every Ubuntu release builds *entirely* on the previous one. Changes incorporated from upstreams are merged with the existing versions in Ubuntu, and whenever there is no longer a reason to carry Ubuntu-specific changes, they are dropped, in an effort to keep the delta with upstream (Debian in special) as small as possible.

I know it was recently mentioned in a thread you posted that Ubuntu "doesn't build on its previous releases, but takes a snapshot of Sid with every release", hence your asking this. That's not true. Ubuntu-specific changes are preserved between releases for as long as is necessary, while effort is made to get them upstream as well whenever it makes sense, in which case they are dropped.

---

