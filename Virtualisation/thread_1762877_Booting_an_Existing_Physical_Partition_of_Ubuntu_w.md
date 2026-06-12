---
title: "Booting an Existing Physical Partition of Ubuntu with KVM"
date: 2011-05-19
forum: Virtualisation
---

### Post by drbrando007 on 2011-05-19
Goal:
Use of KVM to boot a pre-existing, currently viable, Ubuntu partition, that already resides on the host machine's hard drive.

Synopsis:
Ok, I have a laptop computer, so for the sake of this discussion, there will be no option of attaching an additional hard drive, i.e. sdb.
Processors are VT enabled, as is the bios.
Host Machine: Lucid 10.4
Proposed Guest: Maverick 10.10

Maverick is already installed, in a dual boot fashion to a partition of the hard drive, sda. Lucid is installed, in a dual boot fashion, on a partition of the SAME hard drive, sda.

I should already have enough of the correct KVM/QEMU-KVM packages installed on my system in order to accomplish said goal.

I am trying to use Lucid as the host, and the already living Maverick as the guest OS. The ideal method would be through the use of KVM. I have had difficulty finding a concise answer from searching on the web, figured I would try our community.

Thanks-
Dr. TheFugitive

---

