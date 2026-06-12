---
title: "ClamAV - clamscan with libclamav error (opcode and bytecode)"
date: 2011-07-23
forum: Security
---

### Post by gyalokai on 2011-07-23
Hello,

after upgrading ClamAV to version 0.97.1 and run the command 

```
clamscan -r -i / --exclude-dir=^/sys --exclude-dir=^/dev --exclude-dir=^/proc | mail -s "clamav scan report XYSERVER" xy@mail.com
```the following errors appeared:

LibClamAV Error: Opcode 20 of type 0 is not implemented yet!
LibClamAV Warning: Bytecode 18 failed to run: Invalid argument passed to function
LibClamAV Error: Opcode 20 of type 0 is not implemented yet!
LibClamAV Warning: Bytecode 18 failed to run: Invalid argument passed to function
LibClamAV Error: Opcode 20 of type 0 is not implemented yet!
LibClamAV Warning: Bytecode 18 failed to run: Invalid argument passed to function
LibClamAV Error: Opcode 20 of type 0 is not implemented yet!
LibClamAV Warning: Bytecode 18 failed to run: Invalid argument passed to function
LibClamAV Error: Opcode 20 of type 0 is not implemented yet!
LibClamAV Warning: Bytecode 18 failed to run: Invalid argument passed to function
LibClamAV Error: Opcode 20 of type 0 is not implemented yet!
LibClamAV Warning: Bytecode 18 failed to run: Invalid argument passed to function
LibClamAV Error: Opcode 20 of type 0 is not implemented yet!
LibClamAV Warning: Bytecode 18 failed to run: Invalid argument passed to function
LibClamAV Error: Opcode 20 of type 0 is not implemented yet!
LibClamAV Warning: Bytecode 18 failed to run: Invalid argument passed to function
LibClamAV Error: Opcode 20 of type 0 is not implemented yet!
LibClamAV Warning: Bytecode 18 failed to run: Invalid argument passed to function
LibClamAV Error: Opcode 20 of type 0 is not implemented yet!
LibClamAV Warning: Bytecode 18 failed to run: Invalid argument passed to function

Does anybody noticed such error lines like that?

My Ubuntu server version: 10.04 (Lucid)
Kernel: Linux 2.6.32-33-generic-pae
All packages are up-to-date.

Could you please help me to analyze and solve this annoying problem? Thanks forward...

---

### Post by gyalokai on 2011-07-25
up

---

### Post by gyalokai on 2011-08-04
Upgrade to version 0.97.2, it solves the problem.

---

### Post by martywd on 2011-08-16
> **gyalokai said:**
> Upgrade to version 0.97.2, it solves the problem.

Thanks for the heads up regarding this issue. Upgrading to 0.97.2 on 10.04.3 LTS fixes this for me, too.

---

