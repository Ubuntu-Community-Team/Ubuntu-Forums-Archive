---
title: "KVM Passthroug in virtual maachine moore than 3 usb device"
date: 2018-09-12
forum: Virtualisation
---

### Post by desg1 on 2018-09-12
I have a question, how can i passthroug in virtual machine more than 3 usb device?
  I have usb hub and i cannot passtrought in virtual machine more than 3  usb device. My usb device connect to usb hub, but if i connect them to  mother board i have the same error error: ERROR: No free USB ports
  
I have: 

1) 4.13.0-43-generic Ubuntu 17.10 qemu-kvm Version: 1:2.10+dfsg-0ubuntu3.8 libvirt version 3.6.0
  
2) Virtual machin Windows 7x64 Config Virtual machine:
  
<domain type='kvm'>
<name>A1</name>
<uuid>6ba27623-0f5c-41c9-bca9-6a51c5cdf4c2</uuid>
<memory unit='KiB'>2097152</memory>
<currentMemory unit='KiB'>2097152</currentMemory>
<vcpu placement='static'>2</vcpu>
<os>
<type arch='x86_64' machine='pc-i440fx-artful'>hvm</type>
<boot dev='cdrom'/>
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
</features>
<cpu mode='custom' match='exact' check='partial'>
<model fallback='allow'>Haswell-noTSX-IBRS</model>
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
  <driver name='qemu' type='qcow2' cache='none'/>
  <source file='/kvm/vhdd/A1.qcow2'/>
  <target dev='vda' bus='virtio'/>
  <address type='pci' domain='0x0000' bus='0x00' slot='0x05' function='0x0'/>
</disk>
<controller type='pci' index='0' model='pci-root'/>
<controller type='ide' index='0'>
  <address type='pci' domain='0x0000' bus='0x00' slot='0x01' function='0x1'/>
</controller>
<controller type='usb' index='0' model='nec-xhci'>
  <address type='pci' domain='0x0000' bus='0x00' slot='0x04' function='0x0'/>
</controller>
<interface type='bridge'>
  <mac address='52:54:00:86:70:01'/>
  <source bridge='br0'/>
  <model type='virtio'/>
  <address type='pci' domain='0x0000' bus='0x00' slot='0x03' function='0x0'/>
</interface>
<serial type='pty'>
  <target port='0'/>
</serial>
<console type='pty'>
  <target type='serial' port='0'/>
</console>
<input type='tablet' bus='usb'>
  <address type='usb' bus='0' port='1'/>
</input>
<input type='mouse' bus='ps2'/>
<input type='keyboard' bus='ps2'/>
<graphics type='vnc' port='-1' autoport='yes' listen='0.0.0.0'>
  <listen type='address' address='0.0.0.0'/>
</graphics>
<video>
  <model type='vga' vram='16384' heads='1' primary='yes'/>
  <address type='pci' domain='0x0000' bus='0x00' slot='0x02' function='0x0'/>
</video>
<memballoon model='virtio'>
  <address type='pci' domain='0x0000' bus='0x00' slot='0x06' function='0x0'/>
</memballoon>
</devices>
</domain>
  ]
3)My usb device have numbers: 6, 5, 4, 7. Device number 8 is card reader. lsusb - 
  
Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 046d:c328 Logitech, Inc. 
Bus 003 Device 008: ID 05e3:0723 Genesys Logic, Inc. GL827L SD/MMC/MS Flash Card Reader
Bus 003 Device 009: ID 067b:2528 Prolific Technology, Inc. Storage device (8gB thumb drive)
Bus 003 Device 006: ID 090c:1000 Silicon Motion, Inc. - Taiwan (formerly Feiya Technology Corp.) Flash Drive
Bus 003 Device 005: ID 0951:1666 Kingston Technology DataTraveler G4
Bus 003 Device 004: ID 0951:1666 Kingston Technology DataTraveler G4
Bus 003 Device 002: ID 1a40:0201 Terminus Technology Inc. FE 2.1 7-port Hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
  
4) lsusb -t
  
/:  Bus 04.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/6p, 5000M
/:  Bus 03.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/12p, 480M
|__ Port 5: Dev 2, If 0, Class=Hub, Driver=hub/7p, 480M
    |__ Port 4: Dev 9, If 0, Class=Mass Storage, Driver=usb-storage, 480M
    |__ Port 2: Dev 5, If 0, Class=Mass Storage, Driver=usb-storage, 480M
    |__ Port 5: Dev 8, If 0, Class=Mass Storage, Driver=usbfs, 480M
    |__ Port 3: Dev 6, If 0, Class=Mass Storage, Driver=usbfs, 480M
    |__ Port 1: Dev 4, If 0, Class=Mass Storage, Driver=usb-storage, 480M
|__ Port 6: Dev 3, If 0, Class=Human Interface Device, Driver=usbhid, 1.5M
|__ Port 6: Dev 3, If 1, Class=Human Interface Device, Driver=usbhid, 1.5M
/:  Bus 02.Port 1: Dev 1, Class=root_hub, Driver=ehci-pci/2p, 480M
    |__ Port 1: Dev 2, If 0, Class=Hub, Driver=hub/6p, 480M
/:  Bus 01.Port 1: Dev 1, Class=root_hub, Driver=ehci-pci/2p, 480M
    |__ Port 1: Dev 2, If 0, Class=Hub, Driver=hub/6p, 480M
  


Soo, how can i fix that problem?

---

### Post by TheFu on 2018-09-12
I couldn't find any limits to USB devices anywhere. 

If you install a pcie usb card, then you can pass the whole controller through.  That would require PCI passthru and IOMMU enabled.  

Just another option to get native-like USB support inside a VM.

---

