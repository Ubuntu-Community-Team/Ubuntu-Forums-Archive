---
title: "No module symbols loaded - kernel modules not enabled"
date: 2008-12-01
forum: Server Platforms
---

### Post by Isomeruk on 2008-12-01
Hi,

For some unknown reason my server machine no longer boots. The problem appears to be due it no longer loading kernel modules.

The apparent offending lines of the kern.log are:

```

Dec 1 23:48:49 server kernel: Inspecting /boot/System.map-2.6.15-26-server
Dec 1 23:48:49 server kernel: Loaded 23239 symbols from /boot/System.map-2.6.15-26-server.
Dec 1 23:48:49 server kernel: Symbols match kernel version 2.6.15.
Dec 1 23:48:49 server kernel: No module symbols loaded - kernel modules not enabled.
Dec 1 23:48:49 server kernel: [42949372.960000] Linux version 2.6.15-26-server(buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 SMP Fri Sep 8 21:00:37 UTC 2006

```

I've not changed anything significant recently. It just stopped booting.

Any help, suggestions, comments, etc appreciated.
Thanks

Edit:

Forgot to mention: the server is runnning Ubuntu 6.06 Dapper, LAMP Server.

---

### Post by Isomeruk on 2008-12-02
I knew there would be a simple fix!

Running depmod -a solved the problem. Still not sure what caused the problem though...

---

