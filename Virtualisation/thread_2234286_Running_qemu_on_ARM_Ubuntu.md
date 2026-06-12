---
title: "Running qemu on ARM Ubuntu"
date: 2014-07-13
forum: Virtualisation
---

### Post by maciej8 on 2014-07-13
Hello everyone,

I'm trying to run qemu on the Ubuntu disk image for ARM (arm-ubuntu-natty-headless.img) that is available as a part of the gem5 simulator ([http://www.gem5.org/Download](http://www.gem5.org/Download))

```
qemu-system-arm -machine [machine-name] arm-ubuntu-natty-headless.img
```

I tried all the available ARM machines and experimented with various RAM sizes. Unfortunately,
none of the combinations I tried worked; in ~50% of the cases qemu just hangs, in the remaining ones
I get errors that look like this:

qemu: fatal: Trying to execute code outside RAM or ROM at 0x00800000


```
R00=00000000 R01=00000000 R02=00000000 R03=00000000
R04=00000000 R05=00000000 R06=00000000 R07=00000000
R08=00000000 R09=00000000 R10=00000000 R11=00000000
R12=00000000 R13=00000000 R14=00000000 R15=00800000
PSR=400001d3 -Z-- A svc32
FPSCR: 00000000
Aborted (core dumped)

```

Does anyone has an idea on how to make this thing work?

Thanks!

---

