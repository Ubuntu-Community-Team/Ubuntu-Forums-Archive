---
title: "patch server packages"
date: 2008-02-29
forum: Server Platforms
---

### Post by prezbedard on 2008-02-29
My desktop @ home has the automatic update check wigit to check for patches and such.

How do I do this on cli server using aptitiude? Do I simply run aptitude upgrade or is there a way to just patch installed packaged with any fixes that might be available?

Thanks

---

### Post by jonabyte on 2008-02-29
try:

```
 sudo apt-get updates
```

then:

```
sudo apt-get upgrade
```

---

### Post by prezbedard on 2008-03-10
It worked only thing is the syntax should be "update" not "updates" .

Thx

---

