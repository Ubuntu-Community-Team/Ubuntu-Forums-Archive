---
title: "Problems trying to create or run a Virtual Machine in VMware Workstation"
date: 2007-08-18
forum: Virtualisation
---

### Post by blop on 2007-08-18
Hi all,

Sadly my conversation to Ubuntu has been undermined by my need now to run CS3 not just PS but the whole suite.

I have VMworkstation so i thought i could run it within a Virtual XP Machine on my Ubuntu box. Not ideal but i dont want to dual boot because if i start using windows then i lll start being lazy and using it for other stuff.

Now my virtual machines are on a seperate NTFS partition from my Vista install, VMlinux wont boot any of virtual machines it recognisesthem but it has an error message when trying to boot them...

The same error message when i try to create a new VM image in VMlinux on the NTFS partition....

Error:

VMware Workstation unrecoverable error: (vcpu-0)
Failed to allocate page for guest RAM!
A log file is available in "/media/sda3/Virtual Machines/xp/xp/vmware.log".  A core file is available in "/media/sda3/Virtual Machines/xp/xp/core".  Please request support and include the contents of the log file and core file.  


Log:
Aug 18 10:01:57.376: vmx| Log for VMware Workstation pid=7855 version=6.0.0 build=build-45731 option=Release
Aug 18 10:01:57.376: vmx| Hostname=matt-laptop
Aug 18 10:01:57.376: vmx| Command line: "/usr/lib/vmware/bin/vmware-vmx" "-#" "product=1;name=VMware Workstation;version=6.0.0;licensename=VMware Workstation for Linux;licenseversion=6.0 build-45731;" "-@" "pipe=/tmp/vmware-matt/vmxe42739a2e2768f74;readyEvent=58" "/media/sda3/Virtual Machines/xp/xp/Windows XP Professional.vmx"
Aug 18 10:01:57.377: vmx| Ready event: 58
Aug 18 10:01:57.501: vmx| UI Connecting to pipe '/tmp/vmware-matt/vmxe42739a2e2768f74' with user '(null)'
Aug 18 10:01:57.522: vmx| Sig_Init already initialized 
Aug 18 10:01:57.544: vmx| VMMon_GetkHzEstimate: Calculated 1729000 kHz
Aug 18 10:01:57.546: vmx| CPUID[0] vendor: GenuntelineI
Aug 18 10:01:57.546: vmx| CPUID[0] level 00000000, 0: 0x0000000a 0x756e6547 0x6c65746e 0x49656e69
Aug 18 10:01:57.546: vmx| CPUID[0] level 00000001, 0: 0x000006f2 0x00020800 0x0000e39d 0xbfebfbff
Aug 18 10:01:57.546: vmx| CPUID[0] level 00000002, 0: 0x05b0b101 0x005657f0 0x00000000 0x2cb4307d
Aug 18 10:01:57.546: vmx| CPUID[0] level 00000003, 0: 0x00000000 0x00000000 0x00000000 0x00000000
Aug 18 10:01:57.546: vmx| CPUID[0] level 00000004, 0: 0x04000121 0x01c0003f 0x0000003f 0x00000001
Aug 18 10:01:57.546: vmx| CPUID[0] level 00000005, 0: 0x00000040 0x00000040 0x00000003 0x00022220
Aug 18 10:01:57.546: vmx| CPUID[0] level 00000006, 0: 0x00000001 0x00000002 0x00000001 0x00000000
Aug 18 10:01:57.546: vmx| CPUID[0] level 00000007, 0: 0x00000000 0x00000000 0x00000000 0x00000000
Aug 18 10:01:57.546: vmx| CPUID[0] level 00000008, 0: 0x00000400 0x00000000 0x00000000 0x00000000
Aug 18 10:01:57.546: vmx| CPUID[0] level 00000009, 0: 0x00000000 0x00000000 0x00000000 0x00000000
Aug 18 10:01:57.546: vmx| CPUID[0] level 0000000a, 0: 0x07280202 0x00000000 0x00000000 0x00000000
Aug 18 10:01:57.546: vmx| CPUID[0] level 80000000, 0: 0x80000008 0x00000000 0x00000000 0x00000000
Aug 18 10:01:57.546: vmx| CPUID[0] level 80000001, 0: 0x00000000 0x00000000 0x00000001 0x20000000
Aug 18 10:01:57.546: vmx| CPUID[0] level 80000002, 0: 0x65746e49 0x2952286c 0x726f4320 0x4d542865
Aug 18 10:01:57.546: vmx| CPUID[0] level 80000003, 0: 0x43203229 0x20205550 0x20202020 0x54202020
Aug 18 10:01:57.546: vmx| CPUID[0] level 80000004, 0: 0x30303335 0x20402020 0x33372e31 0x007a4847
Aug 18 10:01:57.546: vmx| CPUID[0] level 80000005, 0: 0x00000000 0x00000000 0x00000000 0x00000000
Aug 18 10:01:57.546: vmx| CPUID[0] level 80000006, 0: 0x00000000 0x00000000 0x08006040 0x00000000
Aug 18 10:01:57.546: vmx| CPUID[0] level 80000007, 0: 0x00000000 0x00000000 0x00000000 0x00000000
Aug 18 10:01:57.546: vmx| CPUID[0] level 80000008, 0: 0x00003024 0x00000000 0x00000000 0x00000000
Aug 18 10:01:57.546: vmx| CPUID[1] vendor: GenuntelineI
Aug 18 10:01:57.546: vmx| CPUID[1] level 00000000, 0: 0x0000000a 0x756e6547 0x6c65746e 0x49656e69
Aug 18 10:01:57.546: vmx| CPUID[1] level 00000001, 0: 0x000006f2 0x01020800 0x0000e39d 0xbfebfbff
Aug 18 10:01:57.546: vmx| CPUID[1] level 00000002, 0: 0x05b0b101 0x005657f0 0x00000000 0x2cb4307d
Aug 18 10:01:57.546: vmx| CPUID[1] level 00000003, 0: 0x00000000 0x00000000 0x00000000 0x00000000
Aug 18 10:01:57.546: vmx| CPUID[1] level 00000004, 0: 0x04000121 0x01c0003f 0x0000003f 0x00000001
Aug 18 10:01:57.546: vmx| CPUID[1] level 00000005, 0: 0x00000040 0x00000040 0x00000003 0x00022220
Aug 18 10:01:57.546: vmx| CPUID[1] level 00000006, 0: 0x00000001 0x00000002 0x00000001 0x00000000
Aug 18 10:01:57.546: vmx| CPUID[1] level 00000007, 0: 0x00000000 0x00000000 0x00000000 0x00000000
Aug 18 10:01:57.546: vmx| CPUID[1] level 00000008, 0: 0x00000400 0x00000000 0x00000000 0x00000000
Aug 18 10:01:57.546: vmx| CPUID[1] level 00000009, 0: 0x00000000 0x00000000 0x00000000 0x00000000
Aug 18 10:01:57.546: vmx| CPUID[1] level 0000000a, 0: 0x07280202 0x00000000 0x00000000 0x00000000
Aug 18 10:01:57.546: vmx| CPUID[1] level 80000000, 0: 0x80000008 0x00000000 0x00000000 0x00000000
Aug 18 10:01:57.546: vmx| CPUID[1] level 80000001, 0: 0x00000000 0x00000000 0x00000001 0x20000000
Aug 18 10:01:57.546: vmx| CPUID[1] level 80000002, 0: 0x65746e49 0x2952286c 0x726f4320 0x4d542865
Aug 18 10:01:57.546: vmx| CPUID[1] level 80000003, 0: 0x43203229 0x20205550 0x20202020 0x54202020
Aug 18 10:01:57.546: vmx| CPUID[1] level 80000004, 0: 0x30303335 0x20402020 0x33372e31 0x007a4847
Aug 18 10:01:57.546: vmx| CPUID[1] level 80000005, 0: 0x00000000 0x00000000 0x00000000 0x00000000
Aug 18 10:01:57.546: vmx| CPUID[1] level 80000006, 0: 0x00000000 0x00000000 0x08006040 0x00000000
Aug 18 10:01:57.546: vmx| CPUID[1] level 80000007, 0: 0x00000000 0x00000000 0x00000000 0x00000000
Aug 18 10:01:57.546: vmx| CPUID[1] level 80000008, 0: 0x00003024 0x00000000 0x00000000 0x00000000
Aug 18 10:01:57.546: vmx| hostCPUID vendor: GenuntelineI
Aug 18 10:01:57.546: vmx| hostCPUID level 00000000, 0: 0x0000000a 0x756e6547 0x6c65746e 0x49656e69
Aug 18 10:01:57.546: vmx| hostCPUID level 00000001, 0: 0x000006f2 0x00020800 0x0000e39d 0xbfebfbff
Aug 18 10:01:57.546: vmx| hostCPUID level 00000002, 0: 0x05b0b101 0x005657f0 0x00000000 0x2cb4307d
Aug 18 10:01:57.547: vmx| hostCPUID level 00000003, 0: 0x00000000 0x00000000 0x00000000 0x00000000
Aug 18 10:01:57.547: vmx| hostCPUID level 00000004, 0: 0x04000121 0x01c0003f 0x0000003f 0x00000001
Aug 18 10:01:57.547: vmx| hostCPUID level 00000005, 0: 0x00000040 0x00000040 0x00000003 0x00022220
Aug 18 10:01:57.547: vmx| hostCPUID level 00000006, 0: 0x00000001 0x00000002 0x00000001 0x00000000
Aug 18 10:01:57.547: vmx| hostCPUID level 00000007, 0: 0x00000000 0x00000000 0x00000000 0x00000000
Aug 18 10:01:57.547: vmx| hostCPUID level 00000008, 0: 0x00000400 0x00000000 0x00000000 0x00000000
Aug 18 10:01:57.547: vmx| hostCPUID level 00000009, 0: 0x00000000 0x00000000 0x00000000 0x00000000
Aug 18 10:01:57.547: vmx| hostCPUID level 0000000a, 0: 0x07280202 0x00000000 0x00000000 0x00000000
Aug 18 10:01:57.547: vmx| hostCPUID level 80000000, 0: 0x80000008 0x00000000 0x00000000 0x00000000
Aug 18 10:01:57.547: vmx| hostCPUID level 80000001, 0: 0x00000000 0x00000000 0x00000001 0x20000000
Aug 18 10:01:57.547: vmx| hostCPUID level 80000002, 0: 0x65746e49 0x2952286c 0x726f4320 0x4d542865
Aug 18 10:01:57.547: vmx| hostCPUID level 80000003, 0: 0x43203229 0x20205550 0x20202020 0x54202020
Aug 18 10:01:57.547: vmx| hostCPUID level 80000004, 0: 0x30303335 0x20402020 0x33372e31 0x007a4847
Aug 18 10:01:57.547: vmx| hostCPUID level 80000005, 0: 0x00000000 0x00000000 0x00000000 0x00000000
Aug 18 10:01:57.547: vmx| hostCPUID level 80000006, 0: 0x00000000 0x00000000 0x08006040 0x00000000
Aug 18 10:01:57.547: vmx| hostCPUID level 80000007, 0: 0x00000000 0x00000000 0x00000000 0x00000000
Aug 18 10:01:57.547: vmx| hostCPUID level 80000008, 0: 0x00003024 0x00000000 0x00000000 0x00000000
Aug 18 10:01:57.547: vmx| CPUID Maximum Physical Address Bits supported across all CPUs : 36
Aug 18 10:01:57.583: vmx| Host ACPI: can't find SRAT
Aug 18 10:01:57.583: vmx| Host: SRAT tables not found in memory
Aug 18 10:01:57.774: vmx| FILE: ObtainMachineID machineID is (2B0gnQAW1PY-qwAA)
Aug 18 10:01:57.775: vmx| Removing stale symlink /var/run/vmware/d635d79c28018a339f60fff600ed6608
Aug 18 10:01:57.775: vmx| Setup symlink /var/run/vmware/d635d79c28018a339f60fff600ed6608 -> /var/run/vmware/matt_1000/1187427717377195_7855
Aug 18 10:01:57.775: vmx| ACL_InitCapabilities: current IPC thread
Aug 18 10:01:57.775: vmx| ACL_InitCapabilities: done
Aug 18 10:01:57.776: vmx| changing directory to /media/sda3/Virtual Machines/xp/xp/.
Aug 18 10:01:57.776: vmx| Config file: /media/sda3/Virtual Machines/xp/xp/Windows XP Professional.vmx
Aug 18 10:01:57.914: vmx| VMXVmdb_LoadRawConfig: Loading raw config
Aug 18 10:01:57.960: vmx| VMXVmdbCbVmVmxExecState: Exec state change requested to state poweredOn without reset
Aug 18 10:01:57.960: vmx| PowerOn
Aug 18 10:01:57.961: vmx| Host ACPI: can't find SRAT
Aug 18 10:01:57.961: vmx| Host: SRAT tables not found in memory
Aug 18 10:01:57.968: vmx| VMXVmdb_LoadRawConfig: Loading raw config
Aug 18 10:01:57.972: vmx| HOST sysname Linux, nodename matt-laptop, release 2.6.20-16-generic, version #2 SMP Thu Jun 7 20:19:32 UTC 2007, machine i686, SMP, hz=250
Aug 18 10:01:57.999: vmx| DICT --- USER PREFERENCES
Aug 18 10:01:57.999: vmx| DICT       pref.grabOnKeyPress = FALSE
Aug 18 10:01:57.999: vmx| DICT       pref.eula.0.appName = VMware Workstation
Aug 18 10:01:57.999: vmx| DICT   pref.eula.0.buildNumber = 45731
Aug 18 10:01:58.000: vmx| DICT     pref.mruDest0.present = FALSE
Aug 18 10:01:58.000: vmx| DICT  pref.mruDest0.destString = 
Aug 18 10:01:58.000: vmx| DICT        pref.mruDest0.user = 
Aug 18 10:01:58.000: vmx| DICT     pref.mruDest1.present = FALSE
Aug 18 10:01:58.001: vmx| DICT  pref.mruDest1.destString = 
Aug 18 10:01:58.001: vmx| DICT        pref.mruDest1.user = 
Aug 18 10:01:58.001: vmx| DICT     pref.mruDest2.present = FALSE
Aug 18 10:01:58.001: vmx| DICT  pref.mruDest2.destString = 
Aug 18 10:01:58.001: vmx| DICT        pref.mruDest2.user = 
Aug 18 10:01:58.002: vmx| DICT     pref.mruDest3.present = FALSE
Aug 18 10:01:58.002: vmx| DICT  pref.mruDest3.destString = 
Aug 18 10:01:58.002: vmx| DICT        pref.mruDest3.user = 
Aug 18 10:01:58.002: vmx| DICT     pref.mruDest4.present = FALSE
Aug 18 10:01:58.002: vmx| DICT  pref.mruDest4.destString = 
Aug 18 10:01:58.003: vmx| DICT        pref.mruDest4.user = 
Aug 18 10:01:58.003: vmx| DICT     pref.mruDest5.present = FALSE
Aug 18 10:01:58.003: vmx| DICT  pref.mruDest5.destString = 
Aug 18 10:01:58.003: vmx| DICT        pref.mruDest5.user = 
Aug 18 10:01:58.003: vmx| DICT     pref.mruDest6.present = FALSE
Aug 18 10:01:58.003: vmx| DICT  pref.mruDest6.destString = 
Aug 18 10:01:58.004: vmx| DICT        pref.mruDest6.user = 
Aug 18 10:01:58.004: vmx| DICT     pref.mruDest7.present = FALSE
Aug 18 10:01:58.004: vmx| DICT  pref.mruDest7.destString = 
Aug 18 10:01:58.004: vmx| DICT        pref.mruDest7.user = 
Aug 18 10:01:58.004: vmx| DICT      pref.mruATS0.present = FALSE
Aug 18 10:01:58.005: vmx| DICT    pref.mruATS0.atsString = 
Aug 18 10:01:58.005: vmx| DICT       pref.mruATS0.domain = 
Aug 18 10:01:58.005: vmx| DICT         pref.mruATS0.user = 
Aug 18 10:01:58.005: vmx| DICT       pref.mruATS0.secure = FALSE
Aug 18 10:01:58.006: vmx| DICT         pref.mruATS0.port = 0
Aug 18 10:01:58.006: vmx| DICT      pref.mruATS1.present = FALSE
Aug 18 10:01:58.006: vmx| DICT    pref.mruATS1.atsString = 
Aug 18 10:01:58.006: vmx| DICT       pref.mruATS1.domain = 
Aug 18 10:01:58.006: vmx| DICT         pref.mruATS1.user = 
Aug 18 10:01:58.007: vmx| DICT       pref.mruATS1.secure = FALSE
Aug 18 10:01:58.007: vmx| DICT         pref.mruATS1.port = 0
Aug 18 10:01:58.007: vmx| DICT      pref.mruATS2.present = FALSE
Aug 18 10:01:58.007: vmx| DICT    pref.mruATS2.atsString = 
Aug 18 10:01:58.007: vmx| DICT       pref.mruATS2.domain = 
Aug 18 10:01:58.007: vmx| DICT         pref.mruATS2.user = 
Aug 18 10:01:58.008: vmx| DICT       pref.mruATS2.secure = FALSE
Aug 18 10:01:58.008: vmx| DICT         pref.mruATS2.port = 0
Aug 18 10:01:58.008: vmx| DICT      pref.mruATS3.present = FALSE
Aug 18 10:01:58.008: vmx| DICT    pref.mruATS3.atsString = 
Aug 18 10:01:58.008: vmx| DICT       pref.mruATS3.domain = 
Aug 18 10:01:58.009: vmx| DICT         pref.mruATS3.user = 
Aug 18 10:01:58.009: vmx| DICT       pref.mruATS3.secure = FALSE
Aug 18 10:01:58.009: vmx| DICT         pref.mruATS3.port = 0
Aug 18 10:01:58.009: vmx| DICT      pref.mruATS4.present = FALSE
Aug 18 10:01:58.009: vmx| DICT    pref.mruATS4.atsString = 
Aug 18 10:01:58.010: vmx| DICT       pref.mruATS4.domain = 
Aug 18 10:01:58.010: vmx| DICT         pref.mruATS4.user = 
Aug 18 10:01:58.010: vmx| DICT       pref.mruATS4.secure = FALSE
Aug 18 10:01:58.010: vmx| DICT         pref.mruATS4.port = 0
Aug 18 10:01:58.010: vmx| DICT      pref.mruATS5.present = FALSE
Aug 18 10:01:58.011: vmx| DICT    pref.mruATS5.atsString = 
Aug 18 10:01:58.011: vmx| DICT       pref.mruATS5.domain = 
Aug 18 10:01:58.011: vmx| DICT         pref.mruATS5.user = 
Aug 18 10:01:58.011: vmx| DICT       pref.mruATS5.secure = FALSE
Aug 18 10:01:58.011: vmx| DICT         pref.mruATS5.port = 0
Aug 18 10:01:58.012: vmx| DICT      pref.mruATS6.present = FALSE
Aug 18 10:01:58.012: vmx| DICT    pref.mruATS6.atsString = 
Aug 18 10:01:58.109: vmx| DICT       pref.mruATS6.domain = 
Aug 18 10:01:58.110: vmx| DICT         pref.mruATS6.user = 
Aug 18 10:01:58.110: vmx| DICT       pref.mruATS6.secure = FALSE
Aug 18 10:01:58.110: vmx| DICT         pref.mruATS6.port = 0
Aug 18 10:01:58.110: vmx| DICT      pref.mruATS7.present = FALSE
Aug 18 10:01:58.111: vmx| DICT    pref.mruATS7.atsString = 
Aug 18 10:01:58.111: vmx| DICT       pref.mruATS7.domain = 
Aug 18 10:01:58.111: vmx| DICT         pref.mruATS7.user = 
Aug 18 10:01:58.111: vmx| DICT       pref.mruATS7.secure = FALSE
Aug 18 10:01:58.112: vmx| DICT         pref.mruATS7.port = 0
Aug 18 10:01:58.112: vmx| DICT            pref.tip.index = 6
Aug 18 10:01:58.112: vmx| DICT       webUpdate.checkLast = 1187425704
Aug 18 10:01:58.112: vmx| DICT pref.ws.openedObj0.present = TRUE
Aug 18 10:01:58.112: vmx| DICT   pref.ws.openedObj0.type = vm
Aug 18 10:01:58.113: vmx| DICT   pref.ws.openedObj0.path = /vm/#e42739a2e2768f74/
Aug 18 10:01:58.113: vmx| DICT   pref.ws.openedObj0.file = /media/sda3/Virtual Machines/xp/xp/Windows XP Professional.vmx
Aug 18 10:01:58.113: vmx| DICT   pref.ws.openedObj0.dest = /host2/#_client/
Aug 18 10:01:58.113: vmx| DICT  pref.ws.openedObj.maxNum = 1
Aug 18 10:01:58.114: vmx| DICT   pref.ws.currentObj.path = /vm/#a33cdf29cbc8fb2f/
Aug 18 10:01:58.114: vmx| DICT   pref.ws.currentObj.type = vm
Aug 18 10:01:58.114: vmx| DICT      pref.placement.right = 1440
Aug 18 10:01:58.114: vmx| DICT     pref.placement.bottom = 827
Aug 18 10:01:58.114: vmx| DICT --- USER DEFAULTS
Aug 18 10:01:58.115: vmx| DICT --- HOST DEFAULTS
Aug 18 10:01:58.115: vmx| DICT    vmnet1.hostonlyaddress = 192.168.102.1
Aug 18 10:01:58.115: vmx| DICT           product.version = 6.0.0
Aug 18 10:01:58.115: vmx| DICT          control.fullpath = /usr/bin/vmware-cmd
Aug 18 10:01:58.115: vmx| DICT            authd.fullpath = /usr/sbin/vmware-authd
Aug 18 10:01:58.116: vmx| DICT             loop.fullpath = /usr/bin/vmware-loop
Aug 18 10:01:58.116: vmx| DICT                    libdir = /usr/lib/vmware
Aug 18 10:01:58.116: vmx| DICT           vmware.fullpath = /usr/bin/vmware
Aug 18 10:01:58.116: vmx| DICT       product.buildnumber = 45731
Aug 18 10:01:58.117: vmx| DICT    vmnet1.hostonlynetmask = 255.255.255.0
Aug 18 10:01:58.117: vmx| DICT            dhcpd.fullpath = /usr/bin/vmnet-dhcpd
Aug 18 10:01:58.117: vmx| DICT              product.name = VMware Workstation
Aug 18 10:01:58.117: vmx| DICT                vix.libdir = /usr/lib/vmware-vix/lib
Aug 18 10:01:58.117: vmx| DICT --- SITE DEFAULTS
Aug 18 10:01:58.120: vmx| DICT                  tag.help = introduction.htm
Aug 18 10:01:58.120: vmx| DICT   tag.configurationEditor = config_editor_newvm.htm
Aug 18 10:01:58.120: vmx| DICT             tag.ideConfig = devices_virtualdrive.htm
Aug 18 10:01:58.120: vmx| DICT          tag.floppyConfig = devices_floppy.htm
Aug 18 10:01:58.121: vmx| DICT           tag.mouseConfig = devices_mouse.htm
Aug 18 10:01:58.121: vmx| DICT             tag.netConfig = devices_netadapter.htm
Aug 18 10:01:58.121: vmx| DICT        tag.parallelConfig = devices_parallel.htm
Aug 18 10:01:58.121: vmx| DICT          tag.serialConfig = devices_serial.htm
Aug 18 10:01:58.122: vmx| DICT           tag.soundConfig = devices_sound.htm
Aug 18 10:01:58.122: vmx| DICT             tag.memConfig = configvm_memory.htm
Aug 18 10:01:58.122: vmx| DICT            tag.miscConfig = configvm.htm
Aug 18 10:01:58.122: vmx| DICT             tag.usbConfig = devices_usb.htm
Aug 18 10:01:58.123: vmx| DICT         tag.displayConfig = configvm_display-problems.htm
Aug 18 10:01:58.123: vmx| DICT                 tag.tools = vmtools.htm
Aug 18 10:01:58.123: vmx| DICT --- COMMAND LINE
Aug 18 10:01:58.123: vmx| DICT             gui.available = TRUE
Aug 18 10:01:58.123: vmx| DICT --- CONFIGURATION
Aug 18 10:01:58.124: vmx| DICT            config.version = 8
Aug 18 10:01:58.124: vmx| DICT         virtualHW.version = 6
Aug 18 10:01:58.124: vmx| DICT             scsi0.present = TRUE
Aug 18 10:01:58.124: vmx| DICT                   memsize = 1000
Aug 18 10:01:58.125: vmx| DICT     MemAllowAutoScaleDown = FALSE
Aug 18 10:01:58.125: vmx| DICT            ide0:0.present = TRUE
Aug 18 10:01:58.126: vmx| DICT           ide0:0.fileName = Windows XP Professional.vmdk
Aug 18 10:01:58.126: vmx| DICT            ide1:0.present = TRUE
Aug 18 10:01:58.126: vmx| DICT         ide1:0.autodetect = TRUE
Aug 18 10:01:58.126: vmx| DICT         ide1:0.deviceType = cdrom-raw
Aug 18 10:01:58.127: vmx| DICT    floppy0.startConnected = FALSE
Aug 18 10:01:58.127: vmx| DICT        floppy0.autodetect = TRUE
Aug 18 10:01:58.127: vmx| DICT         ethernet0.present = TRUE
Aug 18 10:01:58.127: vmx| DICT   ethernet0.wakeOnPcktRcv = FALSE
Aug 18 10:01:58.128: vmx| DICT               usb.present = TRUE
Aug 18 10:01:58.128: vmx| DICT              ehci.present = TRUE
Aug 18 10:01:58.128: vmx| DICT             sound.present = TRUE
Aug 18 10:01:58.128: vmx| DICT            sound.fileName = -1
Aug 18 10:01:58.128: vmx| DICT          sound.autodetect = TRUE
Aug 18 10:01:58.129: vmx| DICT           svga.autodetect = TRUE
Aug 18 10:01:58.129: vmx| DICT        pciBridge0.present = TRUE
Aug 18 10:01:58.129: vmx| DICT isolation.tools.hgfs.disable = TRUE
Aug 18 10:01:58.130: vmx| DICT               displayName = Windows XP Professional
Aug 18 10:01:58.130: vmx| DICT                   guestOS = winxppro
Aug 18 10:01:58.130: vmx| DICT                     nvram = Windows XP Professional.nvram
Aug 18 10:01:58.131: vmx| DICT        deploymentPlatform = windows
Aug 18 10:01:58.131: vmx| DICT virtualHW.productCompatibility = hosted
Aug 18 10:01:58.131: vmx| DICT    RemoteDisplay.vnc.port = 0
Aug 18 10:01:58.131: vmx| DICT      tools.upgrade.policy = useGlobal
Aug 18 10:01:58.131: vmx| DICT          floppy0.fileName = /dev/fd0
Aug 18 10:01:58.132: vmx| DICT     ethernet0.addressType = generated
Aug 18 10:01:58.132: vmx| DICT             uuid.location = 56 4d bb 02 38 32 80 97-7a 66 86 48 9d 73 7c 7e
Aug 18 10:01:58.132: vmx| DICT                 uuid.bios = 56 4d bb 02 38 32 80 97-7a 66 86 48 9d 73 7c 7e
Aug 18 10:01:58.132: vmx| DICT               ide0:0.redo = 
Aug 18 10:01:58.133: vmx| DICT  pciBridge0.pciSlotNumber = 17
Aug 18 10:01:58.133: vmx| DICT       scsi0.pciSlotNumber = 16
Aug 18 10:01:58.133: vmx| DICT   ethernet0.pciSlotNumber = 32
Aug 18 10:01:58.133: vmx| DICT       sound.pciSlotNumber = 33
Aug 18 10:01:58.134: vmx| DICT        ehci.pciSlotNumber = 34
Aug 18 10:01:58.134: vmx| DICT ethernet0.generatedAddress = 00:0c:29:73:7c:7e
Aug 18 10:01:58.134: vmx| DICT ethernet0.generatedAddressOffset = 0
Aug 18 10:01:58.134: vmx| DICT        extendedConfigFile = Windows XP Professional.vmxf
Aug 18 10:01:58.135: vmx| DICT --- USER DEFAULTS
Aug 18 10:01:58.135: vmx| DICT --- HOST DEFAULTS
Aug 18 10:01:58.135: vmx| DICT    vmnet1.hostonlyaddress = 192.168.102.1
Aug 18 10:01:58.135: vmx| DICT           product.version = 6.0.0
Aug 18 10:01:58.136: vmx| DICT          control.fullpath = /usr/bin/vmware-cmd
Aug 18 10:01:58.136: vmx| DICT            authd.fullpath = /usr/sbin/vmware-authd
Aug 18 10:01:58.136: vmx| DICT             loop.fullpath = /usr/bin/vmware-loop
Aug 18 10:01:58.136: vmx| DICT                    libdir = /usr/lib/vmware
Aug 18 10:01:58.136: vmx| DICT           vmware.fullpath = /usr/bin/vmware
Aug 18 10:01:58.137: vmx| DICT       product.buildnumber = 45731
Aug 18 10:01:58.137: vmx| DICT    vmnet1.hostonlynetmask = 255.255.255.0
Aug 18 10:01:58.137: vmx| DICT            dhcpd.fullpath = /usr/bin/vmnet-dhcpd
Aug 18 10:01:58.138: vmx| DICT              product.name = VMware Workstation
Aug 18 10:01:58.138: vmx| DICT                vix.libdir = /usr/lib/vmware-vix/lib
Aug 18 10:01:58.138: vmx| DICT --- SITE DEFAULTS
Aug 18 10:01:58.138: vmx| DICT                  tag.help = introduction.htm
Aug 18 10:01:58.139: vmx| DICT   tag.configurationEditor = config_editor_newvm.htm
Aug 18 10:01:58.139: vmx| DICT             tag.ideConfig = devices_virtualdrive.htm
Aug 18 10:01:58.139: vmx| DICT          tag.floppyConfig = devices_floppy.htm
Aug 18 10:01:58.139: vmx| DICT           tag.mouseConfig = devices_mouse.htm
Aug 18 10:01:58.140: vmx| DICT             tag.netConfig = devices_netadapter.htm
Aug 18 10:01:58.163: vmx| DICT        tag.parallelConfig = devices_parallel.htm
Aug 18 10:01:58.163: vmx| DICT          tag.serialConfig = devices_serial.htm
Aug 18 10:01:58.163: vmx| DICT           tag.soundConfig = devices_sound.htm
Aug 18 10:01:58.164: vmx| DICT             tag.memConfig = configvm_memory.htm
Aug 18 10:01:58.164: vmx| DICT            tag.miscConfig = configvm.htm
Aug 18 10:01:58.164: vmx| DICT             tag.usbConfig = devices_usb.htm
Aug 18 10:01:58.164: vmx| DICT         tag.displayConfig = configvm_display-problems.htm
Aug 18 10:01:58.164: vmx| DICT                 tag.tools = vmtools.htm
Aug 18 10:01:58.165: vmx| DICT --- GLOBAL SETTINGS
Aug 18 10:01:58.165: vmx| Msg_Hint: msg.guestos.xp (sent)
Aug 18 10:01:58.165: vmx| The Microsoft Windows XP product activation feature creates a key based on the virtual hardware in the virtual machine where it is installed. Changes in the virtual machine configuration may require you to reactivate the guest operating system. To minimize those changes, be sure to set the final memory size for the virtual machine and install VMware Tools before you activate Windows XP.
Aug 18 10:01:58.165: vmx| For more information about Windows XP product activation and virtual machines see our Web site at "http://www.vmware.com/info?id=50".
Aug 18 10:01:58.165: vmx| 
Aug 18 10:01:58.165: vmx| ---------------------------------------
Aug 18 10:02:00.611: vmx| hostCpuFeatures = 0x500001ba
Aug 18 10:02:00.611: vmx| hostNumPerfCounters = 2
Aug 18 10:02:00.613: vmx| guestCpuFeatures = 0x500001b0
Aug 18 10:02:00.763: vmx| XINFO X fd is 53
Aug 18 10:02:00.763: vmx| XINFO depth 24 bpp 32 class 4
Aug 18 10:02:01.115: vmx| XINFO WARNING: XF86MISC version 0.9
Aug 18 10:02:01.156: vmx| VT redirected kernel output to /dev/tty1
Aug 18 10:02:01.157: vmx| Host display topology 1440x900.
Aug 18 10:02:01.158: vmx| SVGA using 2360x1770.
Aug 18 10:02:01.159: vmx| WSSCAN: reserved mem (in MB) min=32 max=1952 recommended=1952
Aug 18 10:02:01.159: vmx|         hostMem=2048 maxAllowedAll=-1 maxAllowedVM=8192
Aug 18 10:02:01.159: vmx|         totOverhead=16
Aug 18 10:02:01.160: vmx| WSSCAN: used rec mem (in MB) 1952
Aug 18 10:02:01.161: vmx| WSSCAN: Overhead 263997 paged 7810 nonpaged 4096 maxFBSize
Aug 18 10:02:01.161: vmx| WSSCAN 1 1 458416 458416 499712 -1 50 0
Aug 18 10:02:01.164: vmx| LICENSE using: '/home/matt/.vmware/license.ws.6.0.200907' 
Aug 18 10:02:01.196: vmx| LOG failed to remove stats32-2 failed: No such file or directory
Aug 18 10:02:01.197: vmx| LOG failed to remove stats64-2 failed: No such file or directory
Aug 18 10:02:01.199: vmx| APIC: Host Local APIC at 0xfee00000
Aug 18 10:02:01.207: vmx| vmm32-modules: [vmm.vmm32 .data:0x2b000 .sdata:0x2c000 .statvars:0x2d000 .peer:0x2e000 .shared:0x54000 .bss:0x65000 .rodata:0x6c000 .text:0x77000 .kstatvars:0x3000 ,mmu-pae.vmm32 .rodata:0x75d6c .data:0x2bdb0 .peer:0x52928 .shared:0x639f0 .bss:0x6abc0 .text:0xc996c .comment:0x40000cf0 .statvars:0x2000 .kstatvars:0x2000 .scb:0x400035a0 .shared_meta:0x400034b0 .peer_meta:0x40000ba0 ,sharedmmu-none.vmm32 .text:0xd3834 .comment:0x40000dec ,pv-none.vmm32 .data:0x2bdcc .peer:0x1000 .shared:0x64300 .bss:0x6b120 .text:0xd3850 .comment:0x40000dfe .statvars:0x1000 .kstatvars:0x1000 .shared_meta:0x40003720 ,hv-none.vmm32 .data:0x2bdd0 .peer:0x1000 .shared:0x1000 .bss:0x6b19c .text:0xd3950 .comment:0x40000e46 .statvars:0x1000 .kstatvars:0x1000 ,buslogic-buslogic.vmm32 .shared:0x64448 .bss:0x1000 .text:0xd39b4 .comment:0x40000e58 .scb:0x400036c0 .shared_meta:0x400037b0 ,<MonSrcFile> .rodata:0x75d7c ]
Aug 18 10:02:01.215: vmx| KHZEstimate 1729000
Aug 18 10:02:01.216: vmx| MHZEstimate 1729
Aug 18 10:02:01.216: vmx| NumVCPUs 1
Aug 18 10:02:01.217: vmx| guestCPUID vendor: GenuntelineI
Aug 18 10:02:01.217: vmx| guestCPUID level 00000000, 0: 0x0000000a 0x756e6547 0x6c65746e 0x49656e69
Aug 18 10:02:01.218: vmx| guestCPUID level 00000001, 0: 0x000006f8 0x00010800 0x00000211 0x0febfbff
Aug 18 10:02:01.218: vmx| guestCPUID level 00000002, 0: 0x05b0b101 0x005657f0 0x00000000 0x2cb4307d
Aug 18 10:02:01.241: vmx| guestCPUID level 00000003, 0: 0x00000000 0x00000000 0x00000000 0x00000000
Aug 18 10:02:01.241: vmx| guestCPUID level 00000004, 0: 0x04000121 0x01c0003f 0x0000003f 0x00000001
Aug 18 10:02:01.242: vmx| guestCPUID level 00000005, 0: 0x00000040 0x00000040 0x00000003 0x00022220
Aug 18 10:02:01.242: vmx| guestCPUID level 00000006, 0: 0x00000001 0x00000002 0x00000001 0x00000000
Aug 18 10:02:01.242: vmx| guestCPUID level 00000007, 0: 0x00000000 0x00000000 0x00000000 0x00000000
Aug 18 10:02:01.243: vmx| guestCPUID level 00000008, 0: 0x00000400 0x00000000 0x00000000 0x00000000
Aug 18 10:02:01.243: vmx| guestCPUID level 00000009, 0: 0x00000000 0x00000000 0x00000000 0x00000000
Aug 18 10:02:01.243: vmx| guestCPUID level 0000000a, 0: 0x07280202 0x00000000 0x00000000 0x00000000
Aug 18 10:02:01.243: vmx| guestCPUID level 80000000, 0: 0x80000008 0x00000000 0x00000000 0x00000000
Aug 18 10:02:01.243: vmx| guestCPUID level 80000001, 0: 0x00000000 0x00000000 0x00000000 0x00000800
Aug 18 10:02:01.244: vmx| guestCPUID level 80000002, 0: 0x65746e49 0x2952286c 0x726f4320 0x4d542865
Aug 18 10:02:01.244: vmx| guestCPUID level 80000003, 0: 0x43203229 0x20205550 0x20202020 0x54202020
Aug 18 10:02:01.244: vmx| guestCPUID level 80000004, 0: 0x30303335 0x20402020 0x33372e31 0x007a4847
Aug 18 10:02:01.244: vmx| guestCPUID level 80000005, 0: 0x00000000 0x00000000 0x00000000 0x00000000
Aug 18 10:02:01.244: vmx| guestCPUID level 80000006, 0: 0x00000000 0x00000000 0x08006040 0x00000000
Aug 18 10:02:01.245: vmx| guestCPUID level 80000007, 0: 0x00000000 0x00000000 0x00000000 0x00000000
Aug 18 10:02:01.245: vmx| guestCPUID level 80000008, 0: 0x00003024 0x00000000 0x00000000 0x00000000
Aug 18 10:02:01.245: vmx| PShare: enabled 1, scanRate 32, checkRate 16
Aug 18 10:02:01.246: vmx| UUID: location-UUID is 56 4d bb 02 38 32 80 97-7a 66 86 48 9d 73 7c 7e
Aug 18 10:02:01.272: vmx| MM: Using partialmap, 256000 pages AC 0 CE 1 TM 0 DOHU 0
Aug 18 10:02:01.272: vmx| UUID: canonical path is /media/sda3/Virtual Machines/xp/xp/Windows XP Professional.vmx
Aug 18 10:02:01.272: vmx| UUID: location-UUID is 56 4d bb 02 38 32 80 97-7a 66 86 48 9d 73 7c 7e
Aug 18 10:02:01.274: vmx| FILE: ScanDirectory discarding file '/media/sda3/Virtual Machines/xp/xp/564dbb02-3832-8097-7a66-86489d737c7e.vmem.lck/M25424.lck'; invalid executionID.
Aug 18 10:02:01.347: vmx| MM: using '/media/sda3/Virtual Machines/xp/xp/564dbb02-3832-8097-7a66-86489d737c7e.vmem' as a paging file
Aug 18 10:02:01.347: vmx| Msg_Reset:
Aug 18 10:02:01.347: vmx| ----------------------------------------
Aug 18 10:02:01.347: vmx| Opened paging file /media/sda3/Virtual Machines/xp/xp/564dbb02-3832-8097-7a66-86489d737c7e.vmem
Aug 18 10:02:01.377: vmx| Mapped mainmem as pageable
Aug 18 10:02:01.378: vmx| MStat: Creating Stat vm.uptime
Aug 18 10:02:01.380: vmx| MStat: Creating Stat vm.suspendTime
Aug 18 10:02:01.380: vmx| MStat: Creating Stat vm.powerOnTimeStamp
Aug 18 10:02:01.398: vmx| VMXVmdb_LoadRawConfig: Loading raw config
Aug 18 10:02:01.402: vmx| DISK: OPEN ide0:0 '/media/sda3/Virtual Machines/xp/xp/Windows XP Professional.vmdk' persistent R[(null)]
Aug 18 10:02:01.426: vmx| FILE: ScanDirectory discarding file '/media/sda3/Virtual Machines/xp/xp/Windows XP Professional.vmdk.lck/M00760.lck'; invalid executionID.
Aug 18 10:02:01.496: vmx| DISKLIB-DSCPTR: Opened [0]: "Windows XP Professional-s001.vmdk" (0xa)
Aug 18 10:02:01.535: vmx| DISKLIB-DSCPTR: Opened [1]: "Windows XP Professional-s002.vmdk" (0xa)
Aug 18 10:02:01.557: vmx| DISKLIB-DSCPTR: Opened [2]: "Windows XP Professional-s003.vmdk" (0xa)
Aug 18 10:02:01.585: vmx| DISKLIB-DSCPTR: Opened [3]: "Windows XP Professional-s004.vmdk" (0xa)
Aug 18 10:02:01.604: vmx| DISKLIB-DSCPTR: Opened [4]: "Windows XP Professional-s005.vmdk" (0xa)
Aug 18 10:02:01.628: vmx| DISKLIB-DSCPTR: Opened [5]: "Windows XP Professional-s006.vmdk" (0xa)
Aug 18 10:02:01.660: vmx| DISKLIB-DSCPTR: Opened [6]: "Windows XP Professional-s007.vmdk" (0xa)
Aug 18 10:02:01.686: vmx| DISKLIB-DSCPTR: Opened [7]: "Windows XP Professional-s008.vmdk" (0xa)
Aug 18 10:02:01.729: vmx| DISKLIB-DSCPTR: Opened [8]: "Windows XP Professional-s009.vmdk" (0xa)
Aug 18 10:02:01.758: vmx| DISKLIB-DSCPTR: Opened [9]: "Windows XP Professional-s010.vmdk" (0xa)
Aug 18 10:02:01.759: vmx| DISKLIB-DSCPTR: Opened [10]: "Windows XP Professional-s011.vmdk" (0xa)
Aug 18 10:02:01.760: vmx| DISKLIB-LINK  : Opened '/media/sda3/Virtual Machines/xp/xp/Windows XP Professional.vmdk' (0xa): twoGbMaxExtentSparse, 41943040 sectors / 20480 Mb.
Aug 18 10:02:01.782: vmx| DISKLIB-LIB   : Opened "/media/sda3/Virtual Machines/xp/xp/Windows XP Professional.vmdk" (flags 0xa). 0x8811664
Aug 18 10:02:01.782: vmx| DiskGetGeometry: Reading of disk partition table
Aug 18 10:02:01.840: vmx| DISK: OPEN '/media/sda3/Virtual Machines/xp/xp/Windows XP Professional.vmdk' Geo (16383/16/63) BIOS Geo (0/0/0) freeSpace=41520Mb, ide
Aug 18 10:02:01.903: vmx| Msg_Reset:
Aug 18 10:02:01.903: vmx| ----------------------------------------
Aug 18 10:02:01.931: vmx| TimeTracker host to guest rate conversion 3703370830965 @ 1729000000Hz -> 3703370830965 @ 1729000000Hz
Aug 18 10:02:01.931: vmx| TimeTracker host to guest rate conversion ((x * 2147483648) >> 31) + 0
Aug 18 10:02:01.932: vmx| USB: Initializing 'Generic' backend
Aug 18 10:02:01.932: vmx| USBGL: Usbfs found at /proc/bus/usb
Aug 18 10:02:01.933: vmx| USB: Initializing 'Virtual Hub' backend
Aug 18 10:02:01.933: vmx| USB: Initializing 'Virtual Mouse' backend
Aug 18 10:02:01.934: vmx| Host display topology 1440x900.
Aug 18 10:02:01.934: vmx| SVGA using 2360x1770.
Aug 18 10:02:01.936: vmx| XINFO X fd is 53
Aug 18 10:02:01.937: vmx| XINFO depth 24 bpp 32 class 4
Aug 18 10:02:01.944: vmx| XINFO WARNING: XF86MISC version 0.9
Aug 18 10:02:01.944: vmx| VT redirected kernel output to /dev/tty1
Aug 18 10:02:01.948: vmx| MKS REMOTE Loading VNC Configuration from VM config file
Aug 18 10:02:01.962: vmx| DISKUTIL: ide0:0 : capacity=41943040
Aug 18 10:02:01.963: vmx| DVGA: Full screen VGA will not be available.
Aug 18 10:02:01.963: vmx| Host display topology 1440x900 with 1 displays.
Aug 18 10:02:01.963: vmx| SVGA using 2360x1770.
Aug 18 10:02:01.977: vmx| SCSI0: UNTAGGED commands will be converted to ORDER tags.
Aug 18 10:02:01.977: vmx| VLANCE: send cluster threshold is 80, size = 2 recalcInterval is 2 ticks
Aug 18 10:02:01.978: vmx| Ethernet0 MAC Address: 00:0c:29:73:7c:7e
Aug 18 10:02:01.978: vmx| VMXNET: send cluster threshold is 80, size = 2 recalcInterval is 2 ticks, dontClusterSize is 128
Aug 18 10:02:01.979: vmx| E1000: checksum cycles/kB: C=881 asm=681
Aug 18 10:02:01.979: vmx| USB: Initializing 'UHCI' host controller
Aug 18 10:02:01.979: vmx| USB: Initializing 'EHCI' host controller
Aug 18 10:02:01.980: vmx| MStat: Creating Stat vm.heartbeat
Aug 18 10:02:01.980: vmx| DISKUTIL: ide0:0 : toolsVersion = 0
Aug 18 10:02:01.981: vmx| DISKUTIL: Offline toolsVersion = 0
Aug 18 10:02:01.981: vmx| TOOLS INSTALL initializing state to IDLE on power on.
Aug 18 10:02:02.036: vmx| PTSC to VMI Wallclock (nsec) 3703598572375 @ 1729000000Hz -> 1187427722000000000 @ 1000000000Hz
Aug 18 10:02:02.036: vmx| PTSC to VMI Wallclock (nsec) ((x * 2484075937) >> 32) + 1187425579953399899
Aug 18 10:02:02.038: vmx| TOOLS received request in VMX to set option 'enableDnD' -> '1'
Aug 18 10:02:02.039: vmx| TOOLS received request in VMX to set option 'copypaste' -> '1'
Aug 18 10:02:02.062: vmx| USB: Found device [name:Chicony\ USB\ 2.0\ Camera vid:04f2 pid:b008 path:5/5 speed:high family:other,video autoclean:1]
Aug 18 10:02:02.062: vmx| VMXVmdbLoadUsbDevices: New set of 1 USB devices
Aug 18 10:02:02.063: vmx| VMX_PowerOn: ModuleTable_PowerOn = 1
Aug 18 10:02:02.063: vmx| VMX setting maximum IPC write buffers to 0 packets, 0 bytes
Aug 18 10:02:02.063: mks| Async MKS thread is alive
Aug 18 10:02:02.073: vmx| DnD rpc already set to 1
Aug 18 10:02:02.074: vmx| DnD CopyPasteRegisterRpc already set to 1
Aug 18 10:02:02.074: vcpu-0| APIC: version = 0x14, max LVT = 5
Aug 18 10:02:02.074: vcpu-0| APIC: LDR = 0x1000000, DFR = 0xffffffff
Aug 18 10:02:02.090: vcpu-0| guestCpuFeatures = 0x500001b0
Aug 18 10:02:02.090: vcpu-0| Init modules.
Aug 18 10:02:02.119: mks| Connecting to window system.
Aug 18 10:02:02.120: mks| XINFO X fd is 53
Aug 18 10:02:02.120: mks| XINFO depth 24 bpp 32 class 4
Aug 18 10:02:02.127: mks| XINFO WARNING: XF86MISC version 0.9
Aug 18 10:02:02.127: mks| VT redirected kernel output to /dev/tty1
Aug 18 10:02:02.128: mks| rasterops MMXEXT accelerations enabled
Aug 18 10:02:02.128: mks| XINFO unsupported XF86VidMode version: 2.2
Aug 18 10:02:02.174: mks| XINFO XFree86 VidMode 0: 1440x900 flags: 0xa
Aug 18 10:02:02.175: mks| XINFO XFree86 VidMode 1: 1280x800 flags: 0x5
Aug 18 10:02:02.175: mks| XINFO XFree86 VidMode 2: 1280x768 flags: 0x5
Aug 18 10:02:02.175: mks| XINFO XFree86 VidMode 3: 1024x768 flags: 0xa
Aug 18 10:02:02.175: mks| XINFO XFree86 VidMode 4: 840x525 flags: 0x25
Aug 18 10:02:02.176: mks| XINFO XFree86 VidMode 5: 800x600 flags: 0x5
Aug 18 10:02:02.176: mks| XINFO XFree86 VidMode 6: 800x600 flags: 0x25
Aug 18 10:02:02.176: mks| XINFO XFree86 VidMode 7: 800x512 flags: 0x2a
Aug 18 10:02:02.177: mks| XINFO XFree86 VidMode 8: 720x450 flags: 0x25
Aug 18 10:02:02.177: mks| XINFO XFree86 VidMode 9: 640x512 flags: 0x25
Aug 18 10:02:02.177: mks| XINFO XFree86 VidMode 10: 640x480 flags: 0x25
Aug 18 10:02:02.177: mks| XINFO XFree86 VidMode 11: 640x480 flags: 0xa
Aug 18 10:02:02.178: mks| XINFO XFree86 VidMode 12: 640x400 flags: 0x25
Aug 18 10:02:02.178: mks| XINFO XFree86 VidMode 13: 640x384 flags: 0x25
Aug 18 10:02:02.178: mks| XINFO XFree86 VidMode 14: 512x384 flags: 0x2a
Aug 18 10:02:02.179: mks| XINFO XFree86 VidMode 15: 400x300 flags: 0x25
Aug 18 10:02:02.179: mks| XINFO XFree86 VidMode 16: 320x240 flags: 0x2a
Aug 18 10:02:02.179: mks| KHBKL: Unable to parse keystring at: ''
Aug 18 10:02:02.290: vcpu-0| CPU reset: hard
Aug 18 10:02:02.354: vmx| VNET: Notification enabled for Ethernet0
Aug 18 10:02:02.355: vmx| CDROM: Using autodetect backend /dev/scd0 for ide1:0.
Aug 18 10:02:02.356: vmx| CDROM: Connecting ide1:0 to '/dev/scd0'. img=0 raw=1 excl=0 remote=0
Aug 18 10:02:02.361: vmx| CDROM-LIN:  Implementing mediaChange workaround.
Aug 18 10:02:02.364: vmx| CDROM-LIN:  SEND PACKET API Heuristic active.
Aug 18 10:02:02.365: vmx| CDROM-LIN:  Using SG_IO ioctl for pass-through.
Aug 18 10:02:02.418: vmx| USB: Found device [name:Chicony\ USB\ 2.0\ Camera vid:04f2 pid:b008 path:5/5 speed:high family:other,video autoclean:1]
Aug 18 10:02:02.467: vcpu-0| sz=3051488
Aug 18 10:02:02.493: vcpu-0| vmm32 initialized: Releasebuild-45731. cflags: 0x00000000.18000000.54000600.00000002
Aug 18 10:02:02.496: vcpu-0| MonitorInitNumaUnmapVMM32
Aug 18 10:02:02.521: vcpu-0| Could not mmap paging file : No such device
Aug 18 10:02:02.555: vcpu-0| Could not mmap paging file : No such device
Aug 18 10:02:02.555: vcpu-0| Failed to allocate page for guest RAM!
Aug 18 10:02:02.555: vcpu-0| Backtrace:
Aug 18 10:02:02.556: vcpu-0| Backtrace[0] 0xb4b06de8 eip 0x8053410 
Aug 18 10:02:02.556: vcpu-0| Backtrace[1] 0xb4b07218 eip 0x80f187d 
Aug 18 10:02:02.556: vcpu-0| Backtrace[2] 0xb4b07268 eip 0x82e74cc 
Aug 18 10:02:02.557: vcpu-0| Backtrace[3] 0xb4b072b8 eip 0x82e7661 
Aug 18 10:02:02.557: vcpu-0| Backtrace[4] 0xb4b07308 eip 0x8364f43 
Aug 18 10:02:02.606: vcpu-0| Backtrace[5] 0xb4b07328 eip 0x836de25 
Aug 18 10:02:02.606: vcpu-0| Backtrace[6] 0xb4b07358 eip 0x837c86b 
Aug 18 10:02:02.606: vcpu-0| Backtrace[7] 0xb4b07368 eip 0x836ddc1 
Aug 18 10:02:02.606: vcpu-0| Backtrace[8] 0xb4b073c8 eip 0x80b015f 
Aug 18 10:02:02.607: vcpu-0| Backtrace[9] 0xb4b074b8 eip 0xb7f1c31b 
Aug 18 10:02:02.607: vcpu-0| Backtrace[10] 00000000 eip 0xb7ea557e 
Aug 18 10:02:02.607: vcpu-0| Core dump limit is 0 kb.
Aug 18 10:02:02.608: vcpu-0| Remapping region BusMemFrame14 as MAP_PRIVATE (addr=0xb42dd000, size=0x1000, offset=0xddd000)
Aug 18 10:02:02.609: vcpu-0| Cannot remap region PhysRegion14 (addr=(nil), size=0x1000, offset=0xddc000)
Aug 18 10:02:02.609: vcpu-0| Remapping region BusMemFrame13 as MAP_PRIVATE (addr=0xb42df000, size=0x1000, offset=0xddb000)
Aug 18 10:02:02.610: vcpu-0| Remapping region BusMemFrame12 as MAP_PRIVATE (addr=0xb42e0000, size=0x1000, offset=0xdda000)
Aug 18 10:02:02.797: vcpu-0| Cannot remap region PhysRegion12 (addr=(nil), size=0x20000, offset=0xdba000)
Aug 18 10:02:02.797: vcpu-0| Cannot remap region DFCR3PTvcpu0 (addr=(nil), size=0x1000, offset=0xdb9000)
Aug 18 10:02:02.797: vcpu-0| Cannot remap region DFCR3vcpu0 (addr=(nil), size=0x3000, offset=0xdb6000)
Aug 18 10:02:02.798: vcpu-0| Cannot remap region DFStackvcpu0 (addr=(nil), size=0x1000, offset=0xdb5000)
Aug 18 10:02:02.798: vcpu-0| Remapping region BusMemFrame11 as MAP_PRIVATE (addr=0xb5309000, size=0x4000, offset=0xdb1000)
Aug 18 10:02:02.798: vcpu-0| Remapping region BusMemFrame10 as MAP_PRIVATE (addr=0xb530d000, size=0x20000, offset=0xd91000)
Aug 18 10:02:02.799: vcpu-0| Remapping region BusMemFrame9 as MAP_PRIVATE (addr=0xb532d000, size=0x1000, offset=0xd90000)
Aug 18 10:02:02.799: vcpu-0| Cannot remap region PhysRegion9 (addr=(nil), size=0x10000, offset=0xd80000)
Aug 18 10:02:02.799: vcpu-0| Remapping region BusMemFrame8 as MAP_PRIVATE (addr=0xb533e000, size=0x1000, offset=0xd7f000)
Aug 18 10:02:02.800: vcpu-0| Cannot remap region PhysRegion8 (addr=(nil), size=0x4000, offset=0xd7b000)
Aug 18 10:02:02.852: vcpu-0| Remapping region BusMemFrame7 as MAP_PRIVATE (addr=0xb5343000, size=0x1000, offset=0xd7a000)
Aug 18 10:02:02.852: vcpu-0| Cannot remap region PhysRegion7 (addr=(nil), size=0x8000, offset=0xd72000)
Aug 18 10:02:02.853: vcpu-0| Remapping region BusMemFrame6 as MAP_PRIVATE (addr=0xb534c000, size=0x1000, offset=0xd71000)
Aug 18 10:02:02.853: vcpu-0| Cannot remap region PhysRegion6 (addr=(nil), size=0x1000, offset=0xd70000)
Aug 18 10:02:02.854: vcpu-0| Cannot remap region SVGAFIFO (addr=(nil), size=0x200000, offset=0xb70000)
Aug 18 10:02:02.854: vcpu-0| Cannot remap region VGA (addr=(nil), size=0x40000, offset=0xb30000)
Aug 18 10:02:02.854: vcpu-0| Cannot remap region VIDE_KSEG1 (addr=(nil), size=0x8000, offset=0xb28000)
Aug 18 10:02:02.855: vcpu-0| Cannot remap region VIDE_KSEG0 (addr=(nil), size=0x8000, offset=0xb20000)
Aug 18 10:02:02.904: vcpu-0| Remapping region BusMemFrame5 as MAP_PRIVATE (addr=0xb559e000, size=0x1000, offset=0xb1f000)
Aug 18 10:02:02.905: vcpu-0| Cannot remap region PhysRegion5 (addr=(nil), size=0x1000, offset=0xb1e000)
Aug 18 10:02:02.905: vcpu-0| Remapping region BusMemFrame4 as MAP_PRIVATE (addr=0xb55a0000, size=0x1000, offset=0xb1d000)
Aug 18 10:02:02.905: vcpu-0| Cannot remap region PhysRegion4 (addr=(nil), size=0x80000, offset=0xa9d000)
Aug 18 10:02:02.907: vcpu-0| Cannot remap region StateLoggerLogBuf (addr=(nil), size=0x200000, offset=0x89d000)
Aug 18 10:02:02.909: vcpu-0| Remapping region BusMemFrame3 as MAP_PRIVATE (addr=0xb6e22000, size=0x7d0000, offset=0xcd000)
Aug 18 10:02:02.909: vcpu-0| Cannot remap region IOSpace (addr=(nil), size=0x2000, offset=0xcb000)
Aug 18 10:02:02.961: vcpu-0| Cannot remap region MonitorOther32 (addr=(nil), size=0x2000, offset=0xc9000)
Aug 18 10:02:02.962: vcpu-0| Remapping region BusMemFrame2 as MAP_PRIVATE (addr=0xb7792000, size=0x1000, offset=0x32000)
Aug 18 10:02:02.962: vcpu-0| Cannot remap region APICs (addr=(nil), size=0x1000, offset=0x31000)
Aug 18 10:02:02.962: vcpu-0| Cannot remap region MonWired (addr=(nil), size=0x13000, offset=0x1e000)
Aug 18 10:02:02.962: vcpu-0| Cannot remap region PShareMPN (addr=(nil), size=0x1000, offset=0x1d000)
Aug 18 10:02:02.963: vcpu-0| Remapping region BusMemFrame1 as MAP_PRIVATE (addr=0xb7b1d000, size=0x1000, offset=0x1c000)
Aug 18 10:02:02.963: vcpu-0| Remapping region BusMemFrame0 as MAP_PRIVATE (addr=0xb7f5a000, size=0x1000, offset=0x1b000)
Aug 18 10:02:02.963: vcpu-0| Cannot remap region PhysRegion0 (addr=(nil), size=0x1000, offset=0x1a000)
Aug 18 10:02:02.963: vcpu-0| Remapping region TraceBitmapMainMem as MAP_PRIVATE (addr=0xb7b1e000, size=0x8000, offset=0x12000)
Aug 18 10:02:02.963: vcpu-0| Remapping region SharedArea as MAP_PRIVATE (addr=0xb7794000, size=0x12000, offset=0x0)
Aug 18 10:02:02.964: vcpu-0| Attempting to dump core...
Aug 18 10:02:03.614: vcpu-0| Core dump pipes to process /usr/share/apport/apport, core file unreliableMsg_Post: Error
Aug 18 10:02:03.615: vcpu-0| [msg.log.error.unrecoverable] VMware Workstation unrecoverable error: (vcpu-0)
Aug 18 10:02:03.615: vcpu-0| Failed to allocate page for guest RAM!
Aug 18 10:02:03.615: vcpu-0| [msg.panic.haveLog] A log file is available in "/media/sda3/Virtual Machines/xp/xp/vmware.log".  [msg.panic.haveCore] A core file is available in "/media/sda3/Virtual Machines/xp/xp/core".  [msg.panic.requestSupport.withLogAndCore] Please request support and include the contents of the log file and core file.  [msg.panic.requestSupport.vmSupport] 
Aug 18 10:02:03.615: vcpu-0| To collect files to submit to VMware support, run "vm-support".
Aug 18 10:02:03.615: vcpu-0| [msg.panic.response] We will respond on the basis of your support entitlement.
Aug 18 10:02:03.615: vcpu-0| ----------------------------------------





