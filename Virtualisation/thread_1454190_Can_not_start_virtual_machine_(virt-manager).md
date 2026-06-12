---
title: "Can not start virtual machine (virt-manager)"
date: 2010-04-14
forum: Virtualisation
---

### Post by gunksta on 2010-04-14
Using virt-manager and kvm, I have created a virtual machine in /var/lib/libvirt/images. The image is called winxp, but the virtual machine is not the problem.

I can not seem to use virsh or virt-manager to start this virtual image. But, I can start it with 
```
sudo kvm /var/lib/libvirt/images/winxp.img
```

I was pretty confused when I first installed libvirt and I may have messed up my permissions. I have tried setting the group of "images" to root, kvm and libvirtd and now I don't know what the correct setting is.

**Question: ** What do the permissions look like for /var/lib/libvirt/images on a properly configured system? I want to check owner and group.

Once I know for sure that my permissions are right, I'll post the error message that I see.

thanks

---

