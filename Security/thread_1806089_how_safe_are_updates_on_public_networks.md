---
title: "how safe are updates on public networks ?"
date: 2011-07-17
forum: Security
---

### Post by 601 on 2011-07-17
Hi,

I was wondering how safe is it to run Ubuntu updates when I'm connecting via a public network (wireless or wired) from a hotel (or other public settings). I'm not familiar with the internals but is there an additional validation mechanism for the package servers other than the URL ?

---

### Post by CharlesA on 2011-07-17
Each package is checked via hash to ensure they weren't corrupted during download.

It's fine to do updates like that.

I wouldn't surf on a public network without using an SSH tunnel, but that's just me. :)

---

### Post by Lars Noodén on 2011-07-17
Each package is checked with a hash. 

The actual list of hashes is signed using PGP.  So you can be certain that the packages you are getting are the right ones and not fakes, regardless of which network(s) you are using.

---

### Post by Lars Noodén on 2011-07-17
Here is a short description of how APT works:

[http://wiki.debian.org/SecureApt](http://wiki.debian.org/SecureApt)

---

### Post by 601 on 2011-07-17
Thank you all for your replies and for clearing up this issue!

---