Any help appreciated.

---

### Post by HermanAB on 2007-08-18
The default NTFS device driver is a read only driver.  VMware needs write access to NTFS.  To get that, you have to install ntfs-3g.

Cheers,

Herman

---

### Post by blop on 2007-08-18
I have done that or think i have....either the ntfs-3g driver install or through Automatix. Either way i have full read and write power to the NTFS partition i have just check....i can make delete and change files and folders.

cheers

EDIT:

I have just tested to see if i can make and run a VM on the linux partition and i can so the problem lies somewhere in the  ability of VMware to run and use VMs on NTFS.....i do have NTFS config tool installed...

---

### Post by blop on 2007-08-18
bump

---

### Post by blop on 2007-08-20
Can anyone help me...

its really weird how Virtual Box will create and or run a virtual machine off my NTFS partition in Ubuntu but VMware wont...

---

### Post by cpjaimes on 2007-08-22
[I]Hi to all of you!
I got a similar problem.. I want to install minix3 in ubuntu by using vmware workstation 6.0

This message appears:[/I]

VMware Workstation unrecoverable error: (vcpu-0)
ASSERT /build/mts/release/bora-45731/bora/vmcore/private/iospace_shared.h:491 bugNr=64440
A log file is available in "/home/christian/vmware/minix3/vmware.log".  A core file is available in "/home/christian/vmware/minix3/core".  Please request support and include the contents of the log file and core file.  
To collect files to submit to VMware support, run "vm-support".
We will respond on the basis of your support entitlement.

