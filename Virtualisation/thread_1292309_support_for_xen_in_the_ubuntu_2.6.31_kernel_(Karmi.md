---
title: "support for xen in the ubuntu 2.6.31 kernel (Karmic)"
date: 2009-10-15
forum: Virtualisation
---

### Post by pythonscript on 2009-10-15
Will Karmic have support for the xen hypervisor within the 2.6.31 kernel? According to this article

[https://help.ubuntu.com/community/Xen#Installation](https://help.ubuntu.com/community/Xen#Installation)

jaunty doesn't even have full support, but I'm wondering if karmic will because it's supposed to focus more on cloud computing. Thanks!

---

### Post by GigaVolt on 2009-11-01
grep -i xen /boot/config-2.6.31-14-generic-pae 
CONFIG_NETXEN_NIC=m

---

