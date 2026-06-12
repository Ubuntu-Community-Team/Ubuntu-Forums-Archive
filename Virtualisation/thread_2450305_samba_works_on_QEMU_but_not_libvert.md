---
title: "samba works on QEMU but not libvert"
date: 2020-09-10
forum: Virtualisation
---

### Post by jeff-milton on 2020-09-10
I can connect to samba from a windows 10 VM guest on an Arch host with QEMU, but when I load the VM with libvirt, it can't see the network.
It's a bit crazy how difficult it is to access a host folder. I have tried the following with no success: samba (only works in QEMU), remote desktop, spice-webdav, filesystem via virt-viewer, Plan 9 and libguestfs.


libguestfs crashes with a:
```

supermin: failure: failed to parse epoch:version-release field 2.04-11.1

```

But this has been confirmed to be a bug in the way it parses the version numbers, but the latest GitHub patched version won't compile on Arch.
The ONLY one that worked so far is samba and only when loaded with QEMU, not VMM, which is odd as VMM uses QEMU, so I assume it must be the XML, but I can't see anything wrong.


Am I missing something?

Here is how I load the VM in QEMU VM:
```

/usr/sbin/qemu-system-x86_64 \
-net nic \
-net user,smb=/home/jw/store \
-device intel-hda \
-device hda-duplex \
-device virtio-gpu-pci \
-full-screen \
-usb \
-device usb-tablet \
-smp 2 \
-cpu host \
-enable-kvm \
-m 4096 \
-drive format=qcow2,file=/home/jw/store/libvirt/images/Win10.qcow2

```

Here is the XML for the libvirt VM:


```
<domain type='kvm' xmlns:qemu='http://libvirt.org/schemas/domain/qemu/1.0'>
  <name>Win10ProNew</name>
  <uuid>43949c43-3dfa-4615-b645-7e66f0256fe4</uuid>
  <metadata>
    <libosinfo:libosinfo xmlns:libosinfo="http://libosinfo.org/xmlns/libvirt/domain/1.0">
      <libosinfo:os id="http://microsoft.com/win/2k19"/>
    </libosinfo:libosinfo>
  </metadata>
  <memory unit='KiB'>4194304</memory>
  <currentMemory unit='KiB'>4194304</currentMemory>
  <vcpu placement='static'>2</vcpu>
  <os>
    <type arch='x86_64' machine='pc-q35-5.1'>hvm</type>
    <boot dev='hd'/>
  </os>
  <features>
    <acpi/>
    <apic/>
    <hyperv>
      <relaxed state='on'/>
      <vapic state='on'/>
      <spinlocks state='on' retries='8191'/>
    </hyperv>
    <vmport state='off'/>
  </features>
  <cpu mode='host-model' check='partial'/>
  <clock offset='localtime'>
    <timer name='rtc' tickpolicy='catchup'/>
    <timer name='pit' tickpolicy='delay'/>
    <timer name='hpet' present='no'/>
    <timer name='hypervclock' present='yes'/>
  </clock>
  <on_poweroff>destroy</on_poweroff>
  <on_reboot>restart</on_reboot>
  <on_crash>destroy</on_crash>
  <pm>
    <suspend-to-mem enabled='no'/>
    <suspend-to-disk enabled='no'/>
  </pm>
  <devices>
    <emulator>/usr/bin/qemu-system-x86_64</emulator>
    <disk type='file' device='disk'>
      <driver name='qemu' type='qcow2'/>
      <source file='/var/lib/libvirt/images/Win10ProNew.qcow2'/>
      <target dev='sda' bus='sata'/>
      <address type='drive' controller='0' bus='0' target='0' unit='0'/>
    </disk>
    <disk type='file' device='cdrom'>
      <driver name='qemu' type='raw'/>
      <source file='/home/jw/Documents/software/isos/Win10_Pro_1511_English_x64_july_2016.iso'/>
      <target dev='sdb' bus='sata'/>
      <readonly/>
      <address type='drive' controller='0' bus='0' target='0' unit='1'/>
    </disk>
    <controller type='usb' index='0' model='qemu-xhci' ports='15'>
      <address type='pci' domain='0x0000' bus='0x02' slot='0x00' function='0x0'/>
    </controller>
    <controller type='sata' index='0'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x1f' function='0x2'/>
    </controller>
    <controller type='pci' index='0' model='pcie-root'/>
    <controller type='pci' index='1' model='pcie-root-port'>
      <model name='pcie-root-port'/>
      <target chassis='1' port='0x10'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x02' function='0x0' multifunction='on'/>
    </controller>
    <controller type='pci' index='2' model='pcie-root-port'>
      <model name='pcie-root-port'/>
      <target chassis='2' port='0x11'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x02' function='0x1'/>
    </controller>
    <controller type='pci' index='3' model='pcie-root-port'>
      <model name='pcie-root-port'/>
      <target chassis='3' port='0x12'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x02' function='0x2'/>
    </controller>
    <controller type='pci' index='4' model='pcie-root-port'>
      <model name='pcie-root-port'/>
      <target chassis='4' port='0x13'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x02' function='0x3'/>
    </controller>
    <controller type='pci' index='5' model='pcie-root-port'>
      <model name='pcie-root-port'/>
      <target chassis='5' port='0x14'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x02' function='0x4'/>
    </controller>
    <controller type='virtio-serial' index='0'>
      <address type='pci' domain='0x0000' bus='0x03' slot='0x00' function='0x0'/>
    </controller>
    <interface type='network'>
      <mac address='52:54:00:bc:97:1d'/>
      <source network='default'/>
      <model type='e1000e'/>
      <address type='pci' domain='0x0000' bus='0x01' slot='0x00' function='0x0'/>
    </interface>
    <serial type='pty'>
      <target type='isa-serial' port='0'>
        <model name='isa-serial'/>
      </target>
    </serial>
    <console type='pty'>
      <target type='serial' port='0'/>
    </console>
    <channel type='spicevmc'>
      <target type='virtio' name='com.redhat.spice.0'/>
      <address type='virtio-serial' controller='0' bus='0' port='1'/>
    </channel>
    <input type='tablet' bus='usb'>
      <address type='usb' bus='0' port='1'/>
    </input>
    <input type='mouse' bus='ps2'/>
    <input type='keyboard' bus='ps2'/>
    <graphics type='spice' autoport='yes'>
      <listen type='address'/>
      <image compression='off'/>
    </graphics>
    <sound model='ich9'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x1b' function='0x0'/>
    </sound>
    <video>
      <model type='qxl' ram='65536' vram='65536' vgamem='16384' heads='1' primary='yes'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x01' function='0x0'/>
    </video>
    <redirdev bus='usb' type='spicevmc'>
      <address type='usb' bus='0' port='2'/>
    </redirdev>
    <redirdev bus='usb' type='spicevmc'>
      <address type='usb' bus='0' port='3'/>
    </redirdev>
    <memballoon model='virtio'>
      <address type='pci' domain='0x0000' bus='0x04' slot='0x00' function='0x0'/>
    </memballoon>
  </devices>
  <qemu:commandline>
    <qemu:arg value='-net'/>
    <qemu:arg value='user,smb=/home/jw/store'/>
  </qemu:commandline>
</domain>

```

