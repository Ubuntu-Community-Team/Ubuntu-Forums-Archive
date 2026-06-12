---
title: "Guest crash ? Memory problem"
date: 2010-06-11
forum: Server Platforms
---

### Post by Adylas on 2010-06-11
Hello,

I am running backuppc in a guest (Ubuntu 10.04 host, Ubuntu 10.04 as guest with latest updates)

As soon as I start a new backup job (it read files on disk to compare with old backup data for incremental) the memory fill (nromal buffer usage) and BOOM I got a Kernel Panic that looks like this :
```

[20588.818138] smbclient: page allocation failure. order:0, mode:0x20
[20588.818148] Pid: 1286, comm: smbclient Not tainted 2.6.32-21-server #32-Ubuntu
[20588.818151] Call Trace:
[20588.818153]  <IRQ> [<ffffffff810f97de>] __alloc_pages_slowpath+0x56e/0x580

```

My swap partition looks good (big empty, well formated and swapon all good)

Anyone has a clue ?

Thanks !

---

### Post by Adylas on 2010-06-14
Any idea ?

---

