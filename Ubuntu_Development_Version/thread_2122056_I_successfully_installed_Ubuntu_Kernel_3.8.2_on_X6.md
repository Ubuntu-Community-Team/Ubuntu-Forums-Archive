---
title: "I successfully installed Ubuntu Kernel 3.8.2 on X64 13.04 Nightly."
date: 2013-03-03
forum: Ubuntu Development Version
---

### Post by kevpan815 on 2013-03-03
Just FYI.

---

### Post by zika on 2013-03-04
Ditto...

---

### Post by longint on 2013-03-13
Did you install it manually?
Why is the "official" repository not offering it?

---

### Post by zika on 2013-03-13
> **longint said:**
> Did you install it manually?
Why is the "official" repository not offering it?
Where did You get idea that it is not being offered? 3.8.0-12-generic is, as far as I know, just that...
We installed it manually from mainline and there is a period of adjustments and testing before it gets to &#8222;official&#8220; repository... As usual...

---

### Post by longint on 2013-03-13
Sure, I already run 3.8.0-12 (default for 13.04?) so lets try other way round: What is the proposed way to get 3.8.2 installed at 13.04?

---

### Post by zika on 2013-03-14
> **longint said:**
> Sure, I already run 3.8.0-12 (default for 13.04?) so lets try other way round: What is the proposed way to get 3.8.2 installed at 13.04?
Go to [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.8.2-raring/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.8.2-raring/) ...
DL 4 packages (3 architecture dependent and one not ("all") and install them```
sudo dpkg -i linux*.deb
```executed in folder that contains these DL-ed packages (and only them with names starting with „linux“ or alter command given above)...

---

### Post by longint on 2013-03-16
OK, the manual way. Thats what I was asking for. There is no repository where I can get the updates "automatically"!?

---

### Post by pqwoerituytrueiwoq on 2013-03-16
> **longint said:**
> OK, the manual way. Thats what I was asking for. There is no repository where I can get the updates "automatically"!?

i have written a script to check and notify and make updating quick (relative to your net speed)/easy
i attached it for you

---

