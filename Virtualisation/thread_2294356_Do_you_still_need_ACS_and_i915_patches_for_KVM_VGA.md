---
title: "Do you still need ACS and i915 patches for KVM VGA Passthrough with kernel 4.2?"
date: 2015-09-10
forum: Virtualisation
---

### Post by pepsifx357 on 2015-09-10
I saw ACS in the Kernel config but not i915.  Do you still need these in 4.2?

---

### Post by redger on 2015-09-11
afaik i915 patch will NEVER be included because it breaks things (DRI ?) ... so you will always need that to use Intel IGP on host .... unless you use UEFI boot ... then you don't need the i915 patch

---

### Post by pepsifx357 on 2015-09-14
Cool, thanks!

---

