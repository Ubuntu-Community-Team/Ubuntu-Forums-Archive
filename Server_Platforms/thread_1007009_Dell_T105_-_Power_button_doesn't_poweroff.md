---
title: "Dell T105 - Power button doesn't poweroff"
date: 2008-12-10
forum: Server Platforms
---

### Post by ripcurl on 2008-12-10
Hi list,

My Dell T105 arrived a few days ago. It's an Opteron 1212 machine with 2GB of memory. I've installed Ubuntu 8.04.1 LTS i386 on it. No problems so far except when pressing the power button at the front panel doesn't poweroff the server. I suspect it's an ACPI problem but I'm not sure. Does anyone else have this issue ? Is there a workaround for this ?

Kernel from dmesg shows:
Linux version 2.6.24-19-server (buildd@terranova) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed Aug 20 23:54:28 UTC 2008 (Ubuntu 2.6.24-19.41-server)

Please let me know if I need to provide anything else. TIA

:w

---

### Post by ripcurl on 2008-12-30
Hi,

To answer my own question, I've managed to resolve this. Apparently Ubuntu Server edition doesn't install the 'acpid' module. Doing a 'sudo apt-get install acpid' fixed it.

The same applies to Dell T100 server and possibly others.

:w

---

