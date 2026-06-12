---
title: "Ubuntu server or enterprise cloud?"
date: 2011-04-27
forum: Ubuntu Cloud and Juju
---

### Post by tushicomeng on 2011-04-27
I want to create a private cloud using ubuntu enterprise cloud. But the main doubt that I have is that should I use ubuntu enterprise cloud or ubuntu server edition as I faced some problems while installing the node in ubuntu enterprise cloud due to virtualisation. This may be due to KVM package. If I would like to use XEN, then what should I do?

---

### Post by kim0 on 2011-05-03
UEC cloud only supports KVM. You can use Xen on its own as a virtualization solution for single servers. Integrating Xen with UEC is not easy :)

---

