---
title: "Mounting disks in VirtualBox"
date: 2007-12-28
forum: Virtualisation
---

### Post by MarsmanA on 2007-12-28
HI!
I have some problems mounting disks. First, I don't find system>administration>disks on my ubuntu 7.10. How can I access mounting and partitioning then? 

Another question: Is there some problem finding partitions (windows partitions on the same computer and possibly disk) and network computers when you use some virtual machine (I use Virtualbox). Is this possible? Do I have to configure VirtualBox? 

Thanx.

---

### Post by |2eason on 2008-01-03
Well, you can install the partitioner with 'sudo apt-get install gparted', but if it's on a guest OS, it won't help you much as the guest won't see normal partitions and disks. You have to share your 'real' disks via the built in 'shared folder's menu in virtualbox. Then from inside the guest OS you can add the folders as network drives.

---

