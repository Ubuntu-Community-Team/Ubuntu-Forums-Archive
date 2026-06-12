---
title: "GPU VFIO QEMU - No HDMI audio"
date: 2016-02-21
forum: Virtualisation
---

### Post by dominik-a on 2016-02-21
Hello,

I have a problem with my GPU passthrough with Qemu 2.1.2 on Ubuntu 14.04. I have a Windows 10 VM up and running, all is working well, the graphic card is available (NVIDIA Geforce 960) and the drivers are installed. I can play over Steam on a thin client. Only the audio makes problems. Windows says the audio device is not responding.

I used this guide: [http://vfio.blogspot.co.at/2015/05/vfio-gpu-how-to-series-part-4-our-first.html](http://vfio.blogspot.co.at/2015/05/vfio-gpu-how-to-series-part-4-our-first.html)

lspci -nnk:
```

03:00.0 VGA compatible controller [0300]: NVIDIA Corporation GM206 [GeForce GTX 960] [10de:1401] (rev a1)
        Subsystem: Micro-Star International Co., Ltd. [MSI] Device [1462:3205]
        Kernel driver in use: vfio-pci
03:00.1 Audio device [0403]: NVIDIA Corporation Device [10de:0fba] (rev a1)
        Subsystem: Micro-Star International Co., Ltd. [MSI] Device [1462:3205]
        Kernel driver in use: vfio-pci

```

Both of them are passthroughed to the machine.

VM XML:
```

<domain type='kvm'>
  <name>win10-gaming</name>
  <uuid>1ec5e702-e331-4f8a-8cdf-bdf3db039745</uuid>
  <memory unit='KiB'>4194304</memory>
  <currentMemory unit='KiB'>4194304</currentMemory>
  <vcpu placement='static'>4</vcpu>
  <cputune>
    <vcpupin vcpu='0' cpuset='4'/>
    <vcpupin vcpu='1' cpuset='5'/>
    <vcpupin vcpu='2' cpuset='10'/>
    <vcpupin vcpu='3' cpuset='11'/>
  </cputune>
  <os>
    <type arch='x86_64' machine='pc-i440fx-trusty'>hvm</type>
    <loader>/usr/share/edk2.git/ovmf-x64/OVMF_CODE-pure-efi.fd</loader>
    <boot dev='hd'/>
  </os>
  <features>
    <acpi/>
    <apic/>
    <pae/>
    <kvm>
      <hidden state='on'/>
    </kvm>
  </features>
  <cpu mode='custom' match='exact'>
    <model fallback='allow'>SandyBridge</model>
    <vendor>Intel</vendor>
    <topology sockets='1' cores='2' threads='2'/>
    <feature policy='require' name='vme'/>
    <feature policy='require' name='dtes64'/>
    <feature policy='require' name='invpcid'/>
    <feature policy='require' name='vmx'/>
    <feature policy='require' name='erms'/>
    <feature policy='require' name='xtpr'/>
    <feature policy='require' name='smep'/>
    <feature policy='require' name='pbe'/>
    <feature policy='require' name='est'/>
    <feature policy='require' name='monitor'/>
    <feature policy='require' name='smx'/>
    <feature policy='require' name='abm'/>
    <feature policy='require' name='tm'/>
    <feature policy='require' name='acpi'/>
    <feature policy='require' name='fma'/>
    <feature policy='require' name='osxsave'/>
    <feature policy='require' name='ht'/>
    <feature policy='require' name='dca'/>
    <feature policy='require' name='pdcm'/>
    <feature policy='require' name='pdpe1gb'/>
    <feature policy='require' name='fsgsbase'/>
    <feature policy='require' name='f16c'/>
    <feature policy='require' name='ds'/>
    <feature policy='require' name='invtsc'/>
    <feature policy='require' name='tm2'/>
    <feature policy='require' name='avx2'/>
    <feature policy='require' name='ss'/>
    <feature policy='require' name='bmi1'/>
    <feature policy='require' name='bmi2'/>
    <feature policy='require' name='pcid'/>
    <feature policy='require' name='ds_cpl'/>
    <feature policy='require' name='movbe'/>    <feature policy='require' name='rdrand'/>
  </cpu>
  <clock offset='localtime'>
    <timer name='rtc' tickpolicy='catchup'/>
    <timer name='pit' tickpolicy='delay'/>
    <timer name='hpet' present='no'/>
  </clock>
  <on_poweroff>destroy</on_poweroff>
  <on_reboot>restart</on_reboot>
  <on_crash>restart</on_crash>
  <pm>
    <suspend-to-mem enabled='no'/>
    <suspend-to-disk enabled='no'/>
  </pm>
  <devices>
    <emulator>/usr/bin/qemu-system-x86_64</emulator>
    <disk type='file' device='disk'>
      <driver name='qemu' type='qcow2'/>
      <source file='/home/dominik/win10.qcow2'/>
      <target dev='vda' bus='virtio'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x07' function='0x0'/>
    </disk>
    <disk type='file' device='cdrom'>
      <driver name='qemu' type='raw'/>
      <source file='/home/dominik/virtio-win.iso'/>
      <target dev='hda' bus='ide'/>
      <readonly/>
      <address type='drive' controller='0' bus='0' target='0' unit='0'/>
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
    <interface type='bridge'>
      <mac address='52:54:00:4d:d4:83'/>
      <source bridge='br0'/>
      <model type='rtl8139'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x03' function='0x0'/>
    </interface>
    <hostdev mode='subsystem' type='pci' managed='yes'>
      <source>
        <address domain='0x0000' bus='0x03' slot='0x00' function='0x0'/>
      </source>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x02' function='0x0'/>
    </hostdev>
    <hostdev mode='subsystem' type='pci' managed='yes'>
      <source>
        <address domain='0x0000' bus='0x03' slot='0x00' function='0x1'/>
      </source>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x04' function='0x0'/>
    </hostdev>
    <memballoon model='virtio'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x08' function='0x0'/>
    </memballoon>
  </devices>
</domain>



```

First I thought the audio device is not correctly passthrough, but it uses the correct driver I think.
Maybe anyone has an idea, why this is not gonna work, do I need a dummy audio adapter maybe?

Best regards
Dominik

---

### Post by T.J. on 2016-02-25
> 

First I thought the audio device is not correctly passthrough, but it uses the correct driver I think.
Maybe anyone has an idea, why this is not gonna work, do I need a dummy audio adapter maybe?



I can't say for sure. I'm not an expert in using virt-manager.  I don't use it anymore, but use a native qemu instead. I can tell you that virt-manager can cause issues with hardware that works under qemu, because libvirt blocks certain things by default. You might have edit your libvirt configuration.  

Have you tested using qemu on your hardware without virt-manager?

---

