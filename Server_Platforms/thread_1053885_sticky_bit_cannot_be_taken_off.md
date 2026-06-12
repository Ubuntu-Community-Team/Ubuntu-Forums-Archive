---
title: "sticky bit cannot be taken off?"
date: 2009-01-29
forum: Server Platforms
---

### Post by jf/ on 2009-01-29
Not too sure what's happening here, but why, and what is causing this for ubuntu:

# chmod 2750 a
# ls -l
drwxr-s--- 2 j j 6 2009-01-29 18:04 a
# chmod 0750 a
drwxr-s--- 2 j j 6 2009-01-29 18:04 a


It seems like once the sticky bit is set, there's no way to remove it, except to remove the directory itself (and start all over)?

---

### Post by jf/ on 2009-01-30
nobody?

---

### Post by capscrew on 2009-01-30
It works for me.  I can set the sticky bit and later remove it.  Not sure what your problem is.

---

### Post by deadball on 2009-01-30
try 

sudo chmod g-s a

---

### Post by jf/ on 2009-02-05
> **deadball said:**
> try 

sudo chmod g-s a

woohoo yeah, that worked! was expecting '0750' to work, though. Any idea why it doesn't?

---

### Post by laughing-boy on 2011-03-30
You can set or clear the bits with symbolic modes like **u+s** and **g-s**, and you can set **(but  not  clear)** the bits with a numeric mode.

---

