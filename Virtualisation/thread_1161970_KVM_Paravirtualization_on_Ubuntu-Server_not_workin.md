---
title: "KVM Paravirtualization on Ubuntu-Server not working?"
date: 2009-05-17
forum: Virtualisation
---

### Post by 2shanfernando on 2009-05-17
Hi,

I've been trying to get KVM working on a fresh install of Ubuntu-Server 9.04 on a P5QL-Pro (with a E6750). I know that VT is enabled in the BIOS because I installed XenServer 5.0 earlier and it booted fine. 

After installing Ubuntu 9.04 Server (x64) fresh (so no Xen etc) I installed the necessary components for KVM to work, then on another box installed virt-manager, connected and tried to make a new paravirtualised VM but the option was disabled.

Is there a way of validating if I've done something wrong?

Some info that you may need:
> 
thushan@ZEUSY:~$ grep CONFIG_KVM_GUEST /boot/config-$(uname -r)
CONFIG_KVM_GUEST=y
thushan@ZEUSY:~$ lsmod | grep kvm
kvm_intel              57696  1
kvm                   176624  1 kvm_intel

This is just a test install of Ubuntu Desktop.

Created with:
```


thushan@ZEUSY:~$ sudo virt-install --connect qemu:///system -n UbuntuDesktop -r 1024 --vcpus=1 -f ~/ubuntudesktop.qcow2 -s 12 -c ~/ubuntu-9.04-desktop-i386.iso --vnc --vncport=5900 --noautoconsole --os-type linux --os-variant debianLenny --accelerate --network=bridge:br0 --hvm

```

Instead of the --hvm I tried --paravirtualized but it said:
> 
ERROR    Unsupported virtualization type 'xen'

Heres the capabilities
> 
thushan@ZEUSY:~$ virsh capabilities
Connecting to uri: qemu:///system
<capabilities>

  <host>
    <cpu>
      <arch>x86_64</arch>
    </cpu>
  </host>

  <guest>
    <os_type>hvm</os_type>
    <arch name='i686'>
      <wordsize>32</wordsize>
      <emulator>/usr/bin/kvm</emulator>
      <machine>pc</machine>
      <machine>isapc</machine>
      <domain type='qemu'>
      </domain>
      <domain type='kvm'>
        <emulator>/usr/bin/kvm</emulator>
      </domain>
    </arch>
    <features>
      <pae/>
      <nonpae/>
      <acpi default='on' toggle='yes'/>
      <apic default='on' toggle='no'/>
    </features>
  </guest>

  <guest>
    <os_type>hvm</os_type>
    <arch name='x86_64'>
      <wordsize>64</wordsize>
      <emulator>/usr/bin/kvm</emulator>
      <machine>pc</machine>
      <machine>isapc</machine>
      <domain type='qemu'>
      </domain>
      <domain type='kvm'>
        <emulator>/usr/bin/kvm</emulator>
      </domain>
    </arch>
    <features>
      <acpi default='on' toggle='yes'/>
      <apic default='on' toggle='no'/>
    </features>
  </guest>

</capabilities>


Any ideas?

---

