---
title: "hydra  invalid pointer"
date: 2009-12-21
forum: Security
---

### Post by isat on 2009-12-21
dear all,
i have compiling and installing hydra in my ubuntu, but i got some trouble when i use its,i got invalid pointer, and i dont understand it why, here is  i capture the error, wish i can get some clue to solve its.
regards

isat

---

### Post by liztrd on 2009-12-21
you need to patch hydra with  [http://packetstorm.linuxsecurity.com/groups/thc/hydra-http-form.patch](http://packetstorm.linuxsecurity.com/groups/thc/hydra-http-form.patch)

```
patch -p0 < hydra-http-form.patch
```

---

