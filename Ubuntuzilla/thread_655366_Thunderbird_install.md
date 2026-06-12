---
title: "Thunderbird install"
date: 2008-01-01
forum: Ubuntuzilla
---

### Post by FlyingIsFun1217 on 2008-01-01
Hey!

Just downloaded the script, and unlike older versions, every time I attempt to install thunderbird using 'ubuntuzilla.py -a install thunderbird', it starts installing firefox!

This a bug?

FlyingIsFun1217

---

### Post by nanotube on 2008-01-08
> **FlyingIsFun1217 said:**
> Hey!

Just downloaded the script, and unlike older versions, every time I attempt to install thunderbird using 'ubuntuzilla.py -a install thunderbird', it starts installing firefox!

This a bug?

FlyingIsFun1217

hi, it's supposed to be
```
ubuntuzilla.py -a install -p thunderbird
```
(notice the "-p")
try that :)

---

### Post by FlyingIsFun1217 on 2008-01-11
Thanks, I'll try that!

FlyingIsFun1217

---

### Post by AsianSpanker on 2009-10-28
I tried that install also and it just said command not found.

---

### Post by nanotube on 2009-10-28
> **AsianSpanker said:**
> I tried that install also and it just said command not found.

first, you have to install the ubuntuzilla package.

---

