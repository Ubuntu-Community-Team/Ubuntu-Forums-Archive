---
title: "Intestesting: Inconsistency detected by ld.so"
date: 2009-06-06
forum: Server Platforms
---

### Post by Paintrick on 2009-06-06
Hello people,

All of a sudden today i got the following message:
Inconsistency detected by ld.so: ../sysdeps/x86_64/dl-machine.h: 458: elf_machine_rela_relative: Assertion `((reloc->r_info) & 0xffffffff) == 8' failed!

in my log file for apache when i tried to start apache.

and then after that quite some time later,
i tried to run zf.sh script and got the exact same message on screen
not in a logfile this time.

Anyone knows a solution?

---

### Post by martine.ginette on 2009-10-12
Hi!

Same problem! Did you find the solution?

---

