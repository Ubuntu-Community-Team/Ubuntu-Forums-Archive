---
title: "Unable to locate Apt-Proxy"
date: 2011-05-03
forum: Server Platforms
---

### Post by MacTuxLin on 2011-05-03
Hi,

I've just setup Natty & am trying:
```

sudo apt-get install apt-proxy

```But I get:
```

Reading package lists... Done
Building dependency tree
Reading state information... Done
Unable to locate package apt-proxy

```Any advice for me to check?

Thanks!

---

### Post by falko on 2011-05-03
That package doesn't exist in Natty. You might want to try apt-cacher or apt-cacher-ng instead.

---

### Post by MacTuxLin on 2011-05-03
Oh, no wonder. Got it. I'll try that. Thank you!

---

