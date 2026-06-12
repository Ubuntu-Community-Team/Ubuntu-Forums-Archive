---
title: "How to set &quot;Enforce read-only kernel data: Enabled&quot;"
date: 2012-04-29
forum: Security
---

### Post by Hungry Man on 2012-04-29
Running Checksec.sh shows Enforce read-only kernel data: Disabled.

I compile my own kernel, and I'd like to flip this to enabled.

Full list:

 GCC stack protector support:            Enabled
  Strict user copy checks:                Enabled
  Enforce read-only kernel data:          Disabled
  Restrict /dev/mem access:               Enabled
  Restrict /dev/kmem access:              Enabled


Anyone know where this option is?

---

### Post by unspawn on 2012-04-29
> **Hungry Man said:**
> Anyone know where this option is?
Just read the checksec.sh source Luke, it's *CONFIG_DEBUG_RODATA*.

---

### Post by Hungry Man on 2012-04-29
I see. I'll look for that.

---

### Post by Hungry Man on 2012-04-29
I added "CONFIG_DEBUG_RODATA" to the end of my .config file (it didn't exist in it) and set it =y

Still not getting it.

Ideas?

---

### Post by unspawn on 2012-04-29
Just appending the line to your .config won't work because 0) it depends on CONFIG_DEBUG_KERNEL being set and 1) these settings only apply if you recompile the kernel. IMHO you should not enable it just because checksec.sh says it's disabled but because you *understand if and why* you need it.

---

### Post by Hungry Man on 2012-04-29
It's not hard to understand what it is. Checksec is just what let me know that it had been disabled.

CONFIG_DEBUG_KERNEL is set to y.

And I am recompiling the kernel. 3.3.4. The same issue was on 3.2.15 and 3.2.16.

---

