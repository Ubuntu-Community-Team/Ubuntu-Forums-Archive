---
title: "pci passthrough kvm ubuntu server 9.10"
date: 2009-11-04
forum: Virtualisation
---

### Post by Werner4 on 2009-11-04
Hi everybody,
I have installed Ubuntu Server 9.10. There are running 2 virtual machines on it. Now I'd like to passthrough a pci networkadapter to one of the vm's.
Does anybody know how to configure this?

Thanks for help!

Rgds W4

---

### Post by HRH_H_Crab on 2010-03-26
I'd be interested to know too.
I've tried to attach my 3com nic to an Ubuntu vm - it looks like its working but when I try and start the vm it fails to start.

---

### Post by gbear14275 on 2010-06-17
I am experiencing the same issue only with 10.04.  After assigning a PCI device (NIC) to my VM, it fails to start.  Removing the default virtual networks changes the type of error.  Specifically here is what I am getting.

With virnet still assigned:

Error starting domain: monitor socket did not show up.: Connection refused


Traceback (most recent call last):
  File "/usr/share/virt-manager/virtManager/engine.py", line 588, in run_domain
    vm.startup()
  File "/usr/share/virt-manager/virtManager/domain.py", line 150, in startup
    self._backend.create()
  File "/usr/lib/python2.6/dist-packages/libvirt.py", line 300, in create
    if ret == -1: raise libvirtError ('virDomainCreate() failed', dom=self)
libvirtError: monitor socket did not show up.: Connection refused


With no virnet's assigned:

Error starting domain: operation failed: failed to retrieve chardev info in qemu with 'info chardev'

Traceback (most recent call last):
  File "/usr/share/virt-manager/virtManager/engine.py", line 588, in run_domain
    vm.startup()
  File "/usr/share/virt-manager/virtManager/domain.py", line 150, in startup
    self._backend.create()
  File "/usr/lib/python2.6/dist-packages/libvirt.py", line 300, in create
    if ret == -1: raise libvirtError ('virDomainCreate() failed', dom=self)
libvirtError: operation failed: failed to retrieve chardev info in qemu with 'info chardev'

---

### Post by sjhaffner on 2010-08-10
I get this:

