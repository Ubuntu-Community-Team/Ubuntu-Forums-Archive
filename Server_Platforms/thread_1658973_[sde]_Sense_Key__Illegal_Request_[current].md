---
title: "[sde] Sense Key : Illegal Request [current]"
date: 2011-01-03
forum: Server Platforms
---

### Post by igorm80 on 2011-01-03
Hi, I have an MD3000 storage attached to dell server via sas cables, running ubuntu server.
the kernel keeps throwing these messages every other second on the console, but the drives from MD are fully accessible.

Can someone please help me figuring these messages out?

Thanks!

Jan  3 12:04:24 node2 kernel: [71041.035822] sd 5:0:1:0: [sde] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jan  3 12:04:24 node2 kernel: [71041.035828] sd 5:0:1:0: [sde] Sense Key : Illegal Request [current]
Jan  3 12:04:24 node2 kernel: [71041.035833] sd 5:0:1:0: [sde] <<vendor>> ASC=0x94 ASCQ=0x1ASC=0x94 ASCQ=0x1

---

### Post by europa on 2011-08-29
These errors indicate that the box sent a command that the storage did not understand. It does not necessarily indicate an problem. I have seen this with other Dell-MDxxx devices.

---