If I add the following commandline args to the XMLfile,  libvirt crashes with a meaningless (to me) error (see attached)
```

<qemu:arg value='-net'/>
<qemu:arg value='nic'/>

```

[IMG]https://mega.nz/file/tu4z3LoY#_TZUzPxZ2ZLCLzlZg7wz0YuFMb1ZtlRYPuGgop5VnhE[/IMG]
[IMG]https://raw.githubusercontent.com/tholonia/the-book/master/Images/screenshot2.png[/IMG]
[IMG]https://mega.nz/file/tu4z3LoY#_TZUzPxZ2ZLCLzlZg7wz0YuFMb1ZtlRYPuGgop5VnhE[/IMG]

---

### Post by TheFu on 2020-09-11
Please don't post images.  Copy/paste the text here. Please edit the post above to correct that issue.

As for accessing a VM over the network, how did you setup the networking used by each VM?  NAT, host-only, bridged, NIC passthru?  libvirt sets up NAT by default, but not the others.  Usually, a bridge is what people running servers need. Setting up a bridge happens in the host OS networking, not in the virtual machines.

18.04 and later Ubuntu releases use netplan to configure server networking.  
A reference: [https://fabianlee.org/2019/04/01/kvm-creating-a-bridged-network-with-netplan-on-ubuntu-bionic/](https://fabianlee.org/2019/04/01/kvm-creating-a-bridged-network-with-netplan-on-ubuntu-bionic/) should be how to setup a bridge.

BTW, for the VMs, using virtio for disk and networking will be more efficient. Most Unix-like OSes have the virtio drivers built-in, so they "just work."  I don't know about recent Windows.  Win7 did NOT have virtio drivers, so I had to get them from Redhat. Not sure if the hassles are worth the added performance. Whenever Windows fails to boot, the "safe mode" needs the virtio drivers loaded to work. That's a huge hassle, since Windows fails to boot so often.  OTOH, seeing 25-35 Gbps network transfers between the VMs running on the same physical machine is pretty great.  
Sadly, disk performance is usually limited by physics and my disks might be 250-550 Mbps range. There are slight differences between the SATA and SCSI virtual disk controllers.  SCSI is more flexible and doesn't have limits that some larger storage VMs may run into.  I've never been anywhere near those limitations with the SATA drivers, but since I use virtio almost always, I wouldn't.  Until PB of storage is connected, the choice doesn't matter.

Sorry I'm not any real help.  I've been using KVM+libvirt+virsh since 2010.  It's much better than Xen was back then and vastly more flexible than ESXi and much faster and more stable than virtualbox.

---

