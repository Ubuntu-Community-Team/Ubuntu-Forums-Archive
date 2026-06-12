---
title: "ovmf wont boot windows iso"
date: 2015-10-14
forum: Virtualisation
---

### Post by fredwntr1 on 2015-10-14
im trying to setup a virtual machine using uefi (ovmf) with virt-manager and for some reason vm wont boot the iso image. Ive tried 2 install cds and 2 different iso images.


this is my vm 




<domain type='kvm'>
  <name>win7</name>
  <uuid>4500082d-1cf0-452a-8d7a-16025d26bba1</uuid>
  <memory unit='KiB'>9267200</memory>
  <currentMemory unit='KiB'>9267200</currentMemory>
  <vcpu placement='static'>6</vcpu>
  <os>
    <type arch='x86_64' machine='pc-q35-2.1'>hvm</type>
    <loader>/usr/share/OVMF/OVMF_CODE.fd</loader>
    <bootmenu enable='yes'/>
  </os>
  <features>
    <acpi/>
    <apic/>
    <pae/>
    <kvm>
      <hidden state='on'/>
    </kvm>
  </features>
  <cpu mode='host-model'>
    <model fallback='allow'/>
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
    <emulator>/usr/bin/kvm-spice</emulator>
    <disk type='block' device='disk'>
      <driver name='qemu' type='raw' cache='unsafe' io='threads'/>
      <source dev='/dev/sdb1'/>
      <target dev='vda' bus='virtio'/>
      <address type='pci' domain='0x0000' bus='0x02' slot='0x05' function='0x0'/>
    </disk>
    <disk type='file' device='cdrom'>
      <driver name='qemu' type='raw'/>
      <source file='/home/fred/Downloads/virtio.iso'/>
      <target dev='sda' bus='sata'/>
      <readonly/>
      <address type='drive' controller='0' bus='0' target='0' unit='0'/>
    </disk>
    <disk type='file' device='cdrom'>
      <driver name='qemu' type='raw'/>
      <source file='/home/fred/Downloads/9600.17050.WINBLUE_REFRESH.140317-1640_X64FRE_ENTERPRISE_EVAL_EN-US-IR3_CENA_X64FREE_EN-US_DV9.ISO'/>
      <target dev='sdc' bus='sata'/>
 <readonly/>
      <boot order='1'/>
      <address type='drive' controller='0' bus='0' target='0' unit='2'/>
    </disk>
    <controller type='usb' index='0' model='ich9-ehci1'>
      <address type='pci' domain='0x0000' bus='0x02' slot='0x03' function='0x7'/>
    </controller>
    <controller type='usb' index='0' model='ich9-uhci1'>
      <master startport='0'/>
      <address type='pci' domain='0x0000' bus='0x02' slot='0x03' function='0x0' multifunction='on'/>
    </controller>
    <controller type='usb' index='0' model='ich9-uhci2'>
      <master startport='2'/>
      <address type='pci' domain='0x0000' bus='0x02' slot='0x03' function='0x1'/>
    </controller>
    <controller type='usb' index='0' model='ich9-uhci3'>
      <master startport='4'/>
      <address type='pci' domain='0x0000' bus='0x02' slot='0x03' function='0x2'/>
    </controller>
    <controller type='sata' index='0'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x1f' function='0x2'/>
    </controller>
    <controller type='pci' index='0' model='pcie-root'/>
    <controller type='pci' index='1' model='dmi-to-pci-bridge'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x1e' function='0x0'/>
    </controller>
    <controller type='pci' index='2' model='pci-bridge'>
      <address type='pci' domain='0x0000' bus='0x01' slot='0x01' function='0x0'/>
    </controller>
    <controller type='virtio-serial' index='0'>
      <address type='pci' domain='0x0000' bus='0x02' slot='0x04' function='0x0'/>
    </controller>
    <controller type='scsi' index='0'>
      <address type='pci' domain='0x0000' bus='0x02' slot='0x09' function='0x0'/>
    </controller>
    <interface type='bridge'>
      <mac address='52:54:00:5d:68:43'/>
      <source bridge='xenbr0'/>
      <model type='rtl8139'/>
      <address type='pci' domain='0x0000' bus='0x02' slot='0x01' function='0x0'/>
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
    <input type='tablet' bus='usb'/>
    <input type='mouse' bus='ps2'/>
    <input type='keyboard' bus='ps2'/>
    <graphics type='vnc' port='-1' autoport='yes'/>
    <sound model='ich6'>
      <address type='pci' domain='0x0000' bus='0x02' slot='0x02' function='0x0'/>
    </sound>
    <video>
      <model type='qxl' ram='65536' vram='65536' heads='1'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x01' function='0x0'/>
    </video>
    <hostdev mode='subsystem' type='pci' managed='yes'>
      <source>
        <address domain='0x0000' bus='0x01' slot='0x00' function='0x0'/>
      </source>
      <address type='pci' domain='0x0000' bus='0x02' slot='0x06' function='0x0'/>
    </hostdev>
    <hostdev mode='subsystem' type='pci' managed='yes'>
      <source>
        <address domain='0x0000' bus='0x01' slot='0x00' function='0x1'/>


  </hostdev>
    <redirdev bus='usb' type='spicevmc'>
    </redirdev>
    <redirdev bus='usb' type='spicevmc'>
    </redirdev>
    <memballoon model='virtio'>
      <address type='pci' domain='0x0000' bus='0x02' slot='0x08' function='0x0'/>
    </memballoon>
  </devices>
</domain>

---

### Post by KillerKelvUK on 2015-10-16
Hi, try changing the machine type to i440fx instead of Q35...had lots of problems with OVMF and Q35 configurations.  Plus are you using the latest OVMF dailies or the ubuntu stock repo?

---

### Post by fredwntr1 on 2015-10-17
i solved it just a few minutes ago i installed debian 8 instead of ubuntu and used their latest .deb of ovmf funny thing is it wouldnt work with i440fx either... but regardless its solvedd

---