*and the log file is the following:*

Aug 22 11:49:11.333: vmx| Log for VMware Workstation pid=19954 version=6.0.0 build=build-45731 option=Release
Aug 22 11:49:11.333: vmx| Hostname=christian-laptop
Aug 22 11:49:11.333: vmx| Command line: "/usr/lib/vmware/bin/vmware-vmx" "-#" "product=1;name=VMware Workstation;version=6.0.0;licensename=VMware Workstation for Linux;licenseversion=6.0 build-45731;" "-@" "pipe=/tmp/vmware-christian/vmx454ad4d87857b6a3;readyEvent=58" "/home/christian/vmware/minix3/minix3.vmx"
Aug 22 11:49:11.334: vmx| Ready event: 58
Aug 22 11:49:11.370: vmx| UI Connecting to pipe '/tmp/vmware-christian/vmx454ad4d87857b6a3' with user '(null)'
Aug 22 11:49:11.439: vmx| Sig_Init already initialized 
Aug 22 11:49:11.441: vmx| VMMon_GetkHzEstimate: Calculated 1045045 kHz
Aug 22 11:49:11.441: vmx| CPUID[0] vendor: AuthcAMDenti
Aug 22 11:49:11.442: vmx| CPUID[0] level 00000000, 0: 0x00000001 0x68747541 0x444d4163 0x69746e65
Aug 22 11:49:11.442: vmx| CPUID[0] level 00000001, 0: 0x000006a0 0x00000000 0x00000000 0x0383f9ff
Aug 22 11:49:11.442: vmx| CPUID[0] level 80000000, 0: 0x80000008 0x68747541 0x444d4163 0x69746e65
Aug 22 11:49:11.442: vmx| CPUID[0] level 80000001, 0: 0x000007a0 0x00000000 0x00000000 0xc1cbf9ff
Aug 22 11:49:11.442: vmx| CPUID[0] level 80000002, 0: 0x69626f6d 0x4120656c 0x4120444d 0x6f6c6874
Aug 22 11:49:11.442: vmx| CPUID[0] level 80000003, 0: 0x6d74286e 0x50582029 0x28204d2d 0x2029564c
Aug 22 11:49:11.442: vmx| CPUID[0] level 80000004, 0: 0x30303232 0x0000002b 0x00000000 0x00000000
Aug 22 11:49:11.442: vmx| CPUID[0] level 80000005, 0: 0x0408ff08 0xff20ff10 0x40020140 0x40020140
Aug 22 11:49:11.442: vmx| CPUID[0] level 80000006, 0: 0x00000000 0x41004100 0x02008140 0x00000000
Aug 22 11:49:11.442: vmx| CPUID[0] level 80000007, 0: 0x00000000 0x00000000 0x00000000 0x00000007
Aug 22 11:49:11.442: vmx| CPUID[0] level 80000008, 0: 0x00002022 0x00000000 0x00000000 0x00000000
Aug 22 11:49:11.442: vmx| hostCPUID vendor: AuthcAMDenti
Aug 22 11:49:11.442: vmx| hostCPUID level 00000000, 0: 0x00000001 0x68747541 0x444d4163 0x69746e65
Aug 22 11:49:11.442: vmx| hostCPUID level 00000001, 0: 0x000006a0 0x00000000 0x00000000 0x0383f9ff
Aug 22 11:49:11.442: vmx| hostCPUID level 80000000, 0: 0x80000008 0x68747541 0x444d4163 0x69746e65
Aug 22 11:49:11.442: vmx| hostCPUID level 80000001, 0: 0x000007a0 0x00000000 0x00000000 0xc1cbf9ff
Aug 22 11:49:11.442: vmx| hostCPUID level 80000002, 0: 0x69626f6d 0x4120656c 0x4120444d 0x6f6c6874
Aug 22 11:49:11.442: vmx| hostCPUID level 80000003, 0: 0x6d74286e 0x50582029 0x28204d2d 0x2029564c
Aug 22 11:49:11.442: vmx| hostCPUID level 80000004, 0: 0x30303232 0x0000002b 0x00000000 0x00000000
Aug 22 11:49:11.442: vmx| hostCPUID level 80000005, 0: 0x0408ff08 0xff20ff10 0x40020140 0x40020140
Aug 22 11:49:11.442: vmx| hostCPUID level 80000006, 0: 0x00000000 0x41004100 0x02008140 0x00000000
Aug 22 11:49:11.442: vmx| hostCPUID level 80000007, 0: 0x00000000 0x00000000 0x00000000 0x00000007
Aug 22 11:49:11.442: vmx| hostCPUID level 80000008, 0: 0x00002024 0x00000000 0x00000000 0x00000000
Aug 22 11:49:11.442: vmx| CPUID Maximum Physical Address Bits supported across all CPUs : 34
Aug 22 11:49:11.447: vmx| Host ACPI: can't find SRAT
Aug 22 11:49:11.447: vmx| Host: SRAT tables not found in memory
Aug 22 11:49:11.449: vmx| FILE: ObtainMachineID machineID is (B7ERAgBARSSuawAA)
Aug 22 11:49:11.450: vmx| Removing stale symlink /var/run/vmware/03a7b2a0b0cf554363f9c44876713d5e
Aug 22 11:49:11.450: vmx| Setup symlink /var/run/vmware/03a7b2a0b0cf554363f9c44876713d5e -> /var/run/vmware/christian_1000/1187801351333910_19954
Aug 22 11:49:11.450: vmx| ACL_InitCapabilities: current IPC thread
Aug 22 11:49:11.450: vmx| ACL_InitCapabilities: done
Aug 22 11:49:11.450: vmx| changing directory to /home/christian/vmware/minix3/.
Aug 22 11:49:11.450: vmx| Config file: /home/christian/vmware/minix3/minix3.vmx
Aug 22 11:49:11.487: vmx| VMXVmdb_LoadRawConfig: Loading raw config
Aug 22 11:49:11.742: vmx| VMXVmdbCbVmVmxExecState: Exec state change requested to state poweredOn without reset
Aug 22 11:49:11.742: vmx| PowerOn
Aug 22 11:49:11.743: vmx| Host ACPI: can't find SRAT
Aug 22 11:49:11.743: vmx| Host: SRAT tables not found in memory
Aug 22 11:49:11.752: vmx| VMXVmdb_LoadRawConfig: Loading raw config
Aug 22 11:49:11.757: vmx| HOST sysname Linux, nodename christian-laptop, release 2.6.17-12-generic, version #2 SMP Mon Jul 16 19:37:58 UTC 2007, machine i686, SMP, hz=250
Aug 22 11:49:11.757: vmx| DICT --- USER PREFERENCES
Aug 22 11:49:11.757: vmx| DICT       pref.grabOnKeyPress = FALSE
Aug 22 11:49:11.757: vmx| DICT       pref.eula.0.appName = VMware Player
Aug 22 11:49:11.757: vmx| DICT   pref.eula.0.buildNumber = 29634
Aug 22 11:49:11.757: vmx| DICT            pref.eula.size = 1
Aug 22 11:49:11.757: vmx| DICT    pref.autoFitFullScreen = fitHostToGuest
Aug 22 11:49:11.757: vmx| DICT     pref.view.navBar.type = favorites
Aug 22 11:49:11.757: vmx| DICT     pref.mruDest0.present = FALSE
Aug 22 11:49:11.757: vmx| DICT  pref.mruDest0.destString = 
Aug 22 11:49:11.757: vmx| DICT        pref.mruDest0.user = 
Aug 22 11:49:11.757: vmx| DICT     pref.mruDest1.present = FALSE
Aug 22 11:49:11.757: vmx| DICT  pref.mruDest1.destString = 
Aug 22 11:49:11.757: vmx| DICT        pref.mruDest1.user = 
Aug 22 11:49:11.757: vmx| DICT     pref.mruDest2.present = FALSE
Aug 22 11:49:11.757: vmx| DICT  pref.mruDest2.destString = 
Aug 22 11:49:11.757: vmx| DICT        pref.mruDest2.user = 
Aug 22 11:49:11.758: vmx| DICT     pref.mruDest3.present = FALSE
Aug 22 11:49:11.758: vmx| DICT  pref.mruDest3.destString = 
Aug 22 11:49:11.758: vmx| DICT        pref.mruDest3.user = 
Aug 22 11:49:11.758: vmx| DICT     pref.mruDest4.present = FALSE
Aug 22 11:49:11.758: vmx| DICT  pref.mruDest4.destString = 
Aug 22 11:49:11.758: vmx| DICT        pref.mruDest4.user = 
Aug 22 11:49:11.758: vmx| DICT     pref.mruDest5.present = FALSE
Aug 22 11:49:11.758: vmx| DICT  pref.mruDest5.destString = 
Aug 22 11:49:11.758: vmx| DICT        pref.mruDest5.user = 
Aug 22 11:49:11.758: vmx| DICT     pref.mruDest6.present = FALSE
Aug 22 11:49:11.758: vmx| DICT  pref.mruDest6.destString = 
Aug 22 11:49:11.758: vmx| DICT        pref.mruDest6.user = 
Aug 22 11:49:11.758: vmx| DICT     pref.mruDest7.present = FALSE
Aug 22 11:49:11.758: vmx| DICT  pref.mruDest7.destString = 
Aug 22 11:49:11.758: vmx| DICT        pref.mruDest7.user = 
Aug 22 11:49:11.758: vmx| DICT       webUpdate.checkLast = 1187669545
Aug 22 11:49:11.758: vmx| DICT webUpdate.lastCheck.status = done_updates
Aug 22 11:49:11.758: vmx| DICT       pref.eula.1.appName = VMware Workstation
Aug 22 11:49:11.758: vmx| DICT   pref.eula.1.buildNumber = 45731
Aug 22 11:49:11.758: vmx| DICT      pref.mruATS0.present = FALSE
Aug 22 11:49:11.758: vmx| DICT    pref.mruATS0.atsString = 
Aug 22 11:49:11.758: vmx| DICT       pref.mruATS0.domain = 
Aug 22 11:49:11.758: vmx| DICT         pref.mruATS0.user = 
Aug 22 11:49:11.758: vmx| DICT       pref.mruATS0.secure = FALSE
Aug 22 11:49:11.758: vmx| DICT         pref.mruATS0.port = 0
Aug 22 11:49:11.758: vmx| DICT      pref.mruATS1.present = FALSE
Aug 22 11:49:11.758: vmx| DICT    pref.mruATS1.atsString = 
Aug 22 11:49:11.758: vmx| DICT       pref.mruATS1.domain = 
Aug 22 11:49:11.758: vmx| DICT         pref.mruATS1.user = 
Aug 22 11:49:11.758: vmx| DICT       pref.mruATS1.secure = FALSE
Aug 22 11:49:11.758: vmx| DICT         pref.mruATS1.port = 0
Aug 22 11:49:11.758: vmx| DICT      pref.mruATS2.present = FALSE
Aug 22 11:49:11.758: vmx| DICT    pref.mruATS2.atsString = 
Aug 22 11:49:11.758: vmx| DICT       pref.mruATS2.domain = 
Aug 22 11:49:11.758: vmx| DICT         pref.mruATS2.user = 
Aug 22 11:49:11.758: vmx| DICT       pref.mruATS2.secure = FALSE
Aug 22 11:49:11.758: vmx| DICT         pref.mruATS2.port = 0
Aug 22 11:49:11.758: vmx| DICT      pref.mruATS3.present = FALSE
Aug 22 11:49:11.758: vmx| DICT    pref.mruATS3.atsString = 
Aug 22 11:49:11.758: vmx| DICT       pref.mruATS3.domain = 
Aug 22 11:49:11.758: vmx| DICT         pref.mruATS3.user = 
Aug 22 11:49:11.758: vmx| DICT       pref.mruATS3.secure = FALSE
Aug 22 11:49:11.758: vmx| DICT         pref.mruATS3.port = 0
Aug 22 11:49:11.758: vmx| DICT      pref.mruATS4.present = FALSE
Aug 22 11:49:11.758: vmx| DICT    pref.mruATS4.atsString = 
Aug 22 11:49:11.758: vmx| DICT       pref.mruATS4.domain = 
Aug 22 11:49:11.758: vmx| DICT         pref.mruATS4.user = 
Aug 22 11:49:11.758: vmx| DICT       pref.mruATS4.secure = FALSE
Aug 22 11:49:11.758: vmx| DICT         pref.mruATS4.port = 0
Aug 22 11:49:11.758: vmx| DICT      pref.mruATS5.present = FALSE
Aug 22 11:49:11.758: vmx| DICT    pref.mruATS5.atsString = 
Aug 22 11:49:11.758: vmx| DICT       pref.mruATS5.domain = 
Aug 22 11:49:11.758: vmx| DICT         pref.mruATS5.user = 
Aug 22 11:49:11.758: vmx| DICT       pref.mruATS5.secure = FALSE
Aug 22 11:49:11.758: vmx| DICT         pref.mruATS5.port = 0
Aug 22 11:49:11.758: vmx| DICT      pref.mruATS6.present = FALSE
Aug 22 11:49:11.758: vmx| DICT    pref.mruATS6.atsString = 
Aug 22 11:49:11.758: vmx| DICT       pref.mruATS6.domain = 
Aug 22 11:49:11.758: vmx| DICT         pref.mruATS6.user = 
Aug 22 11:49:11.758: vmx| DICT       pref.mruATS6.secure = FALSE
Aug 22 11:49:11.758: vmx| DICT         pref.mruATS6.port = 0
Aug 22 11:49:11.759: vmx| DICT      pref.mruATS7.present = FALSE
Aug 22 11:49:11.759: vmx| DICT    pref.mruATS7.atsString = 
Aug 22 11:49:11.759: vmx| DICT       pref.mruATS7.domain = 
Aug 22 11:49:11.759: vmx| DICT         pref.mruATS7.user = 
Aug 22 11:49:11.759: vmx| DICT       pref.mruATS7.secure = FALSE
Aug 22 11:49:11.759: vmx| DICT         pref.mruATS7.port = 0
Aug 22 11:49:11.759: vmx| DICT            pref.tip.index = 3
Aug 22 11:49:11.759: vmx| DICT pref.ws.openedObj0.present = TRUE
Aug 22 11:49:11.759: vmx| DICT   pref.ws.openedObj0.type = vm
Aug 22 11:49:11.759: vmx| DICT   pref.ws.openedObj0.path = /vm/#454ad4d87857b6a3/
Aug 22 11:49:11.759: vmx| DICT   pref.ws.openedObj0.file = /home/christian/vmware/minix3/minix3.vmx
Aug 22 11:49:11.759: vmx| DICT   pref.ws.openedObj0.dest = /host2/#_client/
Aug 22 11:49:11.759: vmx| DICT  pref.ws.openedObj.maxNum = 1
Aug 22 11:49:11.759: vmx| DICT   pref.ws.currentObj.path = /vm/#454ad4d87857b6a3/
Aug 22 11:49:11.759: vmx| DICT   pref.ws.currentObj.type = vm
Aug 22 11:49:11.759: vmx| DICT       pref.placement.left = 16
Aug 22 11:49:11.759: vmx| DICT        pref.placement.top = 100
Aug 22 11:49:11.759: vmx| DICT      pref.placement.right = 966
Aug 22 11:49:11.759: vmx| DICT     pref.placement.bottom = 661
Aug 22 11:49:11.759: vmx| DICT --- USER DEFAULTS
Aug 22 11:49:11.759: vmx| DICT --- HOST DEFAULTS
Aug 22 11:49:11.759: vmx| DICT    vmnet1.hostonlyaddress = 192.168.136.1
Aug 22 11:49:11.759: vmx| DICT    vmnet1.hostonlynetmask = 255.255.255.0
Aug 22 11:49:11.759: vmx| DICT          control.fullpath = /usr/bin/vmware-cmd
Aug 22 11:49:11.759: vmx| DICT             loop.fullpath = /usr/bin/vmware-loop
Aug 22 11:49:11.759: vmx| DICT            dhcpd.fullpath = /usr/bin/vmnet-dhcpd
Aug 22 11:49:11.759: vmx| DICT                    libdir = /usr/lib/vmware
Aug 22 11:49:11.759: vmx| DICT           vmware.fullpath = /usr/bin/vmware
Aug 22 11:49:11.759: vmx| DICT           product.version = 6.0.0
Aug 22 11:49:11.759: vmx| DICT            authd.fullpath = /usr/sbin/vmware-authd
Aug 22 11:49:11.759: vmx| DICT       product.buildnumber = 45731
Aug 22 11:49:11.759: vmx| DICT              product.name = VMware Workstation
Aug 22 11:49:11.759: vmx| DICT --- SITE DEFAULTS
Aug 22 11:49:11.759: vmx| DICT                  tag.help = introduction.htm
Aug 22 11:49:11.759: vmx| DICT   tag.configurationEditor = config_editor_newvm.htm
Aug 22 11:49:11.759: vmx| DICT             tag.ideConfig = devices_virtualdrive.htm
Aug 22 11:49:11.759: vmx| DICT          tag.floppyConfig = devices_floppy.htm
Aug 22 11:49:11.759: vmx| DICT           tag.mouseConfig = devices_mouse.htm
Aug 22 11:49:11.759: vmx| DICT             tag.netConfig = devices_netadapter.htm
Aug 22 11:49:11.759: vmx| DICT        tag.parallelConfig = devices_parallel.htm
Aug 22 11:49:11.759: vmx| DICT          tag.serialConfig = devices_serial.htm
Aug 22 11:49:11.759: vmx| DICT           tag.soundConfig = devices_sound.htm
Aug 22 11:49:11.759: vmx| DICT             tag.memConfig = configvm_memory.htm
Aug 22 11:49:11.759: vmx| DICT            tag.miscConfig = configvm.htm
Aug 22 11:49:11.759: vmx| DICT             tag.usbConfig = devices_usb.htm
Aug 22 11:49:11.759: vmx| DICT         tag.displayConfig = configvm_display-problems.htm
Aug 22 11:49:11.759: vmx| DICT                 tag.tools = vmtools.htm
Aug 22 11:49:11.759: vmx| DICT --- COMMAND LINE
Aug 22 11:49:11.759: vmx| DICT             gui.available = TRUE
Aug 22 11:49:11.759: vmx| DICT --- CONFIGURATION
Aug 22 11:49:11.759: vmx| DICT            config.version = 8
Aug 22 11:49:11.759: vmx| DICT         virtualHW.version = 6
Aug 22 11:49:11.759: vmx| DICT             scsi0.present = TRUE
Aug 22 11:49:11.759: vmx| DICT                   memsize = 160
Aug 22 11:49:11.759: vmx| DICT     MemAllowAutoScaleDown = FALSE
Aug 22 11:49:11.759: vmx| DICT            ide0:0.present = TRUE
Aug 22 11:49:11.759: vmx| DICT           ide0:0.fileName = minix3.vmdk
Aug 22 11:49:11.759: vmx| DICT            ide1:0.present = TRUE
Aug 22 11:49:11.759: vmx| DICT         ide1:0.autodetect = TRUE
Aug 22 11:49:11.759: vmx| DICT         ide1:0.deviceType = cdrom-raw
Aug 22 11:49:11.759: vmx| DICT    floppy0.startConnected = FALSE
Aug 22 11:49:11.760: vmx| DICT        floppy0.autodetect = TRUE
Aug 22 11:49:11.760: vmx| DICT         ethernet0.present = TRUE
Aug 22 11:49:11.760: vmx| DICT   ethernet0.wakeOnPcktRcv = FALSE
Aug 22 11:49:11.760: vmx| DICT             sound.present = TRUE
Aug 22 11:49:11.760: vmx| DICT            sound.fileName = -1
Aug 22 11:49:11.760: vmx| DICT          sound.autodetect = TRUE
Aug 22 11:49:11.760: vmx| DICT           svga.autodetect = FALSE
Aug 22 11:49:11.760: vmx| DICT        pciBridge0.present = TRUE
Aug 22 11:49:11.760: vmx| DICT isolation.tools.hgfs.disable = TRUE
Aug 22 11:49:11.760: vmx| DICT               displayName = minix3
Aug 22 11:49:11.760: vmx| DICT                   guestOS = other
Aug 22 11:49:11.760: vmx| DICT                     nvram = minix3.nvram
Aug 22 11:49:11.760: vmx| DICT        deploymentPlatform = windows
Aug 22 11:49:11.760: vmx| DICT virtualHW.productCompatibility = hosted
Aug 22 11:49:11.760: vmx| DICT    RemoteDisplay.vnc.port = 0
Aug 22 11:49:11.760: vmx| DICT      tools.upgrade.policy = useGlobal
Aug 22 11:49:11.760: vmx| DICT          floppy0.fileName = /dev/fd0
Aug 22 11:49:11.760: vmx| DICT     ethernet0.addressType = generated
Aug 22 11:49:11.760: vmx| DICT             uuid.location = 56 4d d8 91 79 2e 85 29-55 88 aa b2 0e bb 92 ec
Aug 22 11:49:11.760: vmx| DICT                 uuid.bios = 56 4d d8 91 79 2e 85 29-55 88 aa b2 0e bb 92 ec
Aug 22 11:49:11.760: vmx| DICT               ide0:0.redo = 
Aug 22 11:49:11.760: vmx| DICT  pciBridge0.pciSlotNumber = 17
Aug 22 11:49:11.760: vmx| DICT       scsi0.pciSlotNumber = 16
Aug 22 11:49:11.760: vmx| DICT   ethernet0.pciSlotNumber = 32
Aug 22 11:49:11.760: vmx| DICT       sound.pciSlotNumber = 33
Aug 22 11:49:11.760: vmx| DICT ethernet0.generatedAddress = 00:0c:29:bb:92:ec
Aug 22 11:49:11.760: vmx| DICT ethernet0.generatedAddressOffset = 0
Aug 22 11:49:11.760: vmx| DICT        extendedConfigFile = minix3.vmxf
Aug 22 11:49:11.760: vmx| DICT           floppy0.present = FALSE
Aug 22 11:49:11.760: vmx| DICT             svga.maxWidth = 1280
Aug 22 11:49:11.760: vmx| DICT            svga.maxHeight = 1024
Aug 22 11:49:11.760: vmx| DICT             svga.vramSize = 5242880
Aug 22 11:49:11.760: vmx| DICT --- USER DEFAULTS
Aug 22 11:49:11.760: vmx| DICT --- HOST DEFAULTS
Aug 22 11:49:11.760: vmx| DICT    vmnet1.hostonlyaddress = 192.168.136.1
Aug 22 11:49:11.760: vmx| DICT    vmnet1.hostonlynetmask = 255.255.255.0
Aug 22 11:49:11.760: vmx| DICT          control.fullpath = /usr/bin/vmware-cmd
Aug 22 11:49:11.760: vmx| DICT             loop.fullpath = /usr/bin/vmware-loop
Aug 22 11:49:11.760: vmx| DICT            dhcpd.fullpath = /usr/bin/vmnet-dhcpd
Aug 22 11:49:11.760: vmx| DICT                    libdir = /usr/lib/vmware
Aug 22 11:49:11.760: vmx| DICT           vmware.fullpath = /usr/bin/vmware
Aug 22 11:49:11.760: vmx| DICT           product.version = 6.0.0
Aug 22 11:49:11.760: vmx| DICT            authd.fullpath = /usr/sbin/vmware-authd
Aug 22 11:49:11.760: vmx| DICT       product.buildnumber = 45731
Aug 22 11:49:11.760: vmx| DICT              product.name = VMware Workstation
Aug 22 11:49:11.760: vmx| DICT --- SITE DEFAULTS
Aug 22 11:49:11.760: vmx| DICT                  tag.help = introduction.htm
Aug 22 11:49:11.760: vmx| DICT   tag.configurationEditor = config_editor_newvm.htm
Aug 22 11:49:11.760: vmx| DICT             tag.ideConfig = devices_virtualdrive.htm
Aug 22 11:49:11.760: vmx| DICT          tag.floppyConfig = devices_floppy.htm
Aug 22 11:49:11.760: vmx| DICT           tag.mouseConfig = devices_mouse.htm
Aug 22 11:49:11.760: vmx| DICT             tag.netConfig = devices_netadapter.htm
Aug 22 11:49:11.760: vmx| DICT        tag.parallelConfig = devices_parallel.htm
Aug 22 11:49:11.760: vmx| DICT          tag.serialConfig = devices_serial.htm
Aug 22 11:49:11.760: vmx| DICT           tag.soundConfig = devices_sound.htm
Aug 22 11:49:11.760: vmx| DICT             tag.memConfig = configvm_memory.htm
Aug 22 11:49:11.760: vmx| DICT            tag.miscConfig = configvm.htm
Aug 22 11:49:11.760: vmx| DICT             tag.usbConfig = devices_usb.htm
Aug 22 11:49:11.760: vmx| DICT         tag.displayConfig = configvm_display-problems.htm
Aug 22 11:49:11.760: vmx| DICT                 tag.tools = vmtools.htm
Aug 22 11:49:11.760: vmx| DICT --- GLOBAL SETTINGS
Aug 22 11:49:11.820: vmx| hostCpuFeatures = 0x4000090
Aug 22 11:49:11.820: vmx| hostNumPerfCounters = 4
Aug 22 11:49:11.823: vmx| guestCpuFeatures = 0x40000b0
Aug 22 11:49:11.830: vmx| WSSCAN: reserved mem (in MB) min=32 max=320 recommended=320
Aug 22 11:49:11.830: vmx|         hostMem=480 maxAllowedAll=-1 maxAllowedVM=8192
Aug 22 11:49:11.830: vmx|         totOverhead=16
Aug 22 11:49:11.830: vmx| WSSCAN: used rec mem (in MB) 320
Aug 22 11:49:11.830: vmx| WSSCAN: Overhead 46141 paged 5674 nonpaged 1280 maxFBSize
Aug 22 11:49:11.830: vmx| WSSCAN 1 1 81920 90096 81920 -1 50 0
Aug 22 11:49:11.832: vmx| LICENSE using: '/home/christian/.vmware/license.ws.6.0.200610' 
Aug 22 11:49:11.852: vmx| LOG failed to remove stats32-2 failed: No such file or directory
Aug 22 11:49:11.852: vmx| LOG failed to remove stats64-2 failed: No such file or directory
Aug 22 11:49:11.861: vmx| vmm32-modules: [vmm.vmm32 .data:0x2b000 .sdata:0x2c000 .statvars:0x2d000 .peer:0x2e000 .shared:0x54000 .bss:0x65000 .rodata:0x6c000 .text:0x77000 .kstatvars:0x3000 ,mmu-pae.vmm32 .rodata:0x75d6c .data:0x2bdb0 .peer:0x52928 .shared:0x639f0 .bss:0x6abc0 .text:0xc996c .comment:0x40000cf0 .statvars:0x2000 .kstatvars:0x2000 .scb:0x400035a0 .shared_meta:0x400034b0 .peer_meta:0x40000ba0 ,sharedmmu-none.vmm32 .text:0xd3834 .comment:0x40000dec ,pv-none.vmm32 .data:0x2bdcc .peer:0x1000 .shared:0x64300 .bss:0x6b120 .text:0xd3850 .comment:0x40000dfe .statvars:0x1000 .kstatvars:0x1000 .shared_meta:0x40003720 ,hv-none.vmm32 .data:0x2bdd0 .peer:0x1000 .shared:0x1000 .bss:0x6b19c .text:0xd3950 .comment:0x40000e46 .statvars:0x1000 .kstatvars:0x1000 ,buslogic-buslogic.vmm32 .shared:0x64448 .bss:0x1000 .text:0xd39b4 .comment:0x40000e58 .scb:0x400036c0 .shared_meta:0x400037b0 ,<MonSrcFile> .rodata:0x75d7c ]
Aug 22 11:49:11.871: vmx| KHZEstimate 1045045
Aug 22 11:49:11.871: vmx| MHZEstimate 1045
Aug 22 11:49:11.871: vmx| NumVCPUs 1
Aug 22 11:49:11.872: vmx| guestCPUID vendor: AuthcAMDenti
Aug 22 11:49:11.872: vmx| guestCPUID level 00000000, 0: 0x00000001 0x68747541 0x444d4163 0x69746e65
Aug 22 11:49:11.872: vmx| guestCPUID level 00000001, 0: 0x000006a0 0x00000000 0x00000000 0x0383fbff
Aug 22 11:49:11.872: vmx| guestCPUID level 80000000, 0: 0x80000008 0x68747541 0x444d4163 0x69746e65
Aug 22 11:49:11.872: vmx| guestCPUID level 80000001, 0: 0x000007a0 0x00000000 0x00000000 0xc1c3fbff
Aug 22 11:49:11.872: vmx| guestCPUID level 80000002, 0: 0x69626f6d 0x4120656c 0x4120444d 0x6f6c6874
Aug 22 11:49:11.872: vmx| guestCPUID level 80000003, 0: 0x6d74286e 0x50582029 0x28204d2d 0x2029564c
Aug 22 11:49:11.872: vmx| guestCPUID level 80000004, 0: 0x30303232 0x0000002b 0x00000000 0x00000000
Aug 22 11:49:11.872: vmx| guestCPUID level 80000005, 0: 0x0408ff08 0xff20ff10 0x40020140 0x40020140
Aug 22 11:49:11.872: vmx| guestCPUID level 80000006, 0: 0x00000000 0x41004100 0x02008140 0x00000000
Aug 22 11:49:11.872: vmx| guestCPUID level 80000007, 0: 0x00000000 0x00000000 0x00000000 0x00000007
Aug 22 11:49:11.872: vmx| guestCPUID level 80000008, 0: 0x00002024 0x00000000 0x00000000 0x00000000
Aug 22 11:49:11.873: vmx| PShare: enabled 1, scanRate 32, checkRate 16
Aug 22 11:49:11.873: vmx| UUID: location-UUID is 56 4d d8 91 79 2e 85 29-55 88 aa b2 0e bb 92 ec
Aug 22 11:49:11.873: vmx| MM: Using partialmap, 40960 pages AC 0 CE 1 TM 0 DOHU 0
Aug 22 11:49:11.873: vmx| UUID: canonical path is /home/christian/vmware/minix3/minix3.vmx
Aug 22 11:49:11.873: vmx| UUID: location-UUID is 56 4d d8 91 79 2e 85 29-55 88 aa b2 0e bb 92 ec
Aug 22 11:49:11.874: vmx| FILE: ScanDirectory discarding file '/home/christian/vmware/minix3/564dd891-792e-8529-5588-aab20ebb92ec.vmem.lck/M06411.lck'; invalid executionID.
Aug 22 11:49:11.874: vmx| MM: using '/home/christian/vmware/minix3/564dd891-792e-8529-5588-aab20ebb92ec.vmem' as a paging file
Aug 22 11:49:11.874: vmx| Msg_Reset:
Aug 22 11:49:11.874: vmx| ----------------------------------------
Aug 22 11:49:11.874: vmx| Opened paging file /home/christian/vmware/minix3/564dd891-792e-8529-5588-aab20ebb92ec.vmem
Aug 22 11:49:11.883: vmx| Mapped mainmem as pageable
Aug 22 11:49:11.884: vmx| MStat: Creating Stat vm.uptime
Aug 22 11:49:11.884: vmx| MStat: Creating Stat vm.suspendTime
Aug 22 11:49:11.884: vmx| MStat: Creating Stat vm.powerOnTimeStamp
Aug 22 11:49:11.903: vmx| VMXVmdb_LoadRawConfig: Loading raw config
Aug 22 11:49:11.908: vmx| DISK: OPEN ide0:0 '/home/christian/vmware/minix3/minix3.vmdk' persistent R[(null)]
Aug 22 11:49:11.909: vmx| FILE: ScanDirectory discarding file '/home/christian/vmware/minix3/minix3.vmdk.lck/M39420.lck'; invalid executionID.
Aug 22 11:49:11.909: vmx| DISKLIB-DSCPTR: Opened [0]: "minix3-flat.vmdk" 0 (0xa)
Aug 22 11:49:11.909: vmx| DISKLIB-LINK  : Opened '/home/christian/vmware/minix3/minix3.vmdk' (0xa): monolithicFlat, 2097152 sectors / 1024 Mb.
Aug 22 11:49:11.909: vmx| DISKLIB-LIB   : Opened "/home/christian/vmware/minix3/minix3.vmdk" (flags 0xa). 0x86c8684
Aug 22 11:49:11.909: vmx| DiskGetGeometry: Reading of disk partition table
Aug 22 11:49:11.910: vmx| DISK: OPEN '/home/christian/vmware/minix3/minix3.vmdk' Geo (2080/16/63) BIOS Geo (0/0/0) freeSpace=7839Mb, ide
Aug 22 11:49:11.910: vmx| Msg_Reset:
Aug 22 11:49:11.910: vmx| ----------------------------------------
Aug 22 11:49:11.910: vmx| TimeTracker host to guest rate conversion 1871081114166 @ 1045045000Hz -> 1871081114166 @ 1045045000Hz
Aug 22 11:49:11.910: vmx| TimeTracker host to guest rate conversion ((x * 2147483648) >> 31) + 0
Aug 22 11:49:11.912: vmx| XINFO X fd is 53
Aug 22 11:49:11.913: vmx| XINFO depth 24 bpp 32 class 4
Aug 22 11:49:11.923: vmx| XINFO WARNING: XF86MISC version 0.9
Aug 22 11:49:11.923: vmx| VT redirected kernel output to /dev/tty1
Aug 22 11:49:11.929: vmx| MKS REMOTE Loading VNC Configuration from VM config file
Aug 22 11:49:11.931: vmx| DISKUTIL: ide0:0 : capacity=2097152
Aug 22 11:49:11.932: vmx| DVGA: Full screen VGA will not be available.
Aug 22 11:49:11.933: vmx| SCSI0: UNTAGGED commands will be converted to ORDER tags.
Aug 22 11:49:11.933: vmx| VLANCE: send cluster threshold is 80, size = 2 recalcInterval is 2 ticks
Aug 22 11:49:11.933: vmx| Ethernet0 MAC Address: 00:0c:29:bb:92:ec
Aug 22 11:49:11.934: vmx| VMXNET: send cluster threshold is 80, size = 2 recalcInterval is 2 ticks, dontClusterSize is 128
Aug 22 11:49:11.934: vmx| E1000: checksum cycles/kB: C=828 asm=373
Aug 22 11:49:11.934: vmx| MStat: Creating Stat vm.heartbeat
Aug 22 11:49:11.935: vmx| DISKUTIL: ide0:0 : toolsVersion = 0
Aug 22 11:49:11.935: vmx| DISKUTIL: Offline toolsVersion = 0
Aug 22 11:49:11.935: vmx| TOOLS INSTALL initializing state to IDLE on power on.
Aug 22 11:49:11.945: vmx| PTSC to VMI Wallclock (nsec) 1871139184928 @ 1045045000Hz -> 1187801351000000000 @ 1000000000Hz
Aug 22 11:49:11.945: vmx| PTSC to VMI Wallclock (nsec) ((x * 4109839572) >> 32) + 1187799560513289171
Aug 22 11:49:11.948: vmx| TOOLS received request in VMX to set option 'enableDnD' -> '1'
Aug 22 11:49:11.948: vmx| TOOLS received request in VMX to set option 'copypaste' -> '1'
Aug 22 11:49:11.977: vmx| VMX_PowerOn: ModuleTable_PowerOn = 1
Aug 22 11:49:11.977: vmx| VMX setting maximum IPC write buffers to 0 packets, 0 bytes
Aug 22 11:49:11.977: mks| Async MKS thread is alive
Aug 22 11:49:11.978: vmx| DnD rpc already set to 1
Aug 22 11:49:11.978: vmx| DnD CopyPasteRegisterRpc already set to 1
Aug 22 11:49:12.008: mks| Connecting to window system.
Aug 22 11:49:12.009: mks| XINFO X fd is 53
Aug 22 11:49:12.009: mks| XINFO depth 24 bpp 32 class 4
Aug 22 11:49:12.016: mks| XINFO WARNING: XF86MISC version 0.9
Aug 22 11:49:12.016: mks| VT redirected kernel output to /dev/tty1
Aug 22 11:49:12.016: mks| rasterops MMXEXT accelerations enabled
Aug 22 11:49:12.016: mks| XINFO unsupported XF86VidMode version: 2.2
Aug 22 11:49:12.017: mks| XINFO XFree86 VidMode 0: 1024x768 flags: 0xa
Aug 22 11:49:12.017: mks| KHBKL: Unable to parse keystring at: ''
Aug 22 11:49:12.436: vcpu-0| guestCpuFeatures = 0x40000b0
Aug 22 11:49:12.437: vcpu-0| Init modules.
Aug 22 11:49:12.445: vcpu-0| CPU reset: hard
Aug 22 11:49:12.453: vmx| VNET: Notification enabled for Ethernet0
Aug 22 11:49:12.454: vmx| CDROM: Using autodetect backend /dev/hdc for ide1:0.
Aug 22 11:49:12.454: vmx| CDROM: Connecting ide1:0 to '/dev/hdc'. img=0 raw=1 excl=0 remote=0
Aug 22 11:49:12.455: vmx| CDROM-LIN:  Implementing mediaChange workaround.
Aug 22 11:49:12.456: vmx| CDROM-LIN:  SEND PACKET API Heuristic active.
Aug 22 11:49:12.456: vmx| CDROM-LIN:  Using SG_IO ioctl for pass-through.
Aug 22 11:49:12.727: vcpu-0| sz=3059680
Aug 22 11:49:12.732: vcpu-0| vmm32 initialized: Releasebuild-45731. cflags: 0x00000000.08000002.50000600.00000002
Aug 22 11:49:12.737: vcpu-0| MonitorInitNumaUnmapVMM32
Aug 22 11:49:13.115: vcpu-0| SVGA: Registering MemSpace at 0xf0000000(0x0) and 0xe8000000(0x0)
Aug 22 11:49:13.124: vcpu-0| SVGA: Unregistering MemSpace at 0xf0000000(0xf0000000) and 0xe8000000(0xe8000000)
Aug 22 11:49:13.159: vcpu-0| SVGA: Registering MemSpace at 0xf0000000(0xf0000000) and 0xe8000000(0xe8000000)
Aug 22 11:49:13.171: vcpu-0| SVGA: Unregistering MemSpace at 0xf0000000(0xf0000000) and 0xe8000000(0xe8000000)
Aug 22 11:49:13.173: vcpu-0| SVGA: Registering IOSpace at 0x1080
Aug 22 11:49:13.173: vcpu-0| SVGA: Registering MemSpace at 0xf0000000(0xf0000000) and 0xe8000000(0xe8000000)
Aug 22 11:49:13.225: mks| Ignoring update request in VGA_Expose (mode change pending).
Aug 22 11:49:13.557: mks| Ignoring update request in VGA_Expose (mode change pending).
Aug 22 11:49:13.689: mks| Ignoring update request in VGA_Expose (mode change pending).
Aug 22 11:49:13.689: mks| Ignoring update request in VGA_Expose (mode change pending).
Aug 22 11:49:13.771: mks| Ignoring update request in VGA_Expose (mode change pending).
Aug 22 11:49:14.818: vcpu-0| VIDE: Curr CHS info cyls: 2080 heads: 16 sects: 63 lba_cap: 2097152
Aug 22 11:49:15.907: vcpu-0| BIOS-UUID is 56 4d d8 91 79 2e 85 29-55 88 aa b2 0e bb 92 ec
Aug 22 11:49:16.161: vcpu-0| DISKUTIL: ide0:0 : toolsVersion = 0
Aug 22 11:49:16.162: vcpu-0| DISKUTIL: Offline toolsVersion = 0
Aug 22 11:49:16.186: mks| Ignoring update request in VGA_Expose (mode change pending).
Aug 22 11:49:19.342: vmx| DISK: DISK/CDROM timeout of 1.946 seconds on ide1:0 (ok)
Aug 22 11:49:19.889: mks| SVGA: Remote display status changed, enabling local optimizations
Aug 22 11:49:22.627: vcpu-0| SVGA: Unregistering IOSpace at 0x1080
Aug 22 11:49:22.627: vcpu-0| SVGA: Registering IOSpace at 0x10f0
Aug 22 11:49:22.627: vcpu-0| SVGA: Unregistering IOSpace at 0x10f0
Aug 22 11:49:22.628: vcpu-0| SVGA: Registering IOSpace at 0xfff0
Aug 22 11:49:22.628: vcpu-0| SVGA: Unregistering IOSpace at 0xfff0
Aug 22 11:49:22.628: vcpu-0| SVGA: Registering IOSpace at 0xfffff0
Aug 22 11:49:22.629: vcpu-0| SVGA: Unregistering IOSpace at 0xfffff0
Aug 22 11:49:22.629: vcpu-0| SVGA: Registering IOSpace at 0xfffffff0
Aug 22 11:49:22.631: vcpu-0| SVGA: Unregistering IOSpace at 0xfffffff0
Aug 22 11:49:22.631: vcpu-0| SVGA: Registering IOSpace at 0xffffff80
Aug 22 11:49:22.632: vcpu-0| SVGA: Unregistering IOSpace at 0xffffff80
Aug 22 11:49:22.632: vcpu-0| SVGA: Registering IOSpace at 0xffff1080
Aug 22 11:49:22.632: vcpu-0| SVGA: Unregistering IOSpace at 0xffff1080
Aug 22 11:49:22.632: vcpu-0| SVGA: Registering IOSpace at 0xff001080
Aug 22 11:49:22.633: vcpu-0| SVGA: Unregistering IOSpace at 0xff001080
Aug 22 11:49:22.633: vcpu-0| SVGA: Registering IOSpace at 0x1080
Aug 22 11:49:22.856: vcpu-0| IOSPACE: 2nd registration for port 0x20a0 (Lance Morph), old 0x82d4020 user, new 8244810 user
Aug 22 11:49:22.856: vcpu-0| IOSPACE: 2nd registration for port 0x2080 (Lance MAC address PROM), old 0x82d4150 user, new 82418c0 user
Aug 22 11:49:22.856: vcpu-0| IOSPACE: 2nd registration for port 0x2081 (Lance MAC address PROM), old 0x82d4150 user, new 82418c0 user
Aug 22 11:49:22.856: vcpu-0| IOSPACE: 2nd registration for port 0x2082 (Lance MAC address PROM), old 0x82d4150 user, new 82418c0 user
Aug 22 11:49:22.856: vcpu-0| IOSPACE: 2nd registration for port 0x2083 (Lance MAC address PROM), old 0x82d4150 user, new 82418c0 user
Aug 22 11:49:22.857: vcpu-0| IOSPACE: 2nd registration for port 0x2084 (Lance MAC address PROM), old 0x82d0640 user, new 82418c0 user
Aug 22 11:49:22.857: vcpu-0| IOSPACE: 2nd registration for port 0x2085 (Lance MAC address PROM), old 0x82d0640 user, new 82418c0 user
Aug 22 11:49:22.857: vcpu-0| IOSPACE: 2nd registration for port 0x2086 (Lance MAC address PROM), old 0x82d0640 user, new 82418c0 user
Aug 22 11:49:22.857: vcpu-0| IOSPACE: 2nd registration for port 0x2087 (Lance MAC address PROM), old 0x82d0640 user, new 82418c0 user
Aug 22 11:49:22.857: vcpu-0| IOSPACE: 2nd registration for port 0x2088 (Lance MAC address PROM), old 0x82d0690 user, new 82418c0 user
Aug 22 11:49:22.857: vcpu-0| IOSPACE: 2nd registration for port 0x2089 (Lance MAC address PROM), old 0x82d0690 user, new 82418c0 user
Aug 22 11:49:22.857: vcpu-0| IOSPACE: 2nd registration for port 0x208a (Lance MAC address PROM), old 0x82d0690 user, new 82418c0 user
Aug 22 11:49:22.857: vcpu-0| IOSPACE: 2nd registration for port 0x208b (Lance MAC address PROM), old 0x82d0690 user, new 82418c0 user
Aug 22 11:49:22.857: vcpu-0| IOSPACE: 2nd registration for port 0x208c (Lance MAC address PROM), old 0x82d06e0 user, new 82418c0 user
Aug 22 11:49:22.857: vcpu-0| IOSPACE: 2nd registration for port 0x208d (Lance MAC address PROM), old 0x82d06e0 user, new 82418c0 user
Aug 22 11:49:22.857: vcpu-0| IOSPACE: 2nd registration for port 0x208e (Lance MAC address PROM), old 0x82d06e0 user, new 82418c0 user
Aug 22 11:49:22.857: vcpu-0| IOSPACE: 2nd registration for port 0x208f (Lance MAC address PROM), old 0x82d06e0 user, new 82418c0 user
Aug 22 11:49:22.857: vcpu-0| IOSPACE: 2nd registration for port 0x2092 (Lance RAP), old 0x82d3250 user, new 82447b0 user
Aug 22 11:49:22.857: vcpu-0| IOSPACE: 2nd registration for port 0x2094 (Lance reset), old 0x82d1f50 user, new 82428d0 user
Aug 22 11:49:22.857: vcpu-0| IOSPACE: 2nd registration for port 0x2096 (Lance BCR), old 0x82d1f50 user, new 8242510 user
Aug 22 11:49:22.857: vcpu-0| IOSPACE: 2nd registration for port 0x2090 (Lance RDP), old 0x895e700, new 0x4b
Aug 22 11:49:22.857: vcpu-0| IOSPACE: Multiple-registered port (0x20a0) being unregistered, leaving callback (0x8244810 user)
Aug 22 11:49:22.857: vcpu-0| IOSPACE: Multiple-registered port (0x2080) being unregistered, leaving callback (0x82418c0 user)
Aug 22 11:49:22.857: vcpu-0| IOSPACE: Multiple-registered port (0x2081) being unregistered, leaving callback (0x82418c0 user)
Aug 22 11:49:22.857: vcpu-0| IOSPACE: Multiple-registered port (0x2082) being unregistered, leaving callback (0x82418c0 user)
Aug 22 11:49:22.858: vcpu-0| IOSPACE: Multiple-registered port (0x2083) being unregistered, leaving callback (0x82418c0 user)
Aug 22 11:49:22.858: vcpu-0| IOSPACE: Multiple-registered port (0x2084) being unregistered, leaving callback (0x82418c0 user)
Aug 22 11:49:22.858: vcpu-0| IOSPACE: Multiple-registered port (0x2085) being unregistered, leaving callback (0x82418c0 user)
Aug 22 11:49:22.858: vcpu-0| IOSPACE: Multiple-registered port (0x2086) being unregistered, leaving callback (0x82418c0 user)
Aug 22 11:49:22.858: vcpu-0| IOSPACE: Multiple-registered port (0x2087) being unregistered, leaving callback (0x82418c0 user)
Aug 22 11:49:22.858: vcpu-0| IOSPACE: Multiple-registered port (0x2088) being unregistered, leaving callback (0x82418c0 user)
Aug 22 11:49:22.858: vcpu-0| IOSPACE: Multiple-registered port (0x2089) being unregistered, leaving callback (0x82418c0 user)
Aug 22 11:49:22.858: vcpu-0| IOSPACE: Multiple-registered port (0x208a) being unregistered, leaving callback (0x82418c0 user)
Aug 22 11:49:22.858: vcpu-0| IOSPACE: Multiple-registered port (0x208b) being unregistered, leaving callback (0x82418c0 user)
Aug 22 11:49:22.858: vcpu-0| IOSPACE: Multiple-registered port (0x208c) being unregistered, leaving callback (0x82418c0 user)
Aug 22 11:49:22.858: vcpu-0| IOSPACE: Multiple-registered port (0x208d) being unregistered, leaving callback (0x82418c0 user)
Aug 22 11:49:22.858: vcpu-0| IOSPACE: Multiple-registered port (0x208e) being unregistered, leaving callback (0x82418c0 user)
Aug 22 11:49:22.858: vcpu-0| IOSPACE: Multiple-registered port (0x208f) being unregistered, leaving callback (0x82418c0 user)
Aug 22 11:49:22.858: vcpu-0| IOSPACE: Multiple-registered port (0x2092) being unregistered, leaving callback (0x82447b0 user)
Aug 22 11:49:22.858: vcpu-0| IOSPACE: Multiple-registered port (0x2090) being unregistered, leaving callback (0x4b mon)
Aug 22 11:49:22.858: vcpu-0| IOSPACE: Multiple-registered port (0x2094) being unregistered, leaving callback (0x82428d0 user)
Aug 22 11:49:22.858: vcpu-0| IOSPACE: Multiple-registered port (0x2096) being unregistered, leaving callback (0x8242510 user)
Aug 22 11:49:22.891: vcpu-0| ASSERT /build/mts/release/bora-45731/bora/vmcore/private/iospace_shared.h:491 bugNr=64440
Aug 22 11:49:22.891: vcpu-0| Backtrace:
Aug 22 11:49:22.891: vcpu-0| Backtrace[0] 0xb5d2be88 eip 0x8053410 
Aug 22 11:49:22.891: vcpu-0| Backtrace[1] 0xb5d2c2b8 eip 0x80f187d 
Aug 22 11:49:22.891: vcpu-0| Backtrace[2] 0xb5d2c308 eip 0x8373f53 
Aug 22 11:49:22.891: vcpu-0| Backtrace[3] 0xb5d2c318 eip 0x82d1a61 
Aug 22 11:49:22.891: vcpu-0| Backtrace[4] 0xb5d2c338 eip 0x8331207 
Aug 22 11:49:22.891: vcpu-0| Backtrace[5] 0xb5d2c358 eip 0x82077ce 
Aug 22 11:49:22.891: vcpu-0| Backtrace[6] 0xb5d2c398 eip 0x8207cb9 
Aug 22 11:49:22.891: vcpu-0| Backtrace[7] 0xb5d2c3b8 eip 0x836da91 
Aug 22 11:49:22.891: vcpu-0| Backtrace[8] 0xb5d2c3d8 eip 0x836de25 
Aug 22 11:49:22.891: vcpu-0| Backtrace[9] 0xb5d2c408 eip 0x837c86b 
Aug 22 11:49:22.891: vcpu-0| Backtrace[10] 0xb5d2c418 eip 0x836ddc1 
Aug 22 11:49:22.891: vcpu-0| Backtrace[11] 0xb5d2c478 eip 0x80b015f 
Aug 22 11:49:22.891: vcpu-0| Backtrace[12] 0xb5d2c4e8 eip 0xb7f1a504 
Aug 22 11:49:22.891: vcpu-0| Backtrace[13] 00000000 eip 0xb7eae51e 
Aug 22 11:49:22.891: vcpu-0| Core dump limit is 0 kb.
Aug 22 11:49:22.892: vcpu-0| Remapping region BusMemFrame13 as MAP_PRIVATE (addr=0xb5502000, size=0x1000, offset=0x72f000)
Aug 22 11:49:22.893: vcpu-0| Cannot remap region PhysRegion13 (addr=(nil), size=0x1000, offset=0x72e000)
Aug 22 11:49:22.893: vcpu-0| Remapping region BusMemFrame12 as MAP_PRIVATE (addr=0xb5504000, size=0x1000, offset=0x72d000)
Aug 22 11:49:22.893: vcpu-0| Remapping region BusMemFrame11 as MAP_PRIVATE (addr=0xb5505000, size=0x1000, offset=0x72c000)
Aug 22 11:49:22.893: vcpu-0| Cannot remap region PhysRegion11 (addr=(nil), size=0x20000, offset=0x70c000)
Aug 22 11:49:22.893: vcpu-0| Cannot remap region DFCR3PTvcpu0 (addr=(nil), size=0x1000, offset=0x70b000)
Aug 22 11:49:22.893: vcpu-0| Cannot remap region DFCR3vcpu0 (addr=(nil), size=0x3000, offset=0x708000)
Aug 22 11:49:22.893: vcpu-0| Cannot remap region DFStackvcpu0 (addr=(nil), size=0x1000, offset=0x707000)
Aug 22 11:49:22.893: vcpu-0| Remapping region BusMemFrame10 as MAP_PRIVATE (addr=0xb652e000, size=0x4000, offset=0x703000)
Aug 22 11:49:22.893: vcpu-0| Remapping region BusMemFrame9 as MAP_PRIVATE (addr=0xb6532000, size=0xa000, offset=0x6f9000)
Aug 22 11:49:22.893: vcpu-0| Remapping region BusMemFrame8 as MAP_PRIVATE (addr=0xb653c000, size=0x1000, offset=0x6f8000)
Aug 22 11:49:22.893: vcpu-0| Cannot remap region PhysRegion8 (addr=(nil), size=0x10000, offset=0x6e8000)
Aug 22 11:49:22.893: vcpu-0| Remapping region BusMemFrame7 as MAP_PRIVATE (addr=0xb654d000, size=0x1000, offset=0x6e7000)
Aug 22 11:49:22.893: vcpu-0| Cannot remap region PhysRegion7 (addr=(nil), size=0x4000, offset=0x6e3000)
Aug 22 11:49:22.893: vcpu-0| Remapping region BusMemFrame6 as MAP_PRIVATE (addr=0xb6552000, size=0x1000, offset=0x6e2000)
Aug 22 11:49:22.893: vcpu-0| Cannot remap region PhysRegion6 (addr=(nil), size=0x8000, offset=0x6da000)
Aug 22 11:49:22.893: vcpu-0| Cannot remap region SVGAFIFO (addr=(nil), size=0x200000, offset=0x4da000)
Aug 22 11:49:22.893: vcpu-0| Cannot remap region VGA (addr=(nil), size=0x40000, offset=0x49a000)
Aug 22 11:49:22.893: vcpu-0| Cannot remap region VIDE_KSEG1 (addr=(nil), size=0x8000, offset=0x492000)
Aug 22 11:49:22.893: vcpu-0| Cannot remap region VIDE_KSEG0 (addr=(nil), size=0x8000, offset=0x48a000)
Aug 22 11:49:22.893: vcpu-0| Remapping region BusMemFrame5 as MAP_PRIVATE (addr=0xb7caa000, size=0x1000, offset=0x489000)
Aug 22 11:49:22.893: vcpu-0| Cannot remap region PhysRegion5 (addr=(nil), size=0x1000, offset=0x488000)
Aug 22 11:49:22.893: vcpu-0| Remapping region BusMemFrame4 as MAP_PRIVATE (addr=0xb7f53000, size=0x1000, offset=0x487000)
Aug 22 11:49:22.893: vcpu-0| Cannot remap region PhysRegion4 (addr=(nil), size=0x80000, offset=0x407000)
Aug 22 11:49:22.893: vcpu-0| Cannot remap region StateLoggerLogBuf (addr=(nil), size=0x200000, offset=0x207000)
Aug 22 11:49:22.894: vcpu-0| Remapping region BusMemFrame3 as MAP_PRIVATE (addr=0xb79ee000, size=0x140000, offset=0xc7000)
Aug 22 11:49:22.894: vcpu-0| Cannot remap region IOSpace (addr=(nil), size=0x2000, offset=0xc5000)
Aug 22 11:49:22.894: vcpu-0| Cannot remap region MonitorOther32 (addr=(nil), size=0x2000, offset=0xc3000)
Aug 22 11:49:22.894: vcpu-0| Remapping region BusMemFrame2 as MAP_PRIVATE (addr=0xb76f4000, size=0x1000, offset=0x2c000)
Aug 22 11:49:22.894: vcpu-0| Cannot remap region APICs (addr=(nil), size=0x1000, offset=0x2b000)
Aug 22 11:49:22.894: vcpu-0| Cannot remap region MonWired (addr=(nil), size=0x13000, offset=0x18000)
Aug 22 11:49:22.894: vcpu-0| Cannot remap region PShareMPN (addr=(nil), size=0x1000, offset=0x17000)
Aug 22 11:49:22.894: vcpu-0| Remapping region BusMemFrame1 as MAP_PRIVATE (addr=0xb77eb000, size=0x1000, offset=0x16000)
Aug 22 11:49:22.894: vcpu-0| Remapping region BusMemFrame0 as MAP_PRIVATE (addr=0xb77ec000, size=0x1000, offset=0x15000)
Aug 22 11:49:22.894: vcpu-0| Cannot remap region PhysRegion0 (addr=(nil), size=0x1000, offset=0x14000)
Aug 22 11:49:22.894: vcpu-0| Remapping region TraceBitmapMainMem as MAP_PRIVATE (addr=0xb77ee000, size=0x2000, offset=0x12000)
Aug 22 11:49:22.894: vcpu-0| Remapping region SharedArea as MAP_PRIVATE (addr=0xb77f0000, size=0x12000, offset=0x0)
Aug 22 11:49:22.894: vcpu-0| Attempting to dump core...
Aug 22 11:49:23.903: vcpu-0| Msg_Post: Error
Aug 22 11:49:23.903: vcpu-0| [msg.log.error.unrecoverable] VMware Workstation unrecoverable error: (vcpu-0)
Aug 22 11:49:23.903: vcpu-0| ASSERT /build/mts/release/bora-45731/bora/vmcore/private/iospace_shared.h:491 bugNr=64440
Aug 22 11:49:23.903: vcpu-0| [msg.panic.haveLog] A log file is available in "/home/christian/vmware/minix3/vmware.log".  [msg.panic.haveCore] A core file is available in "/home/christian/vmware/minix3/core".  [msg.panic.requestSupport.withLogAndCore] Please request support and include the contents of the log file and core file.  [msg.panic.requestSupport.vmSupport] 
Aug 22 11:49:23.903: vcpu-0| To collect files to submit to VMware support, run "vm-support".
Aug 22 11:49:23.903: vcpu-0| [msg.panic.response] We will respond on the basis of your support entitlement.
Aug 22 11:49:23.903: vcpu-0| ----------------------------------------
Aug 22 11:49:34.694: vmx| VTHREAD watched thread 4 "vcpu-0" died
Aug 22 11:49:34.698: mks| VTHREAD watched thread 0 "vmx" died
Aug 22 11:49:34.778: Worker#0| VTHREAD watched thread 0 "vmx" died

