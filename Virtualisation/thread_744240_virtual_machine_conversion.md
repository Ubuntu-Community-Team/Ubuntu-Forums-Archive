---
title: "virtual machine conversion"
date: 2008-04-03
forum: Virtualisation
---

### Post by Matt26 on 2008-04-03
is it possible to convert a vm created in vmware workstation 6 to run under vmware server?  host OS is ubuntu 7.10.  thanks.

---

### Post by fjgaude on 2008-04-03
I believe it is by commenting out the features that Workstation has and Server doesn't in the .vmx file of the VM. Try comparing, side-by-side, the two .vmx files.

Let us know how you make out.

---

### Post by Matt26 on 2008-04-03
i do not have an existing vmx file for vmware server for comparison... can i obtain a sample copy somewhere?

---

### Post by fjgaude on 2008-04-03
Here's the one from one of my files, I didn't seem to be able to attach it:

```
#!/usr/bin/vmware
config.version = "8"
virtualHW.version = "4"
scsi0.present = "TRUE"
memsize = "512"
mainMem.useNamedFile = FALSE
ide0:0.present = "TRUE"
ide0:0.fileName = "Windows XP Professional-000001.vmdk"
ide0:0.writeThrough = "FALSE"
ide1:0.present = "TRUE"
ide1:0.fileName = "/dev/hdd"
ide1:0.deviceType = "cdrom-raw"
floppy0.fileName = "/dev/fd0"
Ethernet0.present = "TRUE"
Ethernet0.connectionType = "nat"
displayName = "WinXP Pro SP2"
guestOS = "winxppro"
priority.grabbed = "normal"
priority.ungrabbed = "normal"
powerType.powerOff = "hard"
powerType.powerOn = "hard"
powerType.suspend = "hard"
powerType.reset = "hard"
ide0:0.redo = ""
ethernet0.addressType = "generated"
uuid.location = "56 4d d8 a4 8f 56 cf 48-ef 08 da d6 ee 08 86 5f"
uuid.bios = "56 4d 04 8b 41 2c 2b 9d-4c 1e 08 6a 6d f7 c7 69"
ethernet0.generatedAddress = "00:0c:29:f7:c7:69"
ethernet0.generatedAddressOffset = "0"
ide1:0.startConnected = "TRUE"
tools.syncTime = "TRUE"
checkpoint.vmState = ""
snapshot.action = "keep"
gui.exitAtPowerOff = "TRUE"
gui.powerOnAtStartup = "TRUE"
numvcpus = "1"
autostart = "poweron"
checkpoint.vmState.readOnly = "FALSE"
annotation = "WinXP Pro SP2 with Paint Shop Pro, InDesign CS, and Xara Xtreme installed."
usb.present = "TRUE"
usb.generic.autoconnect = "FALSE"
usb.autoConnect.device0 = ""
sound.present = "TRUE"
sound.fileName = "-1"
sound.autodetect = "TRUE"
sound.virtualDev = "es1371"
usb.autoConnect.device1 = ""
floppy0.startConnected = "FALSE"
ethernet0.vnet = "/dev/vmnet8"
sound.startConnected = "FALSE"
uuid.action = "keep"

```

Hope this helps. Let us know.

---

