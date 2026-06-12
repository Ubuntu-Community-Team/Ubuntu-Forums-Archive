---
title: "SSH Server vs Samba file server"
date: 2008-03-19
forum: Server Platforms
---

### Post by SuperMiguel on 2008-03-19
Whats the advantage or point in using a Samba file server, if with ssh server we can share files??

---

### Post by cybergalvez on 2008-03-19
> **SuperMiguel said:**
> Whats the advantage or point in using a Samba file server, if with ssh server we can share files??


Well if you have to share your ubuntu files with windows then you kind of need a samba server (at least I don't think you can use sshfs on windows) but if you're not doing that then there really is no reason to use it.  I prefer and find better throughput with sshfs

Jose

---

### Post by SuperMiguel on 2008-03-19
software call winscp let u do it

---

### Post by dmizer on 2008-03-20
the primary difference is in scope.

yes, you CAN share files with ssh.  but it does many many more things including remote, encrypted CLI access to your system.  while there is absolutely nothing wrong with using ssh as a file transfer protocol (and in some cases it's preferable to alternatives), it's a bit like using a battleship to cruise across a lake.

whereas, samba and (linux native) NFS protocols are designed specifically for trusted (unencrypted) local network file sharing.

that said, the only reason you would want to use samba would be to allow file sharing with windows computers on your network, or to connect to shares on windows computers in your network.  samba can also be used to provide local network name resolution in lieu of configuring /etc/hosts or configuring a local domain server.

in any case, if ssh/scp is working for you, there's no huge reason to explore samba other than as a learning experience.

---

