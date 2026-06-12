---
title: "random number/ character generator"
date: 2012-02-09
forum: The Cafe
---

### Post by threegremlins on 2012-02-09
what software could i use to output a file of random numbers and characters?

---

### Post by Bachstelze on 2012-02-09
Define "random". In particular, what is it for?

---

### Post by HansKisaragi on 2012-02-10
[http://www.random.org/](http://www.random.org/) .. Not sure about software but there some random generators on that site.

---

### Post by Phoenixie on 2012-02-10
```
cat /dev/urandom | tr -dc 'a-zA-Z0-9' | fold -w 50 | head -n 1
```

---

### Post by HermanAB on 2012-02-10
Read either /dev/random or /dev/urandom.

$ cat /dev/random

---

### Post by threegremlins on 2012-02-10
Phoenixie, that is perfect. Yes I read about random, rand and urand but I didn't understand about the options. thanks every one.

---

