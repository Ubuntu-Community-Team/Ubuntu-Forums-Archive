---
title: "Repositories and updates"
date: 2007-05-08
forum: Repositories &amp; Backports
---

### Post by p252 on 2007-05-08
Question. . . Can I add the Medibuntu repository without having the update manager want to update applications from it? I wan to have the repository and install from it but I don't want the system trying to update from it. This doesn't seem to be much problem with Ubuntu but on my Kubuntu machine adding the Medibuntu repository causes the update manager to see all sorts of newer "unsupported" versions of my software. Using Software Sources in the system --> administration menu doesn't give an option to not allow updates from "other" repositories, however, it would be a nice little feature.

Thanks

---

### Post by ohgod on 2007-05-08
This is kind of a crappy fix, but you could always remove the repository from /etc/apt/sources.list once you've installed what you want from Medibuntu.

---

### Post by kwaanens on 2007-05-11
File a feature request in the right place. I think I did it at least a year ago myself, but I think it died in some way.

We should be able to tell Synaptic to:
- "only get updates for package X from Y repo"
- use a default (set of repos) for the majority off packages. "Ignore updates for other packages."

--Ketil

---

### Post by p252 on 2007-05-11
I agree. I'll file a request.

---

### Post by bapoumba on 2007-05-11
In the mean time, I install things from medibuntu and comment the repos once I have what I want. I check from time to time (same thing for the backports) what is new. Not that convenient, I admit.

---

### Post by p252 on 2007-05-11
> **bapoumba said:**
> In the mean time, I install things from medibuntu and comment the repos once I have what I want. I check from time to time (same thing for the backports) what is new. Not that convenient, I admit.

Good idea.

---

