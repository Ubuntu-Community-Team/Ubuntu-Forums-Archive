---
title: "Ubuntu server 20.04 NFS-kernel-server not starting"
date: 2021-01-09
forum: Server Platforms
---

### Post by ccor58 on 2021-01-09
NFS-kernel-server fails to start due to some cyclical startup error apparently related to a slow initial mount -a on start up.
temp fix was to do a manual sudo mount -a then sudo service nfs-kernel-server start then sudo exportfs

Starts the server and enables the shares but is a major pain when server auto starts after a power loss.
Is there any info on this matter to this point I have not seen any improvements after a number of subsequent updates.

Thanks

---

### Post by howefield on 2021-01-09
Thread moved to the "*Server Platforms*" forum.

---

### Post by darkod on 2021-01-09
Is there any specific reason why the mount is so slow? Maybe you can improve that part?

In my case I have a .sh script that does a manual mount I need and after a sleep of 15sec it restarts the nfs-kernel-server service. You could do something similar with a script that runs on boot, adjusted to your scenario.

---

