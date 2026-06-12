---
title: "mtpscsih: errors"
date: 2009-04-06
forum: Server Platforms
---

### Post by hwennink on 2009-04-06
I have several servers with ubuntu server 8.04 lts on Vmware esx.
On one server i got scsi errors, like

Apr  6 13:21:29 p-oostgelre-data kernel: [1624968.872776] mptscsih: ioc0: task abort: SUCCESS (sc=f7f31a00)
Apr  6 13:21:29 p-oostgelre-data kernel: [1624968.872796] mptscsih: ioc0: attempting task abort! (sc=f7f31b40)
Apr  6 13:21:29 p-oostgelre-data kernel: [1624968.872808] mptscsih: ioc0: task abort: SUCCESS (sc=f7f31b40)
Apr  6 13:21:29 p-oostgelre-data kernel: [1624968.872824] mptscsih: ioc0: attempting task abort! (sc=f7f31dc0)

The server is automatic booting, but stops booting half away. The only thing i can do is power off. After that the server is up and running.
Can someone help me with this problem?

Thanx
Herman Wennink

---

