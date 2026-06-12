---
title: "Issues with KVM on fresh install of 12.10 64bit"
date: 2013-01-14
forum: Virtualisation
---

### Post by Doctor.Suse on 2013-01-14
I have a fresh install of 12.10 64bit, with a 6 core AMD CPU (see my lshw).
 
i am running into a problem trying to use virt-manager, here is a screenshot: [http://i.imgur.com/2g5bA.png](http://i.imgur.com/2g5bA.png)

here is output of lshw: [http://paste.ubuntu.com/1532944/](http://paste.ubuntu.com/1532944/)

here is output of kvm-ok:
```
INFO: /dev/kvm exists
KVM acceleration can be used
```

ive done googling and forum searching and th best i could come up with was this: [https://bugs.launchpad.net/ubuntu/+source/qemu-kvm/+bug/1021271](https://bugs.launchpad.net/ubuntu/+source/qemu-kvm/+bug/1021271)

but i dont really know how to interpret it sufficiently to fix the problem. 

does anyone know how to fix this?

---

### Post by Doctor.Suse on 2013-01-14
i jumped into the IRC channel and "compdoc" helped me troubleshoot a bit. i ended up doing this:

 i used "sudo cat /etc/group | grep kvm" and "sudo cat /etc/group | grep qemu" and "sudo cat /etc/group | grep libvirt" to find all groups related to my kvm problem, i then added these users to the groups: root, <username>, libvirt-qemu, libvirt-dnsmasq to all the groups

---

### Post by markbl on 2013-01-15
I think you just needed to add your own username to the libvirtd group, i.e.
```

sudo adduser $(id -un) libvirtd

```

See [https://help.ubuntu.com/community/KVM/Installation](https://help.ubuntu.com/community/KVM/Installation)

---