[I]**THANKS FOR YOUR TIME AND HELP!!!..**

regards,

Christian.[/I]

---

### Post by DeadGhost on 2007-08-23
Ok, installed vm 6 yesterday, had same problem.

[http://www.ntfs-3g.org/support.html#vmware](http://www.ntfs-3g.org/support.html#vmware)

or

[http://www.vmware.com/community/message.jspa?messageID=708752](http://www.vmware.com/community/message.jspa?messageID=708752)

Check this, hope it helps.

---

### Post by ocake on 2007-08-24
i think i found a workaround:

you need to set

mainMem.useNamedFile = "FALSE"

in your VMs vmx file.

this is because FUSE doesn`t support every type of mmap() system call variants.

---

### Post by blop on 2007-09-17
i'll give it a go!

---

### Post by blop on 2007-10-18
no that did not work....i do not have an entry like that in my VMs *.vmx file

derrrr im stupid!!

i had to add that entry not edit one didnt i!!!!


yea that works a treat!!! thanks!

---

### Post by agibby5 on 2007-12-18
> **ocake said:**
> i think i found a workaround:

you need to set

mainMem.useNamedFile = "FALSE"

in your VMs vmx file.

this is because FUSE doesn`t support every type of mmap() system call variants.



I added that line to my .vmx file and its working now... only I have to resolve a bridged networking error.  Thanks a bunch! :)

---

### Post by k66473 on 2008-05-06
> **ocake said:**
> i think i found a workaround:

you need to set

mainMem.useNamedFile = "FALSE"

in your VMs vmx file.

this is because FUSE doesn`t support every type of mmap() system call variants.
cool, this guide worked very well with me

---

### Post by nazgul42 on 2008-09-23
Works great for me! thanks a lot!

---

