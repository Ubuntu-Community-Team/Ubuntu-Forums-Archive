---
title: "KVM: cpu0 unhandled rdmsr"
date: 2009-05-26
forum: Server Platforms
---

### Post by lightnb on 2009-05-26
The messages:

```
[  248.460377] kvm: 3122: cpu0 unhandled rdmsr: 0xc0010117
```

and

```
[  252.422518] kvm: 3131: cpu0 unhandled wrmsr: 0xc0010117 data 0
```

appear occasionally on my Virtual Machine Server terminal.

Is this a cause for concern?

---

### Post by Alekz_ on 2009-05-26
I saw some bug reports of kvm running in some kernel releases.. It may be your problem. Try to google for some bug report about your kernel release..

---

### Post by lightnb on 2009-05-27
I've found some bug reports via Google, but no conclusive answers thus far.

The system is working- both the host and three guests (all Ubuntu 9.04).

I'm just leery about putting this new system into production with CPU errors showing up on the terminal...

---

