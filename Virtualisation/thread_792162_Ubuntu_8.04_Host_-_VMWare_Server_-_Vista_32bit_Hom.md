---
title: "Ubuntu 8.04 Host - VMWare Server - Vista 32bit HomePremium Guest"
date: 2008-05-12
forum: Virtualisation
---

### Post by Vasto on 2008-05-12
Sorry for the punctuated title, I wanted to get the majority of the information up there though. Anyways...

I'm trying to install Vista 32bit Home Premium in VMware Server (Ubuntu Hardy is the host OS). When I power on the OS, a black screen pops up for about a second, then it powers off and returns to the summary tab. I tried using some guides on google that recommended making an iso instead of using the disk, and either way yielded the same results.

Looking at the log, it looks like it is having some problems because I am trying to use my external (NTFS) drive as the location for the virtual machine.

VMX File
```
#!/usr/bin/vmware
config.version = "8"
virtualHW.version = "4"
numvcpus = "2"
scsi0.present = "TRUE"
scsi0.virtualDev = "lsilogic"
memsize = "1028"
scsi0:0.present = "TRUE"
scsi0:0.fileName = "Windows Vista (experimental)"
scsi0:0.writeThrough = "TRUE"
ide1:0.present = "TRUE"
ide1:0.fileName = "auto detect"
ide1:0.deviceType = "cdrom-raw"
floppy0.startConnected = "FALSE"
floppy0.fileName = "/dev/fd0"
Ethernet0.present = "TRUE"
Ethernet0.connectionType = "nat"
displayName = "Windows Vista (experimental)"
guestOS = "longhorn"
priority.grabbed = "normal"
priority.ungrabbed = "normal"
powerType.powerOff = "hard"
powerType.powerOn = "hard"
powerType.suspend = "hard"
powerType.reset = "hard"

ide0:0.present = "FALSE"
ide0:0.fileName = "/home/michael/Desktop/WindowsVista.iso"
ide0:0.deviceType = "cdrom-image"

scsi0:0.redo = ""
ethernet0.addressType = "generated"
uuid.location = "56 4d 6a 47 46 d9 98 5e-21 e6 d1 b3 c9 1b d4 72"
uuid.bios = "56 4d 6a 47 46 d9 98 5e-21 e6 d1 b3 c9 1b d4 72"
ethernet0.generatedAddress = "00:0c:29:1b:d4:72"
ethernet0.generatedAddressOffset = "0"

ide1:1.present = "TRUE"
ide1:1.fileName = "/home/michael/Desktop/WindowsVista.iso"
ide1:1.deviceType = "cdrom-image"

ide1:0.autodetect = "TRUE"
floppy0.present = "FALSE"
```

