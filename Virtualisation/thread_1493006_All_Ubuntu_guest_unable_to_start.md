---
title: "All Ubuntu guest unable to start"
date: 2010-05-25
forum: Virtualisation
---

### Post by satimis on 2010-05-25
Hi folks,

Host - Debian 5.04
KVM

I have Debian/Windows/Ubuntu guests running on the box.  For unknown reason recently all
Ubuntu guests can't start.  Other guests are working.  Always hanging on```

kernel_thread_helper+0x7/0x10

```

Just tried installing a new Ubuntu 10.04 guest without success.  The guest started to
boot but hanging on the screen finally.

Please help.  TIA

B.R
satimis

---

### Post by oohshiny on 2010-05-27
Which kernel version is your guest using? There seems to be a bug with 2.6.32 at present...

---

### Post by satimis on 2010-05-27
> **oohshiny said:**
> Which kernel version is your guest using? There seems to be a bug with 2.6.32 at present...

Hi,

$ uname -a```

Linux vm0.debian50 2.6.26-2-686 #1 SMP Wed May 12 21:56:10 UTC 2010 i686 GNU/Linux

```


Performed following test:-

Boot the host to previous kernel 2.6.26-1-686

All Ubuntu guests revives.  I can install Ubuntu 10.04 as guest.

To my surprise rebooting the host to new kernel 2.6.26-2-686 again, all Ubuntu guests work.  They are still working.  All other Debian/Windows guests are also working.


This virtual machine has been running for sometimes.  IIRC the KVM was download from KVM website.  Its version is quite old.

$ sudo kvm | head -1```

QEMU PC emulator version 0.9.1 (kvm-72), Copyright (c) 2003-2008 Fabrice Bellard

```


$ apt-cache policy qemu-kvm```

qemu-kvm:
  Installed: (none)
  Candidate: 0.12.4+dfsg-1~bpo50+1
  Version table:
     0.12.4+dfsg-1~bpo50+1 0
          1 http://www.backports.org lenny-backports/main Packages

```


I tried to upgrade it on System -> Administration -> Synaptic Package Manager```

- qemu-kvm
- qemu-kvm-dbg

```


On marking them to install following warning popup

```

Mark additional required changes?

To be removed
kvm

To be added
libasyncns0
libcap1
libpulse0

```


My questions are;

1)
On deleting the old package whether it would affect the running virtual machine?

2)
Is there any way to come back in case of problem?


Please help.  TIA


B.R.
satimis

---

