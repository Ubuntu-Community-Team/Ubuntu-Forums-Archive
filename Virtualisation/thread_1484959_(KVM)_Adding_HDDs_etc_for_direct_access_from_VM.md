---
title: "(KVM) Adding HDDs etc for direct access from VM?"
date: 2010-05-16
forum: Virtualisation
---

### Post by Viper187 on 2010-05-16
I finally got an XP install running on KVM under 10.04. I've seen info on booting from physical partitions, but what about just adding them to the XML file so the guest OS has direct access? I'd rather transfer files back and forth that way than mess with networking. I'd also like to know the right way to add my DVD drive so the guest OS can get direct access to it for reading and burning discs.

---

### Post by Viper187 on 2010-05-19
Ok, this is starting to **** me off. I figured out how to get the VM OS to see a physical partition on the host, but it can't see new files added to the partition after the VM boots. Not only that, but it deleted them on shutdown! What the **** is that? Am I missing something here?

```

  <devices>
    <emulator>/usr/bin/kvm</emulator>
    <disk type='file' device='disk'>
      <driver name='qemu' type='raw'/>
      <source file='/home/viper/vpc/windows.qcow2'/>
      <target dev='hda' bus='ide'/>
    </disk>
    <disk type='file' device='disk'>
      <driver name='qemu' type='raw'/>
      <source file='/dev/sdc1'/>
      <target dev='hdb' bus='ide'/>
    </disk>

```

---

