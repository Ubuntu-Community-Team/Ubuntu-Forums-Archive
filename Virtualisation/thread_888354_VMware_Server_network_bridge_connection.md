---
title: "VMware Server network bridge connection"
date: 2008-08-13
forum: Virtualisation
---

### Post by Blind Tiger on 2008-08-13
I am running XP Pro as a guest OS within VMware Server 1.0.6 on Ubuntu 8.04.1 host.  The default bridge networking does not function, despite being correctly installed/configured.  I can get networking up using NAT.  The output of my .vmx file is posted below.  The only difference when using NAT vs Bridged networking is the line:  > Ethernet0.connectionType =  where it's either = "bridged" or = "nat".  How can I repair/activate this bridge, as my VPN client requires bridged networking to properly connect?

> #!/usr/bin/vmware
config.version = "8"
virtualHW.version = "4"
scsi0.present = "TRUE"
memsize = "256"
ide0:0.present = "TRUE"
ide0:0.fileName = "Windows XP Professional.vmdk"
ide0:0.writeThrough = "TRUE"
ide1:0.present = "TRUE"
ide1:0.fileName = "/dev/scd0"
ide1:0.deviceType = "cdrom-raw"
floppy0.fileName = "/dev/fd0"
Ethernet0.present = "TRUE"
displayName = "Windows XP Professional"
guestOS = "winxppro"
priority.grabbed = "normal"
priority.ungrabbed = "normal"
powerType.powerOff = "hard"
powerType.powerOn = "hard"
powerType.suspend = "hard"
powerType.reset = "hard"

ide0:0.redo = ""
ethernet0.addressType = "generated"
uuid.location = "56 4d 13 7a a9 32 1e 82-0c ce 85 9c d6 ef 24 3c"
uuid.bios = "56 4d 13 7a a9 32 1e 82-0c ce 85 9c d6 ef 24 3c"
ethernet0.generatedAddress = "00:0c:29:ef:24:3c"
ethernet0.generatedAddressOffset = "0"

ide1:0.startConnected = "TRUE"
tools.syncTime = "FALSE"

Ethernet1.present = "FALSE"
Ethernet1.connectionType = "custom"
Ethernet1.vnet = "/dev/vmnet0"

ethernet1.addressType = "generated"
ethernet1.generatedAddress = "00:0c:29:ef:24:46"
ethernet1.generatedAddressOffset = "10"

usb.present = "TRUE"
usb.generic.autoconnect = "FALSE"

Ethernet0.startConnected = "TRUE"

Ethernet2.present = "FALSE"
Ethernet2.connectionType = "custom"
Ethernet2.vnet = "/dev/vmnet8"

ethernet2.addressType = "generated"
ethernet2.generatedAddress = "00:0c:29:ef:24:50"
ethernet2.generatedAddressOffset = "20"

Ethernet0.connectionType = "bridged"

usb.autoConnect.device0 = ""

Ethernet0.vnet = "/dev/vmnet0"

---

