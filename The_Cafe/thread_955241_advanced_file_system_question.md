---
title: "advanced file system question"
date: 2008-10-22
forum: The Cafe
---

### Post by savagenator on 2008-10-22
Hello all

This question is to those that know how file systems work.

A file system is set up to hold files and manages the way they are read and written to disk. Ext3 spreads them out and journals them, while ntfs kinda clumps them together for faster reading

when a file system gets a file, how does it find each one when you choose it? I realize there may not be a specific order for where it puts each file

REAL QUESTION:
Now what would be the result if a file system indexed a file, and automatically put it in a sorted order, and then [binary searched]("http://en.wikipedia.org/wiki/Binary_search")for each file? Or is that how it already does it?

---

