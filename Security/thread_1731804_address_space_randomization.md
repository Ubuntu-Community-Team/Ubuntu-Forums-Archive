---
title: "address space randomization"
date: 2011-04-17
forum: Security
---

### Post by weili747 on 2011-04-17
Dear all:

I am running a cache simulator for my work and it seems that for two runs under same enviornment I am getting slightly two different results. I feel that it has something todo with virtual mapping. I am using Ubuntu. Any help on how to turnoff the address space randomization? I am not very expert in this area.

best regards,
malik

---

### Post by mynameisnotbob on 2011-04-19
by address space randomization do you mean DCHP? The answer to that depends on your router.
Sorry, your post is a little confusing.

---

### Post by rookcifer on 2011-04-19
Try setting the value in /proc/sys/kernel/randomize_va_space to 0.  Then reboot.  See if that works -- it did in older kernels.

---

