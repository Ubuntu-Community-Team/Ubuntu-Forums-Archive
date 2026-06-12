---
title: "Kemu GPU passthrough to W7 VM - Radeon RX 570"
date: 2017-11-22
forum: Virtualisation
---

### Post by jayz99 on 2017-11-22
Hi All,
 
I’m building a new system based on Ubuntu 17.04. I need to retain a Windows environment so decided to VM it via QEMU/KVM. The Windows VM needs to have direct access to the GPU and this is where I ran into problems.
 
In a nutshell:
 
**1.** I blacklisted the amdgpu driver that my RX 570 uses. Ubuntu is left with a Radeon HD5400 running on the radeon driver.
**2.** I succeeded in isolating the GPU from Ubuntu via pci-stub.
**3.** I can pass the GPU and what I think is its HDMI sound device to the VM via virt-manager. Adding both devices as a pci host device.
**4. **Windows 7 VM picks up a single new device.
**5.** Installing the most recent drivers or manufacturer drivers results in a BSOD upon boot – most of the time.
 
I managed to boot into Windows twice with the RX 570 drivers installed. When I did, the system felt slow, laggy and eventually froze. I’m using hugepages, passing CPU cores directly and running OS disk on a SSD. It’s blazing fast running on kemu’s QXL/VGA adapter.
 
There are two variations in my config from most of the guides I found online:
 
**A. **I use pci-stub rather than vfio.
**B.** I use SeaBIOS rather than UEFI.
 
The first difference (A) is a result of following a certain guide (see link below), the second difference (B) is my omission during VM setup. Can someone help me troubleshoot the issue / help me understand where I’ve gone wrong? Specific questions I have:
 
**Q1:** Is the odd Windows behaviour upon passthrough related to the use of SeaBIOS rather than UEFI? I really hope it isn’t. My Windows 7 VM is fully configured and migrating to UEFI would be tough; starting afresh would require rework plus I struggle to boot from the Windows CD with UEFI mode in VM.
 
**Q2: **Is the odd Windows behaviour upon passthrough related to the use of pci-stub rather than vfio? If the role of either is to isolate a device and pass to a VM, then it shouldn’t matter too much which I use?
 
**Q3:** Have I missed anything on the Windows configuration part? It’s got all the updates – required and recommended, drivers, etc. One thing I noticed on Ubuntu is that the GPU is MSI capable but not using it. Quite likely the case in the VM too but can’t tweak the driver settings, hence I can’t tell whether this is MSI related.
 
**Q4:** Do I need separate / dedicated interaction devices? When using the host VGA, I used the same mouse and keyboard and it worked great. In theory, nothing should change when I continue using the same devices, but screen output is delivered via another HDMI port.
 
