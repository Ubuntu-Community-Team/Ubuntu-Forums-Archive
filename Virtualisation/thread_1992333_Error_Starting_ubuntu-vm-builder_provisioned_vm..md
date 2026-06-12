---
title: "Error Starting ubuntu-vm-builder provisioned vm."
date: 2012-05-31
forum: Virtualisation
---

### Post by d.justins on 2012-05-31
Hi There, 
I'm hitting an error and don't know where to look. 

I'm trying to use kvm on 12.04 server to start a 12.04 VM provisioned with ubuntu-vm-builder. When i try to start the vm with 

```
virsh start TestVM
```

I get the error 

```
libvirtError: internal error cannot load AppArmor profile 'libvirt-5791cafa-366c-eff7-8255-39c3666cce98'
```

I think there's an error in the generation of the apparmor profile but I really don't know where to look. 

Thanks.

---

### Post by d.justins on 2012-05-31
Provisioning with Virt-Install has no issues. So i'm not sure what's up with ubuntu-vm-builder.

---

