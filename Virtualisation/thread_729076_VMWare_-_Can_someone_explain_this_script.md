---
title: "VMWare - Can someone explain this script?"
date: 2008-03-19
forum: Virtualisation
---

### Post by CoffeeBreath on 2008-03-19
I'm trying to understand linux world.
Thanks



#!/usr/bin/vmware
displayName = "Windows XP"
guestOS = "winxphome"

memsize = "64"
ide0:0.fileName = "WindowsXP.vmdk"
ide1:0.fileName = "WindowsXP.iso"

# DEFAULT SETTINGS UNDER THIS LINE
config.version = "8"
virtualHW.version = "3"

MemAllowAutoScaleDown = "FALSE"
MemTrimRate = "-1"

uuid.location = "56 4d 34 58 fd 57 00 42-76 91 96 91 01 30 46 a5"
uuid.bios = "56 4d 34 58 fd 57 00 42-76 91 96 91 01 30 46 a5"

uuid.action = "create"
checkpoint.vmState = ""

ethernet0.present = "TRUE"
ethernet0.connectionType = "nat"
ethernet0.addressType = "generated"
ethernet0.generatedAddress = "00:0c:29:30:46:a5"
ethernet0.generatedAddressOffset = "0"

usb.present = "FALSE"
sound.present = "FALSE"

scsi0.present = "FALSE"
scsi0.virtualdev = "lsilogic"
scsi0:0.present = "FALSE"
scsi0:0.deviceType = "disk"
scsi0:0.mode = "persistent"
scsi0:0.redo = ""
scsi0:0.writeThrough = "FALSE"
scsi0:0.startConnected = "FALSE"

scsi0:1.present = "FALSE"
floppy0.present = "FALSE"
ide0:0.present = "TRUE"
ide0:1.present = "FALSE"
ide1:1.present = "FALSE"

ide1:0.present = "TRUE"
ide1:0.deviceType = "cdrom-image"
ide1:0.autodetect = "TRUE"
ide1:0.startConnected = "TRUE"

ide0:0.redo = ""

---

### Post by dicecca112 on 2008-03-19
> **CoffeeBreath said:**
> I'm trying to understand linux world.
Thanks



#!/usr/bin/vmware
displayName = "Windows XP"
guestOS = "winxphome"

memsize = "64"
ide0:0.fileName = "WindowsXP.vmdk"
ide1:0.fileName = "WindowsXP.iso"

# DEFAULT SETTINGS UNDER THIS LINE
config.version = "8"
virtualHW.version = "3"

MemAllowAutoScaleDown = "FALSE"
MemTrimRate = "-1"

uuid.location = "56 4d 34 58 fd 57 00 42-76 91 96 91 01 30 46 a5"
uuid.bios = "56 4d 34 58 fd 57 00 42-76 91 96 91 01 30 46 a5"

uuid.action = "create"
checkpoint.vmState = ""

ethernet0.present = "TRUE"
ethernet0.connectionType = "nat"
ethernet0.addressType = "generated"
ethernet0.generatedAddress = "00:0c:29:30:46:a5"
ethernet0.generatedAddressOffset = "0"

usb.present = "FALSE"
sound.present = "FALSE"

scsi0.present = "FALSE"
scsi0.virtualdev = "lsilogic"
scsi0:0.present = "FALSE"
scsi0:0.deviceType = "disk"
scsi0:0.mode = "persistent"
scsi0:0.redo = ""
scsi0:0.writeThrough = "FALSE"
scsi0:0.startConnected = "FALSE"

scsi0:1.present = "FALSE"
floppy0.present = "FALSE"
ide0:0.present = "TRUE"
ide0:1.present = "FALSE"
ide1:1.present = "FALSE"

ide1:0.present = "TRUE"
ide1:0.deviceType = "cdrom-image"
ide1:0.autodetect = "TRUE"
ide1:0.startConnected = "TRUE"

ide0:0.redo = ""

it looks like a configuration file for a VM, usually a .vmx file

The first block of code shows you its Name is Windows XP and your virtualizing Windows XP Home

second says your hard disk is IDE 0, and IDE 1 is the CD ROM using the ISO file it lists

The next 4 I have no idea

5th says you have ethernet and its using an NAT Connection

6th says USB and Sound hardware are not being virtualized and won't be available in the VM

last two are setups for your Virtual HDD And Virtual CDROM

---

### Post by gdrumm on 2008-03-19
The uuid.location information basically tells VMware information about the specific, unique virtual machine. VMWare gives you alot more information about this at their website...

[http://www.vmware.com/support/ws55/doc/ws_move_uuid_format.html]("http://www.vmware.com/support/ws55/doc/ws_move_uuid_format.html")

GLD

---

