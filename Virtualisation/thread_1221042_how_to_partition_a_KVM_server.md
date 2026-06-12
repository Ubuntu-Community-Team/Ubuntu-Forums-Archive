---
title: "how to partition a KVM server?"
date: 2009-07-23
forum: Virtualisation
---

### Post by abraham.varricatt on 2009-07-23
I'll soon be administering an Ubuntu server that I plan to use as a KVM-host. It's going to be a 250GB (hard-disk) system with 8GB RAM. This is how I'm planning to partition it,

/boot    128MB
/           ????
swap     8GB

The ???? is where I need some help. I'm keeping the swap space equal to the amount of system RAM I have. But for the rest, does it make sense to have separate partitions? Like perhaps 100GB for the /var directory?

This system will be used exclusively for KVM-hosting and nothing else.

Any thoughts or comments ?

---

### Post by bodhi.zazen on 2009-07-23
I would either :

1. Make a 10 gb / and a large data partition and a large backup partition for all your guests, the virtual HD, and any backups or templates you wish to keep with kvm.

2. Use LVM and add space as needed. LVM is nice and flexable this way.

---

