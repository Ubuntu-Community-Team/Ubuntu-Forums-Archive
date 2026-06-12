---
title: "FireFox reports several instances but only 4 tabs open"
date: 2012-01-02
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by ventrical on 2012-01-02
I installed htop and noticed all these instances of ffox but I only have 4 tabs open.

---

### Post by chrisccoulson on 2012-01-02
That's because it is showing user threads

---

### Post by MacUntu on 2012-01-02
F2 &#8594; Display options &#8594; Hide userland threads. You can also hide kernel threads if you don't care about those. ;)

---

### Post by ventrical on 2012-01-02
> **MacUntu said:**
> F2 &#8594; Display options &#8594; Hide userland threads. You can also hide kernel threads if you don't care about those. ;)

  I was just curious as to why they are using so much memory when those tabs are not even open.. or am I reading the report wrong ?

---

### Post by ventrical on 2012-01-02
> **chrisccoulson said:**
> That's because it is showing user threads

But is each thread using 9.9 mb of RAM?

---

### Post by MacUntu on 2012-01-02
> **ventrical said:**
> But is each thread using 9.9 mb of RAM?
Nope, that's a *process* property, hence you'll see the same number for every thread in the process.

---

### Post by ventrical on 2012-01-02
> **MacUntu said:**
> Nope, that's a *process* property, hence you'll see the same number for every thread in the process.


Ahhhh.... thanks.

Just checking :)

---

