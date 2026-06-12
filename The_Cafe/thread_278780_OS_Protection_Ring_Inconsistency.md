---
title: "OS Protection Ring Inconsistency"
date: 2006-10-16
forum: The Cafe
---

### Post by neumeka on 2006-10-16
Modern operating systems have the concept of protection rings - a  mechanism implemented in hardware which protects processes and data from other processes and data.  Code segments are assigned privilege levels, with level 0 being the most privileged and level  n being the least.  Only processes running at a privilege level equal to or greater than the CS privilege level are allowed some kind of access to it (i.e. read/write/execute).

The paper that introduces the notion of protection levels in the Multics system  ([A Hardware Architecture for Implementing Protection Rings A Hardware Architecture for Implementing Protection Rings]("ftp://ftp.digital.com/pub/Digital/SRC/publications/mds/protection.pdf")), explains the relationship between rings as follows: > The sets of access capabilities represented by the various rings of a process form a collection of nested subsets, with ring 0 the largest set and ring r — 1 the smallest set in the collection.

In other words, ring 0 has the most privileges, ring 1 has a subset of ring 0's privileges, ring 2 has a subset of ring 1's and so on.  Although the paper makes no mention of "inner" or "outer" rings, the above explanation seems to denote ring 0 as being the outer ring and ring n being the inner ring, because ring n has a restricted subset of ring 0's privileges.

However, most articles on ring mode security that I have found on the internet (including processor programming manuals) denote ring 0 as being the innermost ring.  Does anyone have any explanations for this discrepancy?

---

