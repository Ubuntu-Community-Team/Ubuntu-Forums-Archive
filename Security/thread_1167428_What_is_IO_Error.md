---
title: "What is I/O Error?"
date: 2009-05-22
forum: Security
---

### Post by blogx on 2009-05-22
I just installed BitDefender and scanned the system. It shows that no virus but many I/O Errors. What are they? How to fix them?

---

### Post by blogx on 2009-05-22
The image is too small, so I upload it to my blog.

[IMG]http://img.blogx.us/bd.png[/IMG]

---

### Post by albinootje on 2009-05-22
> **blogx said:**
> The image is too small, so I upload it to my blog.


Input/Output errors. It is possible that it could not read a lot of 
files in e.g. /dev and /proc
Can that software provide you with a proper logfile ?

---

### Post by blogx on 2009-05-22
Yes, it said many files in /proc/ are Permission denied
And two in /usr/share/ are also Permission denied
Is that important?

---

### Post by albinootje on 2009-05-23
> **blogx said:**
> Yes, it said many files in /proc/ are Permission denied
And two in /usr/share/ are also Permission denied
Is that important?

Probably not. 
And /proc is a special case, those are not real files, but a kind of mirror of the Linux kernel.

---

### Post by blogx on 2009-05-23
So, I don't have to notice that at all?

---

