---
title: "All of a sudden, VirtualBox is freezing"
date: 2014-06-24
forum: Virtualisation
---

### Post by fernandojosecabral on 2014-06-24
Using VB for several month. All of a sudden, is started freezing. It shows the initial screen and freezes up.
I can't figure out what happened. Here are the logs I found. First, selectorwindow.log (from .Virtualbox directory)
```
using sysfs
00:00:00.123567 nspr-2   NetIfAdpCtlOut: VBoxNetAdpCtl: Error while retrieving link speed for wlan0: VBoxNetAdpCtl: ioctl failed: Operation not supported
00:00:00.124355 nspr-2   Failed to open "/dev/vboxdrvu", errno=13, rc=VERR_VM_DRIVER_NOT_ACCESSIBLE
00:00:00.124695 nspr-2   VDInit finished
00:00:00.132606 nspr-2   Loading settings file "/home/fernando/VirtualBox VMs/Windows xt/Windows xt.vbox" with version "1.14-linux"
00:00:00.134198 nspr-2   Loading settings file "/home/fernando/VirtualBox VMs/windows 8 64/windows 8 64.vbox" with version "1.14-linux"
00:00:00.135116 nspr-2   Loading settings file "/home/fernando/VirtualBox VMs/Windows XP 64/Windows XP 64.vbox" with version "1.12-linux"
00:00:00.135548 nspr-2   Loading settings file "/home/fernando/VirtualBox VMs/Tails/Tails.vbox" with version "1.12-linux"
00:00:00.135975 nspr-2   Loading settings file "/home/fernando/VirtualBox VMs/kubuntu/kubuntu.vbox" with version "1.12-linux"
00:00:00.523716 nspr-2   **Failed to open "/dev/vboxdrvu", errno=13, rc=VERR_VM_DRIVER_NOT_ACCESSIBLE**

```
Then, VBoxSVC:
```
VirtualBox XPCOM Server 4.3.0 r89960 linux.amd64 (Oct 15 2013 11:23:14) release log
00:00:00.000311 main     Log opened 2014-06-24T22:07:33.286661000Z
00:00:00.000316 main     Build Type: release
00:00:00.000323 main     OS Product: Linux
00:00:00.000325 main     OS Release: 3.11.0-12-generic
00:00:00.000327 main     OS Version: #19-Ubuntu SMP Wed Oct 9 16:20:46 UTC 2013
00:00:00.000366 main     DMI Product Name: HP ENVY dv7 Notebook PC
00:00:00.000379 main     DMI Product Version: 0889120000305920000620100
00:00:00.000506 main     Host RAM: 15938MB total, 14228MB available
00:00:00.000515 main     Executable: /usr/lib/virtualbox/VBoxSVC
00:00:00.000517 main     Process ID: 23852
00:00:00.000518 main     Package type: LINUX_64BITS_UBUNTU_13_04
00:00:00.106967 nspr-2   Loading settings file "/home/fernando/.VirtualBox/VirtualBox.xml" with version "1.12-linux"
00:00:00.117115 nspr-2   Successfully initialised host USB using sysfs
00:00:00.123567 nspr-2   [B]NetIfAdpCtlOut: VBoxNetAdpCtl: Error while retrieving link speed for wlan0: VBoxNetAdpCtl: ioctl failed: Operation not supported
00:00:00.124355 nspr-2   Failed to open "/dev/vboxdrvu", errno=13, rc=VERR_VM_DRIVER_NOT_ACCESSIBLE[/B]
00:00:00.124695 nspr-2   VDInit finished
00:00:00.132606 nspr-2   Loading settings file "/home/fernando/VirtualBox VMs/Windows xt/Windows xt.vbox" with version "1.14-linux"
00:00:00.134198 nspr-2   Loading settings file "/home/fernando/VirtualBox VMs/windows 8 64/windows 8 64.vbox" with version "1.14-linux"
00:00:00.135116 nspr-2   Loading settings file "/home/fernando/VirtualBox VMs/Windows XP 64/Windows XP 64.vbox" with version "1.12-linux"
00:00:00.135548 nspr-2   Loading settings file "/home/fernando/VirtualBox VMs/Tails/Tails.vbox" with version "1.12-linux"
00:00:00.135975 nspr-2   Loading settings file "/home/fernando/VirtualBox VMs/kubuntu/kubuntu.vbox" with version "1.12-linux"
00:00:00.523716 nspr-2   Failed to open "/dev/vboxdrvu", errno=13, rc=VERR_VM_DRIVER_NOT_ACCESSIBLE
00:00:35.381421 main     ERROR [COM]: aRC=VBOX_E_OBJECT_IN_USE (0x80bb000c) aIID={05f2bbb6-a3a6-4fb9-9b49-6d0dda7142ac} aComponent={Medium} aText={Medium '/home/fernando/VirtualBox VMs/Windows xt/Windows xt.vdi' cannot be closed because it is still attached to 1 virtual machines}, preserve=false
00:00:35.381629 main     ERROR [COM]: aRC=VBOX_E_OBJECT_IN_USE (0x80bb000c) aIID={05f2bbb6-a3a6-4fb9-9b49-6d0dda7142ac} aComponent={Medium} aText={Medium '/home/fernando/VirtualBox VMs/windows 8 64/windows 8 64.vdi' cannot be closed because it is still attached to 1 virtual machines}, preserve=false
00:00:35.381792 main     ERROR [COM]: aRC=VBOX_E_OBJECT_IN_USE (0x80bb000c) aIID={05f2bbb6-a3a6-4fb9-9b49-6d0dda7142ac} aComponent={Medium} aText={Medium '/home/fernando/VirtualBox VMs/Windows XP 64/Windows XP 64-disk1.vmdk' cannot be closed because it is still attached to 1 virtual machines}, preserve=false
00:00:35.381932 main     ERROR [COM]: aRC=VBOX_E_OBJECT_IN_USE (0x80bb000c) aIID={05f2bbb6-a3a6-4fb9-9b49-6d0dda7142ac} aComponent={Medium} aText={Medium '/home/fernando/VirtualBox VMs/Tails/Tails-disk1.vmdk' cannot be closed because it is still attached to 1 virtual machines}, preserve=false
00:00:35.382051 main     ERROR [COM]: aRC=VBOX_E_OBJECT_IN_USE (0x80bb000c) aIID={05f2bbb6-a3a6-4fb9-9b49-6d0dda7142ac} aComponent={Medium} aText={Medium '/home/fernando/VirtualBox VMs/kubuntu/kubuntu-disk1.vmdk' cannot be closed because it is still attached to 1 virtual machines}, preserve=false
00:00:35.383020 Watcher  ERROR [COM]: aRC=E_ACCESSDENIED (0x80070005) aIID={fafa4e17-1ee2-4905-a10e-fe7c18bf5554} aComponent={VirtualBox} aText={The object is not ready}, preserve=false

```
I see the following errors, but I can't figure out why. And I don't know if this is what is freezing the virtual machine
```
NetIfAdpCtlOut: VBoxNetAdpCtl: Error while retrieving link speed for  wlan0: VBoxNetAdpCtl: ioctl failed: Operation not supported
00:00:00.124355 nspr-2   Failed to open "/dev/vboxdrvu", errno=13, rc=VERR_VM_DRIVER_NOT_ACCESSIBLE
```

As always, any hints most wellcome.

- fernando

---

