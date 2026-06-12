---
title: "software installation standard"
date: 2008-08-07
forum: The Cafe
---

### Post by Sasa_Ivanovic on 2008-08-07
Is there a standard for software installation on linux.
What i mean by this is a package that could be installed on all distributions. wouldn't this be great...

---

### Post by Lexicon101 on 2008-08-07
It's called source code.
It's amazing!

---

### Post by Lod on 2008-08-07
> **Lexicon101 said:**
> It's called source code.
It's amazing!Well Mike, tell us more :popcorn:

---

### Post by Lexicon101 on 2008-08-07
I was joking. It would be nice to have something easy like a universal package..
I think the SMART package manager is supposed to support different standards..
Also, source isn't that hard.. it usually tells you what else you need to compile it..

---

### Post by akiratheoni on 2008-08-07
There's always been talks about this universal package manager... there are tons of other threads that debate this. In fact I remember one from at least several weeks ago that talked about it.

---

### Post by ibutho on 2008-08-07
> **Sasa_Ivanovic said:**
> Is there a standard for software installation on linux.
What i mean by this is a package that could be installed on all distributions. wouldn't this be great...

There isn't a standard as such, but compiling from source works on all distributions.

---

### Post by sameerds on 2008-08-07
> **Sasa_Ivanovic said:**
> Is there a standard for software installation on linux.
What i mean by this is a package that could be installed on all distributions. wouldn't this be great...

There is no standard to do that. Different systems use different package formats like deb and rpm. But it's not just about the package format. Everybody could agree to use deb, or rpm, or something that is a superset of both. But even with that, there is no guarantee that the package will work on _all_ systems!

The issue here is binary compatibility. A package basically contains binaries that were created on a system with a specific set of libraries with some specific versions. That means the binaries will work only a system with the same libraries. A common package format can't guarantee that. Can a deb meant for Hardy work on Gutsy for example? That's the problem.

Well, if standardisation efforts like the LFS and the LSB become successful, it is true that a package meant for "recent" Ubuntu might work on a "recent" Fedora that supports the same standard. In that case, having a common package format is a trivial issue.

---

