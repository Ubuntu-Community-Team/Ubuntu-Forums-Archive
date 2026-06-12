---
title: "Upgrade to 12.10 causes kernel panic in my gentoo KVM guests"
date: 2012-10-24
forum: Virtualisation
---

### Post by psychotix on 2012-10-24
Hi,

I has KVM running lots of different linux guest vm's inc. gentoo.  When I upgraded to ubuntu 12.10, they halt at a kernel panic (see screenshot).  I'm not sure how to trouble shoot this.  All the other vm's redhat, ubuntu work fine.  

Any ideas?

---

### Post by psychotix on 2012-11-20
Not sure if is a optimal fix or not but, I was able to get the gentoo VM's to boot by changing the Processor model to "kvm64".

---

