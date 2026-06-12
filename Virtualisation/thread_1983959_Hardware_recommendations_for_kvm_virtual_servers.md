---
title: "Hardware recommendations for kvm virtual servers"
date: 2012-05-21
forum: Virtualisation
---

### Post by David Herring on 2012-05-21
What hardware is best for running KVM virtual machines in the data centre ?

I wish to upgrade some HP DL 380 G5's and Dell poweredge 2950 servers to low pwered more modern (faster ?) servers. What are the potiential gains from this ?

Looked briefly at these servers....

[http://www.rackservers.com/Category.aspx?c=42](http://www.rackservers.com/Category.aspx?c=42)

Could you run on the Atom processor ...16 watts !

Thanks for any advice,
Dave

---

### Post by TheR on 2012-05-21
The only hardware requirement for KVM is that CPU must support hardware virtualization. Which I think Atoms don't.

And as much RAM you need for running virtualized machines. KVM itself doesn't use any more resources than your system does. For example system with GUI requires 500MB for itself.

by
TheR

---

