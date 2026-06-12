---
title: "Ubuntu deb packages for own software"
date: 2006-11-01
forum: The Cafe
---

### Post by jamyskis on 2006-11-01
Hi all,

I'm currently writing a couple of games which I'd like to be able to submit to the Ubuntu multiverse repositories. Is this generally allowed, subject to wider testing and such like?

Thanks!

---

### Post by UbuWu on 2006-11-01
[https://wiki.ubuntu.com/MOTU/Packages/New](https://wiki.ubuntu.com/MOTU/Packages/New)

---

### Post by jamyskis on 2006-11-01
> **UbuWu said:**
> [https://wiki.ubuntu.com/MOTU/Packages/New](https://wiki.ubuntu.com/MOTU/Packages/New)

Brilliant. Thanks :mrgreen:

---

### Post by bruce89 on 2006-11-01
> **jamyskis said:**
> I'm currently writing a couple of games which I'd like to be able to submit to the Ubuntu multiverse repositories.

Why multiverse, are they non-free?

---

### Post by jamyskis on 2006-11-01
No, they're GPL, I just wouldn't expect Canonical to support them in any way.

Hmmm, I've tried to build a package but I've been here for two hours trying to figure out what's wrong with my changelog, because dpkg-buildpackage reports that there is some bad formatting on the very last line. I have thought that this might be due to a newline at the end of the line but it wasn't...

I can't think for the life of me what it might be. Maybe I'll request that someone else build this for me because I don't really have enough time to learn the ins and outs of the Debian packaging system.

---

