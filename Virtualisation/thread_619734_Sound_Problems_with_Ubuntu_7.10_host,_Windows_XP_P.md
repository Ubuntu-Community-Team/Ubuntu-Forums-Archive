---
title: "Sound Problems with Ubuntu 7.10 host, Windows XP Pro guest"
date: 2007-11-21
forum: Virtualisation
---

### Post by mtxcoll on 2007-11-21
Hi, I've successfully installed Windows XP Professional as a guest machine using VMware Player and would like to get sound working without the need of killing other sound processes. After installing vmwaredsp-1.3, I symlinked vmplayer to vmware; however, when I start vmwarealsa or vmwaresd I get the following error message:

```

Failed to open sound device /dev/dsp: No such device
Failed to connect virtual device sound.

```

When I run vmware (vmplayer) itself,  if there is another sound program such as xmms running:

```

Failed to open sound device /dev/dsp: Device or resource busy
Failed to connect virtual device sound.

```

My /dev/dsp permissions:

```

crw-rw---- 1 root audio 14, 3 2007-11-21 14:41 /dev/dsp

```

My *.vmx file looks like

```

#!/usr/bin/vmware
config.version = "8"
virtualHW.version = "3"
ide0:0.present = "TRUE"
ide0:0.filename = "WindowsXPPro.vmdk"
memsize = "256"
MemAllowAutoScaleDown = "FALSE"
ide1:0.present = "FALSE"
ide1:0.fileName = "loaded.iso"
ide1:0.deviceType = "cdrom-image"
ide1:0.autodetect = "TRUE"
sound.present = "TRUE"
sound.virtualDev = "es1371"
sound.autodetect = "TRUE"
sound.fileName = "-1"
floppy0.present = "FALSE"
ethernet0.present = "TRUE"
usb.present = "TRUE"
displayName = "Windows XP Pro"
guestOS = "winxppro"
nvram = "WindowsXPPro.nvram"
MemTrimRate = "-1"
ide0:0.redo = ""
ethernet0.connectionType = "nat"
ethernet0.addressType = "generated"
uuid.location = "56 4d af a5 53 85 25 8a-42 ec c1 92 c9 6a 25 41"
uuid.bios = "56 4d af a5 53 85 25 8a-42 ec c1 92 c9 6a 25 41"
ethernet0.generatedAddress = "00:0c:29:6a:25:41"
ethernet0.generatedAddressOffset = "0"
tools.syncTime = "TRUE"
ide1:0.startConnected = "TRUE"
uuid.action = "create"
checkpoint.vmState = ""
tools.remindInstall = "TRUE"
floppy0.clientDevice = "FALSE"
extendedConfigFile = "winxpboot.vmxf"
virtualHW.productCompatibility = "hosted"
tools.upgrade.policy = "manual"
bios.bootDelay = "3000"

usb.autoConnect.device0 = ""

sound.startConnected = "FALSE"

```

---

### Post by dpj23 on 2007-11-21
If the host system is using the sound card... The quest will not have access to it...  I run across this problem often during the course of a work day...  I usually keep the host having the rights to the sound and disconnect the sound device for the virtual machine...

This will eliminate the message you are receiving when the quest is trying to use the sound card...

---

### Post by mtxcoll on 2007-11-22
> **dpj23 said:**
> If the host system is using the sound card... The quest will not have access to it...  I run across this problem often during the course of a work day...  I usually keep the host having the rights to the sound and disconnect the sound device for the virtual machine...

This will eliminate the message you are receiving when the quest is trying to use the sound card...

I could do that; however, I would really like a solution where vmware can play sound simultaneously; that way I can listen to music on my host OS while being able to hear alerts on the guest. I heard that the vmwarealsa and vmwareesd wrappers can take care of this problem; however, I have had the aforementioned error when trying to use them.

---

