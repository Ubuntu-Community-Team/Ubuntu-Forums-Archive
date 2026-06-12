---
title: "[vmware2libvirt] NameError: name 'disk' is not defined"
date: 2008-11-23
forum: Virtualisation
---

### Post by deadland on 2008-11-23
Hi ubuntu community,

I want to switch from vmware server to virt-manager. So I tried to convert my winxppro.vmx to winxp.xml with vmware2libvirt (virt-goodies 0.3) but I've got an error message:

```
sudo vmware2libvirt -f winxppro.vmx > winxp.xml
[sudo] password for obertm: 
Traceback (most recent call last):
  File "/usr/bin/vmware2libvirt", line 232, in <module>
    </disk>''' + get_network(vmx,  bridge) + '''
NameError: name 'disk' is not defined

```

Thats my vmx (vmware server 2):

```
#!/usr/bin/vmware
.encoding = "UTF-8"
config.version = "8"
virtualHW.version = "4"
ide0:0.present = "TRUE"
ide0:0.filename = "winxppro.vmdk"
memsize = "1024"
MemAllowAutoScaleDown = "FALSE"
ide1:0.present = "FALSE"
ide1:0.fileName = "auto detect"
ide1:0.deviceType = "atapi-cdrom"
ide1:0.autodetect = "TRUE"
floppy0.present = "FALSE"
ethernet0.present = "TRUE"
usb.present = "TRUE"
sound.present = "TRUE"
sound.virtualDev = "es1371"
displayName = "Windows XP Pro"
guestOS = "winxppro"
nvram = "WindowsXPPro.nvram"
MemTrimRate = "0"
sched.mem.pshare.enable = "FALSE"

ide0:0.redo = ""
ethernet0.addressType = "generated"
uuid.location = "56 4d 59 69 63 c1 28 02-2d 1f 25 29 cc d8 f4 63"
uuid.bios = "56 4d 59 69 63 c1 28 02-2d 1f 25 29 cc d8 f4 63"
ethernet0.generatedAddress = "00:0c:29:d8:f4:63"
ethernet0.generatedAddressOffset = "0"

tools.syncTime = "TRUE"
ide1:0.startConnected = "TRUE"

uuid.action = "create"

checkpoint.vmState = ""

tools.remindInstall = "FALSE"

ethernet0.connectionType = "nat"


priority.grabbed = "high"
priority.ungrabbed = "normal"

numvcpus = "2"
sound.startConnected = "FALSE"
sound.fileName = "-1"

workingDir = "/home/USER/vmware/winxppro"

debug = "FALSE"
disable_acceleration = "FALSE"
monitor_control.log_vmsample = "FALSE"

fileSearchPath = "."

snapshot.disabled = "TRUE"

ide0:1.present = "TRUE"
ide0:1.fileName = "auto detect"
ide0:1.autodetect = "TRUE"
ide0:1.deviceType = "atapi-cdrom"

sound.autodetect = "TRUE"

ide0:1.startConnected = "TRUE"

ide0:0.mode = "independent-persistent"


extendedConfigFile = "winxppro.vmxf"
virtualHW.productCompatibility = "hosted"
tools.upgrade.policy = "manual"


vmotion.checkpointFBSize = "16777216"
```

Any suggestions?

---

### Post by starman5 on 2009-04-09
i have the same problem any one got a solution

---

### Post by luca219 on 2009-06-17
i have the same problem any one got a solution

---

### Post by Ang Way Chuang on 2011-01-04
I have the same problem. It's solved by renaming ide0:0.filename to ide0:0.fileName. The vmware2libvirt python expects that. I created the vmware image using easyvmx and it worked well on vmwareplayer. I supposed that you created your vmx using the same tool. I shall the modified vmware2libvirt to the author as well.

---