Main guide I followed: [https://davidyat.es/2016/09/08/gpu-passthrough/](https://davidyat.es/2016/09/08/gpu-passthrough/)
 
**Command outputs:**

[COLOR=#ff0000]uname -a[/COLOR]
```
Linux X 4.10.0-40-generic #44-Ubuntu SMP Thu Nov 9 14:49:09 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux
```

[COLOR=#ff0000]dmesg | grep AMD-Vi[/COLOR]
```
[ 0.984726] AMD-Vi: IOMMU performance counters supported
[ 0.986773] AMD-Vi: Found IOMMU at 0000:00:00.2 cap 0x40
[ 0.986774] AMD-Vi: Extended features (0xf77ef22294ada):
[ 0.986776] AMD-Vi: Interrupt remapping enabled
[ 0.986776] AMD-Vi: virtual APIC enabled
[ 0.986884] AMD-Vi: Lazy IO/TLB flushing enabled
```

[COLOR=#ff0000]lspci | grep VGA[/COLOR]
```
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Ellesmere [Radeon RX 470/480/570/580] (rev ef)
0b:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Cedar [Radeon HD 5000/6000/7350/8350 Series]
```

[COLOR=#ff0000]lsmod | grep vfio[/COLOR]
```
vfio_pci 45056 0
vfio_virqfd 16384 1 vfio_pci
irqbypass 16384 2 kvm,vfio_pci
vfio_iommu_type1 24576 0
vfio 32768 2 vfio_iommu_type1,vfio_pci
```

[COLOR=#ff0000]dmesg | grep pci-stub[/COLOR]
```
[ 0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-4.10.0-40-generic root=UUID=ba28b386-e9e6-4b50-a76e-ccb6b82d846a ro amdgpu.blacklist=1 quiet splash amd_iommu=on pci-stub.ids=1002:67df,1002:aaf0 vt.handoff=7
[ 0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.10.0-40-generic root=UUID=ba28b386-e9e6-4b50-a76e-ccb6b82d846a ro amdgpu.blacklist=1 quiet splash amd_iommu=on pci-stub.ids=1002:67df,1002:aaf0 vt.handoff=7
[ 3.536165] pci-stub: add 1002:67DF sub=FFFFFFFF:FFFFFFFF cls=00000000/00000000
[ 3.536176] pci-stub 0000:01:00.0: claimed by stub
[ 3.536184] pci-stub: add 1002:AAF0 sub=FFFFFFFF:FFFFFFFF cls=00000000/00000000
[ 3.536187] pci-stub 0000:01:00.1: claimed by stub
```

[COLOR=#ff0000]dmesg | grep VFIO[/COLOR]
```
[ 4.131697] VFIO - User Level meta-driver version: 0.3
```

[COLOR=#ff0000]Windows VM config[/COLOR]
```
<domain type='kvm'>
  <name>Win7VM</name>
  <uuid>4553eac9-6699-49d6-b9e7-d520945250dc</uuid>
  <memory unit='KiB'>8388608</memory>
  <currentMemory unit='KiB'>8388608</currentMemory>
  <memoryBacking>
    <hugepages/>
  </memoryBacking>
  <vcpu placement='static' current='6'>12</vcpu>
  <os>
    <type arch='x86_64' machine='pc-i440fx-zesty'>hvm</type>
  </os>
  <features>
    <acpi/>
    <apic/>
    <hyperv>
      <relaxed state='on'/>
      <vapic state='on'/>
      <spinlocks state='on' retries='8191'/>
    </hyperv>
  </features>
  <cpu mode='host-passthrough'>
    <topology sockets='1' cores='6' threads='2'/>
  </cpu>
  <clock offset='localtime'>
    <timer name='rtc' tickpolicy='catchup'/>
    <timer name='pit' tickpolicy='delay'/>
    <timer name='hpet' present='no'/>
    <timer name='hypervclock' present='yes'/>
  </clock>
  <on_poweroff>destroy</on_poweroff>
  <on_reboot>restart</on_reboot>
  <on_crash>restart</on_crash>
  <pm>
    <suspend-to-mem enabled='no'/>
    <suspend-to-disk enabled='no'/>
  </pm>
  <devices>
    <emulator>/usr/bin/kvm-spice</emulator>
    <disk type='file' device='disk'>
      <driver name='qemu' type='raw' cache='none' io='native'/>
      <source file='/vm/WindowsVM/Win7VM_D2.img'/>
      <target dev='vda' bus='virtio'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x08' function='0x0'/>
    </disk>
    <disk type='file' device='disk'>
      <driver name='qemu' type='raw' cache='none' io='native'/>
      <source file='/var/lib/libvirt/images/Win7VM_D1.img'/>
      <target dev='vdb' bus='virtio'/>
      <boot order='1'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x09' function='0x0'/>
    </disk>
    <disk type='block' device='cdrom'>
      <driver name='qemu' type='raw'/>
      <source dev='/dev/sr0'/>
      <target dev='hdb' bus='ide'/>
      <readonly/>
      <address type='drive' controller='0' bus='0' target='0' unit='1'/>
    </disk>
    <controller type='usb' index='0' model='ich9-ehci1'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x05' function='0x7'/>
    </controller>
    <controller type='usb' index='0' model='ich9-uhci1'>
      <master startport='0'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x05' function='0x0' multifunction='on'/>
    </controller>
    <controller type='usb' index='0' model='ich9-uhci2'>
      <master startport='2'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x05' function='0x1'/>
    </controller>
    <controller type='usb' index='0' model='ich9-uhci3'>
      <master startport='4'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x05' function='0x2'/>
    </controller>
    <controller type='pci' index='0' model='pci-root'/>
    <controller type='ide' index='0'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x01' function='0x1'/>
    </controller>
    <controller type='virtio-serial' index='0'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x06' function='0x0'/>
    </controller>
    <interface type='network'>
      <mac address='52:54:00:35:b3:4e'/>
      <source network='default'/>
      <model type='rtl8139'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x03' function='0x0'/>
    </interface>
    <serial type='pty'>
      <target port='0'/>
    </serial>
    <console type='pty'>
      <target type='serial' port='0'/>
    </console>
    <channel type='spicevmc'>
      <target type='virtio' name='com.redhat.spice.0'/>
      <address type='virtio-serial' controller='0' bus='0' port='1'/>
    </channel>
    <input type='mouse' bus='ps2'/>
    <input type='keyboard' bus='ps2'/>
    <graphics type='spice' autoport='yes'>
      <listen type='address'/>
    </graphics>
    <sound model='ich6'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x04' function='0x0'/>
    </sound>
    <video>
      <model type='qxl' ram='65536' vram='65536' vgamem='16384' heads='1' primary='yes'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x02' function='0x0'/>
    </video>
    <hostdev mode='subsystem' type='pci' managed='yes'>
      <source>
        <address domain='0x0000' bus='0x01' slot='0x00' function='0x0'/>
      </source>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x0a' function='0x0'/>
    </hostdev>
    <hostdev mode='subsystem' type='pci' managed='yes'>
      <source>
        <address domain='0x0000' bus='0x01' slot='0x00' function='0x1'/>
      </source>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x0b' function='0x0'/>
    </hostdev>
    <redirdev bus='usb' type='spicevmc'>
      <address type='usb' bus='0' port='2'/>
    </redirdev>
    <redirdev bus='usb' type='spicevmc'>
      <address type='usb' bus='0' port='3'/>
    </redirdev>
    <memballoon model='virtio'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x07' function='0x0'/>
    </memballoon>
  </devices>
</domain>
```

Thanks!
Janusz

---

### Post by KillerKelvUK on 2017-11-23
> Q1: Is the odd Windows behaviour upon passthrough related to the use of SeaBIOS rather than UEFI? I really hope it isn’t. My Windows 7 VM is fully configured and migrating to UEFI would be tough; starting afresh would require rework plus I struggle to boot from the Windows CD with UEFI mode in VM.

If the odd windows behaviour is on your host desktop and something similar to bad colours and lines that doesn't resolve other than via a host reboot then the answer is yes.  This is all about VGA arbitration and how the host sequesters GFX resources on boot and then how the VM attempts to take those resources away when it boots.  UEFI resolves this problem but only if your card has a UEFI GOP I believe.

You can look to reverse in UEFI without a reinstall, its not that difficult.

> Q2: Is the odd Windows behaviour upon passthrough related to the use of pci-stub rather than vfio? If the role of either is to isolate a device and pass to a VM, then it shouldn’t matter too much which I use?

So no, as above.  I would however recommend you switch to vfio-pci as this is a cleaner process and less prone to issues with the PCI devices reacting to having their module/driver changed.

> Q3: Have I missed anything on the Windows configuration part? It’s got all the updates – required and recommended, drivers, etc. One thing I noticed on Ubuntu is that the GPU is MSI capable but not using it. Quite likely the case in the VM too but can’t tweak the driver settings, hence I can’t tell whether this is MSI related.

Can't comment on the Windows config for AMD as mines Nvidia.  However regards the MSI capabilities, this is a common optimisation I believe, I certainly have to address this...simple reg hack to get Windows to load the driver with MSI enabled...[https://ubuntuforums.org/showthread.php?t=2311979&highlight=msi](https://ubuntuforums.org/showthread.php?t=2311979&highlight=msi)

> Q4: Do I need separate / dedicated interaction devices? When using the host VGA, I used the same mouse and keyboard and it worked great. In theory, nothing should change when I continue using the same devices, but screen output is delivered via another HDMI port.

My configuration removes the SPICE display as well as the QXL video virtual devices from the guest configuration, I see these are both still in your config and they could also be causing an issue.  To get keyboard and mouse into the guest...when setting up the guest I simply pass through my hosts USB keyboard and mouse device.  Once the guest is setup I then use Synergy ([https://symless.com/synergy](https://symless.com/synergy)) to share host keyboard and mouse with the guest.

---

### Post by ODTech on 2017-11-23
> **jayz99 said:**
> Hi All,
 
I’m building a new system based on Ubuntu 17.04. I need to retain a Windows environment so decided to VM it via QEMU/KVM. The Windows VM needs to have direct access to the GPU and this is where I ran into problems.
 
In a nutshell:
 
**1.** I blacklisted the amdgpu driver that my RX 570 uses. Ubuntu is left with a Radeon HD5400 running on the radeon driver.
**2.** I succeeded in isolating the GPU from Ubuntu via pci-stub.
**3.** I can pass the GPU and what I think is its HDMI sound device to the VM via virt-manager. Adding both devices as a pci host device.
**4. **Windows 7 VM picks up a single new device.
**5.** Installing the most recent drivers or manufacturer drivers results in a BSOD upon boot – most of the time.
 
I managed to boot into Windows twice with the RX 570 drivers installed. When I did, the system felt slow, laggy and eventually froze. I’m using hugepages, passing CPU cores directly and running OS disk on a SSD. It’s blazing fast running on kemu’s QXL/VGA adapter.
 
There are two variations in my config from most of the guides I found online:
 
**A. **I use pci-stub rather than vfio.
**B.** I use SeaBIOS rather than UEFI.
 
The first difference (A) is a result of following a certain guide (see link below), the second difference (B) is my omission during VM setup. Can someone help me troubleshoot the issue / help me understand where I’ve gone wrong? Specific questions I have:
 
**Q1:** Is the odd Windows behaviour upon passthrough related to the use of SeaBIOS rather than UEFI? I really hope it isn’t. My Windows 7 VM is fully configured and migrating to UEFI would be tough; starting afresh would require rework plus I struggle to boot from the Windows CD with UEFI mode in VM.
 
**Q2: **Is the odd Windows behaviour upon passthrough related to the use of pci-stub rather than vfio? If the role of either is to isolate a device and pass to a VM, then it shouldn’t matter too much which I use?
 
**Q3:** Have I missed anything on the Windows configuration part? It’s got all the updates – required and recommended, drivers, etc. One thing I noticed on Ubuntu is that the GPU is MSI capable but not using it. Quite likely the case in the VM too but can’t tweak the driver settings, hence I can’t tell whether this is MSI related.
 
**Q4:** Do I need separate / dedicated interaction devices? When using the host VGA, I used the same mouse and keyboard and it worked great. In theory, nothing should change when I continue using the same devices, but screen output is delivered via another HDMI port.
 
Main guide I followed: [https://davidyat.es/2016/09/08/gpu-passthrough/](https://davidyat.es/2016/09/08/gpu-passthrough/)
 
**Command outputs:**

[COLOR=#ff0000]uname -a[/COLOR]
```
Linux X 4.10.0-40-generic #44-Ubuntu SMP Thu Nov 9 14:49:09 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux
```

[COLOR=#ff0000]dmesg | grep AMD-Vi[/COLOR]
```
[ 0.984726] AMD-Vi: IOMMU performance counters supported
[ 0.986773] AMD-Vi: Found IOMMU at 0000:00:00.2 cap 0x40
[ 0.986774] AMD-Vi: Extended features (0xf77ef22294ada):
[ 0.986776] AMD-Vi: Interrupt remapping enabled
[ 0.986776] AMD-Vi: virtual APIC enabled
[ 0.986884] AMD-Vi: Lazy IO/TLB flushing enabled
```

[COLOR=#ff0000]lspci | grep VGA[/COLOR]
```
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Ellesmere [Radeon RX 470/480/570/580] (rev ef)
0b:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Cedar [Radeon HD 5000/6000/7350/8350 Series]
```

[COLOR=#ff0000]lsmod | grep vfio[/COLOR]
```
vfio_pci 45056 0
vfio_virqfd 16384 1 vfio_pci
irqbypass 16384 2 kvm,vfio_pci
vfio_iommu_type1 24576 0
vfio 32768 2 vfio_iommu_type1,vfio_pci
```

[COLOR=#ff0000]dmesg | grep pci-stub[/COLOR]
```
[ 0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-4.10.0-40-generic root=UUID=ba28b386-e9e6-4b50-a76e-ccb6b82d846a ro amdgpu.blacklist=1 quiet splash amd_iommu=on pci-stub.ids=1002:67df,1002:aaf0 vt.handoff=7
[ 0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.10.0-40-generic root=UUID=ba28b386-e9e6-4b50-a76e-ccb6b82d846a ro amdgpu.blacklist=1 quiet splash amd_iommu=on pci-stub.ids=1002:67df,1002:aaf0 vt.handoff=7
[ 3.536165] pci-stub: add 1002:67DF sub=FFFFFFFF:FFFFFFFF cls=00000000/00000000
[ 3.536176] pci-stub 0000:01:00.0: claimed by stub
[ 3.536184] pci-stub: add 1002:AAF0 sub=FFFFFFFF:FFFFFFFF cls=00000000/00000000
[ 3.536187] pci-stub 0000:01:00.1: claimed by stub
```

[COLOR=#ff0000]dmesg | grep VFIO[/COLOR]
```
[ 4.131697] VFIO - User Level meta-driver version: 0.3
```

[COLOR=#ff0000]Windows VM config[/COLOR]
```
<domain type='kvm'>
  <name>Win7VM</name>
  <uuid>4553eac9-6699-49d6-b9e7-d520945250dc</uuid>
  <memory unit='KiB'>8388608</memory>
  <currentMemory unit='KiB'>8388608</currentMemory>
  <memoryBacking>
    <hugepages/>
  </memoryBacking>
  <vcpu placement='static' current='6'>12</vcpu>
  <os>
    <type arch='x86_64' machine='pc-i440fx-zesty'>hvm</type>
  </os>
  <features>
    <acpi/>
    <apic/>
    <hyperv>
      <relaxed state='on'/>
      <vapic state='on'/>
      <spinlocks state='on' retries='8191'/>
    </hyperv>
  </features>
  <cpu mode='host-passthrough'>
    <topology sockets='1' cores='6' threads='2'/>
  </cpu>
  <clock offset='localtime'>
    <timer name='rtc' tickpolicy='catchup'/>
    <timer name='pit' tickpolicy='delay'/>
    <timer name='hpet' present='no'/>
    <timer name='hypervclock' present='yes'/>
  </clock>
  <on_poweroff>destroy</on_poweroff>
  <on_reboot>restart</on_reboot>
  <on_crash>restart</on_crash>
  <pm>
    <suspend-to-mem enabled='no'/>
    <suspend-to-disk enabled='no'/>
  </pm>
  <devices>
    <emulator>/usr/bin/kvm-spice</emulator>
    <disk type='file' device='disk'>
      <driver name='qemu' type='raw' cache='none' io='native'/>
      <source file='/vm/WindowsVM/Win7VM_D2.img'/>
      <target dev='vda' bus='virtio'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x08' function='0x0'/>
    </disk>
    <disk type='file' device='disk'>
      <driver name='qemu' type='raw' cache='none' io='native'/>
      <source file='/var/lib/libvirt/images/Win7VM_D1.img'/>
      <target dev='vdb' bus='virtio'/>
      <boot order='1'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x09' function='0x0'/>
    </disk>
    <disk type='block' device='cdrom'>
      <driver name='qemu' type='raw'/>
      <source dev='/dev/sr0'/>
      <target dev='hdb' bus='ide'/>
      <readonly/>
      <address type='drive' controller='0' bus='0' target='0' unit='1'/>
    </disk>
    <controller type='usb' index='0' model='ich9-ehci1'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x05' function='0x7'/>
    </controller>
    <controller type='usb' index='0' model='ich9-uhci1'>
      <master startport='0'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x05' function='0x0' multifunction='on'/>
    </controller>
    <controller type='usb' index='0' model='ich9-uhci2'>
      <master startport='2'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x05' function='0x1'/>
    </controller>
    <controller type='usb' index='0' model='ich9-uhci3'>
      <master startport='4'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x05' function='0x2'/>
    </controller>
    <controller type='pci' index='0' model='pci-root'/>
    <controller type='ide' index='0'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x01' function='0x1'/>
    </controller>
    <controller type='virtio-serial' index='0'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x06' function='0x0'/>
    </controller>
    <interface type='network'>
      <mac address='52:54:00:35:b3:4e'/>
      <source network='default'/>
      <model type='rtl8139'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x03' function='0x0'/>
    </interface>
    <serial type='pty'>
      <target port='0'/>
    </serial>
    <console type='pty'>
      <target type='serial' port='0'/>
    </console>
    <channel type='spicevmc'>
      <target type='virtio' name='com.redhat.spice.0'/>
      <address type='virtio-serial' controller='0' bus='0' port='1'/>
    </channel>
    <input type='mouse' bus='ps2'/>
    <input type='keyboard' bus='ps2'/>
    <graphics type='spice' autoport='yes'>
      <listen type='address'/>
    </graphics>
    <sound model='ich6'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x04' function='0x0'/>
    </sound>
    <video>
      <model type='qxl' ram='65536' vram='65536' vgamem='16384' heads='1' primary='yes'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x02' function='0x0'/>
    </video>
    <hostdev mode='subsystem' type='pci' managed='yes'>
      <source>
        <address domain='0x0000' bus='0x01' slot='0x00' function='0x0'/>
      </source>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x0a' function='0x0'/>
    </hostdev>
    <hostdev mode='subsystem' type='pci' managed='yes'>
      <source>
        <address domain='0x0000' bus='0x01' slot='0x00' function='0x1'/>
      </source>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x0b' function='0x0'/>
    </hostdev>
    <redirdev bus='usb' type='spicevmc'>
      <address type='usb' bus='0' port='2'/>
    </redirdev>
    <redirdev bus='usb' type='spicevmc'>
      <address type='usb' bus='0' port='3'/>
    </redirdev>
    <memballoon model='virtio'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x07' function='0x0'/>
    </memballoon>
  </devices>
</domain>
```

Thanks!
Janusz

I will just leave this here, maybe it helps you. The guide is based on qemu kvm and does not use virtmanager.

> Important: Several users passing through Radeon RX 480 and Radeon RX 470 cards have reported reboot loops after updating and installing the Radeon drivers. If you pass through a Radeon graphics card, it is better to replace the -machine line in the startup script with the following line:

-machine type=pc,accel=kvm
to use the default i440fx emulation.

Source: [https://forums.linuxmint.com/viewtopic.php?f=231&t=212692](https://forums.linuxmint.com/viewtopic.php?f=231&t=212692)

---

### Post by jayz99 on 2017-11-25
Thanks both. So I'm now capturing the devices using vfio-pci; Windows seems slightly more stable now. I can boot into the system and it takes about 10-15 seconds post boot for things to start grinding to a halt. I can't really run any diagnostics on Windows in that time.

[COLOR=#ff0000]lspci -k[/COLOR]
```
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Ellesmere [Radeon RX 470/480/570/580] (rev ef)
    Subsystem: ASUSTeK Computer Inc. Ellesmere [Radeon RX 470/480]
    Kernel driver in use: vfio-pci
    Kernel modules: amdgpu
01:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Ellesmere [Radeon RX 580]
    Subsystem: ASUSTeK Computer Inc. Device aaf0
    Kernel driver in use: vfio-pci
    Kernel modules: snd_hda_intel
```

Next thing I should probably try is using UEFI. I've got the following options the way I see it:

**1. **Create another OS instance with UEFI and test passthrough there. The preferred option, however, no matter what I do, I can't seem to get the UEFI shell to boot any of my devices - CD, USB, does not see OS images either. 
**2. **Migrate current VM MBR drive to GPT and convert the installation to UEFI type. So that's a maybe but I've got no guarantee the OVMF ecosystem is functioning given odd behavior during fresh install attempt.

So far I've been using virt-manager - perhaps this is contributing to the problem? OK:

**3.** Created the following VM config using the Mint tutorial you posted earlier. When attempting to run the script the reply I get is:

qemu-system-x86_64: cpu topology: sockets (1) * cores (6) * threads (2) > maxcpus (6)
./runvm.sh: line 35: -device: command not found
./runvm.sh: line 44: -netdev: command not found

```
#!/bin/bash


vmname="Windows7"


if ps -A | grep -q $vmname; then
   echo "$vmname is already running." &
   exit 1


else


# use pulseaudio
export QEMU_AUDIO_DRV=pa
export QEMU_PA_SAMPLES=8192
export QEMU_AUDIO_TIMER_PERIOD=99
export QEMU_PA_SERVER=/run/user/1000/pulse/native


cp /usr/share/OVMF/OVMF_VARS.fd /tmp/my_vars.fd


qemu-system-x86_64 \
  -name $vmname,process=$vmname \
  -machine type=q35,accel=kvm \
  -cpu host,kvm=off \
  -smp 6,sockets=1,cores=6,threads=2 \
  -m 8G \
  -mem-path /run/hugepages/kvm \
  -mem-prealloc \
  -balloon none \
  -rtc clock=host,base=localtime \
  -vga none \
  -nographic \
  -serial none \
  -parallel none \
  -soundhw hda \
  -usb -usbdevice host:046d:c062 -usbdevice host:045e:0745 \ 
  -device vfio-pci,host=01:00.0,multifunction=on \
  -device vfio-pci,host=01:00.1 \
  -drive if=pflash,format=raw,readonly,file=/usr/share/OVMF/OVMF_CODE.fd \
  -drive if=pflash,format=raw,file=/tmp/my_vars.fd \
  -boot order=dc \
  -drive id=disk0,if=virtio,cache=none,io=native,format=raw,file=/var/lib/libvirt/images/Win7VM_D1.img \
  -drive id=disk1,if=virtio,cache=none,io=native,format=raw,file=/vm/WindowsVM/Win7VM_D2.img \
  #-drive file=/home/user/ISOs/win10.iso,index=3,media=cdrom \
  #-drive file=/home/user/Downloads/virtio-win-0.1.140.iso,index=4,media=cdrom \
  -netdev type=tap,id=net0,ifname=tap0,vhost=on \
  -device virtio-net-pci,netdev=net0,mac=00:16:3e:00:01:01


   exit 0
fi
```

**4. **Noticed the 'vga none' in the VM script above. Perhaps I could replicate that in virt-manager? virsh edit etc. Despite removing the vga section, virt-manager adds it in whenever VM is started. *Sigh* I was hoping maybe it's the virtualised VGA device that's causing problems for the RX 570.

Where have I gone wrong? :)

---

### Post by KillerKelvUK on 2017-11-26
> however, no matter what I do, I can't seem to get the UEFI shell to boot any of my devices - CD, USB, does not see OS images either

So this should not be an issue, if you are using 17.04 stock binaries installed from Ubuntu's ppa?  My usual config see's the disk using virtio (which your original XML had the same) and then the CDROM device I specify as SATA, it could be your OVMF VARs file has some bad config in from all your attempts, you could try and delete it and create it from new (just cp from /usr/share/OVMF/OVMF/OVMF_VARS.fd ensuring you keep the filename as per the original).  Also if youre getting to the UEFI shell you can "exit" into the UEFI manager and try adding the boot device appropriate to your source.  For me in my OVMF w/ Q35 none of this was needed but I note another forum member has advised i440fx for AMD compatibility...you should be able to work out these kinks easy enough.

> Noticed the 'vga none' in the VM script above. Perhaps I could replicate that in virt-manager? virsh edit etc. Despite removing the vga section, virt-manager adds it in whenever VM is started. *Sigh* I was hoping maybe it's the virtualised VGA device that's causing problems for the RX 570.

So you can do this in virt-manager, you just have to ensure both the video AND display devices are removed as adding/keeping one has a dependency on the other and virt-manager will enforce dependencies.

Regards using the Mint tutorial, its good and if you prefer cmdline environments there is nothing wrong with it.  However cmdline for the inexperienced isn't the easiest to pick up, I'm not diminishing it as its a necessary capability for effective linux administration and customisation...however to get you up and running I'd recommend sticking with one specific approach and refining, the fact you got a guest up and running with passthrough is a success, switching strategies on failure should really be a last resort IMO.

---

### Post by ODTech on 2017-11-26
> **jayz99 said:**
> Thanks both. So I'm now capturing the devices using vfio-pci; Windows seems slightly more stable now. I can boot into the system and it takes about 10-15 seconds post boot for things to start grinding to a halt. I can't really run any diagnostics on Windows in that time.

[COLOR=#ff0000]lspci -k[/COLOR]
```
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Ellesmere [Radeon RX 470/480/570/580] (rev ef)
    Subsystem: ASUSTeK Computer Inc. Ellesmere [Radeon RX 470/480]
    Kernel driver in use: vfio-pci
    Kernel modules: amdgpu
01:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Ellesmere [Radeon RX 580]
    Subsystem: ASUSTeK Computer Inc. Device aaf0
    Kernel driver in use: vfio-pci
    Kernel modules: snd_hda_intel
```

Next thing I should probably try is using UEFI. I've got the following options the way I see it:

**1. **Create another OS instance with UEFI and test passthrough there. The preferred option, however, no matter what I do, I can't seem to get the UEFI shell to boot any of my devices - CD, USB, does not see OS images either. 
**2. **Migrate current VM MBR drive to GPT and convert the installation to UEFI type. So that's a maybe but I've got no guarantee the OVMF ecosystem is functioning given odd behavior during fresh install attempt.

So far I've been using virt-manager - perhaps this is contributing to the problem? OK:

**3.** Created the following VM config using the Mint tutorial you posted earlier. When attempting to run the script the reply I get is:

qemu-system-x86_64: cpu topology: sockets (1) * cores (6) * threads (2) > maxcpus (6)
./runvm.sh: line 35: -device: command not found
./runvm.sh: line 44: -netdev: command not found

```
#!/bin/bash


vmname="Windows7"


if ps -A | grep -q $vmname; then
   echo "$vmname is already running." &
   exit 1


else


# use pulseaudio
export QEMU_AUDIO_DRV=pa
export QEMU_PA_SAMPLES=8192
export QEMU_AUDIO_TIMER_PERIOD=99
export QEMU_PA_SERVER=/run/user/1000/pulse/native


cp /usr/share/OVMF/OVMF_VARS.fd /tmp/my_vars.fd


qemu-system-x86_64 \
  -name $vmname,process=$vmname \
  -machine type=q35,accel=kvm \
  -cpu host,kvm=off \
  -smp 6,sockets=1,cores=6,threads=2 \
  -m 8G \
  -mem-path /run/hugepages/kvm \
  -mem-prealloc \
  -balloon none \
  -rtc clock=host,base=localtime \
  -vga none \
  -nographic \
  -serial none \
  -parallel none \
  -soundhw hda \
  -usb -usbdevice host:046d:c062 -usbdevice host:045e:0745 \ 
  -device vfio-pci,host=01:00.0,multifunction=on \
  -device vfio-pci,host=01:00.1 \
  -drive if=pflash,format=raw,readonly,file=/usr/share/OVMF/OVMF_CODE.fd \
  -drive if=pflash,format=raw,file=/tmp/my_vars.fd \
  -boot order=dc \
  -drive id=disk0,if=virtio,cache=none,io=native,format=raw,file=/var/lib/libvirt/images/Win7VM_D1.img \
  -drive id=disk1,if=virtio,cache=none,io=native,format=raw,file=/vm/WindowsVM/Win7VM_D2.img \
  #-drive file=/home/user/ISOs/win10.iso,index=3,media=cdrom \
  #-drive file=/home/user/Downloads/virtio-win-0.1.140.iso,index=4,media=cdrom \
  -netdev type=tap,id=net0,ifname=tap0,vhost=on \
  -device virtio-net-pci,netdev=net0,mac=00:16:3e:00:01:01


   exit 0
fi
```

**4. **Noticed the 'vga none' in the VM script above. Perhaps I could replicate that in virt-manager? virsh edit etc. Despite removing the vga section, virt-manager adds it in whenever VM is started. *Sigh* I was hoping maybe it's the virtualised VGA device that's causing problems for the RX 570.

Where have I gone wrong? :)

Placing comments midway through the qemu script interrupts the script. Either remove the lines or move them to the bottom of the script.

---

### Post by jayz99 on 2017-12-02
[FONT=trebuchet ms]Thanks Both. Here's what I tried:[B]

1.[/B] Same config (**virt-manager, i440fx, SeaBIOS**) – I looked into the VM config and was able to delete the VGA when I got rid of Spice display as well – thanks. Problem is I can’t view anything that way. The RX 570 clearly isn’t initialised early enough or used as a VGA – HDMI output is blank.
 
**2.** Confirmed vfio-pci enables the GPU when VM is started. So this is definitely not on Linux side – device is intercepted on boot, enabled when VM starts and passed through to the VM.
 
**3.** New VM (**virt-manager, Q35, OVMF**) – Finally managed to install UEFI W7. Knew about the boot manager but my images must’ve been the problem. Removed VGA and Spice display. Windows stuck at boot logo but clearly getting output from HDMI / RX 570.
 
**4.** New VM (**virt-manager, i440fx, OVMF**) – No VGA and no displays. Boot is fine but when I arrive at the desktop, it's grinding to a halt and as slow as i440fx on SeaBIOS.
 
**5.** Config as per points 1,3 and 4 but removed the GPU sound device – made no difference to any of the options.

**6.** Finally, removed comments from QEMU launch script – output upon running it is as follows:
 
```
qemu-system-x86_64: cpu topology: sockets (1) * cores (6) * threads (2) > maxcpus (6)
./runvm.sh: line 35: -device: command not found
```
 
I.e. the '-device vfio-pci,host=01:00.0,multifunction=on \' device. Why? The device is confirmed intercepted by vfio-pci, plus I can see it under the Windows VM.

I'm really close - I can see the GPU run. In the first instance, it boots ok and then gets hyper slow. In the second instance it's stuck at boot. Any ideas what I could try to make either configuration work?

Janusz

[/FONT]

---

### Post by ODTech on 2017-12-03
> **jayz99 said:**
> [FONT=trebuchet ms]Thanks Both. Here's what I tried:[B]

1.[/B] Same config (**virt-manager, i440fx, SeaBIOS**) – I looked into the VM config and was able to delete the VGA when I got rid of Spice display as well – thanks. Problem is I can’t view anything that way. The RX 570 clearly isn’t initialised early enough or used as a VGA – HDMI output is blank.
 
**2.** Confirmed vfio-pci enables the GPU when VM is started. So this is definitely not on Linux side – device is intercepted on boot, enabled when VM starts and passed through to the VM.
 
**3.** New VM (**virt-manager, Q35, OVMF**) – Finally managed to install UEFI W7. Knew about the boot manager but my images must’ve been the problem. Removed VGA and Spice display. Windows stuck at boot logo but clearly getting output from HDMI / RX 570.
 
**4.** New VM (**virt-manager, i440fx, OVMF**) – No VGA and no displays. Boot is fine but when I arrive at the desktop, it's grinding to a halt and as slow as i440fx on SeaBIOS.
 
**5.** Config as per points 1,3 and 4 but removed the GPU sound device – made no difference to any of the options.

**6.** Finally, removed comments from QEMU launch script – output upon running it is as follows:
 
```
qemu-system-x86_64: cpu topology: sockets (1) * cores (6) * threads (2) > maxcpus (6)
./runvm.sh: line 35: -device: command not found
```
 
I.e. the '-device vfio-pci,host=01:00.0,multifunction=on \' device. Why? The device is confirmed intercepted by vfio-pci, plus I can see it under the Windows VM.

I'm really close - I can see the GPU run. In the first instance, it boots ok and then gets hyper slow. In the second instance it's stuck at boot. Any ideas what I could try to make either configuration work?

Janusz

[/FONT]

What is the full specs and models of the host hardware?

---

### Post by jayz99 on 2017-12-03
[LIST]
[*]AMD - Ryzen 5 1600 3.2GHz 6-Core Processor
[*]ASRock - AB350 Pro4 ATX AM4 Motherboard
[*]Corsair - Vengeance LPX 16GB (2 x 8GB) DDR4-2666 Memory
[*]Crucial - MX300 275GB M.2-2280 Solid State Drive
[*]Seagate - BarraCuda 1TB 3.5" 7200RPM Internal Hard Drive
[*]XFX - Radeon HD 5400 1 GB (host VGA)
[*]Asus - Radeon RX 570 4GB ROG STRIX Video Card (target VM VGA)
[*]LG - 23MP68VQ-P 23.0" 1920x1080 60Hz Monitor (listing because it uses FreeSync... and it seems that the 'griding to a halt' part in the VM might be a sudden drop in refresh rate)
[/LIST]

---

### Post by ODTech on 2017-12-03
> **jayz99 said:**
> [LIST]
[*]AMD - Ryzen 5 1600 3.2GHz 6-Core Processor
[*]ASRock - AB350 Pro4 ATX AM4 Motherboard
[*]Corsair - Vengeance LPX 16GB (2 x 8GB) DDR4-2666 Memory
[*]Crucial - MX300 275GB M.2-2280 Solid State Drive
[*]Seagate - BarraCuda 1TB 3.5" 7200RPM Internal Hard Drive
[*]XFX - Radeon HD 5400 1 GB (host VGA)
[*]Asus - Radeon RX 570 4GB ROG STRIX Video Card (target VM VGA)
[*]LG - 23MP68VQ-P 23.0" 1920x1080 60Hz Monitor (listing because it uses FreeSync... and it seems that the 'griding to a halt' part in the VM might be a sudden drop in refresh rate)
[/LIST]

Kernel version?

There's a guy on the mint forum also using a ryzen system that has the same problem as you.
He updated his kernel to 4.12 and updated qemu to 2.6 with this ppa.
[HTML]https://launchpad.net/~jacob/+archive/ubuntu/virtualisation[/HTML]
If you are going to stick with kvm and virtmanager  you can obviously skip the qemu update.

Edit:
[https://forums.linuxmint.com/viewtopic.php?f=231&t=212692&p=1335698&hilit=radeon#p1335698](https://forums.linuxmint.com/viewtopic.php?f=231&t=212692&p=1335698&hilit=radeon#p1335698)
User procabiak

---

### Post by ODTech on 2017-12-03
I just noticed the jacob ppa also has a version of virt-manager and libvirt so i guess it's worth a try to update those two packages from the ppa too.

---

### Post by KillerKelvUK on 2017-12-03
Okay so I think you cracked it with your test scenario #3...

> 3. New VM (virt-manager, Q35, OVMF) – Finally managed to install UEFI W7. Knew about the boot manager but my images must’ve been the problem. Removed VGA and Spice display. Windows stuck at boot logo but clearly getting output from HDMI / RX 570.

Windows 7 doesn't boot as a KVM guest using Q35, OVMF and QXL gfx...were you attempting to setup the guest OS before adding in the pass through card?  Switch to W10 and I'm guessing this scenario will work?

---

### Post by jayz99 on 2017-12-03
[COLOR=#ff0000]uname -a[/COLOR]
[COLOR=#000000]Code:
Linux X 4.10.0-40-generic #44-Ubuntu SMP Thu Nov 9 14:49:09 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux[/COLOR]
Thanks! I'll check it out and report back.

---

### Post by jayz99 on 2017-12-06
OK so I tried this:

**1. i440fx, OVMF **-> installed W7 previously but it did not work. Upgraded to W10 - GPU recognised, output on HDMI but suddenly the system froze and a few seconds the host died too. It seems this behaviour might be related to the "[Windows (10?) guest freezes entire host on shutdown if using PCI passthrough]("https://bugs.launchpad.net/qemu/+bug/1580459")" bug. See the host syslog below.

**2. Q35, OVMF **-> fresh install of W7 does not boot. This happens during the very first HDD boot, immediately post install.

**3. Q35, OVMF -**> fresh install of W10. Crashed immediately post driver installation. Upon VGA/display removal, boots up fine but stays on desktop for 10-15 seconds and BSOD stating video tdr failure as the reason. I've added a TdrDelay=8 value to W10 registry to give the GPU a grace period to respond - didn't help. Tried minimal and full Radeon driver install.

[COLOR=#ff0000]**4. Kernel update to 4.14 and motherboard UEFI update **[/COLOR](to get AGESA 1.0.0.6+). Using VM config from (3) above, I'm pleasantly surprised to report that this seems to have done the trick! I clocked 10 min in W10 and saw no problems with my RX 570 being recognized and used by the system! [Btw. I also disabled the AMD Event Service in W10 previously] I'll do some thorough testing tomorrow and report back.

I really appreciate your help - thank you!

Syslog:
```
Dec  5 21:50:59 BlueRidge kernel: [ 1850.863186] audit: type=1400 audit(1512510659.957:29): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="libvirt-4553eac9-6699-49d6-b9e7-d520945250dc" pid=4435 comm="apparmor_parser"
Dec  5 21:50:59 BlueRidge libvirtd[1211]: Domain id=2 name='Win7VM' uuid=4553eac9-6699-49d6-b9e7-d520945250dc is tainted: host-cpu
Dec  5 21:51:00 BlueRidge libvirtd[1211]: internal error: unknown CPU feature __kvm_hv_spinlocks
Dec  5 21:51:00 BlueRidge virtlogd[3211]: End of file while reading data: Input/output error
Dec  5 21:51:00 BlueRidge virt-manager[3151]: Drawing a gadget with negative dimensions. Did you forget to allocate a size? (node box owner virtManager+autodrawer+AutoDrawer)
Dec  5 21:51:01 BlueRidge virt-manager[3151]: message repeated 5 times: [ Drawing a gadget with negative dimensions. Did you forget to allocate a size? (node box owner virtManager+autodrawer+AutoDrawer)]
Dec  5 21:51:01 BlueRidge avahi-daemon[1100]: Joining mDNS multicast group on interface vnet0.IPv6 with address fe80::fc54:ff:fe35:b34e.
Dec  5 21:51:01 BlueRidge avahi-daemon[1100]: New relevant interface vnet0.IPv6 for mDNS.
Dec  5 21:51:01 BlueRidge avahi-daemon[1100]: Registering new address record for fe80::fc54:ff:fe35:b34e on vnet0.*.
Dec  5 21:51:01 BlueRidge virt-manager[3151]: Drawing a gadget with negative dimensions. Did you forget to allocate a size? (node box owner virtManager+autodrawer+AutoDrawer)
Dec  5 21:51:01 BlueRidge kernel: [ 1852.587935] virbr0: port 2(vnet0) entered learning state
Dec  5 21:51:03 BlueRidge virt-manager[3151]: message repeated 75 times: [ Drawing a gadget with negative dimensions. Did you forget to allocate a size? (node box owner virtManager+autodrawer+AutoDrawer)]
Dec  5 21:51:03 BlueRidge NetworkManager[1097]: <info>  [1512510663.7020] device (virbr0): link connected
Dec  5 21:51:03 BlueRidge kernel: [ 1854.604070] virbr0: port 2(vnet0) entered forwarding state
Dec  5 21:51:03 BlueRidge kernel: [ 1854.604072] virbr0: topology change detected, propagating
Dec  5 21:51:04 BlueRidge virt-manager[3151]: Drawing a gadget with negative dimensions. Did you forget to allocate a size? (node box owner virtManager+autodrawer+AutoDrawer)
Dec  5 21:51:09 BlueRidge virt-manager[3151]: message repeated 51 times: [ Drawing a gadget with negative dimensions. Did you forget to allocate a size? (node box owner virtManager+autodrawer+AutoDrawer)]
Dec  5 21:51:09 BlueRidge systemd[1]: Reloading.
Dec  5 21:51:10 BlueRidge virt-manager[3151]: Drawing a gadget with negative dimensions. Did you forget to allocate a size? (node box owner virtManager+autodrawer+AutoDrawer)
Dec  5 21:51:13 BlueRidge virt-manager[3151]: message repeated 35 times: [ Drawing a gadget with negative dimensions. Did you forget to allocate a size? (node box owner virtManager+autodrawer+AutoDrawer)]
Dec  5 21:51:13 BlueRidge dnsmasq-dhcp[1858]: DHCPDISCOVER(virbr0) 52:54:00:35:b3:4e
Dec  5 21:51:13 BlueRidge dnsmasq-dhcp[1858]: DHCPOFFER(virbr0) 192.168.122.91 52:54:00:35:b3:4e
Dec  5 21:51:13 BlueRidge dnsmasq-dhcp[1858]: DHCPREQUEST(virbr0) 192.168.122.91 52:54:00:35:b3:4e
Dec  5 21:51:13 BlueRidge dnsmasq-dhcp[1858]: DHCPACK(virbr0) 192.168.122.91 52:54:00:35:b3:4e Win7VM
Dec  5 21:51:14 BlueRidge virt-manager[3151]: Drawing a gadget with negative dimensions. Did you forget to allocate a size? (node box owner virtManager+autodrawer+AutoDrawer)
Dec  5 21:51:16 BlueRidge virt-manager[3151]: message repeated 8 times: [ Drawing a gadget with negative dimensions. Did you forget to allocate a size? (node box owner virtManager+autodrawer+AutoDrawer)]
Dec  5 21:51:16 BlueRidge dnsmasq-dhcp[1858]: DHCPINFORM(virbr0) 192.168.122.91 52:54:00:35:b3:4e
Dec  5 21:51:16 BlueRidge dnsmasq-dhcp[1858]: DHCPACK(virbr0) 192.168.122.91 52:54:00:35:b3:4e Win7VM
Dec  5 21:51:16 BlueRidge virt-manager[3151]: Drawing a gadget with negative dimensions. Did you forget to allocate a size? (node box owner virtManager+autodrawer+AutoDrawer)
Dec  5 21:51:32 BlueRidge virt-manager[3151]: message repeated 378 times: [ Drawing a gadget with negative dimensions. Did you forget to allocate a size? (node box owner virtManager+autodrawer+AutoDrawer)]

```

---

### Post by jayz99 on 2017-12-07
[COLOR=#ff0000]Confirmed. The above solution worked. Passthrough fully functional.[/COLOR] Recap of what is needed and why for others reading through the thread:

**1.** IOMMU / AMD-Vi enabled in order to pass through physical devices.
**2.** Driver blacklisting and VFIO-PCI used to capture and segregate the GPU at boot.
**3. **Q35 chipset for VM - better for modern systems.
**4.** OVMF (UEFI) - better than BIOS/SeaBIOS due to VGA arbitration at boot.
**5.** Motherboard software - must support [COLOR=#000000]AGESA 1.0.0.6 or higher. This means your UEFI/BIOS must have been updated post May 2017.
**6. **Linux kernel - use 4.12 or higher.
**7. **Windows 10 used as guest OS due to better support of the above technologies. 

[/COLOR]ODTech and KillerKelvUK - thank you again for your help!

Thanks & pozdrowienia,
Janusz

---

### Post by KillerKelvUK on 2017-12-07
Well done for persevering and getting this working!

 :popcorn:

---

