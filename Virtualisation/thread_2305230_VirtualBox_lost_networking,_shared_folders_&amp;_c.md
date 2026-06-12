---
title: "VirtualBox lost networking, shared folders &amp; clipboard, &amp; printing to USB printer"
date: 2015-12-03
forum: Virtualisation
---

### Post by BPickle on 2015-12-03
Last Friday, due to a recent virtualbox update, my WinXP guest on Ubuntu 14.04 refused to boot up. Eventually I discovered that the extensions were the problem.

Since then I've tried multiple versions, and tried using the official versions from Oracle, and I still can't get a VM that is fully functional. I am lacking:


[LIST]
[*]Networking. 
[*]Shared clipboard. 
[*]Shared folders. 
[*]Printing to a USB printer. 
[*]The tray icon. 
[/LIST]

I can't terminate the VboxTray and VBoxService processes via TaskManager. The WinXP event log indicates that VBoxService didn't start properly, though it does appear in TaskManager.

If I "connect" the network cable in VirtualBox, the WinXP guest notices and tried to get an IP, unsuccessfully. I can mouse out to the host and in to the guest, which tells me that guest additions are working at least somewhat. But if I try to browse to \\VBoxsvr using Explorer, it sort of hangs when I click that, never showing the two shared folders I set up.

Anyone have any suggestions?

---

### Post by zexelon2 on 2015-12-04
If I understand correctly you already updated the "Extensions Pack" to the current version of VBox you are using? Did you also try un-installing and completely re-installing the guest additions in the VM Guest?

---

### Post by BPickle on 2015-12-04
I've done both repeatedly, over and over again, making sure that the version of both matches the version of VirtualBox I'm trying.

In fiddling with it a little more, I discovered some entries in VBoxSVC.log:

