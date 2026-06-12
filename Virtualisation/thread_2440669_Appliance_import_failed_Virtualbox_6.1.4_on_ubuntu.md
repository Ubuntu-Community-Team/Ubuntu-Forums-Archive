---
title: "Appliance import failed Virtualbox 6.1.4 on ubuntu 20.04"
date: 2020-04-13
forum: Virtualisation
---

### Post by mbudd on 2020-04-13
I am setting up a new XPS-15 with uBuntu 20.04. On the old machine I upgraded Virtualbox to the 6.1 latest and exported three VMs. One XP Pro, two Windows 10 home, three Windows 10 Pro. Then moved the .ova files to the new machine and imported them. The first two worked fine. The Windows 10 Pro does not work. It fails and here is the last part of the import failure:

```
vboxmanage import "/home/mbudd/Documents/VirtualboxBkup/Windows 10 Procur.ova"
0%...10%...20%...30%...40%...50%...60%...70%...80%...90%...100%
Interpreting /home/mbudd/Documents/VirtualboxBkup/Windows 10 Procur.ova...
OK.
Disks:
  vmdisk1	53687091200	-1	http://www.vmware.com/interfaces/specifications/vmdk.html#streamOptimized Windows 10 Procur-disk001.vmdk	-1	-1	

Virtual system 0:
 0: Suggested OS type: "Windows10_64"
    (change with "--vsys 0 --ostype <type>"; use "list ostypes" to list all possible values)
 1: Suggested VM name "Windows 10 Pro"
    (change with "--vsys 0 --vmname <name>")
 2: Suggested VM group "/"
    (change with "--vsys 0 --group <group>")
 3: Suggested VM settings file name "/home/mbudd/VirtualBox VMs/Windows 10 Pro/Windows 10 Pro.vbox"
    (change with "--vsys 0 --settingsfile <filename>")
 4: Suggested VM base folder "/home/mbudd/VirtualBox VMs"
    (change with "--vsys 0 --basefolder <path>")
 5: Number of CPUs: 2
    (change with "--vsys 0 --cpus <n>")
 6: Guest memory: 4096 MB
    (change with "--vsys 0 --memory <MB>")
 7: Sound card (appliance expects "", can change on import)
    (disable with "--vsys 0 --unit 7 --ignore")
 8: USB controller
    (disable with "--vsys 0 --unit 8 --ignore")
 9: Network adapter: orig NAT, config 3, extra slot=0;type=NAT
10: CD-ROM
    (disable with "--vsys 0 --unit 10 --ignore")
11: SATA controller, type AHCI
(disable with "--vsys 0 --unit 11 --ignore")
12: Hard disk image: source image=Windows 10 Procur-disk001.vmdk, target path=Windows 10 Procur-disk001.vmdk, controller=11;channel=0
(change target path with "--vsys 0 --unit 12 --disk path";
disable with "--vsys 0 --unit 12 --ignore")
0%...10%...20%...30%...
Progress state: NS_ERROR_INVALID_ARG
VBoxManage: error: Appliance import failed
VBoxManage: error: Code NS_ERROR_INVALID_ARG (0x80070057) - Invalid argument value (extended info not available)
VBoxManage: error: Context: "RTEXITCODE handleImportAppliance(HandlerArg*)" at line 1118 of file VBoxManageAppliance.cpp
```

Please help me get this going. I have a meeting on Wednesday and will need this.
Marvin

---

### Post by DuckHook on 2020-04-14
*Thread moved to **Virtualisation** as the more appropriate forum.*

---

### Post by mbudd on 2020-04-14
Follow up with this here - [https://forums.virtualbox.org/viewtopic.php?f=1&t=97659&p=473851#p473851](https://forums.virtualbox.org/viewtopic.php?f=1&t=97659&p=473851#p473851). The solution to the error was not found. But copying the actual VM files to the new machine and then using Machine Add to incorporate them in the new laptop allowed me to circumvent the export/import fault.

---

