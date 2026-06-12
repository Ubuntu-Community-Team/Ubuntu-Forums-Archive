---
title: "paxtest 64bit?"
date: 2012-04-23
forum: Security
---

### Post by Hungry Man on 2012-04-23
Where can I find paxtest for 64bit? The default is 32bit, that's all I can find, and it's not going to give accurate results.

---

### Post by rookcifer on 2012-04-24
Try [this script]("http://www.trapkit.de/tools/checksec.html") instead.  It does basically the same thing.

---

### Post by Hungry Man on 2012-04-24
EDIT:

Interesting. Can someone post their vanilla output?

I run it with --kernel and:

> * grsecurity / PaX: Custom GRKERNSEC

  Non-executable kernel pages:            Disabled
  Prevent userspace pointer deref:        Disabled
  Prevent kobject refcount overflow:      Disabled
  Bounds check heap object copies:        Disabled
  Disable writing to kmem/mem/port:       Enabled
  Disable privileged I/O:                 Disabled
  Harden module auto-loading:             Disabled
  Hide kernel symbols:                    Enabled

These are fine and expected... except for the non-executable kernel pages. I have this setting enabled in pax, what's up?

And what is kernheap hardening?

I run it with --proc-all and I get all processes with PAX Disabled.

full kernel output:

>   wpa_supplicant    986 Partial RELRO     Canary found           PaX disabled  No PIE                  
root@colin-vaio:/home/colin/Downloads# ./checksec.sh --kernel
* Kernel protection information:

  Description - List the status of kernel protection mechanisms. Rather than
  inspect kernel mechanisms that may aid in the prevention of exploitation of
  userspace processes, this option lists the status of kernel configuration
  options that harden the kernel itself against attack.

  Kernel config: /boot/config-3.2.16grsec1.4-grsec

  Warning: The config on disk may not represent running kernel config!

  GCC stack protector support:            Enabled
  Strict user copy checks:                Enabled
  Enforce read-only kernel data:          Disabled
  Restrict /dev/mem access:               Enabled
  Restrict /dev/kmem access:              Enabled

* grsecurity / PaX: Custom GRKERNSEC

  Non-executable kernel pages:            Disabled
  Prevent userspace pointer deref:        Disabled
  Prevent kobject refcount overflow:      Disabled
  Bounds check heap object copies:        Disabled
  Disable writing to kmem/mem/port:       Enabled
  Disable privileged I/O:                 Disabled
  Harden module auto-loading:             Disabled
  Hide kernel symbols:                    Enabled


---

### Post by rookcifer on 2012-04-24
Sorry I simply don't have the knowledge of PaX to be able to help.  You might try going to the PaX mailing list directly.  I personally don't use it because I feel the native kernel hardening is good enough (though I realize PaX is stronger).

---

### Post by Hungry Man on 2012-04-24
Would you be able to run the file? That way I can have a "baseline" to compare to. No need to compile pax or any such thing, just cd/ing to it and typing ./checksec.sh --kernel

---

### Post by rookcifer on 2012-04-24
```
Warning: The config on disk may not represent running kernel config!

  GCC stack protector support:            Enabled
  Strict user copy checks:                Disabled
  Enforce read-only kernel data:          Enabled
  Restrict /dev/mem access:               Enabled
  Restrict /dev/kmem access:              Enabled

* grsecurity / PaX: No GRKERNSEC

  The grsecurity / PaX patchset is available here:
    http://grsecurity.net/

* Kernel Heap Hardening: No KERNHEAP

  The KERNHEAP hardening patchset is available here:
    https://www.subreption.com/kernheap/
```

---

### Post by Hungry Man on 2012-04-24
Thank you !

---