```
VirtualBox XPCOM Server 4.3.34_Ubuntu r104062 linux.amd64 (Nov 23 2015 18:06:43) release log
00:00:00.000335 main     Log opened 2015-12-04T16:35:32.571250000Z
00:00:00.000337 main     Build Type: release
00:00:00.000340 main     OS Product: Linux
00:00:00.000341 main     OS Release: 3.16.0-53-generic
00:00:00.000342 main     OS Version: #72~14.04.1-Ubuntu SMP Fri Nov 6 18:17:23 UTC 2015
00:00:00.000366 main     DMI Product Name: MS-7693
00:00:00.000374 main     DMI Product Version: 4.0
00:00:00.000444 main     Host RAM: 7773MB total, 4974MB available
00:00:00.000447 main     Executable: /usr/lib/virtualbox/VBoxSVC
00:00:00.000447 main     Process ID: 22899
00:00:00.000448 main     Package type: LINUX_64BITS_GENERIC (OSE)
00:00:00.105680 nspr-2   Home directory: '/home/bpickle/.VirtualBox'
00:00:00.106105 nspr-2   Loading settings file "/home/bpickle/.VirtualBox/VirtualBox.xml" with version "1.12-linux"
00:00:00.109911 nspr-2   Failed to retrive disk info: getDiskName(/dev/mapper/ubuntu--vg-root) --> ubuntu--vg-root
00:00:00.110886 nspr-2   HostDnsMonitor: old information
00:00:00.110903 nspr-2     no server entries
00:00:00.110917 nspr-2     no search string entries
00:00:00.110928 nspr-2     no domain set
00:00:00.110938 nspr-2   HostDnsMonitor: new information
00:00:00.110948 nspr-2     server 1: 127.0.1.1
00:00:00.110961 nspr-2     search string 1: home
00:00:00.110972 nspr-2     domain: home
00:00:00.110988 nspr-2   HostDnsMonitorProxy::notify
00:00:00.112972 nspr-2   VDInit finished
00:00:00.120325 nspr-2   Loading settings file "/home/bpickle/VirtualBox VMs/WinXP/WinXP.vbox" with version "1.13-linux"
00:00:00.122201 nspr-2   Loading settings file "/home/bpickle/VirtualBox VMs/TinyLinux/TinyLinux.vbox" with version "1.14-linux"
00:00:00.261144 nspr-3   WARNING [COM]: aRC=NS_ERROR_FAILURE (0x80004005) aIID={93269330-48ca-4096-b4a2-1189df336267} aComponent={Host} aText={VirtualBox is not currently allowed to access USB devices.  You can change this by adding your user to the 'vboxusers' group.  Please see the user manual for a more detailed explanation}, preserve=true 
00:00:00.396866 nspr-2   WARNING [COM]: aRC=NS_ERROR_FAILURE (0x80004005) aIID={93269330-48ca-4096-b4a2-1189df336267} aComponent={Host} aText={VirtualBox is not currently allowed to access USB devices.  You can change this by adding your user to the 'vboxusers' group.  Please see the user manual for a more detailed explanation}, preserve=true 
00:00:00.397966 nspr-2   WARNING [COM]: aRC=NS_ERROR_FAILURE (0x80004005) aIID={93269330-48ca-4096-b4a2-1189df336267} aComponent={Host} aText={VirtualBox is not currently allowed to access USB devices.  You can change this by adding your user to the 'vboxusers' group.  Please see the user manual for a more detailed explanation}, preserve=true 
00:04:37.147693 nspr-2   WARNING [COM]: aRC=NS_ERROR_FAILURE (0x80004005) aIID={93269330-48ca-4096-b4a2-1189df336267} aComponent={Host} aText={VirtualBox is not currently allowed to access USB devices.  You can change this by adding your user to the 'vboxusers' group.  Please see the user manual for a more detailed explanation}, preserve=true 
00:04:37.149337 nspr-2   WARNING [COM]: aRC=NS_ERROR_FAILURE (0x80004005) aIID={93269330-48ca-4096-b4a2-1189df336267} aComponent={Host} aText={VirtualBox is not currently allowed to access USB devices.  You can change this by adding your user to the 'vboxusers' group.  Please see the user manual for a more detailed explanation}, preserve=true 
00:04:37.384222 nspr-2   WARNING [COM]: aRC=NS_ERROR_FAILURE (0x80004005) aIID={93269330-48ca-4096-b4a2-1189df336267} aComponent={Host} aText={VirtualBox is not currently allowed to access USB devices.  You can change this by adding your user to the 'vboxusers' group.  Please see the user manual for a more detailed explanation}, preserve=true 
00:04:37.385350 nspr-3   WARNING [COM]: aRC=NS_ERROR_FAILURE (0x80004005) aIID={93269330-48ca-4096-b4a2-1189df336267} aComponent={Host} aText={VirtualBox is not currently allowed to access USB devices.  You can change this by adding your user to the 'vboxusers' group.  Please see the user manual for a more detailed explanation}, preserve=true 
00:04:37.389921 nspr-3   WARNING [COM]: aRC=NS_ERROR_FAILURE (0x80004005) aIID={93269330-48ca-4096-b4a2-1189df336267} aComponent={Host} aText={VirtualBox is not currently allowed to access USB devices.  You can change this by adding your user to the 'vboxusers' group.  Please see the user manual for a more detailed explanation}, preserve=true 
00:04:37.400057 nspr-3   WARNING [COM]: aRC=NS_ERROR_FAILURE (0x80004005) aIID={93269330-48ca-4096-b4a2-1189df336267} aComponent={Host} aText={VirtualBox is not currently allowed to access USB devices.  You can change this by adding your user to the 'vboxusers' group.  Please see the user manual for a more detailed explanation}, preserve=true 
00:04:37.401601 nspr-3   Load [/usr/lib/virtualbox/ExtensionPacks/Oracle_VM_VirtualBox_Extension_Pack/linux.amd64/VBoxHostWebcam.so] rc VINF_SUCCESS
00:04:37.417442 nspr-2   ERROR [COM]: aRC=VBOX_E_IPRT_ERROR (0x80bb0005) aIID={480cf695-2d8d-4256-9c7c-cce4184fa048} aComponent={SessionMachine} aText={Saved screenshot data is not available (VERR_NOT_SUPPORTED)}, preserve=false
00:04:37.418832 nspr-3   WARNING [COM]: aRC=NS_ERROR_FAILURE (0x80004005) aIID={93269330-48ca-4096-b4a2-1189df336267} aComponent={Host} aText={VirtualBox is not currently allowed to access USB devices.  You can change this by adding your user to the 'vboxusers' group.  Please see the user manual for a more detailed explanation}, preserve=true 
00:04:37.432639 nspr-3   WARNING [COM]: aRC=NS_ERROR_FAILURE (0x80004005) aIID={93269330-48ca-4096-b4a2-1189df336267} aComponent={Host} aText={VirtualBox is not currently allowed to access USB devices.  You can change this by adding your user to the 'vboxusers' group.  Please see the user manual for a more detailed explanation}, preserve=true 
00:04:37.538596 nspr-3   WARNING [COM]: aRC=NS_ERROR_FAILURE (0x80004005) aIID={93269330-48ca-4096-b4a2-1189df336267} aComponent={Host} aText={VirtualBox is not currently allowed to access USB devices.  You can change this by adding your user to the 'vboxusers' group.  Please see the user manual for a more detailed explanation}, preserve=true 
00:04:37.539059 nspr-3   WARNING [COM]: aRC=NS_ERROR_FAILURE (0x80004005) aIID={93269330-48ca-4096-b4a2-1189df336267} aComponent={Host} aText={VirtualBox is not currently allowed to access USB devices.  You can change this by adding your user to the 'vboxusers' group.  Please see the user manual for a more detailed explanation}, preserve=true 
00:04:37.539768 nspr-3   WARNING [COM]: aRC=NS_ERROR_FAILURE (0x80004005) aIID={93269330-48ca-4096-b4a2-1189df336267} aComponent={Host} aText={VirtualBox is not currently allowed to access USB devices.  You can change this by adding your user to the 'vboxusers' group.  Please see the user manual for a more detailed explanation}, preserve=true 
00:04:38.259559 nspr-2   WARNING [COM]: aRC=NS_ERROR_FAILURE (0x80004005) aIID={93269330-48ca-4096-b4a2-1189df336267} aComponent={Host} aText={VirtualBox is not currently allowed to access USB devices.  You can change this by adding your user to the 'vboxusers' group.  Please see the user manual for a more detailed explanation}, preserve=true 
00:04:38.260908 nspr-3   WARNING [COM]: aRC=NS_ERROR_FAILURE (0x80004005) aIID={93269330-48ca-4096-b4a2-1189df336267} aComponent={Host} aText={VirtualBox is not currently allowed to access USB devices.  You can change this by adding your user to the 'vboxusers' group.  Please see the user manual for a more detailed explanation}, preserve=true 
00:07:40.006364 nspr-3   WARNING [COM]: aRC=NS_ERROR_FAILURE (0x80004005) aIID={93269330-48ca-4096-b4a2-1189df336267} aComponent={Host} aText={VirtualBox is not currently allowed to access USB devices.  You can change this by adding your user to the 'vboxusers' group.  Please see the user manual for a more detailed explanation}, preserve=true 
00:07:40.007427 nspr-2   WARNING [COM]: aRC=NS_ERROR_FAILURE (0x80004005) aIID={93269330-48ca-4096-b4a2-1189df336267} aComponent={Host} aText={VirtualBox is not currently allowed to access USB devices.  You can change this by adding your user to the 'vboxusers' group.  Please see the user manual for a more detailed explanation}, preserve=true 
00:07:43.905538 nspr-4   WARNING [COM]: aRC=NS_ERROR_FAILURE (0x80004005) aIID={93269330-48ca-4096-b4a2-1189df336267} aComponent={Host} aText={VirtualBox is not currently allowed to access USB devices.  You can change this by adding your user to the 'vboxusers' group.  Please see the user manual for a more detailed explanation}, preserve=true 
00:07:43.907065 nspr-4   WARNING [COM]: aRC=NS_ERROR_FAILURE (0x80004005) aIID={93269330-48ca-4096-b4a2-1189df336267} aComponent={Host} aText={VirtualBox is not currently allowed to access USB devices.  You can change this by adding your user to the 'vboxusers' group.  Please see the user manual for a more detailed explanation}, preserve=true 

```

I've made sure that my user name is in the vboxusers group, so I don't know why I'm getting that error message.

I still don't have networking, and shared folders & clipboard, and can't print to a USB printer.

---

