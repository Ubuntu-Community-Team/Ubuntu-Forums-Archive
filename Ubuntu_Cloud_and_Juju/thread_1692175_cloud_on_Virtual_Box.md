---
title: "cloud on Virtual Box"
date: 2011-02-21
forum: Ubuntu Cloud and Juju
---

### Post by meisel on 2011-02-21
hi,.
whether private cloud can install ubuntu on VirtualBox?

---

### Post by kim0 on 2011-02-21
Hi,

The officially supported configuration needs 2 machines. One acts as NC, the other as CLC/CC/SC/Walrus. The NC machine needs to have CPU virt extensions (Intel VT) so it cannot be a VM itself.

With a lot of hacking however, you may be able to get something working. If you choose to try this route, my article here on running UEC on top of EC2 might be helpful (uses qemu emulator instead of kvm virtualization to avoid VT requirement)

[http://foss-boss.blogspot.com/2010/10/cloud-on-cloud-uec-on-ec2.html](http://foss-boss.blogspot.com/2010/10/cloud-on-cloud-uec-on-ec2.html)

---

### Post by harsh9t on 2011-02-22
thanks kimo that was usefull!

---

