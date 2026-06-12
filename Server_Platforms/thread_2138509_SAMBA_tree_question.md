---
title: "SAMBA tree question"
date: 2013-04-24
forum: Server Platforms
---

### Post by rmohan80 on 2013-04-24
I've configured Ubuntu samba but my smbtree shows something very strange as follows:


MSHOME     \\TUX                   tux server (Samba, Ubuntu)         \\TUX\IPC$              IPC Service (tux server (Samba, Ubuntu))         \\TUX\xyx masked download            \\TUX\vuze downloads    VUZE         \\TUX\print$            Printer Drivers

So my question is why is there 2 levels inside the workgroup (MSHOME)? This is causing multiple problems while trying to access via
Windows, viz. i'm unable to use the IP to access the shares, I have to give the name \\Tux\Tux to get the folders -- just giving \\Tux
results in no authentication happening.

Any help would be appreciated

---

