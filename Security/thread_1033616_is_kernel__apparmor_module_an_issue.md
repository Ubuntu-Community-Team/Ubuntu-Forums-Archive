---
title: "is kernel  apparmor module an issue?"
date: 2009-01-07
forum: Security
---

### Post by pdatta on 2009-01-07
Hi,

I'm using UDP sockets for a USB device driver to communicate between my application server. The driver runs fine in fedora8(no crashes when talking to application). Since I have other issues in fedora8, I'm trying with xubuntu 8.04.

In xubuntu 8.04, The driver log shows these messages. It crashes almost always after starting the application. I don't see these AppArmor hooks in fedora 8. Is this hook call causing kernel to wait and crash?

Please help.

----------------------------------------------

AppArmor Debug: Hook being called from interrupt context

[ 1147.641167] Pid: 4592, comm: Xorg Not tainted 2.6.24-19-generic #1

[ 1147.641191]  [<c01fed33>] aa_revalidate_sk+0xa3/0xb0

---

