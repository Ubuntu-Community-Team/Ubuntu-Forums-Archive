---
title: "KVM on ubuntu 10.10 server with only one IP available"
date: 2012-04-05
forum: Virtualisation
---

### Post by jbos on 2012-04-05
Hello,
I'm very new to all KVM and I was setting up KVM according to [http://www.howtoforge.com/virtualization-with-kvm-on-ubuntu-10.10](http://www.howtoforge.com/virtualization-with-kvm-on-ubuntu-10.10)

So far it is working fine.

Well, I'm supposed to only use one IP for the entire server. Is there a good concept to handle this restriction (and still keeping the vm accessable from the outside world)?

Thanks,

Jbos

---

### Post by CharlesA on 2012-04-05
Using NAT with port redirection might work.

[http://rcritical.blogspot.com/2011/01/iptables-port-forwarding-to-kvm-virtual.html](http://rcritical.blogspot.com/2011/01/iptables-port-forwarding-to-kvm-virtual.html)

---

### Post by jbos on 2012-04-16
Hi,
thanks, this work fine. I used NAT and iptables to forward ports to the KVM.

Jbos

---

### Post by CharlesA on 2012-04-16
Glad you got it working.

---

