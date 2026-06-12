---
title: "no USB in Windows 7 guest"
date: 2014-11-12
forum: Virtualisation
---

### Post by ac7nj on 2014-11-12
I'm trying to use Virtualbox to run my Dell V725w printer, scaner, and copier and quicken software. 
I store the quicken files on a USB. windows 7 can't see the USB device.
I've tried to set up a workgroup and file share with the host using samba all with no success.

I'm new to Ubuntu file sharing and have never used Windows file share so don't assume I know what I'm doing LOL
I've added some information that I thought you might ask for:

Randy AC7NJ

[HTML]randy@AC7NJ:~$ lsusb
Bus 002 Device 003: ID 0930:6545 Toshiba Corp. Kingston DataTraveler 102 Flash Drive / HEMA Flash Drive 2 GB / PNY Attache 4GB Stick
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 0c45:6480 Microdia Sonix 1.3 MP Laptop Integrated Webcam
Bus 001 Device 008: ID 413c:8160 Dell Computer Corp. Wireless 365 Bluetooth
Bus 001 Device 007: ID 413c:8162 Dell Computer Corp. Integrated Touchpad [Synaptics]
Bus 001 Device 006: ID 413c:8161 Dell Computer Corp. Integrated Keyboard
Bus 001 Device 003: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
[/HTML]

log file info
```
VirtualBox VM 4.3.10_Ubuntu r93012 linux.amd64 (Apr  7 2014 03:37:47) release log
00:00:00.606417 Log opened 2014-11-12T19:35:59.600751000Z
00:00:00.606418 Build Type: release
00:00:00.606423 OS Product: Linux
00:00:00.606424 OS Release: 3.13.0-39-generic
00:00:00.606424 OS Version: #66-Ubuntu SMP Tue Oct 28 13:30:27 UTC 2014
00:00:00.606450 DMI Product Name: Inspiron N7010
00:00:00.606457 DMI Product Version: A11  
00:00:00.606570 Host RAM: 3752MB total, 2963MB available
00:00:00.606574 Executable: /usr/lib/virtualbox/VirtualBox
00:00:00.606574 Process ID: 3818
00:00:00.606575 Package type: LINUX_64BITS_GENERIC (OSE)
00:00:00.646624 Installed Extension Packs:
00:00:00.646716   Oracle VM VirtualBox Extension Pack (Version: 4.3.10 r93012; VRDE Module: VBoxVRDP)
00:00:00.646756   VNC (Version: 4.3.10 r93012; VRDE Module: VBoxVNC)
00:00:00.654143 UIMediumEnumerator: Medium-enumeration finished!
00:00:00.655066 Using XKB for keycode to scan code conversion
00:00:00.775453 SUP: Loaded VMMR0.r0 (/usr/lib/virtualbox/VMMR0.r0) at 0xffffffffa0a3c020 - ModuleInit at ffffffffa0a597a0 and ModuleTerm at ffffffffa0a59a40
00:00:00.775559 SUP: VMMR0EntryEx located at ffffffffa0a5ae00, VMMR0EntryFast at ffffffffa0a5aa20 and VMMR0EntryInt at ffffffffa0a5aa10
00:00:00.782048 Guest OS type: 'Windows7_64'
00:00:00.787795 fHMForced=true - 64-bit guest
00:00:00.800860 File system of '/home/randy/VirtualBox VMs/Windows/Snapshots' (snapshots) is unknown
00:00:00.800975 File system of '/home/randy/VirtualBox VMs/Windows/Windows.vdi' is unknown
00:00:00.847800 Shared clipboard mode: Bidirectional
00:00:00.857423 Drag'n'drop mode: Bidirectional
00:00:00.867983 ************************* CFGM dump *************************
```

---

### Post by ajgreeny on 2014-11-12
Install the VBox-guest-additions avaiable from the VBox website [http://download.virtualbox.org/virtualbox/4.3.18/Oracle_VM_VirtualBox_Extension_Pack-4.3.18-96516.vbox-extpack](http://download.virtualbox.org/virtualbox/4.3.18/Oracle_VM_VirtualBox_Extension_Pack-4.3.18-96516.vbox-extpack)  to host and guest.

That should do it, if you haven't already installed it.

---

### Post by ac7nj on 2014-11-13
Thank you for your reply this is form the log file I included 
"00:00:00.646716   Oracle VM VirtualBox Extension Pack (Version: 4.3.10 r93012; VRDE Module: VBoxVRDP)"
so I think I did get the extension pack? Your link went to a different version " 4.3.18-96516.vbox-extpack"and I have "4.3.10_Ubunyu r93012 "
Is this a upgrade issue?

---

### Post by TheFu on 2014-11-13
[http://ubuntuforums.org/showthread.php?t=2238515](http://ubuntuforums.org/showthread.php?t=2238515) might help.

---

### Post by ac7nj on 2014-11-13
I upgraded Virtualbox and problem solved

---

