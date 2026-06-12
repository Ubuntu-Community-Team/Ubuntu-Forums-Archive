---
title: "how to identify find process doing IO?"
date: 2008-11-22
forum: Server Platforms
---

### Post by davidmaxwaterman on 2008-11-22
Hi,

My server has LEDs on the front for disk IO, and one of them is pretty much constantly on (it flickers so I can tell it's not always on).

How can I tell what process is doing the IO?

Max.

---

### Post by jpkotta on 2008-11-22
```
sudo aptitude install iotop
iotop
```

---

### Post by davidmaxwaterman on 2008-11-23
> **jpkotta said:**
> ```
sudo aptitude install iotop
iotop
```

Excellent...just the job, thanks.

It was mythtv-backend.

Max.

---

