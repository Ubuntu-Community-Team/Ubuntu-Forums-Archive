---
title: "NX bit doesn't work in 64-bit kubuntu"
date: 2010-02-21
forum: Security
---

### Post by roome on 2010-02-21
I'm using kubuntu-9.10-desktop-amd64.iso live (booted via grub2 loopback directly from iso on hd, in case that makes a difference).
Processor is a E2180 which according to the Intel website supports the NX bit. I've enabled the option "Execute Bit Support" in the BIOS. /proc/cpuinfo shows both nx and pae in both flags lines.
But dmesg says "Using x86 segment limits to approximate NX protection".
Any idea what the problem could be?

---

### Post by rookcifer on 2010-02-21
So, are you running this from a VM or what?

---

### Post by FuturePilot on 2010-02-21
This was a bug and it has been fixed. [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/454285]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/454285")

---

