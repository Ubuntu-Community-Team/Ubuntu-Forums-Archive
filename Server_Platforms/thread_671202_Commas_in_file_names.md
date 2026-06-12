---
title: "Commas in file names"
date: 2008-01-18
forum: Server Platforms
---

### Post by da__smith on 2008-01-18
Hi

Are there any issues with allowing file names to contain commas on a Linux server in general?

For example:
thing,file-name.html

all the best
Dave

---

### Post by MJN on 2008-01-18
No issues with Linux itself - commas are fine in general but true ISO9660-standard CD's are very restrictive with character sets and don't like commas. You may however not have any trouble with them in practice.

You are right to question it - see [http://en.wikipedia.org/wiki/Filename](http://en.wikipedia.org/wiki/Filename) for details of what is, and isn't, allowed on various filesystems - it is wise to accomodate the lowest common denominator of any filesystem that you might reasonably expect to interact with.

Mathew

---

### Post by koenn on 2008-01-18
I'd avoid them even if they are possible.
When you do command line stuff / scripts, anything that could be a delimiter in some way or have any other special meaning (whitespace, commas, slashes, ... ), will sooner or later interfere with commands or control structures in scripts and you'll have to jump through hoops to work around them.

---

