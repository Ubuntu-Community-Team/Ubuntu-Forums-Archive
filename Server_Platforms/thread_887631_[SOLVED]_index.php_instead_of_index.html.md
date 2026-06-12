---
title: "[SOLVED] index.php instead of index.html"
date: 2008-08-12
forum: Server Platforms
---

### Post by Anders B on 2008-08-12
Im running Apache2 on Ubuntu 8.04

Ive installed a punBB forum, and its running flawlessly, BUT...

In the browser i have to enter [http://[myurl]/index.php](http://[myurl]/index.php), instead og just [http://[myurl]](http://[myurl]).

It just opens the index.html as default :(, when it should be index.php.

How do i fix this?

---

### Post by ibutho on 2008-08-12
Why not rename the index.html to something else or change the DocumentIndex section in apache, so that index.php is first (don't know if this will actually make a difference).

---

### Post by Anders B on 2008-08-12
I simply just deleted the index.html :)

Ty

---

