---
title: "No Internet in Virtualbox (Windows XP)"
date: 2009-03-20
forum: Virtualisation
---

### Post by Shampyon on 2009-03-20
I run Xp in VirtualBox for my IT class assignments because the course is very Windows specific. I installed the closed source version of VB, and had internet access from it for a while. Now I don't. I have no idea why.

I'm not sure what information I need to supply for you to help me properly.

---

### Post by Jose Catre-Vandis on 2009-03-20
Type the following in a terminal 
```
VBoxManage list vms
```

Check the name for your XP VM and return the output here:

---

### Post by Shampyon on 2009-03-20
```
VirtualBox Command Line Management Interface Version 2.1.4
(C) 2005-2009 Sun Microsystems, Inc.                      
All rights reserved.                                      

Name:            TAFE
Guest OS:        Windows XP
UUID:            0bce735e-a94d-4683-a831-a857db013101
Config file:     /home/shampyon/.VirtualBox/Machines/TAFE/TAFE.xml
Memory size:     256MB                                       
VRAM size:       8MB                                         
Boot menu mode:  message and menu                            
ACPI:            on                                          
IOAPIC:          off                                         
PAE:             off                                         
Time offset:     0 ms                                        
Hardw. virt.ext: off                                         
Nested Paging:   off                                         
VT-x VPID:       off                                         
State:           powered off (since 2009-03-20T03:21:57.000000000)
Monitor count:   1                                                
3D Acceleration: off                                              
Floppy:          empty                                            
SATA:            enabled                                          
IDE Controller:  PIIX4                                            
Primary master:  /home/shampyon/.VirtualBox/VDI/TAFE.vdi (UUID: 98b00dd2-3851-42c8-bd6d-1db8e8fd0d08)
DVD:             empty
NIC 1:           MAC: 080027BB0A06, Attachment: NAT, Cable connected: on, Trace: off (file: none), Type: Am79C973, Reported speed: 0 Mbps
NIC 2:           MAC: 080027CCAF36, Attachment: NAT, Cable connected: on, Trace: off (file: none), Type: 82540EM, Reported speed: 0 Mbps
NIC 3:           MAC: 0800276F9CC1, Attachment: NAT, Cable connected: on, Trace: off (file: none), Type: Am79C970A, Reported speed: 0 Mbps
NIC 4:           MAC: 0800271AA670, Attachment: NAT, Cable connected: on, Trace: off (file: none), Type: 82543GC, Reported speed: 0 Mbps
NIC 5:           disabled
NIC 6:           disabled
NIC 7:           disabled
NIC 8:           disabled
UART 1:          disabled
UART 2:          disabled
Audio:           enabled (Driver: OSS, Controller: AC97)
Clipboard Mode:  Bidirectional
VRDP:            disabled
USB:             enabled

USB Device Filters:

<none>

Shared folders:

Name: 'TAFE', Host path: '/home/shampyon/TAFE' (machine mapping), writable

Guest:

Statistics update:                   disabled

```

---

### Post by Jose Catre-Vandis on 2009-03-20
Hmmm

The only real difference I can see when comparing with my VMs is the number of netowrk interfaces you have on board the VM (other than the enabled SATA controller, I don't have one on my host so don't need to enable, but can't see how this would affect internet access?)

Why 4 NICs? Are you trying to connect with them all?

Try deleting down to one, suggest you use the most basic; The PCnet-PCI II, and work up from there.

If that doesn't work, try running (instead of NAT) as host interface with eth0 selected.

---

### Post by Shampyon on 2009-03-20
OOps, I forgot about the network interfeces. I was activating them one at a time and got no result, so I tried activating them all at once to see what would happen.

I'll give the host interface thing a go.

---

### Post by Jose Catre-Vandis on 2009-03-20
Another thought, what about firewall settings on your host?

---

### Post by Shampyon on 2009-03-20
I'm using GuardDog firewall settings manager. I thought I had the right ports opened.. what ports does Virtualbox need to access the host connection?

---

### Post by cfree220 on 2009-03-21
Do you have Guest Additions for Windows installed on your VM? I have a Vista Ultimate VM and A Windows 7 beta VM, neither of which were able to connect to the internet until Guest Additions were installed.

---

### Post by Shampyon on 2009-03-21
I changed the settings to use the host interface and turned off the firewall part of the internet security suite I'd installed in the guest. Guest internet access is now at 100%.

Thank you all for your help!

---

### Post by Jose Catre-Vandis on 2009-03-22
:)

One Step at a time :)

---

### Post by LucasCordina on 2009-06-04
Yeah I pretty much had the same problem, I need windows to complete my course *.*, i just need to make internet work on my virtual box and if it doesn't wellllllll =[ i'll actually have to use windows as my main OS.... we don't want that, do we?

---

