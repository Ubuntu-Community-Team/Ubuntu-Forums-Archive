---
title: "[SOLVED] Can't setup joes under vmware-server 1.04"
date: 2007-12-07
forum: Server Platforms
---

### Post by deadland on 2007-12-07
Hi there,

some can help me to install joes under vmware-server 1.04, because it doesn't work for me.

Best way would be, if someone could send me his working vmx file.

Thanks

---

### Post by deadland on 2007-12-07
I've got it work by using the combination:

ide and lsilogic

---

### Post by deadland on 2007-12-07
```
#!/usr/bin/vmware
config.version = "8"
virtualHW.version = "4"
scsi0.present = "TRUE"
scsi0.virtualDev = "lsilogic"
memsize = "512"
ide0:0.present = "TRUE"
ide0:0.fileName = "Ubuntu 5.vmdk"
ide0:0.writeThrough = "FALSE"
ide1:0.present = "TRUE"
ide1:0.fileName = "/home/*****USERNAME***/Desktop/ubuntu-7.10-jeos-i386.iso"
ide1:0.deviceType = "cdrom-image"
floppy0.startConnected = "FALSE"
floppy0.fileName = "/dev/fd0"
Ethernet0.present = "TRUE"
displayName = "Ubuntu 5"
guestOS = "ubuntu"
priority.grabbed = "normal"
priority.ungrabbed = "normal"
powerType.powerOff = "hard"
powerType.powerOn = "hard"
powerType.suspend = "hard"
powerType.reset = "hard"

ide0:0.redo = ""
ethernet0.addressType = "generated"
uuid.location = "56 4d 5e bf 77 ff c1 40-a7 7b 60 5d 06 4e 51 28"
uuid.bios = "56 4d 5e bf 77 ff c1 40-a7 7b 60 5d 06 4e 51 28"
ethernet0.generatedAddress = "00:0c:29:4e:51:28"
ethernet0.generatedAddressOffset = "0"

numvcpus = "2"
floppy0.present = "FALSE"
```

---

