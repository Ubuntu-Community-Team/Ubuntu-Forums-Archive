---
title: "Performance on vmachine off bootable partition"
date: 2008-06-20
forum: Virtualisation
---

### Post by in0ni on 2008-06-20
Does anyone know if there is any performance increase/decrease when running a virtual machine off a bootable partition? Are there any benefits or drawbacks?

Also, for heavy photoshop use (i have already tested alternatives and they do not suit my needs), which would you say gives the best performance? (Xen, VMware, VirtualBox -- have a vt-d cpu & vpro compatible mobo)?

---

### Post by fjgaude on 2008-06-21
I can't see any advantage or disadvantage to running a VM from a bootable drive. If you have more than one disk controller then two disks usually are better than one. I run vmware from a fast boot disk but all the data is on a raid5 array. Works great.

VBox and VMware seemed the same to me when I was testing them about two years, speed, etc. I use VMware because of its reliable copy-paste of text. Notice my signature.

---

### Post by in0ni on 2008-06-21
> **fjgaude said:**
> I can't see any advantage or disadvantage to running a VM from a bootable drive. If you have more than one disk controller then two disks usually are better than one. I run vmware from a fast boot disk but all the data is on a raid5 array. Works great.

VBox and VMware seemed the same to me when I was testing them about two years, speed, etc. I use VMware because of its reliable copy-paste of text. Notice my signature.

Does vmware run from the boot partition or creates an image off the  boot partition? (do you know if vbox does the same?)
main question is that if I decided to just boot from windows for whatever reason, and say i install an application, when i am accessing the partition via the vm will i see my changes? i forgot where, but i think i heard that one of the vms didn't really run off the partition, but created an image from it.

i kinda want to have the flexibility of being able to still boot into windows if i ever really need to, in case i run into any problem with the vm so i can have a functional windows install regardless of the vm.

have you given xen a shot?

oh... and any reason you are running vmware server instead of workstation? isn't vmware workstation a better choice for these types of circumstances, where one guest windows os is the only vm?

---

