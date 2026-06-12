---
title: "nfs not responding"
date: 2008-07-21
forum: Server Platforms
---

### Post by Mr.Jkate on 2008-07-21
Hello, 
I've setup diskless ubuntu client machine. When it boots over netork, it picks up correct linux kernel image and every thing goes fine.
But when it enters in init level 2 and tried to bringups ssh or cups or other services it says NFS not responding and hangs with input/output errorsAny idea ..why it is so?

---

### Post by promodus on 2008-07-22
I'm going to guess your network configuration goes to renew the IP address and breaks the NFS connection.

---

### Post by Mr.Jkate on 2008-07-22
May be you are right. I just removed /nfsroot//etc/rc2.d/S12dbus and it got booted correctly but with one error "Failed to initialized HAL"
Any idea what could be the problem that d-bus might be creating...

---

