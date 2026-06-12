---
title: "Wine crash"
date: 2009-01-19
forum: Wine
---

### Post by qbox on 2009-01-19
Hi

```
qbox@qbox:~$ wine cfg
fixme:ntdll:NtMakeTemporaryObject (0x4c), stub.
wine: Call from 0x7b844f60 to unimplemented function ntoskrnl.exe.ExInitializeResourceLite, aborting
wine: Unimplemented function ntoskrnl.exe.ExInitializeResourceLite called at address 0x7b844f60 (thread 0014), starting debugger...
wineserver crashed, please enable coredumps (ulimit -c unlimited) and restart.


```

After this program is stopped.
Any solution?

---

### Post by qbox on 2009-01-19
Solved!
Upgrade to 1.1.13

---

