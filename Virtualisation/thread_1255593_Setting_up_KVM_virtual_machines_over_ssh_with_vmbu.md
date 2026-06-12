---
title: "Setting up KVM virtual machines over ssh with vmbuilder"
date: 2009-09-01
forum: Virtualisation
---

### Post by DCK on 2009-09-01
Hello all,

I'm a relative newbie when it comes to virtualization. I've found the great guide on the [Ubuntu Server Guide](https://help.ubuntu.com/9.04/serverguide/C/jeos-and-vmbuilder.html) to install a few virtual machines.

Now the execution of the command seems to have produced a proper image, but the rest of the configuration is left out of the tutorial - I don't know how to start the VM from virsh.

There's run.sh created in the same directory as the image but it complains that there's no SDL (which makes sense as I configure all of this over ssh). From what I've understood I need a libvirt configuration XML file to define the VM with virsh. There's no configuration XML file in /etc/libvirt/qemu , and it doesn't make sense no XML file is automagically created with all the config settings I gave the vmbuilder command (and the libvirt XML file won't let me pinpoint the image file anyway).

My config file:
```
[DEFAULT]
arch = amd64
cpus = 2
mem  = 192M
rootsize = 6072
swapsize = 1024

[ubuntu]
suite = jaunty
flavour = virtual
addpkg = acpid, unattended-upgrades

[kvm]
libvirt = qemu:///system
bridge = br0
```

And the creation command:
```

#!/bin/bash
exec vmbuilder kvm ubuntu --config=/vserver/vm.cfg --hostname=dcksx --user=blabla \
--pass=blabla --name=Blabla --mac=bl:bl:bl \
--dest=dcksx-vm --verbose --overwrite

```

After the execution of this command there's a folder dcksx-vm containing a disk0.qcow and run.sh.

I think I'm missing something really obvious here? How do I get this VM up and running in virsh?

---

