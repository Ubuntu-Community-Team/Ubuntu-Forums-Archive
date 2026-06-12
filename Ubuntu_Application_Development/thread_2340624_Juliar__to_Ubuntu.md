---
title: "*Juliar * to Ubuntu"
date: 2016-10-20
forum: Ubuntu Application Development
---

### Post by randy2017 on 2016-10-20
Hey guys,

(I didn't know where to post this message, so please move this topic to appropriate forum)

I would like to port my project to one of the official Ubuntu repos.

What are my steps in doing so?

The language is actively developed on [www.github.com/juliarLang/juliar]("http://www.github.com/juliarLang/juliar")
The language has an official site at [www.juliar.org]("http://www.juliar.org") and forums at [www.juliar.org/forums]("http://www.juliar.org/forums")

The language for the most part is stable.
The language does have an apt repository (instructions can be found at [www.juliar.org/downloads.ju]("http://www.juliar.org/downloads.ju"))

I would really love to port it to an official REPO and perhaps launchpad/PDA.

What are my steps?

Thanks for your time

---

### Post by ericoporto2008 on 2016-11-19
This is an interesting question that I could really benefit from the answer :O

---

### Post by ian-weisser on 2016-11-19
Start by adding the source to Debian.
Since you're already familiar with debs, head to [https://mentors.debian.net/](https://mentors.debian.net/), and start looking for a sponsor for your upload. The source code license must meet the Debian guidelines, of course.
Ubuntu will automatically pick it up from Debian. Ubuntu syncs from Debian every six months.
If it's in Debian, you generally don't need a PPA for wide distribution, though you are welcome to start one for testing.

There is a lightly-traveled Ubuntu-only path that bypasses Debian. It is discouraged, with few exceptions. Ubuntu policy is to sync from Debian as much as possible. Both distros benefit from the wider use and sharing.

If you are interested in snaps instead of debs, head over to developer.ubuntu.com to create your snap and upload it to the Snap store.

---

