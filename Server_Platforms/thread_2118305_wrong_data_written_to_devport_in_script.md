---
title: "wrong data written to /dev/port in script"
date: 2013-02-20
forum: Server Platforms
---

### Post by taiowa on 2013-02-20
using ubuntu server 12.10 as a test platform.

writing a single-bit to the parallel port to signal a controller:

echo -en '\x20' | dd of=/dev/port bs=1 count=1 seek=888

this writes the correct value when issued by single-user root from the console.

when included in any startup script, the value written to the port is not the value in the echo statement...it's instead something like \x2d (the minus character).

scripts tried included rc.local and rc1.d/S90single

any ideas on how to correct?

---