[I][COLOR=#000000][SIZE=2][FONT=arial,helvetica,sans-serif]Traceback (most recent call last):[/FONT][/SIZE][/COLOR]
[COLOR=#000000][SIZE=2][FONT=arial,helvetica,sans-serif]  File "/usr/share/virt-manager/virtManager/engine.py", line 588, in run_domain[/FONT][/SIZE][/COLOR]
[COLOR=#000000][SIZE=2][FONT=arial,helvetica,sans-serif]    vm.startup()[/FONT][/SIZE][/COLOR]
[COLOR=#000000][SIZE=2][FONT=arial,helvetica,sans-serif]  File "/usr/share/virt-manager/virtManager/domain.py", line 150, in startup[/FONT][/SIZE][/COLOR]
[COLOR=#000000][SIZE=2][FONT=arial,helvetica,sans-serif]    self._backend.create()[/FONT][/SIZE][/COLOR]
[COLOR=#000000][SIZE=2][FONT=arial,helvetica,sans-serif]  File "/usr/lib/python2.6/dist-packages/libvirt.py", line 300, in create[/FONT][/SIZE][/COLOR]
[COLOR=#000000][SIZE=2][FONT=arial,helvetica,sans-serif]    if ret == -1: raise libvirtError ('virDomainCreate() failed', dom=self)[/FONT][/SIZE][/COLOR]
[/I]    [COLOR=#000000][SIZE=2][FONT=arial,helvetica,sans-serif][I]libvirtError: monitor socket did not show up.: Connection refused

[/I]I got it to work after a lot of messing around but I'm not sure what I actually did.
[/FONT][/SIZE][/COLOR]

---

### Post by daballiemo on 2010-08-28
Been playing around with passthrough a lot. Check u'r interrupts, I encountered this when having no free interrupts for the the cards.

```
           CPU0       CPU1       CPU2       CPU3       
  0:         26          1          0          0   IO-APIC-edge      timer
  1:          2          3          1          2   IO-APIC-edge      i8042
  6:          1          0          3          1   IO-APIC-edge      floppy
  8:          0          0          1          0   IO-APIC-edge      rtc0
  9:          0          0          0          0   IO-APIC-fasteoi   acpi
 12:         31         29         30         24   IO-APIC-edge      i8042
 16:       3087       3102       3087       3075   IO-APIC-fasteoi   uhci_hcd:usb3
 17:          6         11          2          5   IO-APIC-fasteoi 
 18:          1          0          1          0   IO-APIC-fasteoi   ehci_hcd:usb1, uhci_hcd:usb5, uhci_hcd:usb8
 19:          0          0          0          0   IO-APIC-fasteoi   uhci_hcd:usb7
 21:          0          0          0          0   IO-APIC-fasteoi   uhci_hcd:usb4
 22:       1334       1315       1337       1352   IO-APIC-fasteoi   ata_piix, ata_piix, HDA Intel
 23:          0          0          0          0   IO-APIC-fasteoi   ehci_hcd:usb2, uhci_hcd:usb6
 24:          0          0          0          0  DMAR_MSI-edge      dmar2
 25:          0          0          0          0  DMAR_MSI-edge      dmar0
 26:          0          0          0          0  DMAR_MSI-edge      dmar3
 28:          7         14         15         11   PCI-MSI-edge      eth0
 29:         45         41         41         46   PCI-MSI-edge      eth1
 30:         15         11         12         11   PCI-MSI-edge      i915
NMI:          0          0          0          0   Non-maskable interrupts
LOC:       3279       2790       3613       2325   Local timer interrupts
SPU:          0          0          0          0   Spurious interrupts
PMI:          0          0          0          0   Performance monitoring interrupts
PND:          0          0          0          0   Performance pending work
RES:        125        101        123        201   Rescheduling interrupts
CAL:       1622        108        968        109   Function call interrupts
TLB:        179        641        170        647   TLB shootdowns
TRM:          0          0          0          0   Thermal event interrupts
THR:          0          0          0          0   Threshold APIC interrupts
MCE:          0          0          0          0   Machine check exceptions
MCP:          1          1          1          1   Machine check polls
ERR:          3
MIS:          0
```

I kicked out a number of interrupts with for usb with:

```
virsh nodedev-dettach pci_8086_xxxx
```

I ended up with:

```
cat /proc/interrupts 
           CPU0       CPU1       CPU2       CPU3       
  0:         27          1          3          2   IO-APIC-edge      timer
  1:          2          3          1          2   IO-APIC-edge      i8042
  6:          1          0          3          1   IO-APIC-edge      floppy
  8:          0          0          1          0   IO-APIC-edge      rtc0
  9:          0          0          0          0   IO-APIC-fasteoi   acpi
 12:         31         29         30         24   IO-APIC-edge      i8042
 16:       3087       3102       3087       3075   IO-APIC-fasteoi   uhci_hcd:usb3
 17:          6         11          2          5   IO-APIC-fasteoi 
 18:          1          0          1          0   IO-APIC-fasteoi 
 22:       1370       1355       1378       1392   IO-APIC-fasteoi   ata_piix, ata_piix, HDA Intel
 24:          0          0          0          0  DMAR_MSI-edge      dmar2
 25:          0          0          0          0  DMAR_MSI-edge      dmar0
 26:          0          0          0          0  DMAR_MSI-edge      dmar3
 28:        279        287        290        271   PCI-MSI-edge      eth0
 29:        801        793        784        810   PCI-MSI-edge      eth1
 30:         16         12         15         11   PCI-MSI-edge      i915
NMI:          0          0          0          0   Non-maskable interrupts
LOC:      13926      11096      37817      14875   Local timer interrupts
SPU:          0          0          0          0   Spurious interrupts
PMI:          0          0          0          0   Performance monitoring interrupts
PND:          0          0          0          0   Performance pending work
RES:        127        104        125        205   Rescheduling interrupts
CAL:       1668        108        984        109   Function call interrupts
TLB:        187        656        187        662   TLB shootdowns
TRM:          0          0          0          0   Thermal event interrupts
THR:          0          0          0          0   Threshold APIC interrupts
MCE:          0          0          0          0   Machine check exceptions
MCP:          7          7          7          7   Machine check polls
ERR:          3
MIS:          0
```

after which my virt machine with 3 tunercards was starting:D.

rgds

---

