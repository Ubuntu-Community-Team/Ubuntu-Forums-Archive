---
title: "Ubuntuzilla &amp; libstdc++5"
date: 2009-05-07
forum: Ubuntuzilla
---

### Post by Gary Nored on 2009-05-07
Contrary to web page assertion, Ubuntuzilla 4.6.1 does not resolve the libstdc++5 issue. Anyone know how to get this library? (every link I've followed has been error 404).

Gracias

---

### Post by chellrose on 2009-05-07
> **Gary Nored said:**
> Contrary to web page assertion, Ubuntuzilla 4.6.1 does not resolve the libstdc++5 issue. Anyone know how to get this library? (every link I've followed has been error 404).

Gracias

I don't know what issue you're referring to, but this library shows up in my repository.  So...

```

sudo apt-get install libstdc++5

```

---

### Post by Gary Nored on 2009-05-09
For whatever reason it did not show up in my repository, regardles of sources.list setting. I finally solved the issue by upgrading to ver 8. Thanks for reply.

---

