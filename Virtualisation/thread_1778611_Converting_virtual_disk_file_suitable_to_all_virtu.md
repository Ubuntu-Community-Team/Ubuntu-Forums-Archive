---
title: "Converting virtual disk file suitable to all virtualization tools like kvm, xen, etc"
date: 2011-06-09
forum: Virtualisation
---

### Post by linbox289 on 2011-06-09
hi there 

Is there any conversion tool avaliable to convert the file extenstion of virtual disk file of VMware, Xen, KVM, Virtualbox. My requirement is, I will have to migrate a ghost running in vmware to ubuntu server running with kvm. Sometimes vice verse too. So, I would like to know is there a common tool that could covert them.

Thanks in advance !!!

---

### Post by webofunni on 2011-06-09
There are many tutorials in net. Do a google search. VMDK to KVM can be done by

```

qemu-img convert Ubuntu-flat.vmdk -O qcow2 Ubuntu-copy.qemu

```

[https://help.ubuntu.com/community/KVM/FAQ](https://help.ubuntu.com/community/KVM/FAQ)

---

