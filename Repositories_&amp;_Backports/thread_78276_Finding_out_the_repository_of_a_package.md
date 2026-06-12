---
title: "Finding out the repository of a package"
date: 2005-10-18
forum: Repositories &amp; Backports
---

### Post by Tomek on 2005-10-18
Hi,

how can I find out, which installed packages i.e. are from Universe? 

Because it's a server, I cannot use synaptic for this. Thanks.

---

### Post by riggsd on 2005-10-18
You can find out for a single package with:

```
apt-cache policy foobar
```

---

### Post by komputes on 2008-03-03
```
apt-cache madison foobar
```

---

