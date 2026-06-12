---
title: "where are linux-lowlatency and linux-headers-lowlatency?"
date: 2010-05-23
forum: Ubuntu Studio
---

### Post by tubunu on 2010-05-23
I'm following the Ubuntu Studio preparation guide and it says:

```
Then, you may want to install the -lowlatency kernel, you can simply do:

 sudo apt-get install linux-lowlatency linux-headers-lowlatency

If you still experience Xruns or you have a firewire sound card supported by the FFADO project, you may want to install the -rt kernel:

 sudo apt-get install linux-rt linux-headers-rt
```

But I can't get these to install, apparently they are not in the repositories? Which ones should I add to fetch these? Thanks.

---

### Post by trulan on 2010-05-23
If I'm not mistaken those are only available for 64 bit.  Are you running a 32 bit system?

---

### Post by tubunu on 2010-05-23
Yes, I'm on a 32 bit system. Does that mean I cannot install a low latency kernel. I remember I could do that in the past. (previous versions of Ubuntu)

---

### Post by lzap on 2010-07-31
These are from Mediubuntu repository I assume.

---

