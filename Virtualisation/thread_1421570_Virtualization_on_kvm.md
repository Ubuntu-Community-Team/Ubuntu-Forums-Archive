---
title: "Virtualization on kvm"
date: 2010-03-04
forum: Virtualisation
---

### Post by Nick188 on 2010-03-04
Hi,
how can i bind a vm to a specific core or cpu?
Could I assign weights to the vm?

---

### Post by kiranmurari on 2010-03-05
Hi,

You can use virt-install command to create the VM and specify "--cpuset=CPUSET" option to pin down the VM to a specific CPUs, where CPUSET can be a list of numbers or specified in ranges.
   
Hope this helps.

---

### Post by Nick188 on 2010-03-05
Thank's a lot!

---

