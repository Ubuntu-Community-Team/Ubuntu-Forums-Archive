---
title: "KVM no DHCP"
date: 2010-03-03
forum: Virtualisation
---

### Post by ZeldeR on 2010-03-03
Hello community,

I want to merge my openvz servers to KVM, but how can I disable DHCP in the KVM and turn off this stupid firewall which is automatic generated. Another question, is it possible to use KVM bridge without IP Adress like openvz bridge venet0?

---

### Post by bodhi.zazen on 2010-03-03
How are you running KVM ?

By default it uses NAT. You would need to make a bridge. With a bridge you then configure your guest's networking.

The specific steps on how to do that will vary if you are using the command line, virsh, or Virt-manager.

---

### Post by ZeldeR on 2010-03-04
very nice explanation:
[http://wiki.libvirt.org/page/Networking](http://wiki.libvirt.org/page/Networking)

---

