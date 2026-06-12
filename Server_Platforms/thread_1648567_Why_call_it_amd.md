---
title: "Why call it amd?"
date: 2010-12-19
forum: Server Platforms
---

### Post by PalinIsATwit on 2010-12-19
I've downloaded the Ubuntu Server 64AMD version. Will this work with an Intel Xeon processor?
I've an old SuperMicro 1U Server X5DPR-8G2+ Xeon Dual 2.8GHz/1GB I'd like to use. Will Ubuntu Server work with this or do I need the 32bit version?

---

### Post by daqron on 2010-12-19
If it's a 64-bit Xeon processor then yes the AMD64 version is what you want. Check out wikipedia or other threads in the forum for more detailed explanations, but basically the "AMD" is just a naming convention that stuck. I am currently running Ubuntu 10.04 "AMD64" on an Intel i7.

---

### Post by cascade9 on 2010-12-19
The SuperMicro 1U Server X5DPR-8G2 uses 533MHz FSB Xeons,a nd they are 32bit only. 

If they were 64bit capable, then AMD64 would work just fine. AMD created x86-64, so they get to name it, not that much different to i(ntel)586, etc.

---

### Post by sanderj on 2010-12-19
> **PalinIsATwit said:**
> I've downloaded the Ubuntu Server 64AMD version. Will this work with an Intel Xeon processor?
I've an old SuperMicro 1U Server X5DPR-8G2+ Xeon Dual 2.8GHz/1GB I'd like to use. Will Ubuntu Server work with this or do I need the 32bit version?

To see for yourself what cascade9 says, you can just try to boot the 64-bit version.

And: If the system is already running any version of Linux, you can check the 64-bit-ness of the processor:

```
grep -i " lm " /proc/cpuinfo
```

It that ***mand gives output, it's a x86-64-bit processor

---