LOG
```
May 12 18:25:08: vmx| Log for VMware Server pid=1853 version=1.0.4 build=build-56528 option=Release
May 12 18:25:08: vmx| Command line: "/usr/lib/vmware/bin/vmware-vmx" "-C" "-@" """" "/media/Storage/Windows Vista (experimental)/Windows Vista (experimental).vmx"
May 12 18:25:08: vmx| vmxvmdb: Index name being generated from config file
May 12 18:25:08: vmx| VMXVmdbConnectServerd - Trying to discover serverd
May 12 18:25:08: vmx| MStat: Creating Stat system.cpuusage
May 12 18:25:08: vmx| MStat: Creating Stat system.ram
May 12 18:25:08: vmx| MStat: Creating Stat system.uptime
May 12 18:25:08: vmx| MStat: Creating Stat system.load
May 12 18:25:08: vmx| cpuids[0].id81.ecx = 0x1
May 12 18:25:08: vmx| cpuids[1].id81.ecx = 0x1
May 12 18:25:08: vmx| pcpu #0 CPUID numEntries=10 GenuntelineI
May 12 18:25:08: vmx| pcpu #0 CPUID version=0x6fa id1.edx=0xbfebfbff id1.ecx=0xe3bd id1.ebx=0x20800
May 12 18:25:08: vmx| pcpu #0 CPUID id80.eax=80000008 id81.edx=0x20100800 id81.ecx=0x1
May 12 18:25:08: vmx| pcpu #1 CPUID numEntries=10 GenuntelineI
May 12 18:25:08: vmx| pcpu #1 CPUID version=0x6fa id1.edx=0xbfebfbff id1.ecx=0xe3bd id1.ebx=0x1020800
May 12 18:25:08: vmx| pcpu #1 CPUID id80.eax=80000008 id81.edx=0x20100800 id81.ecx=0x1
May 12 18:25:08: vmx| CPUID id1.edx: 0xbfebfbff id1.ecx: 0xe3bd id81.edx: 0x20100800 id81.ecx: 0x1
May 12 18:25:08: vmx| CPUID id88.ecx: 0 id88.edx: 0
May 12 18:25:08: vmx| Removing stale symlink /var/run/vmware/%2Fmedia%2FStorage%2FWindows%20Vista%20%28experimental%29%2FWindows%20Vista%20%28experimental%29%2Evmx
May 12 18:25:08: vmx| Setup symlink /var/run/vmware/%2Fmedia%2FStorage%2FWindows%20Vista%20%28experimental%29%2FWindows%20Vista%20%28experimental%29%2Evmx -> /var/run/vmware/root/1853
May 12 18:25:08: vmx| ACL_InitCapabilities: here 1 (bug 63252)
May 12 18:25:08: vmx| changing directory to /media/Storage/Windows Vista (experimental)/.
May 12 18:25:08: vmx| Config file: /media/Storage/Windows Vista (experimental)/Windows Vista (experimental).vmx
May 12 18:25:08: vmx| FILEIO: Unknown filesystem 0x65735546 for directory /media/Storage/Windows Vista (experimental). Using non-linking locking.
May 12 18:25:08: vmx| FILEIO: Unknown filesystem 0x65735546 for directory /media/Storage/Windows Vista (experimental). Using non-linking locking.
May 12 18:25:08: vmx| FILEIO: Unknown filesystem 0x65735546 for directory /media/Storage/Windows Vista (experimental). Using non-linking locking.
May 12 18:25:08: vmx| FILEIO: Unknown filesystem 0x65735546 for directory /media/Storage/Windows Vista (experimental). Using non-linking locking.
May 12 18:25:08: vmx| FILEIO: Unknown filesystem 0x65735546 for directory /media/Storage/Windows Vista (experimental). Using non-linking locking.
May 12 18:25:08: vmx| FILEIO: Unknown filesystem 0x65735546 for directory /media/Storage/Windows Vista (experimental). Using non-linking locking.
May 12 18:25:08: vmx| FILEIO: Unknown filesystem 0x65735546 for directory /media/Storage/Windows Vista (experimental). Using non-linking locking.
May 12 18:25:08: vmx| FILEIO: Unknown filesystem 0x65735546 for directory /media/Storage/Windows Vista (experimental). Using non-linking locking.
May 12 18:25:08: vmx| FILEIO: Unknown filesystem 0x65735546 for directory /media/Storage/Windows Vista (experimental). Using non-linking locking.
May 12 18:25:08: vmx| Read from FIFO 32 -- connecting to serverd...
May 12 18:25:08: vmx| VMDB: Connected to serverd
May 12 18:25:08: vmx| CnxAcceptConnection: Could not receive fd on 29: invalid control message
May 12 18:25:08: vmx| Failed to get IPC connection
May 12 18:25:08: vmx| VMXVmdbCbVmVmxExecState: Exec state change requested to state poweredOn without reset
May 12 18:25:08: vmx| PowerOn
May 12 18:25:08: vmx| Host ACPI: can't find SRAT
May 12 18:25:08: vmx| FILEIO: Unknown filesystem 0x65735546 for directory /media/Storage/Windows Vista (experimental). Using non-linking locking.
May 12 18:25:08: vmx| FILEIO: Unknown filesystem 0x65735546 for directory /media/Storage/Windows Vista (experimental). Using non-linking locking.
May 12 18:25:08: vmx| FILEIO: Unknown filesystem 0x65735546 for directory /media/Storage/Windows Vista (experimental). Using non-linking locking.
May 12 18:25:08: vmx| HOSTINFO: Seeing Intel CPU, numCoresPerCPU 1 numThreadsPerCore 1.
May 12 18:25:08: vmx| HOSTINFO: This machine has 2 physical CPUS, 2 total cores, and 2 logical CPUs.
May 12 18:25:08: vmx| FILEIO: Unknown filesystem 0x65735546 for directory /media/Storage/Windows Vista (experimental). Using non-linking locking.
May 12 18:25:08: vmx| FILEIO: Unknown filesystem 0x65735546 for directory /media/Storage/Windows Vista (experimental). Using non-linking locking.
May 12 18:25:08: vmx| FILEIO: Unknown filesystem 0x65735546 for directory /media/Storage/Windows Vista (experimental). Using non-linking locking.
May 12 18:25:08: vmx| FILEIO: Unknown filesystem 0x65735546 for directory /media/Storage/Windows Vista (experimental). Using non-linking locking.
May 12 18:25:08: vmx| FILEIO: Unknown filesystem 0x65735546 for directory /media/Storage/Windows Vista (experimental). Using non-linking locking.
May 12 18:25:08: vmx| FILEIO: Unknown filesystem 0x65735546 for directory /media/Storage/Windows Vista (experimental). Using non-linking locking.
May 12 18:25:08: vmx| HOST sysname Linux, nodename michael-ubuntu, release 2.6.24-16-generic, version #1 SMP Thu Apr 10 12:47:45 UTC 2008, machine x86_64, SMP, hz=250
May 12 18:25:08: vmx| DICT --- USER PREFERENCES
May 12 18:25:08: vmx| DICT --- USER DEFAULTS
May 12 18:25:08: vmx| DICT --- HOST DEFAULTS
May 12 18:25:08: vmx| DICT    vmnet1.hostonlyaddress = 172.16.173.1
May 12 18:25:08: vmx| DICT     serverd.init.fullpath = /usr/lib/vmware/serverd/init.pl
May 12 18:25:08: vmx| DICT         authd.client.port = 902
May 12 18:25:08: vmx| DICT          control.fullpath = /usr/bin/vmware-cmd
May 12 18:25:08: vmx| DICT            authd.fullpath = /usr/sbin/vmware-authd
May 12 18:25:08: vmx| DICT             loop.fullpath = /usr/bin/vmware-loop
May 12 18:25:08: vmx| DICT                    libdir = /usr/lib/vmware
May 12 18:25:08: vmx| DICT           vmware.fullpath = /usr/bin/vmware
May 12 18:25:08: vmx| DICT    vmnet1.hostonlynetmask = 255.255.255.0
May 12 18:25:08: vmx| DICT                     vmdir = /var/lib/vmware/Virtual Machines
May 12 18:25:08: vmx| DICT            dhcpd.fullpath = /usr/bin/vmnet-dhcpd
May 12 18:25:08: vmx| DICT          serverd.fullpath = /usr/sbin/vmware-serverd
May 12 18:25:08: vmx| DICT            datastore.name = local
May 12 18:25:08: vmx| DICT       datastore.localpath = /var/lib/vmware/Virtual Machines/
May 12 18:25:08: vmx| DICT --- SITE DEFAULTS
May 12 18:25:08: vmx| DICT                  tag.help = introduction.htm
May 12 18:25:08: vmx| DICT   tag.configurationEditor = config_editor_newvm.htm
May 12 18:25:08: vmx| DICT             tag.ideConfig = devices_virtualdrive.htm
May 12 18:25:08: vmx| DICT          tag.floppyConfig = devices_floppy.htm
May 12 18:25:08: vmx| DICT           tag.mouseConfig = devices_mouse.htm
May 12 18:25:08: vmx| DICT             tag.netConfig = devices_netadapter.htm
May 12 18:25:08: vmx| DICT        tag.parallelConfig = devices_parallel.htm
May 12 18:25:08: vmx| DICT          tag.serialConfig = devices_serial.htm
May 12 18:25:08: vmx| DICT           tag.soundConfig = devices_sound.htm
May 12 18:25:08: vmx| DICT             tag.memConfig = configvm_memory.htm
May 12 18:25:08: vmx| DICT            tag.miscConfig = configvm.htm
May 12 18:25:08: vmx| DICT             tag.usbConfig = devices_usb.htm
May 12 18:25:08: vmx| DICT         tag.displayConfig = configvm_display-problems.htm
May 12 18:25:08: vmx| DICT                 tag.tools = vmtools.htm
May 12 18:25:08: vmx| DICT --- COMMAND LINE
May 12 18:25:08: vmx| DICT          gui.managementUI = TRUE
May 12 18:25:08: vmx| DICT --- CONFIGURATION
May 12 18:25:08: vmx| DICT            config.version = 8
May 12 18:25:08: vmx| DICT         virtualHW.version = 4
May 12 18:25:08: vmx| DICT                  numvcpus = 2
May 12 18:25:08: vmx| DICT             scsi0.present = TRUE
May 12 18:25:08: vmx| DICT          scsi0.virtualDev = lsilogic
May 12 18:25:08: vmx| DICT                   memsize = 1028
May 12 18:25:08: vmx| DICT           scsi0:0.present = TRUE
May 12 18:25:08: vmx| DICT          scsi0:0.fileName = Windows Vista (experimental)
May 12 18:25:08: vmx| DICT      scsi0:0.writeThrough = TRUE
May 12 18:25:08: vmx| DICT            ide1:0.present = TRUE
May 12 18:25:08: vmx| DICT           ide1:0.fileName = auto detect
May 12 18:25:08: vmx| DICT         ide1:0.deviceType = cdrom-raw
May 12 18:25:08: vmx| DICT    floppy0.startConnected = FALSE
May 12 18:25:08: vmx| DICT          floppy0.fileName = /dev/fd0
May 12 18:25:08: vmx| DICT         Ethernet0.present = TRUE
May 12 18:25:08: vmx| DICT  Ethernet0.connectionType = nat
May 12 18:25:08: vmx| DICT               displayName = Windows Vista (experimental)
May 12 18:25:08: vmx| DICT                   guestOS = longhorn
May 12 18:25:08: vmx| DICT          priority.grabbed = normal
May 12 18:25:08: vmx| DICT        priority.ungrabbed = normal
May 12 18:25:08: vmx| DICT        powerType.powerOff = hard
May 12 18:25:08: vmx| DICT         powerType.powerOn = hard
May 12 18:25:08: vmx| DICT         powerType.suspend = hard
May 12 18:25:08: vmx| DICT           powerType.reset = hard
May 12 18:25:08: vmx| DICT            ide0:0.present = FALSE
May 12 18:25:08: vmx| DICT           ide0:0.fileName = /home/michael/Desktop/WindowsVista.iso
May 12 18:25:08: vmx| DICT         ide0:0.deviceType = cdrom-image
May 12 18:25:08: vmx| DICT              scsi0:0.redo = 
May 12 18:25:08: vmx| DICT     ethernet0.addressType = generated
May 12 18:25:08: vmx| DICT             uuid.location = 56 4d 6a 47 46 d9 98 5e-21 e6 d1 b3 c9 1b d4 72
May 12 18:25:08: vmx| DICT                 uuid.bios = 56 4d 6a 47 46 d9 98 5e-21 e6 d1 b3 c9 1b d4 72
May 12 18:25:08: vmx| DICT ethernet0.generatedAddress = 00:0c:29:1b:d4:72
May 12 18:25:08: vmx| DICT ethernet0.generatedAddressOffset = 0
May 12 18:25:08: vmx| DICT            ide1:1.present = TRUE
May 12 18:25:08: vmx| DICT           ide1:1.fileName = /home/michael/Desktop/WindowsVista.iso
May 12 18:25:08: vmx| DICT         ide1:1.deviceType = cdrom-image
May 12 18:25:08: vmx| DICT         ide1:0.autodetect = TRUE
May 12 18:25:08: vmx| DICT           floppy0.present = FALSE
May 12 18:25:08: vmx| DICT --- USER DEFAULTS
May 12 18:25:08: vmx| DICT --- HOST DEFAULTS
May 12 18:25:08: vmx| DICT    vmnet1.hostonlyaddress = 172.16.173.1
May 12 18:25:08: vmx| DICT     serverd.init.fullpath = /usr/lib/vmware/serverd/init.pl
May 12 18:25:08: vmx| DICT         authd.client.port = 902
May 12 18:25:08: vmx| DICT          control.fullpath = /usr/bin/vmware-cmd
May 12 18:25:08: vmx| DICT            authd.fullpath = /usr/sbin/vmware-authd
May 12 18:25:08: vmx| DICT             loop.fullpath = /usr/bin/vmware-loop
May 12 18:25:08: vmx| DICT                    libdir = /usr/lib/vmware
May 12 18:25:08: vmx| DICT           vmware.fullpath = /usr/bin/vmware
May 12 18:25:08: vmx| DICT    vmnet1.hostonlynetmask = 255.255.255.0
May 12 18:25:08: vmx| DICT                     vmdir = /var/lib/vmware/Virtual Machines
May 12 18:25:08: vmx| DICT            dhcpd.fullpath = /usr/bin/vmnet-dhcpd
May 12 18:25:08: vmx| DICT          serverd.fullpath = /usr/sbin/vmware-serverd
May 12 18:25:08: vmx| DICT            datastore.name = local
May 12 18:25:08: vmx| DICT       datastore.localpath = /var/lib/vmware/Virtual Machines/
May 12 18:25:08: vmx| DICT --- SITE DEFAULTS
May 12 18:25:08: vmx| DICT                  tag.help = introduction.htm
May 12 18:25:08: vmx| DICT   tag.configurationEditor = config_editor_newvm.htm
May 12 18:25:08: vmx| DICT             tag.ideConfig = devices_virtualdrive.htm
May 12 18:25:08: vmx| DICT          tag.floppyConfig = devices_floppy.htm
May 12 18:25:08: vmx| DICT           tag.mouseConfig = devices_mouse.htm
May 12 18:25:08: vmx| DICT             tag.netConfig = devices_netadapter.htm
May 12 18:25:08: vmx| DICT        tag.parallelConfig = devices_parallel.htm
May 12 18:25:08: vmx| DICT          tag.serialConfig = devices_serial.htm
May 12 18:25:08: vmx| DICT           tag.soundConfig = devices_sound.htm
May 12 18:25:08: vmx| DICT             tag.memConfig = configvm_memory.htm
May 12 18:25:08: vmx| DICT            tag.miscConfig = configvm.htm
May 12 18:25:08: vmx| DICT             tag.usbConfig = devices_usb.htm
May 12 18:25:08: vmx| DICT         tag.displayConfig = configvm_display-problems.htm
May 12 18:25:08: vmx| DICT                 tag.tools = vmtools.htm
May 12 18:25:08: vmx| DICT --- GLOBAL SETTINGS
May 12 18:25:08: vmx| WSSCAN: reserved mem (in MB) min=32 max=1920 recommended=1920
May 12 18:25:08: vmx|         hostMem=2016 maxAllowedAll=-1 maxAllowedVM=3600
May 12 18:25:08: vmx|         totOverhead=16
May 12 18:25:08: vmx| WSSCAN: used rec mem (in MB) 1920
May 12 18:25:08: vmx| WSSCAN: Overhead 269555 paged 13621 nonpaged 4096 maxFBSize
May 12 18:25:08: vmx| WSSCAN 1 1 458486 458486 491520 -1 50 0
May 12 18:25:08: vmx| LICENSE using: '/etc/vmware/license.vs.1.0-00' 
May 12 18:25:08: vmx| STATDECLGROUP stats Root "" null
May 12 18:25:08: vmx| Host CPUID features: version 0x6f8 id1.edx 0xbfebfbff id1.ecx 0xe3bd id81.edx 0x20100800 id81.ecx 0x1
May 12 18:25:08: vmx| CPU.cpuFeatures = 0xb971ff37
May 12 18:25:08: vmx| CPUID after masking: version 0x6f8 id1.edx 0xfebfbff id1.ecx 0x8215 id81.edx 0x100800 id81.ecx 0x0 id88.ecx 0x0
May 12 18:25:08: vmx| CPU.cpuFeatures = 0x9871fe03
May 12 18:25:08: vmx| APIC: Local APIC at 0xfee00000
May 12 18:25:08: vmx| KHZEstimate 2001000
May 12 18:25:08: vmx| MHZEstimate 2001
May 12 18:25:08: vmx| NumVCPUs 2
May 12 18:25:08: vmx| UUID: location-UUID is 56 4d 6a 47 46 d9 98 5e-21 e6 d1 b3 c9 1b d4 72
May 12 18:25:08: vmx| MM: Using partialmap, 263168 pages AC 0 CE 1 TM 0 DOHU 0
May 12 18:25:08: vmx| UUID: canonical path is /media/Storage/Windows Vista (experimental)/Windows Vista (experimental).vmx
May 12 18:25:08: vmx| UUID: location-UUID is 56 4d 6a 47 46 d9 98 5e-21 e6 d1 b3 c9 1b d4 72
May 12 18:25:08: vmx| FILEIO: Unknown filesystem 0x65735546 for directory /media/Storage/Windows Vista (experimental). Using non-linking locking.
May 12 18:25:08: vmx| FILEIO: Unknown filesystem 0x65735546 for directory /media/Storage/Windows Vista (experimental). Using non-linking locking.
May 12 18:25:08: vmx| FILEIO: Failed to create new lock file /media/Storage/Windows Vista (experimental)/564d6a47-46d9-985e-21e6-d1b3c91bd472.vmem.WRITELOCK (File exists).
May 12 18:25:08: vmx| FILEIO: Found a previous instance of lock file '/media/Storage/Windows Vista (experimental)/564d6a47-46d9-985e-21e6-d1b3c91bd472.vmem.WRITELOCK'. It will be removed automatically.
May 12 18:25:08: vmx| FILEIO: Unknown filesystem 0x65735546 for directory /media/Storage/Windows Vista (experimental). Using non-linking locking.
May 12 18:25:08: vmx| MM: using fileName /media/Storage/Windows Vista (experimental)/564d6a47-46d9-985e-21e6-d1b3c91bd472.vmem for paging
May 12 18:25:08: vmx| Msg_Reset:
May 12 18:25:08: vmx| [msg.monitorInit.vmm64.initHost.VTDisabled] This CPU is VT-capable, but VT is not enabled (check your BIOS settings).
May 12 18:25:08: vmx| [msg.monitorInit.vmm64.initHost.VTDisabled] This CPU is VT-capable, but VT is not enabled (check your BIOS settings).
May 12 18:25:08: vmx| ----------------------------------------
May 12 18:25:08: vmx| Opened paging file /media/Storage/Windows Vista (experimental)/564d6a47-46d9-985e-21e6-d1b3c91bd472.vmem
May 12 18:25:08: vmx| Mapped mainmem as pageable
May 12 18:25:08: vmx| MStat: Creating Stat vm.cpuusage
May 12 18:25:08: vmx| MStat: Creating Stat vm.ram
May 12 18:25:08: vmx| MStat: Creating Stat vm.uptime
May 12 18:25:08: vmx| FILEIO: Unknown filesystem 0x65735546 for directory /media/Storage/Windows Vista (experimental). Using non-linking locking.
May 12 18:25:08: vmx| FILEIO: Unknown filesystem 0x65735546 for directory /media/Storage/Windows Vista (experimental). Using non-linking locking.
May 12 18:25:08: vmx| FILEIO: Unknown filesystem 0x65735546 for directory /media/Storage/Windows Vista (experimental). Using non-linking locking.
May 12 18:25:08: vmx| DISK: OPEN scsi0:0 '/media/Storage/Windows Vista (experimental)/Windows Vista (experimental)' persistent R[(null)]
May 12 18:25:08: vmx| FILEIO: Unknown filesystem 0x65735546 for directory /media/Storage/Windows Vista (experimental). Using non-linking locking.
May 12 18:25:08: vmx| FILEIO: Unknown filesystem 0x65735546 for directory /media/Storage/Windows Vista (experimental). Using non-linking locking.
May 12 18:25:08: vmx| FILEIO: Failed to create new lock file /media/Storage/Windows Vista (experimental)/Windows Vista (experimental).WRITELOCK (File exists).
May 12 18:25:08: vmx| FILEIO: Found a previous instance of lock file '/media/Storage/Windows Vista (experimental)/Windows Vista (experimental).WRITELOCK'. It will be removed automatically.
May 12 18:25:08: vmx| FILEIO: Unknown filesystem 0x65735546 for directory /media/Storage/Windows Vista (experimental). Using non-linking locking.
May 12 18:25:08: vmx| FILEIO: Unknown filesystem 0x65735546 for directory /media/Storage/Windows Vista (experimental). Using non-linking locking.
May 12 18:25:08: vmx| FILEIO: Unknown filesystem 0x65735546 for directory /media/Storage/Windows Vista (experimental). Using non-linking locking.
May 12 18:25:08: vmx| AIOGNRC: Starting 7 I/O threads.
May 12 18:25:08: vmx| DISKLIB-DSCPTR: Opened [0]: "Windows Vista (experimental)-s001" (0x2a)
May 12 18:25:08: vmx| DISKLIB-DSCPTR: Opened [1]: "Windows Vista (experimental)-s002" (0x2a)
May 12 18:25:08: vmx| DISKLIB-DSCPTR: Opened [2]: "Windows Vista (experimental)-s003" (0x2a)
May 12 18:25:08: vmx| DISKLIB-DSCPTR: Opened [3]: "Windows Vista (experimental)-s004" (0x2a)
May 12 18:25:08: vmx| DISKLIB-DSCPTR: Opened [4]: "Windows Vista (experimental)-s005" (0x2a)
May 12 18:25:08: vmx| DISKLIB-DSCPTR: Opened [5]: "Windows Vista (experimental)-s006" (0x2a)
May 12 18:25:08: vmx| DISKLIB-DSCPTR: Opened [6]: "Windows Vista (experimental)-s007" (0x2a)
May 12 18:25:08: vmx| DISKLIB-DSCPTR: Opened [7]: "Windows Vista (experimental)-s008" (0x2a)
May 12 18:25:08: vmx| DISKLIB-DSCPTR: Opened [8]: "Windows Vista (experimental)-s009" (0x2a)
May 12 18:25:08: vmx| DISKLIB-DSCPTR: Opened [9]: "Windows Vista (experimental)-s010" (0x2a)
May 12 18:25:08: vmx| DISKLIB-DSCPTR: Opened [10]: "Windows Vista (experimental)-s011" (0x2a)
May 12 18:25:08: vmx| DISKLIB-DSCPTR: Opened [11]: "Windows Vista (experimental)-s012" (0x2a)
May 12 18:25:08: vmx| DISKLIB-DSCPTR: Opened [12]: "Windows Vista (experimental)-s013" (0x2a)
May 12 18:25:08: vmx| DISKLIB-DSCPTR: Opened [13]: "Windows Vista (experimental)-s014" (0x2a)
May 12 18:25:08: vmx| DISKLIB-DSCPTR: Opened [14]: "Windows Vista (experimental)-s015" (0x2a)
May 12 18:25:08: vmx| DISKLIB-DSCPTR: Opened [15]: "Windows Vista (experimental)-s016" (0x2a)
May 12 18:25:08: vmx| DISKLIB-DSCPTR: Opened [16]: "Windows Vista (experimental)-s017" (0x2a)
May 12 18:25:08: vmx| DISKLIB-DSCPTR: Opened [17]: "Windows Vista (experimental)-s018" (0x2a)
May 12 18:25:08: vmx| DISKLIB-DSCPTR: Opened [18]: "Windows Vista (experimental)-s019" (0x2a)
May 12 18:25:08: vmx| DISKLIB-DSCPTR: Opened [19]: "Windows Vista (experimental)-s020" (0x2a)
May 12 18:25:08: vmx| DISKLIB-DSCPTR: Opened [20]: "Windows Vista (experimental)-s021" (0x2a)
May 12 18:25:08: vmx| DISKLIB-DSCPTR: Opened [21]: "Windows Vista (experimental)-s022" (0x2a)
May 12 18:25:08: vmx| DISKLIB-DSCPTR: Opened [22]: "Windows Vista (experimental)-s023" (0x2a)
May 12 18:25:08: vmx| DISKLIB-DSCPTR: Opened [23]: "Windows Vista (experimental)-s024" (0x2a)
May 12 18:25:08: vmx| DISKLIB-DSCPTR: Opened [24]: "Windows Vista (experimental)-s025" (0x2a)
May 12 18:25:08: vmx| DISKLIB-DSCPTR: Opened [25]: "Windows Vista (experimental)-s026" (0x2a)
May 12 18:25:08: vmx| DISKLIB-DSCPTR: Opened [26]: "Windows Vista (experimental)-s027" (0x2a)
May 12 18:25:08: vmx| DISKLIB-DSCPTR: Opened [27]: "Windows Vista (experimental)-s028" (0x2a)
May 12 18:25:08: vmx| DISKLIB-DSCPTR: Opened [28]: "Windows Vista (experimental)-s029" (0x2a)
May 12 18:25:08: vmx| DISKLIB-DSCPTR: Opened [29]: "Windows Vista (experimental)-s030" (0x2a)
May 12 18:25:08: vmx| DISKLIB-DSCPTR: Opened [30]: "Windows Vista (experimental)-s031" (0x2a)
May 12 18:25:08: vmx| DISKLIB-DSCPTR: Opened [31]: "Windows Vista (experimental)-s032" (0x2a)
May 12 18:25:08: vmx| DISKLIB-DSCPTR: Opened [32]: "Windows Vista (experimental)-s033" (0x2a)
May 12 18:25:08: vmx| DISKLIB-DSCPTR: Opened [33]: "Windows Vista (experimental)-s034" (0x2a)
May 12 18:25:08: vmx| DISKLIB-DSCPTR: Opened [34]: "Windows Vista (experimental)-s035" (0x2a)
May 12 18:25:08: vmx| DISKLIB-DSCPTR: Opened [35]: "Windows Vista (experimental)-s036" (0x2a)
May 12 18:25:08: vmx| DISKLIB-DSCPTR: Opened [36]: "Windows Vista (experimental)-s037" (0x2a)
May 12 18:25:08: vmx| DISKLIB-DSCPTR: Opened [37]: "Windows Vista (experimental)-s038" (0x2a)
May 12 18:25:08: vmx| DISKLIB-DSCPTR: Opened [38]: "Windows Vista (experimental)-s039" (0x2a)
May 12 18:25:08: vmx| DISKLIB-DSCPTR: Opened [39]: "Windows Vista (experimental)-s040" (0x2a)
May 12 18:25:08: vmx| DISKLIB-DSCPTR: Opened [40]: "Windows Vista (experimental)-s041" (0x2a)
May 12 18:25:08: vmx| DISKLIB-DSCPTR: Opened [41]: "Windows Vista (experimental)-s042" (0x2a)
May 12 18:25:08: vmx| DISKLIB-DSCPTR: Opened [42]: "Windows Vista (experimental)-s043" (0x2a)
May 12 18:25:08: vmx| DISKLIB-DSCPTR: Opened [43]: "Windows Vista (experimental)-s044" (0x2a)
May 12 18:25:08: vmx| DISKLIB-DSCPTR: Opened [44]: "Windows Vista (experimental)-s045" (0x2a)
May 12 18:25:08: vmx| DISKLIB-DSCPTR: Opened [45]: "Windows Vista (experimental)-s046" (0x2a)
May 12 18:25:08: vmx| DISKLIB-DSCPTR: Opened [46]: "Windows Vista (experimental)-s047" (0x2a)
May 12 18:25:08: vmx| DISKLIB-DSCPTR: Opened [47]: "Windows Vista (experimental)-s048" (0x2a)
May 12 18:25:08: vmx| DISKLIB-DSCPTR: Opened [48]: "Windows Vista (experimental)-s049" (0x2a)
May 12 18:25:08: vmx| DISKLIB-DSCPTR: Opened [49]: "Windows Vista (experimental)-s050" (0x2a)
May 12 18:25:08: vmx| DISKLIB-DSCPTR: Opened [50]: "Windows Vista (experimental)-s051" (0x2a)
May 12 18:25:08: vmx| DISKLIB-LINK  : Opened '/media/Storage/Windows Vista (experimental)/Windows Vista (experimental)' (0x2a): twoGbMaxExtentSparse, 209715200 sectors / 102400 Mb.
May 12 18:25:08: vmx| DISKLIB-LIB   : Opened "/media/Storage/Windows Vista (experimental)/Windows Vista (experimental)" (flags 0x2a).
May 12 18:25:08: vmx| DISK: OPEN '/media/Storage/Windows Vista (experimental)/Windows Vista (experimental)' Geo (13054/255/63) BIOS Geo (0/0/0) freeSpace=99332Mb
May 12 18:25:08: vmx| TimeTracker host to guest rate conversion 175348772021780 @ 2001000000Hz -> 175348772021780 @ 2001000000Hz
May 12 18:25:08: vmx| TimeTracker host to guest rate conversion ((x * 2147483648) >> 31) + 0
May 12 18:25:08: vmx| MStat: Creating Stat ide1:0.bytesread
May 12 18:25:08: vmx| MStat: Creating Stat ide1:0.byteswritten
May 12 18:25:08: vmx| MStat: Creating Stat ide1:1.bytesread
May 12 18:25:08: vmx| MStat: Creating Stat ide1:1.byteswritten
May 12 18:25:08: vmx| MStat: Creating Stat scsi0:0.bytesread
May 12 18:25:08: vmx| MStat: Creating Stat scsi0:0.byteswritten
May 12 18:25:08: vmx| DISKUTIL: scsi0:0 : capacity=209715200
May 12 18:25:08: vmx| DISKUTIL: scsi0:0 : geometry=13054/255/63
May 12 18:25:08: vmx| SCSI0: UNTAGGED commands will be converted to ORDER tags.
May 12 18:25:08: vmx| MStat: Creating Stat vm.heartbeat
May 12 18:25:08: vmx| DISKUTIL: scsi0:0 : toolsVersion = 0
May 12 18:25:08: vmx| DISKUTIL: Offline toolsVersion = 0
May 12 18:25:08: vmx| TOOLS INSTALL initializing state to IDLE on power on.
May 12 18:25:08: vmx| VMMon_GetkHzEstimate: Calculated 1995271 kHz
May 12 18:25:08: vmx| VLANCE: send cluster threshold is 80, size = 2 recalcInterval is 2 ticks
May 12 18:25:08: vmx| MStat: Creating Stat ethernet0.bytesread
May 12 18:25:08: vmx| MStat: Creating Stat ethernet0.byteswritten
May 12 18:25:08: vmx| Ethernet0 MAC Address: 00:0c:29:1b:d4:72
May 12 18:25:08: vmx| VMXNET: send cluster threshold is 80, size = 2 recalcInterval is 2 ticks, dontClusterSize is 128
May 12 18:25:08: vmx| E1000: checksum cycles/kB: C=672 asm=611
May 12 18:25:08: vmx| VMX_PowerOn: ModuleTable_PowerOn = 1
May 12 18:25:08: vmx| VMX setting maximum IPC write buffers to 0 packets, 0 bytes
May 12 18:25:08: mks| Async MKS thread is alive
May 12 18:25:08: vcpu-0| APIC: version = 0x14, max LVT = 5
May 12 18:25:08: vcpu-0| APIC: LDR = 0x2000000, DFR = 0xffffffff
May 12 18:25:08: vmx| Accepted new connection at 226 for thread servercontrol (0x84da360)
May 12 18:25:08: vmx| VUINewControlConnection: before slow ACL gunk (bug 63252).
May 12 18:25:08: vmx| ACL_InitCapabilities: here 2 (bug 63252)
May 12 18:25:08: vmx| VUINewControlConnection: after slow ACL gunk (bug 63252).
May 12 18:25:08: vmx| VUI: A new VMControl client connected.
May 12 18:25:08: vmx| IPC version negotiation version: VMX returning 2.1 to servercontrol
May 12 18:25:08: vmx| IPC vmcontrol-temp version: VMX returning 11.4 to servercontrol that tried 11.4
May 12 18:25:08: vcpu-0| PShare: enabled 1, scanRate 32, checkRate 16
May 12 18:25:08: vcpu-0| guestCpuFeatures = 0x9871fe03
May 12 18:25:08: vcpu-0| Init modules.
May 12 18:25:08: vcpu-0| CPU reset: hard
May 12 18:25:08: vcpu-0| Could not mmap paging file : No such device
May 12 18:25:08: vcpu-0| Could not mmap paging file : No such device
May 12 18:25:08: vcpu-0| Failed to allocate page for guest RAM!
May 12 18:25:08: vcpu-0| Backtrace:
May 12 18:25:08: vcpu-0| Backtrace[0] 0xf1611e08 eip 0x805af90 
May 12 18:25:08: vcpu-0| Backtrace[1] 0xf1612228 eip 0x80c02fb 
May 12 18:25:08: vcpu-0| Backtrace[2] 0xf16122d8 eip 0x825add1 
May 12 18:25:08: vcpu-0| Backtrace[3] 0xf1612308 eip 0x82b7aac 
May 12 18:25:08: vcpu-0| Backtrace[4] 0xf1612328 eip 0x82bc219 
May 12 18:25:08: vcpu-0| Backtrace[5] 0xf1612358 eip 0x82c4beb 
May 12 18:25:08: vcpu-0| Backtrace[6] 0xf1612368 eip 0x82bc301 
May 12 18:25:08: vcpu-0| Backtrace[7] 0xf16123d8 eip 0x8068449 
May 12 18:25:08: vcpu-0| Backtrace[8] 0xf16124c8 eip 0xf7f5e4fb 
May 12 18:25:08: vcpu-0| Backtrace[9] 00000000 eip 0xf7d5a08e 
May 12 18:25:08: vcpu-0| Core dump limit is 51200 kb.
May 12 18:25:08: vcpu-0| Attempting to dump core...
May 12 18:25:09: vcpu-0| Msg_Post: Error
May 12 18:25:09: vcpu-0| [msg.log.error.unrecoverable] VMware Server unrecoverable error: (vcpu-0)
May 12 18:25:09: vcpu-0| Failed to allocate page for guest RAM!
May 12 18:25:09: vcpu-0| [msg.panic.haveLog] A log file is available in "/media/Storage/Windows Vista (experimental)/vmware.log".  [msg.panic.haveCore] A core file is available in "/media/Storage/Windows Vista (experimental)/core".  [msg.panic.requestSupport.withLogAndCore] Please request support and include the contents of the log file and core file.  [msg.panic.requestSupport.linux] 
May 12 18:25:09: vcpu-0| To collect files to submit to VMware support, run vm-support.
May 12 18:25:09: vcpu-0| [msg.panic.response] We will respond on the basis of your support entitlement.
May 12 18:25:09: vcpu-0| ----------------------------------------
May 12 18:25:09: vcpu-0| POST(no connection): VMware Server unrecoverable error: (vcpu-0)
May 12 18:25:09: vcpu-0| Failed to allocate page for guest RAM!
May 12 18:25:09: vcpu-0| A log file is available in "/media/Storage/Windows Vista (experimental)/vmware.log".  A core file is available in "/media/Storage/Windows Vista (experimental)/core".  Please request support and include the contents of the log file and core file.  
May 12 18:25:09: vcpu-0| To collect files to submit to VMware support, run vm-support.
May 12 18:25:09: vcpu-0| We will respond on the basis of your support entitlement.
May 12 18:25:09: vcpu-0| 
May 12 18:25:09: vmx| VTHREAD watched thread 4 "vcpu-0" died
May 12 18:25:09: IO#0| VTHREAD watched thread 0 "vmx" died
May 12 18:25:09: mks| VTHREAD watched thread 0 "vmx" died
May 12 18:25:09: IO#1| VTHREAD watched thread 0 "vmx" died
May 12 18:25:09: IO#3| VTHREAD watched thread 0 "vmx" died
May 12 18:25:09: IO#4| VTHREAD watched thread 0 "vmx" died
May 12 18:25:09: IO#5| VTHREAD watched thread 0 "vmx" died
May 12 18:25:09: IO#6| VTHREAD watched thread 0 "vmx" died
May 12 18:25:09: IO#2| VTHREAD watched thread 0 "vmx" died
```

---

### Post by Vasto on 2008-05-12
SOLVED:

[quote=http://www.ntfs-3g.org/support.html#vmware]VMware tries to use shared writable mmap for paging files but it can't detect that it's not yet supported.

Workaround: Set "mainMem.useNamedFile=FALSE" in the .vmx file. It will disable paging files and VMware will work fine, often with much better performance.

Status: The VMware bug has been fixed in all hosted products (Workstation, Fusion, Player, ...) released after Jan 30th 2008.[/quote]

The bug must not have been fixed in VMware Server

---

