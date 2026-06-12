---
title: "demo version of workstation for 32 bit ubuntu 9.04 did not worked"
date: 2010-08-26
forum: Virtualisation
---

### Post by jamesbon on 2010-08-26
I downloaded demo version of vmware workstation.
With the ISO of Windows XP 
I tried to create the guest OS but after at least one hour I did not see any thing proceeding any where I had to go and kill process vmware.
 
Initially I thought might be ISO is corrupt so I asked a friend of mine to download Vmware demo version and use the Same ISO on his laptop.
This time it did worked and he was able to install Guest OS in it.So that confirmed that ISO was not corrupt.
 
Tell me which log file should I post here.
Host OS is Ubuntu 9.04 
[FONT=Arial][SIZE=2][FONT=Arial][SIZE=2]I have attached logs.Please see if some one can help.[/SIZE][/FONT][/SIZE][/FONT]
[FONT=Arial][SIZE=2]```
[/SIZE][/FONT]
Aug 20 20:09:03.972: vmx| Log for VMware Workstation pid=10584 version=7.1.1 build=build-282343 option=Release
Aug 20 20:09:03.972: vmx| The process is 32-bit.
Aug 20 20:09:03.972: vmx| Host codepage=UTF-8 encoding=UTF-8
Aug 20 20:09:03.972: vmx| Hostname=tapas-laptop
Aug 20 20:09:03.972: vmx| IP=127.0.0.1 (lo)
Aug 20 20:09:03.972: vmx| IP=192.168.1.2 (eth1)
Aug 20 20:09:03.972: vmx| IP=192.168.185.1 (vmnet1)
Aug 20 20:09:03.972: vmx| IP=172.16.159.1 (vmnet8)
Aug 20 20:09:03.972: vmx| IP=192.168.122.1 (virbr0)
Aug 20 20:09:03.972: vmx| Command line: "/usr/lib/vmware/bin/vmware-vmx" "-s" "vmx.stdio.keep=TRUE" "-#" "product=1;name=VMware Workstation;version=7.1.1;buildnumber=282343;licensename=VMware Workstation;licenseversion=7.0;" "-@" "pipe=/tmp/vmware-tapas/vmx47c2f58bc89da48d;readyEvent=96" "/media/disk-1/Windows XP Professional/Windows XP Professional.vmx"
Aug 20 20:09:03.973: vmx| Msg_SetLocale: HostLocale=UTF-8 UserLocale=NULL
Aug 20 20:09:03.974: vmx| Ready event: 96
Aug 20 20:09:04.131: vmx| UI Connecting to pipe '/tmp/vmware-tapas/vmx47c2f58bc89da48d' with user '(null)'
Aug 20 20:09:04.145: vmx| VMXVmdb: Local connection timeout: 60000 ms.
Aug 20 20:09:04.147: vmx| /media/disk-1/Windows XP Professional/Windows XP Professional.vmx: Setup symlink /var/run/vmware/922fbd3a6362f1ce048d105f3206487e -> /var/run/vmware/tapas_1000/1282315143974009_10584
Aug 20 20:09:04.160: vmx| Vix: [10584 mainDispatch.c:374]: VMAutomation: Initializing VMAutomation.
Aug 20 20:09:04.160: vmx| Vix: [10584 mainDispatch.c:397]: VMAutomation: Detected the VM is not managed
Aug 20 20:09:04.161: vmx| Vix: [10584 mainDispatch.c:658]: VMAutomationOpenListenerSocket() listening
Aug 20 20:09:04.177: vmx| Sig_Init already initialized 
Aug 20 20:09:04.191: vmx| Vix: [10584 mainDispatch.c:3661]: VMAutomation_ReportPowerOpFinished: statevar=0, newAppState=1870, success=1
Aug 20 20:09:04.192: vmx| Transitioned vmx/execState/val to poweredOff
Aug 20 20:09:04.192: vmx| Vix: [10584 mainDispatch.c:3661]: VMAutomation_ReportPowerOpFinished: statevar=1, newAppState=1873, success=1
Aug 20 20:09:04.192: vmx| Vix: [10584 mainDispatch.c:3661]: VMAutomation_ReportPowerOpFinished: statevar=2, newAppState=1877, success=1
Aug 20 20:09:04.192: vmx| Vix: [10584 mainDispatch.c:3661]: VMAutomation_ReportPowerOpFinished: statevar=3, newAppState=1881, success=1
Aug 20 20:09:04.206: vmx| UTIL: Change file descriptor limit from soft 1024,hard 1045 to soft 2048,hard 2048.
Aug 20 20:09:04.206: vmx| VMMon_GetkHzEstimate: Calculated 2100000 kHz
Aug 20 20:09:04.207: vmx| TSC kHz estimates: vmmon 2100000, cpuinfo 1200000, cpufreq 2100000.  Using 2100000 kHz
Aug 20 20:09:04.207: vmx| CPU # 0 TSC = 6403183345366
Aug 20 20:09:04.207: vmx| CPU # 1 TSC = 6403183345335
Aug 20 20:09:04.207: vmx| TSC delta 31
Aug 20 20:09:04.207: vmx| CPU # 0 TSC = 6403183562517
Aug 20 20:09:04.207: vmx| CPU # 1 TSC = 6403183562454
Aug 20 20:09:04.207: vmx| TSC delta 63
Aug 20 20:09:04.207: vmx| CPU # 0 TSC = 6403183753764
Aug 20 20:09:04.207: vmx| CPU # 1 TSC = 6403183753732
Aug 20 20:09:04.207: vmx| TSC delta 32
Aug 20 20:09:04.207: vmx| CPU # 0 TSC = 6403183944895
Aug 20 20:09:04.207: vmx| CPU # 1 TSC = 6403183944832
Aug 20 20:09:04.207: vmx| TSC delta 63
Aug 20 20:09:04.207: vmx| TSC min delta 32
Aug 20 20:09:04.207: vmx| PTSC: RefClockToTSC 1000000Hz -> 2100000000Hz
Aug 20 20:09:04.207: vmx| PTSC: RefClockToTSC ((x * 2202009600) >> 20)
Aug 20 20:09:04.207: vmx| PTSC: using TSC
Aug 20 20:09:04.214: vmx| CPUID[0] vendor: GenuineIntel
Aug 20 20:09:04.214: vmx| CPUID[0]   name: Intel(R) Core(TM)2 Duo CPU     T6500  @ 2.10GHz
Aug 20 20:09:04.214: vmx| CPUID[0] level 00000000, 0: 0x0000000d 0x756e6547 0x6c65746e 0x49656e69
Aug 20 20:09:04.214: vmx| CPUID[0] level 00000001, 0: 0x0001067a 0x00020800 0x0c08e39d 0xbfebfbff
Aug 20 20:09:04.214: vmx| CPUID[0] level 00000002, 0: 0x05b0b101 0x005657f0 0x00000000 0x2cb4307d
Aug 20 20:09:04.214: vmx| CPUID[0] level 00000003, 0: 0x00000000 0x00000000 0x00000000 0x00000000
Aug 20 20:09:04.214: vmx| CPUID[0] level 00000004, 0: 0x04000121 0x01c0003f 0x0000003f 0x00000001
Aug 20 20:09:04.214: vmx| CPUID[0] level 00000005, 0: 0x00000040 0x00000040 0x00000003 0x00022220
Aug 20 20:09:04.214: vmx| CPUID[0] level 00000006, 0: 0x00000001 0x00000002 0x00000003 0x00000000
Aug 20 20:09:04.214: vmx| CPUID[0] level 00000007, 0: 0x00000000 0x00000000 0x00000000 0x00000000
Aug 20 20:09:04.214: vmx| CPUID[0] level 00000008, 0: 0x00000400 0x00000000 0x00000000 0x00000000
Aug 20 20:09:04.214: vmx| CPUID[0] level 00000009, 0: 0x00000000 0x00000000 0x00000000 0x00000000
Aug 20 20:09:04.214: vmx| CPUID[0] level 0000000a, 0: 0x07280202 0x00000000 0x00000000 0x00000503
Aug 20 20:09:04.214: vmx| CPUID[0] level 0000000b, 0: 0x00000000 0x00000000 0x00000000 0x00000000
Aug 20 20:09:04.214: vmx| CPUID[0] level 0000000c, 0: 0x00000000 0x00000000 0x00000000 0x00000000
Aug 20 20:09:04.214: vmx| CPUID[0] level 0000000d, 0: 0x00000003 0x00000240 0x00000240 0x00000000
Aug 20 20:09:04.215: vmx| CPUID[0] level 80000000, 0: 0x80000008 0x00000000 0x00000000 0x00000000
Aug 20 20:09:04.215: vmx| CPUID[0] level 80000001, 0: 0x00000000 0x00000000 0x00000001 0x20100000
Aug 20 20:09:04.215: vmx| CPUID[0] level 80000002, 0: 0x65746e49 0x2952286c 0x726f4320 0x4d542865
Aug 20 20:09:04.215: vmx| CPUID[0] level 80000003, 0: 0x44203229 0x43206f75 0x20205550 0x54202020
Aug 20 20:09:04.215: vmx| CPUID[0] level 80000004, 0: 0x30303536 0x20402020 0x30312e32 0x007a4847
Aug 20 20:09:04.215: vmx| CPUID[0] level 80000005, 0: 0x00000000 0x00000000 0x00000000 0x00000000
Aug 20 20:09:04.215: vmx| CPUID[0] level 80000006, 0: 0x00000000 0x00000000 0x08006040 0x00000000
Aug 20 20:09:04.215: vmx| CPUID[0] level 80000007, 0: 0x00000000 0x00000000 0x00000000 0x00000000
Aug 20 20:09:04.215: vmx| CPUID[0] level 80000008, 0: 0x00003024 0x00000000 0x00000000 0x00000000
Aug 20 20:09:04.215: vmx| CPUID[1] vendor: GenuineIntel
Aug 20 20:09:04.215: vmx| CPUID[1]   name: Intel(R) Core(TM)2 Duo CPU     T6500  @ 2.10GHz
Aug 20 20:09:04.215: vmx| CPUID[1] level 00000000, 0: 0x0000000d 0x756e6547 0x6c65746e 0x49656e69
Aug 20 20:09:04.215: vmx| CPUID[1] level 00000001, 0: 0x0001067a 0x01020800 0x0c08e39d 0xbfebfbff
Aug 20 20:09:04.215: vmx| CPUID[1] level 00000002, 0: 0x05b0b101 0x005657f0 0x00000000 0x2cb4307d
Aug 20 20:09:04.215: vmx| CPUID[1] level 00000003, 0: 0x00000000 0x00000000 0x00000000 0x00000000
Aug 20 20:09:04.215: vmx| CPUID[1] level 00000004, 0: 0x04000121 0x01c0003f 0x0000003f 0x00000001
Aug 20 20:09:04.215: vmx| CPUID[1] level 00000005, 0: 0x00000040 0x00000040 0x00000003 0x00022220
Aug 20 20:09:04.215: vmx| CPUID[1] level 00000006, 0: 0x00000001 0x00000002 0x00000003 0x00000000
Aug 20 20:09:04.215: vmx| CPUID[1] level 00000007, 0: 0x00000000 0x00000000 0x00000000 0x00000000
Aug 20 20:09:04.215: vmx| CPUID[1] level 00000008, 0: 0x00000400 0x00000000 0x00000000 0x00000000
Aug 20 20:09:04.215: vmx| CPUID[1] level 00000009, 0: 0x00000000 0x00000000 0x00000000 0x00000000
Aug 20 20:09:04.215: vmx| CPUID[1] level 0000000a, 0: 0x07280202 0x00000000 0x00000000 0x00000503
Aug 20 20:09:04.215: vmx| CPUID[1] level 0000000b, 0: 0x00000000 0x00000000 0x00000000 0x00000000
Aug 20 20:09:04.215: vmx| CPUID[1] level 0000000c, 0: 0x00000000 0x00000000 0x00000000 0x00000000
Aug 20 20:09:04.215: vmx| CPUID[1] level 0000000d, 0: 0x00000003 0x00000240 0x00000240 0x00000000
Aug 20 20:09:04.215: vmx| CPUID[1] level 80000000, 0: 0x80000008 0x00000000 0x00000000 0x00000000
Aug 20 20:09:04.215: vmx| CPUID[1] level 80000001, 0: 0x00000000 0x00000000 0x00000001 0x20100000
Aug 20 20:09:04.215: vmx| CPUID[1] level 80000002, 0: 0x65746e49 0x2952286c 0x726f4320 0x4d542865
Aug 20 20:09:04.215: vmx| CPUID[1] level 80000003, 0: 0x44203229 0x43206f75 0x20205550 0x54202020
Aug 20 20:09:04.215: vmx| CPUID[1] level 80000004, 0: 0x30303536 0x20402020 0x30312e32 0x007a4847
Aug 20 20:09:04.215: vmx| CPUID[1] level 80000005, 0: 0x00000000 0x00000000 0x00000000 0x00000000
Aug 20 20:09:04.215: vmx| CPUID[1] level 80000006, 0: 0x00000000 0x00000000 0x08006040 0x00000000
Aug 20 20:09:04.215: vmx| CPUID[1] level 80000007, 0: 0x00000000 0x00000000 0x00000000 0x00000000
Aug 20 20:09:04.215: vmx| CPUID[1] level 80000008, 0: 0x00003024 0x00000000 0x00000000 0x00000000
Aug 20 20:09:04.215: vmx| hostCPUID vendor: GenuineIntel
Aug 20 20:09:04.215: vmx| hostCPUID   name: Intel(R) Core(TM)2 Duo CPU     T6500  @ 2.10GHz
Aug 20 20:09:04.215: vmx| hostCPUID level 00000000, 0: 0x0000000d 0x756e6547 0x6c65746e 0x49656e69
Aug 20 20:09:04.215: vmx| hostCPUID level 00000001, 0: 0x0001067a 0x00020800 0x0c08e39d 0xbfebfbff
Aug 20 20:09:04.215: vmx| hostCPUID level 00000002, 0: 0x05b0b101 0x005657f0 0x00000000 0x2cb4307d
Aug 20 20:09:04.215: vmx| hostCPUID level 00000003, 0: 0x00000000 0x00000000 0x00000000 0x00000000
Aug 20 20:09:04.215: vmx| hostCPUID level 00000004, 0: 0x04000121 0x01c0003f 0x0000003f 0x00000001
Aug 20 20:09:04.215: vmx| hostCPUID level 00000005, 0: 0x00000040 0x00000040 0x00000003 0x00022220
Aug 20 20:09:04.216: vmx| hostCPUID level 00000006, 0: 0x00000001 0x00000002 0x00000003 0x00000000
Aug 20 20:09:04.216: vmx| hostCPUID level 00000007, 0: 0x00000000 0x00000000 0x00000000 0x00000000
Aug 20 20:09:04.216: vmx| hostCPUID level 00000008, 0: 0x00000400 0x00000000 0x00000000 0x00000000
Aug 20 20:09:04.216: vmx| hostCPUID level 00000009, 0: 0x00000000 0x00000000 0x00000000 0x00000000
Aug 20 20:09:04.216: vmx| hostCPUID level 0000000a, 0: 0x07280202 0x00000000 0x00000000 0x00000503
Aug 20 20:09:04.216: vmx| hostCPUID level 0000000b, 0: 0x00000000 0x00000000 0x00000000 0x00000000
Aug 20 20:09:04.216: vmx| hostCPUID level 0000000c, 0: 0x00000000 0x00000000 0x00000000 0x00000000
Aug 20 20:09:04.216: vmx| hostCPUID level 0000000d, 0: 0x00000003 0x00000240 0x00000240 0x00000000
Aug 20 20:09:04.216: vmx| hostCPUID level 80000000, 0: 0x80000008 0x00000000 0x00000000 0x00000000
Aug 20 20:09:04.216: vmx| hostCPUID level 80000001, 0: 0x00000000 0x00000000 0x00000001 0x20100000
Aug 20 20:09:04.216: vmx| hostCPUID level 80000002, 0: 0x65746e49 0x2952286c 0x726f4320 0x4d542865
Aug 20 20:09:04.216: vmx| hostCPUID level 80000003, 0: 0x44203229 0x43206f75 0x20205550 0x54202020
Aug 20 20:09:04.216: vmx| hostCPUID level 80000004, 0: 0x30303536 0x20402020 0x30312e32 0x007a4847
Aug 20 20:09:04.216: vmx| hostCPUID level 80000005, 0: 0x00000000 0x00000000 0x00000000 0x00000000
Aug 20 20:09:04.216: vmx| hostCPUID level 80000006, 0: 0x00000000 0x00000000 0x08006040 0x00000000
Aug 20 20:09:04.216: vmx| hostCPUID level 80000007, 0: 0x00000000 0x00000000 0x00000000 0x00000000
Aug 20 20:09:04.216: vmx| hostCPUID level 80000008, 0: 0x00003024 0x00000000 0x00000000 0x00000000
Aug 20 20:09:04.216: vmx| CPUID Maximum Physical Address Bits supported across all CPUs: 36
Aug 20 20:09:04.290: vmx| Host ACPI: can't find SRAT
Aug 20 20:09:04.290: vmx| Host: SRAT tables not found in memory
Aug 20 20:09:04.408: vmx| ConfigCheck: No rules file found. Checks are disabled.
Aug 20 20:09:04.408: vmx| changing directory to /media/disk-1/Windows XP Professional/.
Aug 20 20:09:04.408: vmx| Config file: /media/disk-1/Windows XP Professional/Windows XP Professional.vmx
Aug 20 20:09:04.412: vmx| Vix: [10584 mainDispatch.c:3661]: VMAutomation_ReportPowerOpFinished: statevar=1, newAppState=1873, success=1
Aug 20 20:09:04.412: vmx| Vix: [10584 mainDispatch.c:3661]: VMAutomation_ReportPowerOpFinished: statevar=2, newAppState=1878, success=1
Aug 20 20:09:04.465: vmx| VMXVmdb_LoadRawConfig: Loading raw config
Aug 20 20:09:04.565: vmx| VMXVmdbCbVmVmxExecState: Exec state change requested to state poweredOn without reset, hard, softOptionTimeout: 0.
Aug 20 20:09:04.565: vmx| PowerOn
Aug 20 20:09:04.565: vmx| VMX_PowerOn: VMX build 282343, UI build 282343
Aug 20 20:09:04.567: vmx| Host ACPI: can't find SRAT
Aug 20 20:09:04.567: vmx| Host: SRAT tables not found in memory
Aug 20 20:09:04.580: vmx| VMXVmdb_LoadRawConfig: Loading raw config
Aug 20 20:09:04.584: vmx| Vix: [10584 mainDispatch.c:3661]: VMAutomation_ReportPowerOpFinished: statevar=0, newAppState=1871, success=1
Aug 20 20:09:04.584: vmx| HOST sysname Linux, nodename tapas-laptop, release 2.6.28-11-generic, version #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009, machine i686, SMP, hz=250
Aug 20 20:09:04.584: vmx| DICT --- USER PREFERENCES /home/tapas/.vmware/preferences 
Aug 20 20:09:04.584: vmx| DICT       pref.grabOnKeyPress = FALSE
Aug 20 20:09:04.584: vmx| DICT       pref.eula.0.appName = VMware Workstation
Aug 20 20:09:04.584: vmx| DICT   pref.eula.0.buildNumber = 282343
Aug 20 20:09:04.584: vmx| DICT     pref.trayicon.enabled = true
Aug 20 20:09:04.584: vmx| DICT       pref.usbDev.maxDevs = 0
Aug 20 20:09:04.585: vmx| DICT pref.keyboardAndMouse.maxProfiles = 0
Aug 20 20:09:04.585: vmx| DICT pref.ws.openedObj0.present = TRUE
Aug 20 20:09:04.585: vmx| DICT   pref.ws.openedObj0.dest = /host2/#_client/
Aug 20 20:09:04.585: vmx| DICT  pref.ws.openedObj.maxNum = 2
Aug 20 20:09:04.585: vmx| DICT vmWizard.installMediaType = iso
Aug 20 20:09:04.585: vmx| DICT         vmWizard.guestKey = winxppro
Aug 20 20:09:04.585: vmx| DICT vmWizard.mruISO0.isoLocation = /media/disk/Softwares/WinXP/windows.iso
Aug 20 20:09:04.585: vmx| DICT pref.ws.openedObj1.present = TRUE
Aug 20 20:09:04.585: vmx| DICT   pref.ws.openedObj1.type = vm
Aug 20 20:09:04.585: vmx| DICT   pref.ws.openedObj1.path = /vm/#47c2f58bc89da48d/
Aug 20 20:09:04.585: vmx| DICT   pref.ws.openedObj1.file = /media/disk-1/Windows XP Professional/Windows XP Professional.vmx
Aug 20 20:09:04.585: vmx| DICT   pref.ws.openedObj1.dest = /host2/#_client/
Aug 20 20:09:04.586: vmx| DICT       pref.license.maxNum = 1
Aug 20 20:09:04.586: vmx| DICT     pref.license0.version = 7.0
Aug 20 20:09:04.586: vmx| DICT pref.license0.lastEvalReminder = 30
Aug 20 20:09:04.586: vmx| DICT --- USER DEFAULTS /home/tapas/.vmware/config 
Aug 20 20:09:04.586: vmx| DICT --- HOST DEFAULTS /etc/vmware/config 
Aug 20 20:09:04.586: vmx| DICT           vmware.fullpath = /usr/bin/vmware
Aug 20 20:09:04.586: vmx| DICT                vix.libdir = /usr/lib/vmware-vix
Aug 20 20:09:04.586: vmx| DICT                NETWORKING = yes
Aug 20 20:09:04.586: vmx| DICT installerDefaults.dataCollectionEnabled = yes
Aug 20 20:09:04.586: vmx| DICT            VMBLOCK_CONFED = yes
Aug 20 20:09:04.586: vmx| DICT           gksu.rootMethod = su
Aug 20 20:09:04.587: vmx| DICT                    libdir = /usr/lib/vmware
Aug 20 20:09:04.587: vmx| DICT               VMCI_CONFED = yes
Aug 20 20:09:04.587: vmx| DICT        vix.config.version = 1
Aug 20 20:09:04.587: vmx| DICT              VSOCK_CONFED = yes
Aug 20 20:09:04.587: vmx| DICT             initscriptdir = /etc/init.d
Aug 20 20:09:04.587: vmx| DICT installerDefaults.componentDownloadEnabled = yes
Aug 20 20:09:04.587: vmx| DICT    player.product.version = 3.1.1
Aug 20 20:09:04.587: vmx| DICT installerDefaults.transferVersion = 1
Aug 20 20:09:04.587: vmx| DICT installerDefaults.autoSoftwareUpdateEnabled = no
Aug 20 20:09:04.587: vmx| DICT            authd.fullpath = /usr/sbin/vmware-authd
Aug 20 20:09:04.587: vmx| DICT                    bindir = /usr/bin
Aug 20 20:09:04.587: vmx| DICT       product.buildNumber = 282343
Aug 20 20:09:04.588: vmx| DICT           product.version = 7.1.1
Aug 20 20:09:04.588: vmx| DICT workstation.product.version = 7.1.1
Aug 20 20:09:04.588: vmx| DICT              product.name = VMware Workstation
Aug 20 20:09:04.588: vmx| DICT --- SITE DEFAULTS /usr/lib/vmware/config 
Aug 20 20:09:04.588: vmx| DICT                  tag.help = introduction.htm
Aug 20 20:09:04.588: vmx| DICT   tag.configurationEditor = config_editor_newvm.htm
Aug 20 20:09:04.588: vmx| DICT             tag.ideConfig = devices_virtualdrive.htm
Aug 20 20:09:04.588: vmx| DICT          tag.floppyConfig = devices_floppy.htm
Aug 20 20:09:04.588: vmx| DICT           tag.mouseConfig = devices_mouse.htm
Aug 20 20:09:04.588: vmx| DICT             tag.netConfig = devices_netadapter.htm
Aug 20 20:09:04.588: vmx| DICT        tag.parallelConfig = devices_parallel.htm
Aug 20 20:09:04.589: vmx| DICT          tag.serialConfig = devices_serial.htm
Aug 20 20:09:04.589: vmx| DICT           tag.soundConfig = devices_sound.htm
Aug 20 20:09:04.589: vmx| DICT             tag.memConfig = configvm_memory.htm
Aug 20 20:09:04.589: vmx| DICT            tag.miscConfig = configvm.htm
Aug 20 20:09:04.589: vmx| DICT             tag.usbConfig = devices_usb.htm
Aug 20 20:09:04.589: vmx| DICT         tag.displayConfig = configvm_display-problems.htm
Aug 20 20:09:04.589: vmx| DICT                 tag.tools = vmtools.htm
Aug 20 20:09:04.589: vmx| DICT --- COMMAND LINE
Aug 20 20:09:04.589: vmx| DICT            vmx.stdio.keep = TRUE
Aug 20 20:09:04.589: vmx| DICT             gui.available = TRUE
Aug 20 20:09:04.590: vmx| DICT --- CONFIGURATION /media/disk-1/Windows XP Professional/Windows XP Professional.vmx 
Aug 20 20:09:04.590: vmx| DICT            config.version = 8
Aug 20 20:09:04.590: vmx| DICT         virtualHW.version = 7
Aug 20 20:09:04.590: vmx| DICT             scsi0.present = TRUE
Aug 20 20:09:04.590: vmx| DICT                   memsize = 1024
Aug 20 20:09:04.590: vmx| DICT           scsi0:0.present = TRUE
Aug 20 20:09:04.590: vmx| DICT          scsi0:0.fileName = Windows XP Professional.vmdk
Aug 20 20:09:04.590: vmx| DICT            ide1:0.present = TRUE
Aug 20 20:09:04.590: vmx| DICT           ide1:0.fileName = /media/disk/Softwares/WinXP/windows.iso
Aug 20 20:09:04.590: vmx| DICT         ide1:0.deviceType = cdrom-image
Aug 20 20:09:04.590: vmx| DICT          floppy0.fileType = file
Aug 20 20:09:04.591: vmx| DICT          floppy0.fileName = autoinst.flp
Aug 20 20:09:04.591: vmx| DICT      floppy0.clientDevice = FALSE
Aug 20 20:09:04.591: vmx| DICT         ethernet0.present = TRUE
Aug 20 20:09:04.591: vmx| DICT  ethernet0.connectionType = nat
Aug 20 20:09:04.591: vmx| DICT   ethernet0.wakeOnPcktRcv = FALSE
Aug 20 20:09:04.591: vmx| DICT     ethernet0.addressType = generated
Aug 20 20:09:04.591: vmx| DICT               usb.present = TRUE
Aug 20 20:09:04.591: vmx| DICT              ehci.present = TRUE
Aug 20 20:09:04.591: vmx| DICT             sound.present = TRUE
Aug 20 20:09:04.591: vmx| DICT            sound.fileName = -1
Aug 20 20:09:04.591: vmx| DICT          sound.autodetect = TRUE
Aug 20 20:09:04.591: vmx| DICT              mks.enable3d = TRUE
Aug 20 20:09:04.592: vmx| DICT           serial0.present = TRUE
Aug 20 20:09:04.592: vmx| DICT          serial0.fileType = thinprint
Aug 20 20:09:04.592: vmx| DICT        pciBridge0.present = TRUE
Aug 20 20:09:04.592: vmx| DICT        pciBridge4.present = TRUE
Aug 20 20:09:04.592: vmx| DICT     pciBridge4.virtualDev = pcieRootPort
Aug 20 20:09:04.592: vmx| DICT      pciBridge4.functions = 8
Aug 20 20:09:04.592: vmx| DICT        pciBridge5.present = TRUE
Aug 20 20:09:04.592: vmx| DICT     pciBridge5.virtualDev = pcieRootPort
Aug 20 20:09:04.592: vmx| DICT      pciBridge5.functions = 8
Aug 20 20:09:04.592: vmx| DICT        pciBridge6.present = TRUE
Aug 20 20:09:04.592: vmx| DICT     pciBridge6.virtualDev = pcieRootPort
Aug 20 20:09:04.593: vmx| DICT      pciBridge6.functions = 8
Aug 20 20:09:04.593: vmx| DICT        pciBridge7.present = TRUE
Aug 20 20:09:04.593: vmx| DICT     pciBridge7.virtualDev = pcieRootPort
Aug 20 20:09:04.593: vmx| DICT      pciBridge7.functions = 8
Aug 20 20:09:04.593: vmx| DICT             vmci0.present = TRUE
Aug 20 20:09:04.593: vmx| DICT         buslogic.noDriver = FALSE
Aug 20 20:09:04.593: vmx| DICT    roamingVM.exitBehavior = go
Aug 20 20:09:04.593: vmx| DICT               displayName = Windows XP Professional
Aug 20 20:09:04.593: vmx| DICT                   guestOS = winxppro
Aug 20 20:09:04.593: vmx| DICT                     nvram = Windows XP Professional.nvram
Aug 20 20:09:04.593: vmx| DICT virtualHW.productCompatibility = hosted
Aug 20 20:09:04.593: vmx| DICT          printers.enabled = TRUE
Aug 20 20:09:04.594: vmx| DICT    easyInstall.keepFloppy = TRUE
Aug 20 20:09:04.594: vmx| DICT        extendedConfigFile = Windows XP Professional.vmxf
Aug 20 20:09:04.594: vmx| DICT --- USER DEFAULTS ~/.vmware/config 
Aug 20 20:09:04.594: vmx| DICT --- HOST DEFAULTS /etc/vmware/config 
Aug 20 20:09:04.594: vmx| DICT           vmware.fullpath = /usr/bin/vmware
Aug 20 20:09:04.594: vmx| DICT                vix.libdir = /usr/lib/vmware-vix
Aug 20 20:09:04.594: vmx| DICT                NETWORKING = yes
Aug 20 20:09:04.594: vmx| DICT installerDefaults.dataCollectionEnabled = yes
Aug 20 20:09:04.594: vmx| DICT            VMBLOCK_CONFED = yes
Aug 20 20:09:04.594: vmx| DICT           gksu.rootMethod = su
Aug 20 20:09:04.595: vmx| DICT                    libdir = /usr/lib/vmware
Aug 20 20:09:04.595: vmx| DICT               VMCI_CONFED = yes
Aug 20 20:09:04.595: vmx| DICT        vix.config.version = 1
Aug 20 20:09:04.595: vmx| DICT              VSOCK_CONFED = yes
Aug 20 20:09:04.595: vmx| DICT             initscriptdir = /etc/init.d
Aug 20 20:09:04.595: vmx| DICT installerDefaults.componentDownloadEnabled = yes
Aug 20 20:09:04.595: vmx| DICT    player.product.version = 3.1.1
Aug 20 20:09:04.595: vmx| DICT installerDefaults.transferVersion = 1
Aug 20 20:09:04.595: vmx| DICT installerDefaults.autoSoftwareUpdateEnabled = no
Aug 20 20:09:04.595: vmx| DICT            authd.fullpath = /usr/sbin/vmware-authd
Aug 20 20:09:04.595: vmx| DICT                    bindir = /usr/bin
Aug 20 20:09:04.595: vmx| DICT       product.buildNumber = 282343
Aug 20 20:09:04.596: vmx| DICT           product.version = 7.1.1
Aug 20 20:09:04.596: vmx| DICT workstation.product.version = 7.1.1
Aug 20 20:09:04.596: vmx| DICT              product.name = VMware Workstation
Aug 20 20:09:04.596: vmx| DICT --- SITE DEFAULTS /usr/lib/vmware/config 
Aug 20 20:09:04.596: vmx| DICT                  tag.help = introduction.htm
Aug 20 20:09:04.596: vmx| DICT   tag.configurationEditor = config_editor_newvm.htm
Aug 20 20:09:04.596: vmx| DICT             tag.ideConfig = devices_virtualdrive.htm
Aug 20 20:09:04.596: vmx| DICT          tag.floppyConfig = devices_floppy.htm
Aug 20 20:09:04.596: vmx| DICT           tag.mouseConfig = devices_mouse.htm
Aug 20 20:09:04.596: vmx| DICT             tag.netConfig = devices_netadapter.htm
Aug 20 20:09:04.596: vmx| DICT        tag.parallelConfig = devices_parallel.htm
Aug 20 20:09:04.597: vmx| DICT          tag.serialConfig = devices_serial.htm
Aug 20 20:09:04.597: vmx| DICT           tag.soundConfig = devices_sound.htm
Aug 20 20:09:04.597: vmx| DICT             tag.memConfig = configvm_memory.htm
Aug 20 20:09:04.597: vmx| DICT            tag.miscConfig = configvm.htm
Aug 20 20:09:04.597: vmx| DICT             tag.usbConfig = devices_usb.htm
Aug 20 20:09:04.597: vmx| DICT         tag.displayConfig = configvm_display-problems.htm
Aug 20 20:09:04.597: vmx| DICT                 tag.tools = vmtools.htm
Aug 20 20:09:04.597: vmx| DICT --- GLOBAL SETTINGS /usr/lib/vmware/settings 
Aug 20 20:09:04.599: vmx| Vix: [10584 mainDispatch.c:3661]: VMAutomation_ReportPowerOpFinished: statevar=1, newAppState=1873, success=1
Aug 20 20:09:04.607: vmx| VMXVmdb_LoadRawConfig: Loading raw config
Aug 20 20:09:04.611: vmx| hostCpuFeatures = 0x406001fc
Aug 20 20:09:04.611: vmx| hostNumPerfCounters = 2
Aug 20 20:09:04.611: vmx| CPU0: PMC: bad VMENTRY_CTL_LOAD_CPGC or VMEXIT_CTL_LOAD_CPGC
Aug 20 20:09:04.611: vmx| PMC: Patch Level 0xa07, smmFrz (hw): (1)
Aug 20 20:09:04.611: vmx| PMC: IA32, Penryn [c:0 f:1 e:0]
Aug 20 20:09:04.611: vmx| CPU1: PMC: bad VMENTRY_CTL_LOAD_CPGC or VMEXIT_CTL_LOAD_CPGC
Aug 20 20:09:04.612: vmx| PMC: Patch Level 0xa07, smmFrz (hw): (1)
Aug 20 20:09:04.612: vmx| PMC: IA32, Penryn [c:0 f:1 e:0]
Aug 20 20:09:04.612: vmx| MONITOR MODE: allowed modes          : BT
Aug 20 20:09:04.612: vmx| MONITOR MODE: user requested modes   : BT HV HWMMU
Aug 20 20:09:04.612: vmx| MONITOR MODE: guestOS preferred modes: BT HWMMU HV
Aug 20 20:09:04.612: vmx| MONITOR MODE: filtered list          : BT
Aug 20 20:09:04.612: vmx| HV Settings: virtual exec = 'software'; virtual mmu = 'software'
Aug 20 20:09:04.749: vmx| XINFO X fd is 73
Aug 20 20:09:04.749: vmx| XINFO depth 24 bpp 32 class 4
Aug 20 20:09:04.754: vmx| Host display topology 1366x768.
Aug 20 20:09:04.754: vmx| SVGA: Max size 2560x1600
Aug 20 20:09:04.754: vmx| WSSCAN: reserved mem (in MB) min=32 max=2912 recommended=2912
Aug 20 20:09:04.755: vmx| WSSCAN: used rec mem (in MB) 2912
Aug 20 20:09:04.755: vmx| PShare: enabled 1 adaptive 1 local 1 scanRate [16, 400]
Aug 20 20:09:04.755: vmx| WSSCAN: 296513 9409 262144 32768
Aug 20 20:09:04.755: vmx| WSSCAN 1 0 709874 718066 745472 -1 50 0
Aug 20 20:09:04.755: vmx| Host: Disabling thread priority boosting to work around Linux SMP bug.
Aug 20 20:09:04.756: vmx| MXSemaphoreInitFromPipe: eventfd usage: Enabled
Aug 20 20:09:04.757: vmx| LICENSE using: '/usr/lib/vmware/licenses/user/license-ws-70-e1-200904' 
Aug 20 20:09:04.773: vmx| Host IPI vectors: 0xfb 0xfa
Aug 20 20:09:04.773: vmx| Monitor_PowerOn: HostedVSMP skew tracking is disabled
Aug 20 20:09:04.773: vmx| Monitor_PowerOn: HostedVSMP crosscall yielding is disabled
Aug 20 20:09:04.774: vmx| vmm32-modules: [vmm.vmm32 .data:0x2b000-0x700 .sdata:0x2c000-0x4e4 .statvars:0x2d000-0x3a0 .peer:0x2e000-0x26200 .shared:0x5a000-0x143c0 .bss:0x6f000-0x5de8 .rodata:0x76000-0xb740 .text:0x82000-0x5c63d .kstatvars:0x3000-0x0, mmu-nohv.vmm32 .rodata:0x81740-0x44 .data:0x2b700-0x10 .peer:0x54200-0x5640 .shared:0x6e3c0-0x340 .bss:0x74e00-0x51c .text:0xde640-0xa4e3 .comment:0x40000d5c-0x10e .statvars:0x2000-0x0 .kstatvars:0x2000-0x0 .scb:0x40003cc0-0x180 .shared_meta:0x400042f0-0x330 .peer_meta:0x40000f90-0x1e0 .patchtext:0x40000500-0xb0, pv-none.vmm32 .shared:0x6e700-0x180 .bss:0x75320-0x84 .text:0xe8b24-0xe2 .comment:0x40000e6a-0x48 .shared_meta:0x40004620-0x90, vprobe-none.vmm32 .text:0xe8c08-0x19 .comment:0x40000eb2-0x12, hv-none.vmm32 .rodata:0x81784-0x4 .data:0x1000-0x0 .peer:0x1000-0x0 .shared:0x1000-0x0 .bss:0x1000-0x0 .text:0xe8c24-0x11 .comment:0x40000ec4-0x12 .statvars:0x1000-0x0 .kstatvars:0x1000-0x0, gphys-sw.vmm32 .peer:0x59840-0x40 .shared:0x6e880-0x80 .bss:0x2000-0x0 .text:0xe8c40-0x7d1 .comment:0x40000ed6-0x12 .scb:0x40003e40-0x60 .shared_meta:0x400046b0-0x240 .peer_meta:0x40001170-0x30, vassert-none.vmm32 .text:0xe9414-0x39 .comment:0x40000ee8-0x12, vmsafe-none.vmm32 .text:0xe9450-0x1b .comment:0x40000efa-0x12, buslogic-buslogic.vmm32 .shared:0x6e900-0x40 .bss:0x1000-0x0 .text:0xe9470-0xe9 .comment:0x40000f0c-0x12 .scb:0x40003ea0-0x60 .shared_meta:0x400048f0-0x60, {SharedAreaReservations} .shared:0x6e940-0x40, <MonSrcFile> .rodata:0x81788-0x3ee]
Aug 20 20:09:04.777: vmx| KHZEstimate 2100000
Aug 20 20:09:04.777: vmx| MHZEstimate 2100
Aug 20 20:09:04.777: vmx| NumVCPUs 1
Aug 20 20:09:04.777: vmx| PShare: checkRate 16
Aug 20 20:09:04.778: vmx| UUID: SMBIOS UUID is reported as '44 45 4c 4c 54 00 10 32-80 52 ca c0 4f 33 42 53'.
Aug 20 20:09:04.778: vmx| UUID: location-UUID is 56 4d eb d5 e8 72 83 5f-07 36 3b 58 1e a6 25 c9
Aug 20 20:09:04.778: vmx| UUID: location-UUID is 56 4d eb d5 e8 72 83 5f-07 36 3b 58 1e a6 25 c9
Aug 20 20:09:04.778: vmx| UUID: Writing uuid.bios value: '56 4d eb d5 e8 72 83 5f-07 36 3b 58 1e a6 25 c9'
Aug 20 20:09:04.778: vmx| UUID: Writing uuid.location value: '56 4d eb d5 e8 72 83 5f-07 36 3b 58 1e a6 25 c9'
Aug 20 20:09:04.779: vmx| AIOGNRC: numThreads=18 ide=0, scsi=1, passthru=1
Aug 20 20:09:04.779: vmx| WORKER: Creating new group with numThreads=18 (18)
Aug 20 20:09:04.790: vmx| Replay State = 0
Aug 20 20:09:04.790: vmx| minDEThreshold: 76
Aug 20 20:09:04.791: vmx| MM: Using partialmap, 262144 pages AC 0 CE 1 TM 0 DOHU 0
Aug 20 20:09:04.814: vmx| MMC: Initialized PLS=1 PLR=0 PFS=0 TS=1 BS=1 WZ=0 BufM=576 LOR=0 SOR=1 BlkP=32 W=50 PF=1024
Aug 20 20:09:04.815: vmx| UUID: location-UUID is 56 4d eb d5 e8 72 83 5f-07 36 3b 58 1e a6 25 c9
Aug 20 20:09:04.820: vmx| MM: Opened paging file, '/media/disk-1/Windows XP Professional/564debd5-e872-835f-0736-3b581ea625c9.vmem'.
Aug 20 20:09:04.824: vmx| MStat: Creating Stat vm.uptime
Aug 20 20:09:04.824: vmx| MStat: Creating Stat vm.suspendTime
Aug 20 20:09:04.824: vmx| MStat: Creating Stat vm.powerOnTimeStamp
Aug 20 20:09:04.824: vmx| VMXAIOMGR: Using: simple=Generic unbuf=Generic
Aug 20 20:09:04.835: vmx| VMXVmdb_LoadRawConfig: Loading raw config
Aug 20 20:09:04.839: vmx| DISK: OPEN scsi0:0 '/media/disk-1/Windows XP Professional/Windows XP Professional.vmdk' persistent R[]
Aug 20 20:09:04.859: vmx| DISKLIB-DSCPTR: Opened [0]: "Windows XP Professional.vmdk" (0x1a)
Aug 20 20:09:04.859: vmx| DISKLIB-LINK  : Opened '/media/disk-1/Windows XP Professional/Windows XP Professional.vmdk' (0x1a): monolithicSparse, 16777216 sectors / 8 GB.
Aug 20 20:09:04.859: vmx| DISKLIB-LIB   : Opened "/media/disk-1/Windows XP Professional/Windows XP Professional.vmdk" (flags 0x1a).
Aug 20 20:09:04.860: vmx| DiskGetGeometry: Reading of disk partition table
Aug 20 20:09:04.861: vmx| Setting thread 36 stack size to 1048576.
Aug 20 20:09:04.861: vmx| DISK: OPEN '/media/disk-1/Windows XP Professional/Windows XP Professional.vmdk' Geo (1174/255/56) BIOS Geo (0/0/0)
Aug 20 20:09:04.862: vmx| TimeTracker host to guest rate conversion 6404494375713 @ 2100000000Hz -> 6404494375713 @ 2100000000Hz
Aug 20 20:09:04.862: vmx| TimeTracker host to guest rate conversion ((x * 2147483648) >> 31) + 0
Aug 20 20:09:04.863: vmx| USB: Initializing 'Generic' backend
Aug 20 20:09:04.863: vmx| USB: Unable to open "/proc/bus/usb/devices" (No such file or directory).
Aug 20 20:09:04.864: vmx| USB: Initializing 'Virtual Hub' backend
Aug 20 20:09:04.864: vmx| USB: Initializing 'Virtual Mouse' backend
Aug 20 20:09:04.864: vmx| USB: Initializing 'Virtual Keyboard' backend
Aug 20 20:09:04.864: vmx| USB: Initializing 'Virtual Mass Storage' backend
Aug 20 20:09:04.864: vmx| USB: Initializing 'Virtual CCID' backend
Aug 20 20:09:04.865: vmx| USB-CCID:  dlopened default libpcsclite.so.1.
Aug 20 20:09:04.865: vmx| USB-CCID: Could not establish resource manager context for card ops: SCARD_E_NO_SERVICE(0x8010001d).
Aug 20 20:09:04.865: vmx| USB: Unable to initialize 'Virtual CCID' backend
Aug 20 20:09:04.879: vmx| XINFO X fd is 73
Aug 20 20:09:04.879: vmx| XINFO depth 24 bpp 32 class 4
Aug 20 20:09:04.884: vmx| DisplayTopologyInit: using the XRandR backend.
Aug 20 20:09:04.961: vmx| GLPrimary_Alloc, thread vmx
Aug 20 20:09:04.965: vmx| WORKER: Creating new group with numThreads=1 (19)
Aug 20 20:09:04.965: vmx| MKS: Base polling period is 1000000us
Aug 20 20:09:04.966: vmx| KHBKL: Unable to parse keystring at: ''
Aug 20 20:09:04.966: vmx| MKS REMOTE Loading VNC Configuration from VM config file
Aug 20 20:09:04.972: vmx| VLANCE: send cluster threshold is 80, size = 2 recalcInterval is 2 ticks
Aug 20 20:09:04.972: vmx| VMXNET: send cluster threshold is 80, size = 2 recalcInterval is 2 ticks, dontClusterSize is 128
Aug 20 20:09:04.973: vmx| NetPkt: checksum cycles/kB: C=745 asm1=831 asm2=820
Aug 20 20:09:04.973: vmx| NetPkt: copy and sum cycles/kB: C=933 asm1=811 asm2=814
Aug 20 20:09:04.980: vmx| Chipset version: 0x13
Aug 20 20:09:04.989: vmx| SCSI DEVICE (ide1:0): Computed value of ide1:0.useBounceBuffers: default
Aug 20 20:09:04.990: vmx| DISKUTIL: ide1:0 : capacity=0
Aug 20 20:09:04.990: vmx| DISKUTIL: ide1:0 : geometry=0/0/0
Aug 20 20:09:04.990: vmx| SCSI0: UNTAGGED commands will be converted to ORDER tags.
Aug 20 20:09:04.991: vmx| SCSI DEVICE (scsi0:0): Computed value of scsi0:0.useBounceBuffers: default
Aug 20 20:09:04.991: vmx| DISKUTIL: scsi0:0 : capacity=16777216
Aug 20 20:09:04.991: vmx| DISKUTIL: scsi0:0 : geometry=1174/255/56
Aug 20 20:09:04.993: vmx| SVGA: Device capabilities 0x001fc3e2
Aug 20 20:09:04.993: vmx| Host display topology 1366x768.
Aug 20 20:09:04.994: vmx| SVGA: Max size 2560x1600
Aug 20 20:09:04.995: vmx| Host display topology 1366x768 with 1 displays.
Aug 20 20:09:04.995: vmx| SVGA: Max size 2560x1600
Aug 20 20:09:04.996: vmx| SVGA: FIFO capabilities 0x0000007f
Aug 20 20:09:04.996: vmx| USB: Initializing 'UHCI' host controller
Aug 20 20:09:04.998: vmx| Ethernet0 MAC Address: 00:0c:29:a6:25:c9
Aug 20 20:09:05.003: vmx| SOUND 145.003553 Alsa library version: 1.0.21a.
Aug 20 20:09:05.004: vmx| USB: Initializing 'EHCI' host controller
Aug 20 20:09:05.007: vmx| MStat: Creating Stat vm.heartbeat
Aug 20 20:09:05.008: vmx| TOOLS Generated SessionId 18240087589778809333
Aug 20 20:09:05.009: vmx| VMXVmdbGuest_GetToolsVersion did nothing; tools version has not yet been initialized
Aug 20 20:09:05.009: vmx| DISKUTIL: scsi0:0 : toolsVersion = 0
Aug 20 20:09:05.010: vmx| DISKUTIL: Offline toolsVersion = 0
Aug 20 20:09:05.010: vmx| VMXVmdbGuest_GetToolsVersion did nothing; tools version has not yet been initialized
Aug 20 20:09:05.010: vmx| TOOLS setting legacy tools version to '0', manifest status is 5
Aug 20 20:09:05.011: vmx| VMXVmdb_SetToolsVersionState: status value set to 'noTools'
Aug 20 20:09:05.011: vmx| VMXVmdb_SetToolsVersionState: status value set to 'noTools'
Aug 20 20:09:05.011: vmx| TOOLS INSTALL initializing state to IDLE on power on.
Aug 20 20:09:05.013: vmx| NVRAMMGR: No valid NVRAM file found, will create default NVRAM.
Aug 20 20:09:05.035: vmx| PTSC to VMI Wallclock (nsec) 6404851845861 @ 2100000000Hz -> 1282315145000000000 @ 1000000000Hz
Aug 20 20:09:05.035: vmx| PTSC to VMI Wallclock (nsec) ((x * 4090445043) >> 33) + 1282312095070550194
Aug 20 20:09:05.036: vmx| PTSC to ParaTime RealCycles 0 @ 2100000000Hz -> 0 @ 2100000000Hz
Aug 20 20:09:05.036: vmx| PTSC to ParaTime RealCycles ((x * 1) >> 0) + 0
Aug 20 20:09:05.036: vmx| ParaTime RealCycles to PTSC 0 @ 2100000000Hz -> 0 @ 2100000000Hz
Aug 20 20:09:05.036: vmx| ParaTime RealCycles to PTSC ((x * 1) >> 0) + 0
Aug 20 20:09:05.037: vmx| memoryHotplug: Current size = 1024MB, Minimum size = 1024MB, Maximum size = 1024MB
Aug 20 20:09:05.037: vmx| memoryHotplug: Entry[0]: 00000000000000A0-00000000000A0000
Aug 20 20:09:05.038: vmx| memoryHotplug: Entry[1]: 00000000001000A0-0000000040000000
Aug 20 20:09:05.044: vmx| guestCpuFeatures = 0x404001f8
Aug 20 20:09:05.044: vmx| guestCPUID vendor: GenuineIntel
Aug 20 20:09:05.044: vmx| guestCPUID   name: Intel(R) Core(TM)2 Duo CPU     T6500  @ 2.10GHz
Aug 20 20:09:05.045: vmx| guestCPUID level 00000000, 0: 0x0000000d 0x756e6547 0x6c65746e 0x49656e69
Aug 20 20:09:05.045: vmx| guestCPUID level 00000001, 0: 0x0001067a 0x00010800 0x80080201 0x0febfbff
Aug 20 20:09:05.045: vmx| guestCPUID level 00000002, 0: 0x05b0b101 0x005657f0 0x00000000 0x2cb4307d
Aug 20 20:09:05.045: vmx| guestCPUID level 00000003, 0: 0x00000000 0x00000000 0x00000000 0x00000000
Aug 20 20:09:05.046: vmx| guestCPUID level 00000004, 0: 0x04000121 0x01c0003f 0x0000003f 0x00000001
Aug 20 20:09:05.046: vmx| guestCPUID level 00000005, 0: 0x00000040 0x00000040 0x00000003 0x00022220
Aug 20 20:09:05.046: vmx| guestCPUID level 00000006, 0: 0x00000001 0x00000002 0x00000003 0x00000000
Aug 20 20:09:05.047: vmx| guestCPUID level 00000007, 0: 0x00000000 0x00000000 0x00000000 0x00000000
Aug 20 20:09:05.047: vmx| guestCPUID level 00000008, 0: 0x00000400 0x00000000 0x00000000 0x00000000
Aug 20 20:09:05.047: vmx| guestCPUID level 00000009, 0: 0x00000000 0x00000000 0x00000000 0x00000000
Aug 20 20:09:05.047: vmx| guestCPUID level 0000000a, 0: 0x07280202 0x00000000 0x00000000 0x00000503
Aug 20 20:09:05.047: vmx| guestCPUID level 0000000b, 0: 0x00000000 0x00000000 0x00000000 0x00000000
Aug 20 20:09:05.048: vmx| guestCPUID level 0000000c, 0: 0x00000000 0x00000000 0x00000000 0x00000000
Aug 20 20:09:05.048: vmx| guestCPUID level 0000000d, 0: 0x00000003 0x00000240 0x00000240 0x00000000
Aug 20 20:09:05.048: vmx| guestCPUID level 40000000, 0: 0x40000010 0x61774d56 0x4d566572 0x65726177
Aug 20 20:09:05.048: vmx| guestCPUID level 40000010, 0: 0x00200b20 0x000101d0 0x00000000 0x00000000
Aug 20 20:09:05.048: vmx| guestCPUID level 80000000, 0: 0x80000008 0x00000000 0x00000000 0x00000000
Aug 20 20:09:05.048: vmx| guestCPUID level 80000001, 0: 0x00000000 0x00000000 0x00000000 0x00100000
Aug 20 20:09:05.049: vmx| guestCPUID level 80000002, 0: 0x65746e49 0x2952286c 0x726f4320 0x4d542865
Aug 20 20:09:05.049: vmx| guestCPUID level 80000003, 0: 0x44203229 0x43206f75 0x20205550 0x54202020
Aug 20 20:09:05.049: vmx| guestCPUID level 80000004, 0: 0x30303536 0x20402020 0x30312e32 0x007a4847
Aug 20 20:09:05.049: vmx| guestCPUID level 80000005, 0: 0x00000000 0x00000000 0x00000000 0x00000000
Aug 20 20:09:05.049: vmx| guestCPUID level 80000006, 0: 0x00000000 0x00000000 0x08006040 0x00000000
Aug 20 20:09:05.049: vmx| guestCPUID level 80000007, 0: 0x00000000 0x00000000 0x00000000 0x00000000
Aug 20 20:09:05.050: vmx| guestCPUID level 80000008, 0: 0x00003028 0x00000000 0x00000000 0x00000000
Aug 20 20:09:05.057: vmx| BusMemSample: initPercent 75 touched 196608
Aug 20 20:09:05.058: vmx| TOOLS received request in VMX to set option 'enableDnD' -> '1'
Aug 20 20:09:05.058: vmx| TOOLS received request in VMX to set option 'copypaste' -> '1'
Aug 20 20:09:05.061: vmx| VMXVmdbLoadUsbDevices: New set of 2 USB devices
Aug 20 20:09:05.061: vmx| USB: Found device [name:Microdia\ Integrated_Webcam_1.3M vid:0c45 pid:6400 path:1/6 speed:high family:other,video]
Aug 20 20:09:05.062: vmx| USB: Found device [name:Dell\ Wireless\ 365\ Bluetooth\ Module vid:413c pid:8160 path:3/1/3 speed:full family:vendor,other,wireless,bluetooth]
Aug 20 20:09:05.063: vmx| Vix: [10584 mainDispatch.c:844]: VMAutomation_PowerOn. Powering on.
Aug 20 20:09:05.064: vmx| VMX_PowerOn: ModuleTable_PowerOn = 1
Aug 20 20:09:05.064: vmx| Setting thread 1 stack size to 2097152.
Aug 20 20:09:05.064: mks| Async MKS thread is alive
Aug 20 20:09:05.064: mks| GLPrimaryInit3D, thread mks
Aug 20 20:09:05.065: vmx| Setting thread 4 stack size to 1048576.
Aug 20 20:09:05.065: mks| GLPrimaryHostConnect thread mks
Aug 20 20:09:05.192: mks| OpenGL Version: "2.0 Mesa 7.4" (2.0.0)
Aug 20 20:09:05.192: mks| OpenGL Vendor: "Tungsten Graphics, Inc"
Aug 20 20:09:05.192: mks| OpenGL Renderer: "Mesa DRI Mobile Intel® GM45 Express Chipset GEM 20090326 2009Q1 RC2 x86/MMX/SSE2"
Aug 20 20:09:05.192: mks| OpenGL Extensions: GL_ARB_depth_texture GL_ARB_draw_buffers GL_ARB_fragment_program GL_ARB_fragment_program_shadow
Aug 20 20:09:05.193: mks| OpenGL Extensions: GL_ARB_fragment_shader GL_ARB_multisample GL_ARB_multitexture GL_ARB_occlusion_query
Aug 20 20:09:05.193: mks| OpenGL Extensions: GL_ARB_pixel_buffer_object GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_shader_objects
Aug 20 20:09:05.193: mks| OpenGL Extensions: GL_ARB_shading_language_100 GL_ARB_shadow GL_ARB_texture_border_clamp GL_ARB_texture_compression
Aug 20 20:09:05.193: mks| OpenGL Extensions: GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine
Aug 20 20:09:05.193: mks| OpenGL Extensions: GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat
Aug 20 20:09:05.193: mks| OpenGL Extensions: GL_ARB_texture_non_power_of_two GL_ARB_texture_rectangle GL_ARB_transpose_matrix
Aug 20 20:09:05.193: mks| OpenGL Extensions: GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_vertex_shader GL_ARB_window_pos
Aug 20 20:09:05.194: mks| OpenGL Extensions: GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_equation_separate
Aug 20 20:09:05.194: mks| OpenGL Extensions: GL_EXT_blend_func_separate GL_EXT_blend_logic_op GL_EXT_blend_minmax GL_EXT_blend_subtract
Aug 20 20:09:05.194: mks| OpenGL Extensions: GL_EXT_clip_volume_hint GL_EXT_cull_vertex GL_EXT_compiled_vertex_array GL_EXT_copy_texture
Aug 20 20:09:05.194: mks| OpenGL Extensions: GL_EXT_draw_range_elements GL_EXT_framebuffer_object GL_EXT_fog_coord GL_EXT_multi_draw_arrays
Aug 20 20:09:05.194: mks| OpenGL Extensions: GL_EXT_packed_depth_stencil GL_EXT_packed_pixels GL_EXT_pixel_buffer_object GL_EXT_point_parameters
Aug 20 20:09:05.194: mks| OpenGL Extensions: GL_EXT_polygon_offset GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color
Aug 20 20:09:05.194: mks| OpenGL Extensions: GL_EXT_shadow_funcs GL_EXT_stencil_wrap GL_EXT_subtexture GL_EXT_texture GL_EXT_texture3D
Aug 20 20:09:05.195: mks| OpenGL Extensions: GL_EXT_texture_edge_clamp GL_EXT_texture_env_add GL_EXT_texture_env_combine GL_EXT_texture_env_dot3
Aug 20 20:09:05.195: mks| OpenGL Extensions: GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod_bias GL_EXT_texture_object
Aug 20 20:09:05.195: mks| OpenGL Extensions: GL_EXT_texture_rectangle GL_EXT_texture_sRGB GL_EXT_vertex_array GL_3DFX_texture_compression_FXT1
Aug 20 20:09:05.195: mks| OpenGL Extensions: GL_APPLE_client_storage GL_APPLE_packed_pixels GL_ATI_blend_equation_separate
Aug 20 20:09:05.195: mks| OpenGL Extensions: GL_ATI_texture_env_combine3 GL_ATI_separate_stencil GL_IBM_rasterpos_clip
Aug 20 20:09:05.195: mks| OpenGL Extensions: GL_IBM_texture_mirrored_repeat GL_INGR_blend_func_separate GL_MESA_pack_invert
Aug 20 20:09:05.196: mks| OpenGL Extensions: GL_MESA_ycbcr_texture GL_MESA_window_pos GL_NV_blend_square GL_NV_light_max_exponent
Aug 20 20:09:05.196: mks| OpenGL Extensions: GL_NV_point_sprite GL_NV_texture_rectangle GL_NV_texgen_reflection GL_NV_vertex_program
Aug 20 20:09:05.196: mks| OpenGL Extensions: GL_NV_vertex_program1_1 GL_OES_read_format GL_SGIS_generate_mipmap GL_SGIS_texture_border_clamp
Aug 20 20:09:05.196: mks| OpenGL Extensions: GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod GL_SGIX_depth_texture
Aug 20 20:09:05.196: mks| OpenGL Extensions: GL_SUN_multi_draw_arrays
Aug 20 20:09:05.197: mks| VMGL: Extension present, GL_APPLE_client_storage
Aug 20 20:09:05.198: mks| VMGL: Extension missing, GL_APPLE_fence
Aug 20 20:09:05.198: mks| VMGL: Extension missing, GL_APPLE_flush_buffer_range
Aug 20 20:09:05.198: mks| VMGL: Extension missing, GL_APPLE_texture_range
Aug 20 20:09:05.198: mks| VMGL: Extension missing, GL_APPLE_ycbcr_422
Aug 20 20:09:05.198: mks| VMGL: Extension present, GL_ARB_draw_buffers
Aug 20 20:09:05.198: mks| VMGL: Extension present, GL_ARB_fragment_program
Aug 20 20:09:05.199: mks| VMGL: Extension present, GL_ARB_fragment_shader
Aug 20 20:09:05.199: mks| VMGL: Extension missing, GL_ARB_framebuffer_object
Aug 20 20:09:05.199: mks| VMGL: Extension missing, GL_ARB_half_float_pixel
Aug 20 20:09:05.199: mks| VMGL: Extension missing, GL_ARB_imaging
Aug 20 20:09:05.199: mks| VMGL: Extension missing, GL_ARB_map_buffer_range
Aug 20 20:09:05.199: mks| VMGL: Extension present, GL_ARB_multitexture
Aug 20 20:09:05.199: mks| VMGL: Extension present, GL_ARB_occlusion_query
Aug 20 20:09:05.200: mks| VMGL: Extension present, GL_ARB_pixel_buffer_object
Aug 20 20:09:05.200: mks| VMGL: Extension present, GL_ARB_point_parameters
Aug 20 20:09:05.200: mks| VMGL: Extension present, GL_ARB_point_sprite
Aug 20 20:09:05.200: mks| VMGL: Extension present, GL_ARB_shader_objects
Aug 20 20:09:05.200: mks| VMGL: Extension missing, GL_ARB_shader_texture_lod
Aug 20 20:09:05.200: mks| VMGL: Extension present, GL_ARB_texture_compression
Aug 20 20:09:05.201: mks| VMGL: Extension present, GL_ARB_texture_cube_map
Aug 20 20:09:05.201: mks| VMGL: Extension present, GL_ARB_texture_env_combine
Aug 20 20:09:05.201: mks| VMGL: Extension missing, GL_ARB_texture_float
Aug 20 20:09:05.201: mks| VMGL: Extension present, GL_ARB_texture_non_power_of_two
Aug 20 20:09:05.201: mks| VMGL: Extension present, GL_ARB_texture_rectangle
Aug 20 20:09:05.201: mks| VMGL: Extension missing, GL_ARB_texture_rg
Aug 20 20:09:05.201: mks| VMGL: Extension missing, GL_ARB_uniform_buffer_object
Aug 20 20:09:05.202: mks| VMGL: Extension missing, GL_ARB_vertex_blend
Aug 20 20:09:05.202: mks| VMGL: Extension present, GL_ARB_vertex_buffer_object
Aug 20 20:09:05.202: mks| VMGL: Extension present, GL_ARB_vertex_program
Aug 20 20:09:05.202: mks| VMGL: Extension present, GL_ARB_vertex_shader
Aug 20 20:09:05.202: mks| VMGL: Extension present, GL_ARB_window_pos
Aug 20 20:09:05.202: mks| VMGL: Extension missing, GL_ATI_draw_buffers
Aug 20 20:09:05.202: mks| VMGL: Extension missing, GL_ATI_envmap_bumpmap
Aug 20 20:09:05.203: mks| VMGL: Extension missing, GL_ATI_shader_texture_lod
Aug 20 20:09:05.203: mks| VMGL: Extension missing, GL_EXTX_framebuffer_mixed_formats
Aug 20 20:09:05.203: mks| VMGL: Extension present, GL_EXT_fog_coord
Aug 20 20:09:05.203: mks| VMGL: Extension missing, GL_EXT_framebuffer_blit
Aug 20 20:09:05.203: mks| VMGL: Extension present, GL_EXT_framebuffer_object
Aug 20 20:09:05.203: mks| VMGL: Extension missing, GL_EXT_gpu_shader4
Aug 20 20:09:05.204: mks| VMGL: Extension present, GL_EXT_packed_depth_stencil
Aug 20 20:09:05.204: mks| VMGL: Extension missing, GL_EXT_provoking_vertex
Aug 20 20:09:05.204: mks| VMGL: Extension present, GL_EXT_secondary_color
Aug 20 20:09:05.204: mks| VMGL: Extension missing, GL_EXT_stencil_two_side
Aug 20 20:09:05.204: mks| VMGL: Extension present, GL_EXT_texture3D
Aug 20 20:09:05.204: mks| VMGL: Extension missing, GL_EXT_texture_compression_s3tc
Aug 20 20:09:05.204: mks| VMGL: Extension missing, GL_EXT_texture_cube_map
Aug 20 20:09:05.205: mks| VMGL: Extension present, GL_EXT_texture_filter_anisotropic
Aug 20 20:09:05.205: mks| VMGL: Extension missing, GL_EXT_texture_mirror_clamp
Aug 20 20:09:05.205: mks| VMGL: Extension present, GL_EXT_texture_rectangle
Aug 20 20:09:05.205: mks| VMGL: Extension missing, GL_EXT_texture_swizzle
Aug 20 20:09:05.205: mks| VMGL: Extension missing, GL_EXT_vertex_array_bgra
Aug 20 20:09:05.206: mks| VMGL: Extension missing, GL_NV_fence
Aug 20 20:09:05.206: mks| VMGL: Extension missing, GL_NV_half_float
Aug 20 20:09:05.206: mks| VMGL: Extension missing, GL_NV_packed_depth_stencil
Aug 20 20:09:05.206: mks| VMGL: Extension present, GL_NV_texgen_reflection
Aug 20 20:09:05.206: mks| VMGL: Extension missing, GL_NV_texture_env_combine4
Aug 20 20:09:05.206: mks| VMGL: Extension present, GL_NV_texture_rectangle
Aug 20 20:09:05.206: mks| VMGL: Extension missing, GL_NV_texture_shader
Aug 20 20:09:05.207: mks| VMGL: Extension missing, GL_NV_texture_shader2
Aug 20 20:09:05.207: mks| VMGL: Extension missing, GL_NV_vertex_array_range
Aug 20 20:09:05.207: mks| VMGL: Extension missing, WGL_ARB_make_current_read
Aug 20 20:09:05.207: mks| VMGL: Extension missing, WGL_ARB_pixel_format
Aug 20 20:09:05.207: mks| VMGL: Extension missing, WGL_ARB_render_texture
Aug 20 20:09:05.209: mks| GLManager: Required extension GL_EXT_texture_compression_s3tc is missing.
Aug 20 20:09:05.249: mks| Finish HostDisconnect: thread mks
Aug 20 20:09:05.249: vcpu-0| APIC: version = 0x14, max LVT = 5
Aug 20 20:09:05.251: vcpu-0| APIC: LDR = 0x2000000, DFR = 0xffffffff
Aug 20 20:09:05.251: vmx| USB: Connecting device 0x400000010e0f0003
Aug 20 20:09:05.251: vmx| USB: Automatically connecting virtual hub
Aug 20 20:09:05.251: vmx| USB: Connecting device 0x200000010e0f0002
Aug 20 20:09:05.252: vmx| DnDRegisterRpc: DnD rpc already set to 1
Aug 20 20:09:05.252: vmx| CopyPasteRegisterRpc: already set to 1
Aug 20 20:09:05.256: mks| Msg_Post: Information
Aug 20 20:09:05.256: mks| [msg.glBackend.initFailed] 3D graphics acceleration will be disabled. This computer does not have a 3D graphics system supported by VMware Workstation. ----------------------------------------
Aug 20 20:09:05.522: vcpu-0| CPU reset: hard (mode 2)
Aug 20 20:09:05.523: vcpu-0| memoryHotplug: Entry[0]: 00000000000000A0-00000000000A0000
Aug 20 20:09:05.523: vcpu-0| memoryHotplug: Entry[1]: 00000000001000A0-0000000040000000
Aug 20 20:09:05.524: vcpu-0| PIIX4: PM Resuming from suspend type 0x0.
Aug 20 20:09:05.552: vcpu-0| VNET: MACVNetConnectToNetwork: Ethernet0: notify available
Aug 20 20:09:05.553: vcpu-0| FLOPPYLIB-IMAGE: Floppy geometry 80/2/18 detected from boot sector.
Aug 20 20:09:05.554: vcpu-0| CDROM: Connecting ide1:0 to '/media/disk/Softwares/WinXP/windows.iso'. img=1 raw=0 remote=0
Aug 20 20:09:05.555: vcpu-0| DMG_Open: Not an unencrypted .dmg file (footer signature 0x00000000).
Aug 20 20:09:05.555: vcpu-0| DMG_Close: max cached entries 8
Aug 20 20:09:05.555: vcpu-0| Vix: [10587 mainDispatch.c:3661]: VMAutomation_ReportPowerOpFinished: statevar=0, newAppState=1872, success=1
Aug 20 20:09:05.559: vcpu-0| Vix: [10587 mainDispatch.c:3582]: VMAutomationReportPowerStateChange: Reporting power state change (opcode=0, err=0).
Aug 20 20:09:05.559: vcpu-0| Vix: [10587 mainDispatch.c:3582]: VMAutomationReportPowerStateChange: Reporting power state change (opcode=2, err=0).
Aug 20 20:09:05.559: vcpu-0| Transitioned vmx/execState/val to poweredOn
Aug 20 20:09:05.575: vmx| serial0: try 0 failed to connect to the socket with error 2: No such file or directory
Aug 20 20:09:05.575: mks| Connecting to window system.
Aug 20 20:09:05.578: mks| XINFO X fd is 73
Aug 20 20:09:05.582: mks| XINFO depth 24 bpp 32 class 4
Aug 20 20:09:05.598: mks| DisplayTopologyInit: using the XRandR backend.
Aug 20 20:09:05.693: mks| MKS: Base polling period is 10000us
Aug 20 20:09:05.695: mks| XKeymap_PowerOn: use evdev keycode mapping.
Aug 20 20:09:05.696: mks| rasterops MMXEXT accelerations enabled
Aug 20 20:09:05.769: mks| DisplayTopologyGetEDID: could not obtain EDID data for output with XID 59.
Aug 20 20:09:05.769: mks| XInfoFetchModes: host display mode 0: 1366x768
Aug 20 20:09:05.769: mks| XInfoFetchModes: host display mode 1: 1360x768
Aug 20 20:09:05.770: mks| XInfoFetchModes: host display mode 2: 1024x768
Aug 20 20:09:05.770: mks| XInfoFetchModes: host display mode 3: 832x624
Aug 20 20:09:05.770: mks| XInfoFetchModes: host display mode 4: 800x600
Aug 20 20:09:05.770: mks| XInfoFetchModes: host display mode 5: 640x480
Aug 20 20:09:05.770: mks| XInfoFetchModes: host display mode 6: 720x400
Aug 20 20:09:05.770: mks| XInfoFetchModes: host display mode 7: 640x400
Aug 20 20:09:05.770: mks| XInfoFetchModes: host display mode 8: 640x350
Aug 20 20:09:05.771: mks| XI major version 1, minor version 5
Aug 20 20:09:05.892: mks| HostOps hideCursor before defineCursor!
Aug 20 20:09:05.984: vmx| VMXVmdb_LoadRawConfig: Loading raw config
Aug 20 20:09:06.047: vcpu-0| sz=2961376
Aug 20 20:09:06.054: vcpu-0| vmm32 initialized: Releasebuild-282343. cflags: 0x00000000.00000000.00006000.00090003
Aug 20 20:09:06.056: vcpu-0| MonitorInitNumaUnmapVMM32
Aug 20 20:09:06.213: mks| KHBKL: Unable to parse keystring at: ''
Aug 20 20:09:06.573: vmx| HOSTINFO: Seeing Intel CPU, numCoresPerCPU 2 numThreadsPerCore 1.
Aug 20 20:09:06.573: vmx| HOSTINFO: This machine has 1 physical CPUS, 2 total cores, and 2 logical CPUs.
Aug 20 20:09:06.663: vcpu-0| SVGA: Registering MemSpace at 0xd0000000(0x0) and 0xd8000000(0x0)
Aug 20 20:09:06.668: vcpu-0| SVGA: Unregistering MemSpace at 0xd0000000(0xd0000000) and 0xd8000000(0xd8000000)
Aug 20 20:09:06.849: vcpu-0| SVGA: Registering MemSpace at 0xd0000000(0xd0000000) and 0xd8000000(0xd8000000)
Aug 20 20:09:06.856: vcpu-0| SVGA: Unregistering MemSpace at 0xd0000000(0xd0000000) and 0xd8000000(0xd8000000)
Aug 20 20:09:06.875: vcpu-0| SVGA: Registering IOSpace at 0x10f0
Aug 20 20:09:06.875: vcpu-0| SVGA: Registering MemSpace at 0xd0000000(0xd0000000) and 0xd8000000(0xd8000000)
Aug 20 20:09:06.881: vcpu-0| PCIBridge4: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:06.882: vcpu-0| pciBridge4:1: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:06.883: vcpu-0| pciBridge4:2: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:06.884: vcpu-0| pciBridge4:3: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:06.886: vcpu-0| pciBridge4:4: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:06.887: vcpu-0| pciBridge4:5: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:06.888: vcpu-0| pciBridge4:6: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:06.889: vcpu-0| pciBridge4:7: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:06.890: vcpu-0| PCIBridge5: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:06.892: vcpu-0| pciBridge5:1: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:06.893: vcpu-0| pciBridge5:2: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:06.894: vcpu-0| pciBridge5:3: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:06.896: vcpu-0| pciBridge5:4: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:06.897: vcpu-0| pciBridge5:5: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:06.898: vcpu-0| pciBridge5:6: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:06.899: vcpu-0| pciBridge5:7: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:06.900: vcpu-0| PCIBridge6: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:06.902: vcpu-0| pciBridge6:1: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:06.903: vcpu-0| pciBridge6:2: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:06.904: vcpu-0| pciBridge6:3: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:06.905: vcpu-0| pciBridge6:4: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:06.907: vcpu-0| pciBridge6:5: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:06.908: vcpu-0| pciBridge6:6: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:06.909: vcpu-0| pciBridge6:7: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:06.910: vcpu-0| PCIBridge7: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:06.912: vcpu-0| pciBridge7:1: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:06.913: vcpu-0| pciBridge7:2: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:06.914: vcpu-0| pciBridge7:3: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:06.915: vcpu-0| pciBridge7:4: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:06.917: vcpu-0| pciBridge7:5: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:06.918: vcpu-0| pciBridge7:6: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:06.919: vcpu-0| pciBridge7:7: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:07.167: vcpu-0| PCIBridge4: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:07.168: vcpu-0| pciBridge4:1: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:07.170: vcpu-0| pciBridge4:2: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:07.171: vcpu-0| pciBridge4:3: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:07.172: vcpu-0| pciBridge4:4: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:07.173: vcpu-0| pciBridge4:5: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:07.175: vcpu-0| pciBridge4:6: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:07.176: vcpu-0| pciBridge4:7: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:07.177: vcpu-0| PCIBridge5: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:07.179: vcpu-0| pciBridge5:1: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:07.181: vcpu-0| pciBridge5:2: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:07.183: vcpu-0| pciBridge5:3: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:07.184: vcpu-0| pciBridge5:4: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:07.186: vcpu-0| pciBridge5:5: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:07.187: vcpu-0| pciBridge5:6: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:07.188: vcpu-0| pciBridge5:7: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:07.189: vcpu-0| PCIBridge6: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:07.191: vcpu-0| pciBridge6:1: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:07.192: vcpu-0| pciBridge6:2: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:07.193: vcpu-0| pciBridge6:3: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:07.194: vcpu-0| pciBridge6:4: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:07.195: vcpu-0| pciBridge6:5: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:07.197: vcpu-0| pciBridge6:6: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:07.198: vcpu-0| pciBridge6:7: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:07.199: vcpu-0| PCIBridge7: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:07.201: vcpu-0| pciBridge7:1: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:07.202: vcpu-0| pciBridge7:2: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:07.203: vcpu-0| pciBridge7:3: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:07.204: vcpu-0| pciBridge7:4: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:07.205: vcpu-0| pciBridge7:5: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:07.207: vcpu-0| pciBridge7:6: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:07.208: vcpu-0| pciBridge7:7: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:07.217: vcpu-0| DISKUTIL: scsi0:0 : geometry=1174/255/56
Aug 20 20:09:07.218: vcpu-0| DISKUTIL: scsi0:0 : capacity=16777216
Aug 20 20:09:07.581: vcpu-0| BIOS-UUID is 56 4d eb d5 e8 72 83 5f-07 36 3b 58 1e a6 25 c9
Aug 20 20:09:07.912: mks| HostOps hideCursor before defineCursor!
Aug 20 20:09:09.222: vcpu-0| Unknown int 10h func 0x2000
Aug 20 20:09:09.241: vcpu-0| BUSLOGIC: Store HAL[16] = 0xfff8
Aug 20 20:09:09.241: vcpu-0| BUSLOGIC: Store HAL[18] = 0xfe01
Aug 20 20:09:09.243: vcpu-0| DISKLIB-DDB   : "longContentID" = "6cf6c75702980bdc7793f19b4aed9c45" (was "fd15355ec3e3d1f87d0b7a85fffffffe")
Aug 20 20:09:09.244: vcpu-0| Setting thread 37 stack size to 1048576.
Aug 20 20:09:09.244: vcpu-0| Setting thread 38 stack size to 1048576.
Aug 20 20:09:09.386: vcpu-0| BUSLOGIC: Store HAL[20] = 0x00fb
Aug 20 20:09:09.387: vcpu-0| BUSLOGIC: Store HAL[22] = 0x0400
Aug 20 20:09:09.387: vcpu-0| BUSLOGIC: Store HAL[16] = 0xfff8
Aug 20 20:09:09.388: vcpu-0| BUSLOGIC: Store HAL[18] = 0xfe01
Aug 20 20:09:11.354: mks| SVGA: display status changed, using optimizations for local consoles.
Aug 20 20:09:13.342: vcpu-0| BUSLOGIC: Store HAL[16] = 0xfff8
Aug 20 20:09:13.342: vcpu-0| BUSLOGIC: Store HAL[18] = 0xfe01
Aug 20 20:09:13.343: vcpu-0| BUSLOGIC: Store HAL[16] = 0xfff8
Aug 20 20:09:13.344: vcpu-0| BUSLOGIC: Store HAL[18] = 0xfe01
Aug 20 20:09:13.345: vcpu-0| BUSLOGIC: Store HAL[16] = 0xfff8
Aug 20 20:09:13.345: vcpu-0| BUSLOGIC: Store HAL[18] = 0xfe01
Aug 20 20:09:13.345: vcpu-0| BUSLOGIC: Store HAL[16] = 0xfff8
Aug 20 20:09:13.346: vcpu-0| BUSLOGIC: Store HAL[18] = 0xfe01
Aug 20 20:09:26.031: vcpu-0| BUSLOGIC: Store HAL[16] = 0xfff8
Aug 20 20:09:26.031: vcpu-0| BUSLOGIC: Store HAL[18] = 0xfe01
Aug 20 20:09:26.032: vcpu-0| BUSLOGIC: Store HAL[16] = 0xfff8
Aug 20 20:09:26.032: vcpu-0| BUSLOGIC: Store HAL[18] = 0xfe01
Aug 20 20:09:26.033: vcpu-0| BUSLOGIC: Store HAL[16] = 0xfff8
Aug 20 20:09:26.033: vcpu-0| BUSLOGIC: Store HAL[18] = 0xfe01
Aug 20 20:09:26.033: vcpu-0| BUSLOGIC: Store HAL[16] = 0xfff8
Aug 20 20:09:26.033: vcpu-0| BUSLOGIC: Store HAL[18] = 0xfe01
Aug 20 20:09:28.625: vcpu-0| SVGA: Unregistering IOSpace at 0x10f0
Aug 20 20:09:28.625: vcpu-0| SVGA: Unregistering MemSpace at 0xd0000000(0xd0000000) and 0xd8000000(0xd8000000)
Aug 20 20:09:28.644: vcpu-0| SVGA: Registering IOSpace at 0x10f0
Aug 20 20:09:28.644: vcpu-0| SVGA: Registering MemSpace at 0xd0000000(0xd0000000) and 0xd8000000(0xd8000000)
Aug 20 20:09:28.651: vcpu-0| PCIBridge4: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:28.652: vcpu-0| PCIBridge4: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:28.654: vcpu-0| pciBridge4:1: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:28.655: vcpu-0| pciBridge4:1: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:28.657: vcpu-0| pciBridge4:2: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:28.658: vcpu-0| pciBridge4:2: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:28.660: vcpu-0| pciBridge4:3: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:28.661: vcpu-0| pciBridge4:3: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:28.663: vcpu-0| pciBridge4:4: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:28.663: vcpu-0| pciBridge4:4: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:28.665: vcpu-0| pciBridge4:5: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:28.666: vcpu-0| pciBridge4:5: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:28.669: vcpu-0| pciBridge4:6: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:28.669: vcpu-0| pciBridge4:6: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:28.672: vcpu-0| pciBridge4:7: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:28.672: vcpu-0| pciBridge4:7: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:28.674: vcpu-0| PCIBridge5: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:28.675: vcpu-0| PCIBridge5: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:28.677: vcpu-0| pciBridge5:1: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:28.677: vcpu-0| pciBridge5:1: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:28.680: vcpu-0| pciBridge5:2: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:28.680: vcpu-0| pciBridge5:2: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:28.682: vcpu-0| pciBridge5:3: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:28.683: vcpu-0| pciBridge5:3: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:28.685: vcpu-0| pciBridge5:4: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:28.686: vcpu-0| pciBridge5:4: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:28.688: vcpu-0| pciBridge5:5: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:28.689: vcpu-0| pciBridge5:5: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:28.691: vcpu-0| pciBridge5:6: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:28.691: vcpu-0| pciBridge5:6: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:28.694: vcpu-0| pciBridge5:7: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:28.694: vcpu-0| pciBridge5:7: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:28.697: vcpu-0| PCIBridge6: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:28.697: vcpu-0| PCIBridge6: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:28.699: vcpu-0| pciBridge6:1: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:28.700: vcpu-0| pciBridge6:1: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:28.702: vcpu-0| pciBridge6:2: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:28.702: vcpu-0| pciBridge6:2: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:28.705: vcpu-0| pciBridge6:3: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:28.706: vcpu-0| pciBridge6:3: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:28.708: vcpu-0| pciBridge6:4: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:28.708: vcpu-0| pciBridge6:4: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:28.711: vcpu-0| pciBridge6:5: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:28.711: vcpu-0| pciBridge6:5: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:28.714: vcpu-0| pciBridge6:6: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:28.714: vcpu-0| pciBridge6:6: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:28.717: vcpu-0| pciBridge6:7: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:28.717: vcpu-0| pciBridge6:7: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:28.719: vcpu-0| PCIBridge7: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:28.720: vcpu-0| PCIBridge7: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:28.722: vcpu-0| pciBridge7:1: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:28.722: vcpu-0| pciBridge7:1: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:28.725: vcpu-0| pciBridge7:2: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:28.726: vcpu-0| pciBridge7:2: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:28.728: vcpu-0| pciBridge7:3: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:28.729: vcpu-0| pciBridge7:3: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:28.731: vcpu-0| pciBridge7:4: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:28.732: vcpu-0| pciBridge7:4: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:28.735: vcpu-0| pciBridge7:5: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:28.735: vcpu-0| pciBridge7:5: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:28.738: vcpu-0| pciBridge7:6: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:28.738: vcpu-0| pciBridge7:6: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:28.740: vcpu-0| pciBridge7:7: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:28.741: vcpu-0| pciBridge7:7: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:30.407: vcpu-0| PCIBridge4: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:30.417: vcpu-0| pciBridge4:1: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:30.428: vcpu-0| pciBridge4:2: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:30.438: vcpu-0| pciBridge4:3: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:30.447: vcpu-0| pciBridge4:4: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:30.457: vcpu-0| pciBridge4:5: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:30.467: vcpu-0| pciBridge4:6: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:30.476: vcpu-0| pciBridge4:7: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:30.487: vcpu-0| PCIBridge5: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:30.497: vcpu-0| pciBridge5:1: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:30.507: vcpu-0| pciBridge5:2: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:30.517: vcpu-0| pciBridge5:3: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:30.526: vcpu-0| pciBridge5:4: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:30.536: vcpu-0| pciBridge5:5: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:30.545: vcpu-0| pciBridge5:6: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:30.555: vcpu-0| pciBridge5:7: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:30.565: vcpu-0| PCIBridge6: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:30.574: vcpu-0| pciBridge6:1: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:30.585: vcpu-0| pciBridge6:2: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:30.595: vcpu-0| pciBridge6:3: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:30.605: vcpu-0| pciBridge6:4: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:30.614: vcpu-0| pciBridge6:5: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:30.624: vcpu-0| pciBridge6:6: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:30.633: vcpu-0| pciBridge6:7: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:30.642: vcpu-0| PCIBridge7: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:30.651: vcpu-0| pciBridge7:1: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:30.661: vcpu-0| pciBridge7:2: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:30.671: vcpu-0| pciBridge7:3: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:30.680: vcpu-0| pciBridge7:4: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:30.690: vcpu-0| pciBridge7:5: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:30.699: vcpu-0| pciBridge7:6: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:30.709: vcpu-0| pciBridge7:7: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:09:31.859: vcpu-0| UHCI: Global Reset
Aug 20 20:09:36.941: vcpu-0| CDROM: Mode Sense for Unsupported Page 0x1B
Aug 20 20:09:36.942: vcpu-0| SCSI DEVICE (ide1:0): MODE SENSE(10) for unsupported page 0x1b
Aug 20 20:09:37.825: vcpu-0| DISKUTIL: scsi0:0 : geometry=1174/255/56
Aug 20 20:09:37.825: vcpu-0| DISKUTIL: scsi0:0 : capacity=16777216
Aug 20 20:09:37.826: vcpu-0| SCSI0: RESET BUS
Aug 20 20:09:37.840: vcpu-0| DISKUTIL: scsi0:0 : geometry=1174/255/56
Aug 20 20:09:37.841: vcpu-0| DISKUTIL: scsi0:0 : capacity=16777216
Aug 20 20:09:37.978: vcpu-0| CDROM: Emulate GET CONFIGURATION RT 0 start feature 0
Aug 20 20:09:37.978: vcpu-0| CDROM: Emulate GET CONFIGURATION RT 0 start feature 0
Aug 20 20:09:37.979: vcpu-0| CDROM: Emulate GET CONFIGURATION RT 0 start feature 0
Aug 20 20:09:37.982: vcpu-0| CDROM: Accepting Event Status Notification 0
Aug 20 20:09:37.982: vcpu-0| CDROM: Failed on unsupported 0x4a event 0
Aug 20 20:09:37.982: vcpu-0| CDROM ide1:0: CMD 0x4a (*UNKNOWN (0x4a)*) FAILED (key 0x5 asc 0x24 ascq 0)
Aug 20 20:09:38.021: vcpu-0| SCSI DEVICE (scsi0:0): MODE SENSE(6) for unsupported page 0x1c
Aug 20 20:09:38.386: mks| HostOps hideCursor before defineCursor!
Aug 20 20:09:39.207: vmx| PTSC: using reference clock [TSC: 6465808631005->6475021130812, RC: 4372712670->4377713697]
Aug 20 20:09:46.402: vcpu-0| Setting thread 39 stack size to 1048576.
Aug 20 20:09:57.697: vcpu-0| Setting thread 40 stack size to 1048576.
Aug 20 20:09:57.697: vcpu-0| Setting thread 41 stack size to 1048576.
Aug 20 20:09:57.698: vcpu-0| Setting thread 42 stack size to 1048576.
Aug 20 20:09:57.698: vmx| Setting thread 43 stack size to 1048576.
Aug 20 20:09:57.699: vmx| Setting thread 44 stack size to 1048576.
Aug 20 20:09:57.701: vcpu-0| Setting thread 45 stack size to 1048576.
Aug 20 20:09:58.694: vcpu-0| Setting thread 46 stack size to 1048576.
Aug 20 20:09:58.694: vcpu-0| Setting thread 47 stack size to 1048576.
Aug 20 20:09:58.695: vcpu-0| Setting thread 48 stack size to 1048576.
Aug 20 20:09:58.695: vcpu-0| Setting thread 49 stack size to 1048576.
Aug 20 20:09:58.696: vcpu-0| Setting thread 50 stack size to 1048576.
Aug 20 20:09:58.696: vcpu-0| Setting thread 51 stack size to 1048576.
Aug 20 20:09:58.697: vcpu-0| Setting thread 52 stack size to 1048576.
Aug 20 20:09:58.697: vcpu-0| Setting thread 53 stack size to 1048576.
Aug 20 20:10:06.157: vmx| GuestRpcSendTimedOut: message to toolbox-dnd timed out.
Aug 20 20:10:14.059: vmx| scsi0:0: Command WRITE(10) took 2.365 seconds (ok)
Aug 20 20:10:15.294: vmx| scsi0:0: Command WRITE(10) took 2.817 seconds (ok)
Aug 20 20:10:15.371: vmx| scsi0:0: Command WRITE(10) took 2.894 seconds (ok)
Aug 20 20:10:15.408: vmx| ide1:0: Command READ(10) took 2.924 seconds (ok)
Aug 20 20:10:15.510: vmx| scsi0:0: Command WRITE(10) took 3.034 seconds (ok)
Aug 20 20:10:15.758: vmx| scsi0:0: Command WRITE(10) took 3.282 seconds (ok)
Aug 20 20:10:16.053: vmx| scsi0:0: Command WRITE(10) took 3.577 seconds (ok)
Aug 20 20:10:17.151: vmx| scsi0:0: Command WRITE(10) took 1.704 seconds (ok)
Aug 20 20:10:18.960: vmx| scsi0:0: Command WRITE(10) took 3.513 seconds (ok)
Aug 20 20:10:19.046: vmx| ide1:0: Command READ(10) took 3.596 seconds (ok)
Aug 20 20:10:20.403: vmx| scsi0:0: Command WRITE(10) took 8.709 seconds (ok)
Aug 20 20:10:21.212: vmx| scsi0:0: Command WRITE(10) took 2.080 seconds (ok)
Aug 20 20:10:21.216: vmx| scsi0:0: Command WRITE(10) took 9.522 seconds (ok)
Aug 20 20:10:21.219: vmx| scsi0:0: Command WRITE(10) took 2.087 seconds (ok)
Aug 20 20:10:21.225: vmx| scsi0:0: Command WRITE(10) took 9.531 seconds (ok)
Aug 20 20:10:21.226: vmx| scsi0:0: Command WRITE(10) took 2.093 seconds (ok)
Aug 20 20:10:21.227: vmx| scsi0:0: Command WRITE(10) took 2.094 seconds (ok)
Aug 20 20:10:21.228: vmx| scsi0:0: Command WRITE(10) took 9.535 seconds (ok)
Aug 20 20:10:21.230: vmx| scsi0:0: Command WRITE(10) took 9.526 seconds (ok)
Aug 20 20:10:21.232: vmx| scsi0:0: Command WRITE(10) took 8.756 seconds (ok)
Aug 20 20:10:21.234: vmx| scsi0:0: Command WRITE(10) took 5.787 seconds (ok)
Aug 20 20:10:21.236: vmx| scsi0:0: Command WRITE(10) took 2.105 seconds (ok)
Aug 20 20:10:21.238: vmx| scsi0:0: Command WRITE(10) took 2.106 seconds (ok)
Aug 20 20:10:21.240: vmx| scsi0:0: Command WRITE(10) took 2.108 seconds (ok)
Aug 20 20:10:21.241: vmx| scsi0:0: Command WRITE(10) took 8.765 seconds (ok)
Aug 20 20:10:21.241: vmx| scsi0:0: Command WRITE(10) took 8.765 seconds (ok)
Aug 20 20:10:21.242: vmx| scsi0:0: Command WRITE(10) took 2.110 seconds (ok)
Aug 20 20:10:21.276: vmx| ide1:0: Command READ(10) took 2.140 seconds (ok)
Aug 20 20:10:52.806: vmx| scsi0:0: Command WRITE(10) took 2.204 seconds (ok)
Aug 20 20:10:53.506: vmx| scsi0:0: Command WRITE(10) took 2.457 seconds (ok)
Aug 20 20:10:53.506: vmx| scsi0:0: Command WRITE(10) took 2.457 seconds (ok)
Aug 20 20:10:53.506: vmx| scsi0:0: Command WRITE(10) took 2.457 seconds (ok)
Aug 20 20:10:53.508: vmx| scsi0:0: Command WRITE(10) took 2.458 seconds (ok)
Aug 20 20:10:53.510: vmx| scsi0:0: Command WRITE(10) took 2.461 seconds (ok)
Aug 20 20:10:53.520: vmx| scsi0:0: Command WRITE(10) took 2.470 seconds (ok)
Aug 20 20:10:53.521: vmx| scsi0:0: Command WRITE(10) took 2.471 seconds (ok)
Aug 20 20:10:55.088: vmx| scsi0:0: Command WRITE(10) took 1.015 seconds (ok)
Aug 20 20:10:56.481: vmx| ide1:0: Command READ(10) took 2.022 seconds (ok)
Aug 20 20:10:58.522: vmx| ide1:0: Command READ(10) took 1.913 seconds (ok)
Aug 20 20:10:58.528: vmx| scsi0:0: Command WRITE(10) took 4.452 seconds (ok)
Aug 20 20:10:58.529: vmx| scsi0:0: Command WRITE(10) took 4.452 seconds (ok)
Aug 20 20:10:58.539: vmx| scsi0:0: Command WRITE(10) took 4.460 seconds (ok)
Aug 20 20:10:58.539: vmx| scsi0:0: Command WRITE(10) took 4.458 seconds (ok)
Aug 20 20:10:58.539: vmx| scsi0:0: Command WRITE(10) took 4.455 seconds (ok)
Aug 20 20:10:58.540: vmx| scsi0:0: Command WRITE(10) took 4.340 seconds (ok)
Aug 20 20:10:58.540: vmx| scsi0:0: Command WRITE(10) took 1.933 seconds (ok)
Aug 20 20:10:58.541: vmx| scsi0:0: Command WRITE(10) took 4.084 seconds (ok)
Aug 20 20:11:06.678: vmx| scsi0:0: Command WRITE(10) took 1.092 seconds (ok)
Aug 20 20:11:06.681: vmx| scsi0:0: Command WRITE(10) took 1.090 seconds (ok)
Aug 20 20:11:09.214: vmx| ide1:0: Command READ(10) took 1.155 seconds (ok)
Aug 20 20:11:09.217: vmx| scsi0:0: Command WRITE(10) took 1.146 seconds (ok)
Aug 20 20:11:09.220: vmx| scsi0:0: Command WRITE(10) took 1.288 seconds (ok)
Aug 20 20:11:09.287: vmx| scsi0:0: Command WRITE(10) took 1.243 seconds (ok)
Aug 20 20:11:09.288: vmx| scsi0:0: Command WRITE(10) took 1.243 seconds (ok)
Aug 20 20:11:09.288: vmx| scsi0:0: Command WRITE(10) took 1.241 seconds (ok)
Aug 20 20:11:09.289: vmx| scsi0:0: Command WRITE(10) took 1.239 seconds (ok)
Aug 20 20:11:09.296: vmx| scsi0:0: Command WRITE(10) took 1.242 seconds (ok)
Aug 20 20:11:09.297: vmx| scsi0:0: Command WRITE(10) took 1.241 seconds (ok)
Aug 20 20:11:30.326: vcpu-0| UHCI: HCReset
Aug 20 20:11:30.540: vcpu-0| CPU reset: soft (mode 2)
Aug 20 20:11:30.737: vcpu-0| PCIBridge4: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:30.906: vcpu-0| pciBridge4:1: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:31.043: vcpu-0| pciBridge4:2: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:31.199: vcpu-0| pciBridge4:3: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:31.365: vcpu-0| pciBridge4:4: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:31.535: vcpu-0| pciBridge4:5: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:31.703: vcpu-0| pciBridge4:6: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:31.872: vcpu-0| pciBridge4:7: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:32.052: vcpu-0| PCIBridge5: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:32.312: vcpu-0| pciBridge5:1: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:32.514: vcpu-0| pciBridge5:2: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:32.696: vcpu-0| pciBridge5:3: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:32.896: vcpu-0| pciBridge5:4: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:33.090: vcpu-0| pciBridge5:5: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:33.286: vcpu-0| pciBridge5:6: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:33.482: vcpu-0| pciBridge5:7: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:33.674: vcpu-0| PCIBridge6: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:33.856: vcpu-0| pciBridge6:1: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:33.964: vcpu-0| pciBridge6:2: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:34.003: vcpu-0| pciBridge6:3: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:34.004: vcpu-0| pciBridge6:4: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:34.004: vcpu-0| pciBridge6:5: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:34.005: vcpu-0| pciBridge6:6: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:34.005: vcpu-0| pciBridge6:7: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:34.006: vcpu-0| PCIBridge7: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:34.007: vcpu-0| pciBridge7:1: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:34.007: vcpu-0| pciBridge7:2: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:34.008: vcpu-0| pciBridge7:3: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:34.008: vcpu-0| pciBridge7:4: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:34.009: vcpu-0| pciBridge7:5: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:34.009: vcpu-0| pciBridge7:6: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:34.010: vcpu-0| pciBridge7:7: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:34.280: vcpu-0| SVGA: Unregistering IOSpace at 0x10f0
Aug 20 20:11:34.281: vcpu-0| SVGA: Unregistering MemSpace at 0xd0000000(0xd0000000) and 0xd8000000(0xd8000000)
Aug 20 20:11:34.300: vcpu-0| PCIBridge4: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:34.300: vcpu-0| pciBridge4:1: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:34.301: vcpu-0| pciBridge4:2: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:34.301: vcpu-0| pciBridge4:3: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:34.302: vcpu-0| pciBridge4:4: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:34.302: vcpu-0| pciBridge4:5: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:34.302: vcpu-0| pciBridge4:6: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:34.303: vcpu-0| pciBridge4:7: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:34.303: vcpu-0| PCIBridge5: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:34.304: vcpu-0| pciBridge5:1: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:34.304: vcpu-0| pciBridge5:2: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:34.305: vcpu-0| pciBridge5:3: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:34.305: vcpu-0| pciBridge5:4: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:34.305: vcpu-0| pciBridge5:5: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:34.306: vcpu-0| pciBridge5:6: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:34.306: vcpu-0| pciBridge5:7: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:34.307: vcpu-0| PCIBridge6: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:34.307: vcpu-0| pciBridge6:1: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:34.308: vcpu-0| pciBridge6:2: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:34.308: vcpu-0| pciBridge6:3: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:34.309: vcpu-0| pciBridge6:4: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:34.309: vcpu-0| pciBridge6:5: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:34.310: vcpu-0| pciBridge6:6: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:34.310: vcpu-0| pciBridge6:7: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:34.311: vcpu-0| PCIBridge7: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:34.311: vcpu-0| pciBridge7:1: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:34.312: vcpu-0| pciBridge7:2: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:34.312: vcpu-0| pciBridge7:3: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:34.313: vcpu-0| pciBridge7:4: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:34.313: vcpu-0| pciBridge7:5: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:34.313: vcpu-0| pciBridge7:6: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:34.314: vcpu-0| pciBridge7:7: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:34.574: vcpu-0| SVGA: Registering MemSpace at 0xd0000000(0xd0000000) and 0xd8000000(0xd8000000)
Aug 20 20:11:34.581: vcpu-0| SVGA: Unregistering MemSpace at 0xd0000000(0xd0000000) and 0xd8000000(0xd8000000)
Aug 20 20:11:34.764: vcpu-0| SVGA: Registering MemSpace at 0xd0000000(0xd0000000) and 0xd8000000(0xd8000000)
Aug 20 20:11:34.773: vcpu-0| SVGA: Unregistering MemSpace at 0xd0000000(0xd0000000) and 0xd8000000(0xd8000000)
Aug 20 20:11:34.791: vcpu-0| SVGA: Registering IOSpace at 0x10f0
Aug 20 20:11:34.791: vcpu-0| SVGA: Registering MemSpace at 0xd0000000(0xd0000000) and 0xd8000000(0xd8000000)
Aug 20 20:11:34.798: vcpu-0| PCIBridge4: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:34.800: vcpu-0| pciBridge4:1: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:34.801: vcpu-0| pciBridge4:2: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:34.803: vcpu-0| pciBridge4:3: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:34.804: vcpu-0| pciBridge4:4: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:34.806: vcpu-0| pciBridge4:5: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:34.807: vcpu-0| pciBridge4:6: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:34.809: vcpu-0| pciBridge4:7: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:34.810: vcpu-0| PCIBridge5: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:34.811: vcpu-0| pciBridge5:1: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:34.813: vcpu-0| pciBridge5:2: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:34.815: vcpu-0| pciBridge5:3: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:34.816: vcpu-0| pciBridge5:4: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:34.818: vcpu-0| pciBridge5:5: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:34.819: vcpu-0| pciBridge5:6: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:34.821: vcpu-0| pciBridge5:7: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:34.822: vcpu-0| PCIBridge6: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:34.824: vcpu-0| pciBridge6:1: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:34.825: vcpu-0| pciBridge6:2: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:34.827: vcpu-0| pciBridge6:3: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:34.828: vcpu-0| pciBridge6:4: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:34.830: vcpu-0| pciBridge6:5: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:34.831: vcpu-0| pciBridge6:6: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:34.833: vcpu-0| pciBridge6:7: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:34.834: vcpu-0| PCIBridge7: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:34.835: vcpu-0| pciBridge7:1: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:34.837: vcpu-0| pciBridge7:2: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:34.838: vcpu-0| pciBridge7:3: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:34.840: vcpu-0| pciBridge7:4: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:34.841: vcpu-0| pciBridge7:5: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:34.843: vcpu-0| pciBridge7:6: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:34.844: vcpu-0| pciBridge7:7: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:34.916: mks| HostOps hideCursor before defineCursor!
Aug 20 20:11:35.128: vcpu-0| PCIBridge4: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:35.129: vcpu-0| pciBridge4:1: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:35.131: vcpu-0| pciBridge4:2: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:35.132: vcpu-0| pciBridge4:3: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:35.134: vcpu-0| pciBridge4:4: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:35.135: vcpu-0| pciBridge4:5: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:35.137: vcpu-0| pciBridge4:6: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:35.138: vcpu-0| pciBridge4:7: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:35.140: vcpu-0| PCIBridge5: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:35.142: vcpu-0| pciBridge5:1: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:35.143: vcpu-0| pciBridge5:2: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:35.144: vcpu-0| pciBridge5:3: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:35.146: vcpu-0| pciBridge5:4: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:35.147: vcpu-0| pciBridge5:5: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:35.149: vcpu-0| pciBridge5:6: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:35.150: vcpu-0| pciBridge5:7: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:35.151: vcpu-0| PCIBridge6: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:35.153: vcpu-0| pciBridge6:1: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:35.154: vcpu-0| pciBridge6:2: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:35.156: vcpu-0| pciBridge6:3: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:35.157: vcpu-0| pciBridge6:4: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:35.159: vcpu-0| pciBridge6:5: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:35.160: vcpu-0| pciBridge6:6: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:35.162: vcpu-0| pciBridge6:7: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:35.163: vcpu-0| PCIBridge7: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:35.166: vcpu-0| pciBridge7:1: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:35.167: vcpu-0| pciBridge7:2: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:35.171: vcpu-0| pciBridge7:3: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:35.173: vcpu-0| pciBridge7:4: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:35.185: vcpu-0| pciBridge7:5: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:35.187: vcpu-0| pciBridge7:6: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:35.197: vcpu-0| pciBridge7:7: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:35.213: vcpu-0| DISKUTIL: scsi0:0 : geometry=1174/255/56
Aug 20 20:11:35.213: vcpu-0| DISKUTIL: scsi0:0 : capacity=16777216
Aug 20 20:11:35.341: vcpu-0| BIOS-UUID is 56 4d eb d5 e8 72 83 5f-07 36 3b 58 1e a6 25 c9
Aug 20 20:11:35.895: mks| HostOps hideCursor before defineCursor!
Aug 20 20:11:36.585: vcpu-0| BUSLOGIC: Store HAL[16] = 0xfff8
Aug 20 20:11:36.586: vcpu-0| BUSLOGIC: Store HAL[18] = 0xfe01
Aug 20 20:11:36.587: vcpu-0| BUSLOGIC: Store HAL[16] = 0xfff8
Aug 20 20:11:36.588: vcpu-0| BUSLOGIC: Store HAL[18] = 0xfe01
Aug 20 20:11:36.592: vcpu-0| BUSLOGIC: Store HAL[16] = 0xfff8
Aug 20 20:11:36.592: vcpu-0| BUSLOGIC: Store HAL[18] = 0xfe01
Aug 20 20:11:36.649: vcpu-0| Unknown int 10h func 0x2000
Aug 20 20:11:36.666: vcpu-0| BUSLOGIC: Store HAL[16] = 0xfff8
Aug 20 20:11:36.667: vcpu-0| BUSLOGIC: Store HAL[18] = 0xfe01
Aug 20 20:11:36.669: vcpu-0| BUSLOGIC: Store HAL[16] = 0xfff8
Aug 20 20:11:36.669: vcpu-0| BUSLOGIC: Store HAL[18] = 0xfe01
Aug 20 20:11:36.740: vcpu-0| BUSLOGIC: Store HAL[16] = 0xfff8
Aug 20 20:11:36.741: vcpu-0| BUSLOGIC: Store HAL[18] = 0xfe01
Aug 20 20:11:36.745: vcpu-0| BUSLOGIC: Store HAL[16] = 0xfff8
Aug 20 20:11:36.745: vcpu-0| BUSLOGIC: Store HAL[18] = 0xfe01
Aug 20 20:11:36.777: vcpu-0| BUSLOGIC: Store HAL[20] = 0x00fb
Aug 20 20:11:36.777: vcpu-0| BUSLOGIC: Store HAL[22] = 0x0400
Aug 20 20:11:36.778: vcpu-0| BUSLOGIC: Store HAL[16] = 0xfff8
Aug 20 20:11:36.778: vcpu-0| BUSLOGIC: Store HAL[18] = 0xfe01
Aug 20 20:11:36.806: vcpu-0| BUSLOGIC: Store HAL[16] = 0xfff8
Aug 20 20:11:36.806: vcpu-0| BUSLOGIC: Store HAL[18] = 0xfe01
Aug 20 20:11:36.811: vcpu-0| BUSLOGIC: Store HAL[16] = 0xfff8
Aug 20 20:11:36.811: vcpu-0| BUSLOGIC: Store HAL[18] = 0xfe01
Aug 20 20:11:36.813: vcpu-0| BUSLOGIC: Store HAL[16] = 0xfff8
Aug 20 20:11:36.813: vcpu-0| BUSLOGIC: Store HAL[18] = 0xfe01
Aug 20 20:11:37.513: mks| HostOps hideCursor before defineCursor!
Aug 20 20:11:38.813: vcpu-0| SVGA: Unregistering IOSpace at 0x10f0
Aug 20 20:11:38.814: vcpu-0| SVGA: Unregistering MemSpace at 0xd0000000(0xd0000000) and 0xd8000000(0xd8000000)
Aug 20 20:11:38.832: vcpu-0| SVGA: Registering IOSpace at 0x10f0
Aug 20 20:11:38.832: vcpu-0| SVGA: Registering MemSpace at 0xd0000000(0xd0000000) and 0xd8000000(0xd8000000)
Aug 20 20:11:38.837: vcpu-0| PCIBridge4: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:38.837: vcpu-0| PCIBridge4: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:38.839: vcpu-0| pciBridge4:1: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:38.839: vcpu-0| pciBridge4:1: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:38.840: vcpu-0| pciBridge4:2: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:38.841: vcpu-0| pciBridge4:2: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:38.842: vcpu-0| pciBridge4:3: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:38.843: vcpu-0| pciBridge4:3: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:38.844: vcpu-0| pciBridge4:4: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:38.845: vcpu-0| pciBridge4:4: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:38.846: vcpu-0| pciBridge4:5: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:38.846: vcpu-0| pciBridge4:5: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:38.848: vcpu-0| pciBridge4:6: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:38.848: vcpu-0| pciBridge4:6: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:38.849: vcpu-0| pciBridge4:7: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:38.850: vcpu-0| pciBridge4:7: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:38.851: vcpu-0| PCIBridge5: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:38.851: vcpu-0| PCIBridge5: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:38.852: vcpu-0| pciBridge5:1: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:38.853: vcpu-0| pciBridge5:1: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:38.854: vcpu-0| pciBridge5:2: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:38.854: vcpu-0| pciBridge5:2: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:38.855: vcpu-0| pciBridge5:3: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:38.856: vcpu-0| pciBridge5:3: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:38.857: vcpu-0| pciBridge5:4: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:38.858: vcpu-0| pciBridge5:4: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:38.859: vcpu-0| pciBridge5:5: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:38.859: vcpu-0| pciBridge5:5: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:38.861: vcpu-0| pciBridge5:6: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:38.861: vcpu-0| pciBridge5:6: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:38.862: vcpu-0| pciBridge5:7: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:38.863: vcpu-0| pciBridge5:7: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:38.864: vcpu-0| PCIBridge6: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:38.864: vcpu-0| PCIBridge6: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:38.865: vcpu-0| pciBridge6:1: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:38.866: vcpu-0| pciBridge6:1: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:38.867: vcpu-0| pciBridge6:2: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:38.867: vcpu-0| pciBridge6:2: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:38.869: vcpu-0| pciBridge6:3: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:38.869: vcpu-0| pciBridge6:3: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:38.870: vcpu-0| pciBridge6:4: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:38.871: vcpu-0| pciBridge6:4: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:38.872: vcpu-0| pciBridge6:5: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:38.872: vcpu-0| pciBridge6:5: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:38.874: vcpu-0| pciBridge6:6: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:38.874: vcpu-0| pciBridge6:6: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:38.875: vcpu-0| pciBridge6:7: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:38.876: vcpu-0| pciBridge6:7: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:38.877: vcpu-0| PCIBridge7: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:38.877: vcpu-0| PCIBridge7: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:38.878: vcpu-0| pciBridge7:1: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:38.879: vcpu-0| pciBridge7:1: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:38.880: vcpu-0| pciBridge7:2: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:38.880: vcpu-0| pciBridge7:2: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:38.882: vcpu-0| pciBridge7:3: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:38.882: vcpu-0| pciBridge7:3: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:38.883: vcpu-0| pciBridge7:4: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:38.884: vcpu-0| pciBridge7:4: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:38.885: vcpu-0| pciBridge7:5: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:38.886: vcpu-0| pciBridge7:5: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:38.887: vcpu-0| pciBridge7:6: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:38.887: vcpu-0| pciBridge7:6: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:38.889: vcpu-0| pciBridge7:7: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:38.889: vcpu-0| pciBridge7:7: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:39.388: vcpu-0| PCIBridge4: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:39.393: vcpu-0| pciBridge4:1: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:39.397: vcpu-0| pciBridge4:2: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:39.402: vcpu-0| pciBridge4:3: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:39.406: vcpu-0| pciBridge4:4: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:39.410: vcpu-0| pciBridge4:5: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:39.415: vcpu-0| pciBridge4:6: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:39.419: vcpu-0| pciBridge4:7: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:39.424: vcpu-0| PCIBridge5: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:39.428: vcpu-0| pciBridge5:1: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:39.432: vcpu-0| pciBridge5:2: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:39.438: vcpu-0| pciBridge5:3: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:39.443: vcpu-0| pciBridge5:4: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:39.447: vcpu-0| pciBridge5:5: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:39.451: vcpu-0| pciBridge5:6: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:39.456: vcpu-0| pciBridge5:7: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:39.460: vcpu-0| PCIBridge6: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:39.464: vcpu-0| pciBridge6:1: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:39.468: vcpu-0| pciBridge6:2: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:39.473: vcpu-0| pciBridge6:3: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:39.477: vcpu-0| pciBridge6:4: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:39.481: vcpu-0| pciBridge6:5: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:39.485: vcpu-0| pciBridge6:6: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:39.490: vcpu-0| pciBridge6:7: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:39.494: vcpu-0| PCIBridge7: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:39.497: vcpu-0| pciBridge7:1: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:39.502: vcpu-0| pciBridge7:2: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:39.506: vcpu-0| pciBridge7:3: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:39.511: vcpu-0| pciBridge7:4: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:39.515: vcpu-0| pciBridge7:5: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:39.519: vcpu-0| pciBridge7:6: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:39.524: vcpu-0| pciBridge7:7: ISA/VGA decoding enabled (ctrl 0004)
Aug 20 20:11:43.028: vcpu-0| CDROM: Mode Sense for Unsupported Page 0x1B
Aug 20 20:11:43.028: vcpu-0| SCSI DEVICE (ide1:0): MODE SENSE(10) for unsupported page 0x1b
Aug 20 20:11:43.050: vcpu-0| DISKUTIL: scsi0:0 : geometry=1174/255/56
Aug 20 20:11:43.052: vcpu-0| DISKUTIL: scsi0:0 : capacity=16777216
Aug 20 20:11:43.052: vcpu-0| SCSI0: RESET BUS
Aug 20 20:11:43.068: vcpu-0| DISKUTIL: scsi0:0 : geometry=1174/255/56
Aug 20 20:11:43.069: vcpu-0| DISKUTIL: scsi0:0 : capacity=16777216
Aug 20 20:11:43.135: vcpu-0| SCSI DEVICE (scsi0:0): MODE SENSE(6) for unsupported page 0x1c
Aug 20 20:11:43.523: vcpu-0| CDROM: Emulate GET CONFIGURATION RT 0 start feature 0
Aug 20 20:11:43.523: vcpu-0| CDROM: Emulate GET CONFIGURATION RT 0 start feature 0
Aug 20 20:11:43.524: vcpu-0| CDROM: Emulate GET CONFIGURATION RT 0 start feature 0
Aug 20 20:11:43.558: vcpu-0| UHCI: Global Reset
Aug 20 20:11:46.415: mks| MKS switching absolute mouse on
Aug 20 20:12:08.766: vmx| GuestRpcSendTimedOut: message to toolbox timed out.
Aug 20 20:12:08.808: vmx| Vix: [10584 guestCommands.c:2392]: Error VIX_E_TOOLS_NOT_RUNNING in VMAutomationTranslateGuestRpcError(): VMware Tools are not running in the guest
Aug 20 20:12:08.809: vmx| scsi0:0: Command READ(10) took 16.407 seconds (ok)
Aug 20 20:12:08.810: vmx| scsi0:0: Command WRITE(10) took 15.371 seconds (ok)
Aug 20 20:12:24.861: mks| MKS lock got type None
Aug 20 20:12:27.695: mks| MKS lost grab
Aug 20 20:12:28.498: mks| MKS lost grab
Aug 20 20:12:30.471: mks| MKS lost grab
Aug 20 20:12:33.729: mks| MKS lost grab
Aug 20 20:12:35.846: mks| MKS lost grab
Aug 20 20:12:38.115: mks| MKS lost grab
Aug 20 20:13:11.434: vmx| scsi0:0: Command WRITE(10) took 1.110 seconds (ok)
Aug 20 20:13:11.633: vmx| scsi0:0: Command WRITE(10) took 1.309 seconds (ok)
Aug 20 20:13:11.826: vmx| scsi0:0: Command WRITE(10) took 1.290 seconds (ok)
Aug 20 20:13:13.642: vmx| scsi0:0: Command WRITE(10) took 1.076 seconds (ok)
Aug 20 20:13:16.535: vmx| scsi0:0: Command WRITE(10) took 1.191 seconds (ok)
Aug 20 20:13:16.738: vmx| scsi0:0: Command WRITE(10) took 1.168 seconds (ok)
Aug 20 20:13:31.037: vmx| scsi0:0: Command WRITE(10) took 1.087 seconds (ok)
Aug 20 20:13:31.255: vmx| scsi0:0: Command WRITE(10) took 1.074 seconds (ok)
Aug 20 20:13:32.713: vmx| scsi0:0: Command WRITE(10) took 1.013 seconds (ok)
Aug 20 20:13:36.784: vmx| scsi0:0: Command WRITE(10) took 3.043 seconds (ok)
Aug 20 20:13:37.116: vmx| scsi0:0: Command WRITE(10) took 3.301 seconds (ok)
Aug 20 20:13:37.335: vmx| scsi0:0: Command WRITE(10) took 3.074 seconds (ok)
Aug 20 20:13:37.335: vmx| scsi0:0: Command WRITE(10) took 2.593 seconds (ok)
Aug 20 20:13:37.336: vmx| scsi0:0: Command WRITE(10) took 1.594 seconds (ok)
Aug 20 20:13:37.336: vmx| scsi0:0: Command WRITE(10) took 1.251 seconds (ok)
Aug 20 20:14:12.811: vmx| scsi0:0: Command WRITE(10) took 3.991 seconds (ok)
Aug 20 20:14:13.953: vmx| scsi0:0: Command WRITE(10) took 4.750 seconds (ok)
Aug 20 20:14:14.212: vmx| scsi0:0: Command WRITE(10) took 3.543 seconds (ok)
Aug 20 20:14:14.692: vmx| scsi0:0: Command WRITE(10) took 5.077 seconds (ok)
Aug 20 20:14:15.039: vmx| scsi0:0: Command WRITE(10) took 1.986 seconds (ok)
Aug 20 20:14:17.186: vmx| scsi0:0: Command WRITE(10) took 2.716 seconds (ok)
Aug 20 20:14:17.491: vmx| scsi0:0: Command WRITE(10) took 3.019 seconds (ok)
Aug 20 20:14:19.823: vmx| scsi0:0: Command WRITE(10) took 4.895 seconds (ok)
Aug 20 20:14:20.870: vmx| scsi0:0: Command WRITE(10) took 5.568 seconds (ok)
Aug 20 20:14:24.045: vmx| scsi0:0: Command WRITE(10) took 6.556 seconds (ok)
Aug 20 20:14:24.313: vmx| scsi0:0: Command WRITE(10) took 6.572 seconds (ok)
Aug 20 20:14:31.468: vmx| scsi0:0: Command WRITE(10) took 10.348 seconds (ok)
Aug 20 20:14:32.046: vmx| scsi0:0: Command WRITE(10) took 11.952 seconds (ok)
Aug 20 20:14:32.515: vmx| scsi0:0: Command WRITE(10) took 7.916 seconds (ok)
Aug 20 20:14:32.775: vmx| scsi0:0: Command WRITE(10) took 8.175 seconds (ok)
Aug 20 20:14:33.187: vmx| scsi0:0: Command WRITE(10) took 1.444 seconds (ok)
Aug 20 20:14:36.352: vmx| scsi0:0: Command WRITE(10) took 4.011 seconds (ok)
Aug 20 20:14:36.627: vmx| scsi0:0: Command WRITE(10) took 3.572 seconds (ok)
Aug 20 20:14:37.011: vmx| scsi0:0: Command WRITE(10) took 3.957 seconds (ok)
Aug 20 20:14:37.848: vmx| scsi0:0: Command WRITE(10) took 4.377 seconds (ok)
Aug 20 20:14:38.404: vmx| scsi0:0: Command WRITE(10) took 1.515 seconds (ok)
Aug 20 20:14:38.668: vmx| scsi0:0: Command WRITE(10) took 1.778 seconds (ok)
Aug 20 20:14:42.817: vmx| scsi0:0: Command WRITE(10) took 5.531 seconds (ok)
Aug 20 20:14:46.481: vmx| scsi0:0: Command WRITE(10) took 8.224 seconds (ok)
Aug 20 20:14:50.049: vmx| scsi0:0: Command WRITE(10) took 11.382 seconds (ok)
Aug 20 20:14:50.337: vmx| scsi0:0: Command WRITE(10) took 11.395 seconds (ok)
Aug 20 20:14:51.588: vmx| scsi0:0: Command WRITE(10) took 8.213 seconds (ok)
Aug 20 20:14:51.864: vmx| scsi0:0: Command WRITE(10) took 5.069 seconds (ok)
Aug 20 20:14:53.257: vmx| scsi0:0: Command WRITE(10) took 1.101 seconds (ok)
Aug 20 20:14:54.051: vmx| scsi0:0: Command WRITE(10) took 1.895 seconds (ok)
Aug 20 20:14:54.373: vmx| scsi0:0: Command WRITE(10) took 2.217 seconds (ok)
Aug 20 20:14:55.105: vmx| scsi0:0: Command WRITE(10) took 2.464 seconds (ok)
Aug 20 20:14:56.663: vmx| scsi0:0: Command WRITE(10) took 3.088 seconds (ok)
Aug 20 20:15:00.473: vmx| scsi0:0: Command WRITE(10) took 6.100 seconds (ok)
Aug 20 20:15:00.823: vmx| scsi0:0: Command WRITE(10) took 6.119 seconds (ok)
Aug 20 20:15:01.173: vmx| scsi0:0: Command WRITE(10) took 6.450 seconds (ok)
Aug 20 20:15:01.555: vmx| scsi0:0: Command WRITE(10) took 6.833 seconds (ok)
Aug 20 20:15:01.989: vmx| scsi0:0: Command WRITE(10) took 6.506 seconds (ok)
Aug 20 20:15:02.440: vmx| scsi0:0: Command WRITE(10) took 6.073 seconds (ok)
Aug 20 20:15:02.766: vmx| scsi0:0: Command WRITE(10) took 6.400 seconds (ok)
Aug 20 20:15:03.098: vmx| scsi0:0: Command WRITE(10) took 5.731 seconds (ok)
Aug 20 20:15:03.409: vmx| scsi0:0: Command WRITE(10) took 5.042 seconds (ok)
Aug 20 20:15:03.737: vmx| scsi0:0: Command WRITE(10) took 5.370 seconds (ok)
Aug 20 20:15:04.070: vmx| scsi0:0: Command WRITE(10) took 4.704 seconds (ok)
Aug 20 20:15:04.399: vmx| scsi0:0: Command WRITE(10) took 4.032 seconds (ok)
Aug 20 20:15:04.739: vmx| scsi0:0: Command WRITE(10) took 4.372 seconds (ok)
Aug 20 20:15:05.210: vmx| scsi0:0: Command WRITE(10) took 9.771 seconds (ok)
Aug 20 20:15:06.554: vmx| scsi0:0: Command WRITE(10) took 9.575 seconds (ok)
Aug 20 20:15:09.514: vmx| scsi0:0: Command WRITE(10) took 7.552 seconds (ok)
Aug 20 20:15:11.754: vmx| scsi0:0: Command WRITE(10) took 9.792 seconds (ok)
Aug 20 20:15:56.597: vcpu-0| scsi0:0: Command WRITE(10) took 46.554 seconds (ok)
Aug 20 20:15:57.072: vcpu-0| scsi0:0: Command WRITE(10) took 51.864 seconds (ok)
Aug 20 20:15:57.505: vcpu-0| scsi0:0: Command WRITE(10) took 47.393 seconds (ok)
Aug 20 20:15:57.911: vcpu-0| scsi0:0: Command WRITE(10) took 47.800 seconds (ok)
Aug 20 20:15:58.274: vcpu-0| scsi0:0: Command WRITE(10) took 47.829 seconds (ok)
Aug 20 20:15:58.714: vcpu-0| scsi0:0: Command WRITE(10) took 47.121 seconds (ok)
Aug 20 20:15:59.111: vcpu-0| scsi0:0: Command WRITE(10) took 47.518 seconds (ok)
Aug 20 20:15:59.494: vcpu-0| scsi0:0: Command WRITE(10) took 53.933 seconds (ok)
Aug 20 20:15:59.954: vcpu-0| scsi0:0: Command WRITE(10) took 53.144 seconds (ok)
Aug 20 20:16:00.358: vcpu-0| scsi0:0: Command WRITE(10) took 54.510 seconds (ok)
Aug 20 20:16:00.874: vcpu-0| scsi0:0: Command WRITE(10) took 55.025 seconds (ok)
Aug 20 20:16:01.280: vcpu-0| scsi0:0: Command WRITE(10) took 48.914 seconds (ok)
Aug 20 20:16:01.663: vcpu-0| scsi0:0: Command WRITE(10) took 51.619 seconds (ok)
Aug 20 20:16:02.094: vcpu-0| scsi0:0: Command WRITE(10) took 52.050 seconds (ok)
Aug 20 20:16:02.520: vcpu-0| scsi0:0: Command WRITE(10) took 56.338 seconds (ok)
Aug 20 20:16:02.971: vcpu-0| scsi0:0: Command WRITE(10) took 56.789 seconds (ok)
Aug 20 20:16:03.440: vcpu-0| scsi0:0: Command WRITE(10) took 56.924 seconds (ok)
Aug 20 20:16:03.912: vcpu-0| scsi0:0: Command WRITE(10) took 56.847 seconds (ok)
Aug 20 20:16:04.361: vcpu-0| scsi0:0: Command WRITE(10) took 57.296 seconds (ok)
Aug 20 20:16:04.859: vcpu-0| scsi0:0: Command WRITE(10) took 57.460 seconds (ok)
Aug 20 20:16:05.328: vcpu-0| scsi0:0: Command WRITE(10) took 57.929 seconds (ok)
Aug 20 20:16:05.733: vcpu-0| scsi0:0: Command WRITE(10) took 58.001 seconds (ok)
Aug 20 20:16:06.380: vcpu-0| scsi0:0: Command WRITE(10) took 58.647 seconds (ok)
Aug 20 20:16:06.783: vcpu-0| scsi0:0: Command WRITE(10) took 58.417 seconds (ok)
Aug 20 20:16:07.235: vcpu-0| scsi0:0: Command WRITE(10) took 57.378 seconds (ok)
Aug 20 20:16:07.681: vcpu-0| scsi0:0: Command WRITE(10) took 57.638 seconds (ok)
Aug 20 20:16:08.132: vcpu-0| scsi0:0: Command WRITE(10) took 58.089 seconds (ok)
Aug 20 20:16:08.569: vcpu-0| scsi0:0: Command WRITE(10) took 58.525 seconds (ok)
Aug 20 20:16:09.084: vcpu-0| scsi0:0: Command WRITE(10) took 58.973 seconds (ok)
Aug 20 20:16:09.532: vcpu-0| scsi0:0: Command WRITE(10) took 59.421 seconds (ok)
Aug 20 20:16:09.953: vcpu-0| scsi0:0: Command WRITE(10) took 57.822 seconds (ok)
Aug 20 20:16:10.386: vcpu-0| scsi0:0: Command WRITE(10) took 58.255 seconds (ok)
Aug 20 20:16:10.904: vcpu-0| scsi0:0: Command WRITE(10) took 13.833 seconds (ok)
Aug 20 20:16:11.360: vcpu-0| scsi0:0: Command WRITE(10) took 13.855 seconds (ok)
Aug 20 20:16:11.830: vcpu-0| scsi0:0: Command WRITE(10) took 13.919 seconds (ok)
Aug 20 20:16:12.294: vcpu-0| scsi0:0: Command WRITE(10) took 14.021 seconds (ok)
Aug 20 20:16:12.740: vcpu-0| scsi0:0: Command WRITE(10) took 14.026 seconds (ok)
Aug 20 20:16:13.033: vcpu-0| scsi0:0: Command WRITE(10) took 13.922 seconds (ok)
Aug 20 20:16:13.033: vcpu-0| scsi0:0: Command WRITE(10) took 13.539 seconds (ok)
Aug 20 20:16:13.034: vcpu-0| scsi0:0: Command WRITE(10) took 13.080 seconds (ok)
Aug 20 20:16:13.034: vcpu-0| SCSI0: RESET BUS
Aug 20 20:16:15.781: mks| MKS lost grab
Aug 20 20:16:49.412: vmx| scsi0:0: Command WRITE(10) took 2.311 seconds (ok)
Aug 20 20:16:49.850: vmx| scsi0:0: Command WRITE(10) took 2.517 seconds (ok)
Aug 20 20:16:51.904: vmx| scsi0:0: Command WRITE(10) took 3.803 seconds (ok)
Aug 20 20:16:52.344: vmx| scsi0:0: Command WRITE(10) took 3.243 seconds (ok)
Aug 20 20:16:52.802: vmx| scsi0:0: Command WRITE(10) took 2.952 seconds (ok)
Aug 20 20:16:53.250: vmx| scsi0:0: Command WRITE(10) took 2.962 seconds (ok)
Aug 20 20:16:55.454: vmx| scsi0:0: Command WRITE(10) took 1.112 seconds (ok)
Aug 20 20:16:56.846: vmx| scsi0:0: Command WRITE(10) took 1.822 seconds (ok)
Aug 20 20:16:58.855: vmx| scsi0:0: Command WRITE(10) took 3.785 seconds (ok)
Aug 20 20:16:59.308: vmx| scsi0:0: Command WRITE(10) took 3.426 seconds (ok)
Aug 20 20:17:01.082: vmx| scsi0:0: Command WRITE(10) took 1.217 seconds (ok)
Aug 20 20:17:01.562: vmx| scsi0:0: Command WRITE(10) took 1.369 seconds (ok)
Aug 20 20:17:02.061: vmx| scsi0:0: Command WRITE(10) took 1.305 seconds (ok)
Aug 20 20:17:02.526: vmx| scsi0:0: Command WRITE(10) took 1.661 seconds (ok)
Aug 20 20:17:02.964: vmx| scsi0:0: Command WRITE(10) took 1.403 seconds (ok)
Aug 20 20:17:04.570: vmx| scsi0:0: Command WRITE(10) took 1.138 seconds (ok)
Aug 20 20:17:05.036: vmx| scsi0:0: Command WRITE(10) took 1.604 seconds (ok)
Aug 20 20:17:14.275: vmx| scsi0:0: Command WRITE(10) took 1.931 seconds (ok)
Aug 20 20:17:21.321: vmx| scsi0:0: Command WRITE(10) took 1.793 seconds (ok)
Aug 20 20:17:24.268: vmx| scsi0:0: Command WRITE(10) took 1.458 seconds (ok)
Aug 20 20:17:24.709: vmx| scsi0:0: Command WRITE(10) took 1.358 seconds (ok)
Aug 20 20:17:25.179: vmx| scsi0:0: Command WRITE(10) took 1.828 seconds (ok)
Aug 20 20:17:27.144: vmx| scsi0:0: Command WRITE(10) took 1.466 seconds (ok)
Aug 20 20:17:31.345: vmx| scsi0:0: Command WRITE(10) took 1.781 seconds (ok)
Aug 20 20:17:33.864: vmx| scsi0:0: Command WRITE(10) took 1.027 seconds (ok)
Aug 20 20:17:34.348: vmx| scsi0:0: Command WRITE(10) took 1.510 seconds (ok)
Aug 20 20:17:36.396: vmx| scsi0:0: Command WRITE(10) took 1.004 seconds (ok)
Aug 20 20:17:39.402: vmx| scsi0:0: Command WRITE(10) took 1.003 seconds (ok)
Aug 20 20:17:43.801: vmx| scsi0:0: Command WRITE(10) took 1.557 seconds (ok)
Aug 20 20:17:44.327: vmx| scsi0:0: Command WRITE(10) took 3.445 seconds (ok)
Aug 20 20:17:44.855: mks| MKS lost grab
Aug 20 20:17:46.886: vmx| scsi0:0: Command WRITE(10) took 1.020 seconds (ok)
Aug 20 20:17:49.032: vmx| scsi0:0: Command WRITE(10) took 1.636 seconds (ok)
Aug 20 20:17:51.265: vmx| scsi0:0: Command WRITE(10) took 3.339 seconds (ok)
Aug 20 20:17:54.108: vmx| scsi0:0: Command WRITE(10) took 1.397 seconds (ok)
Aug 20 20:17:54.631: vmx| scsi0:0: Command WRITE(10) took 1.234 seconds (ok)
Aug 20 20:17:56.569: vmx| scsi0:0: Command WRITE(10) took 1.407 seconds (ok)
Aug 20 20:17:58.488: vmx| scsi0:0: Command WRITE(10) took 1.362 seconds (ok)
Aug 20 20:18:00.150: vmx| scsi0:0: Command WRITE(10) took 1.102 seconds (ok)
Aug 20 20:18:00.682: vmx| scsi0:0: Command WRITE(10) took 1.462 seconds (ok)
Aug 20 20:18:03.267: vmx| scsi0:0: Command WRITE(10) took 1.436 seconds (ok)
Aug 20 20:18:06.723: vmx| scsi0:0: Command WRITE(10) took 2.337 seconds (ok)
Aug 20 20:18:10.920: vmx| scsi0:0: Command WRITE(10) took 2.501 seconds (ok)
Aug 20 20:18:11.506: vmx| scsi0:0: Command WRITE(10) took 2.504 seconds (ok)
Aug 20 20:18:17.397: vmx| scsi0:0: Command WRITE(10) took 1.832 seconds (ok)
Aug 20 20:18:17.969: vmx| scsi0:0: Command WRITE(10) took 2.403 seconds (ok)
Aug 20 20:18:20.116: vmx| scsi0:0: Command WRITE(10) took 1.532 seconds (ok)
Aug 20 20:18:22.521: vmx| scsi0:0: Command WRITE(10) took 1.822 seconds (ok)
Aug 20 20:18:25.887: vmx| scsi0:0: Command WRITE(10) took 2.749 seconds (ok)
Aug 20 20:18:29.900: vmx| scsi0:0: Command WRITE(10) took 3.418 seconds (ok)
Aug 20 20:18:33.334: vmx| scsi0:0: Command WRITE(10) took 1.555 seconds (ok)
Aug 20 20:18:35.592: vmx| scsi0:0: Command WRITE(10) took 1.623 seconds (ok)
Aug 20 20:18:37.821: vmx| scsi0:0: Command WRITE(10) took 1.582 seconds (ok)
Aug 20 20:18:39.958: vmx| scsi0:0: Command WRITE(10) took 1.560 seconds (ok)
Aug 20 20:18:42.462: vmx| scsi0:0: Command WRITE(10) took 1.847 seconds (ok)
Aug 20 20:18:46.404: vmx| scsi0:0: Command WRITE(10) took 1.329 seconds (ok)
Aug 20 20:18:47.080: vmx| scsi0:0: Command WRITE(10) took 1.340 seconds (ok)
Aug 20 20:18:52.171: vmx| scsi0:0: Command WRITE(10) took 3.754 seconds (ok)
Aug 20 20:18:52.772: vmx| scsi0:0: Command WRITE(10) took 4.046 seconds (ok)
Aug 20 20:18:57.598: vmx| scsi0:0: Command WRITE(10) took 1.298 seconds (ok)
Aug 20 20:18:58.244: vmx| scsi0:0: Command WRITE(10) took 1.295 seconds (ok)
Aug 20 20:19:00.189: vmx| scsi0:0: Command WRITE(10) took 1.261 seconds (ok)
Aug 20 20:19:00.872: vmx| scsi0:0: Command WRITE(10) took 1.944 seconds (ok)
Aug 20 20:19:01.557: vmx| scsi0:0: Command WRITE(10) took 2.302 seconds (ok)
Aug 20 20:19:04.962: vmx| scsi0:0: Command WRITE(10) took 2.045 seconds (ok)
Aug 20 20:19:05.687: vmx| ToolsSetVersionWork did nothing; new tools version (0) matches old Tools version
Aug 20 20:19:06.426: vmx| scsi0:0: Command WRITE(10) took 3.509 seconds (ok)
Aug 20 20:19:07.147: vmx| scsi0:0: Command WRITE(10) took 4.229 seconds (ok)
Aug 20 20:19:10.164: vmx| scsi0:0: Command WRITE(10) took 1.596 seconds (ok)
Aug 20 20:19:10.827: vmx| scsi0:0: Command WRITE(10) took 2.259 seconds (ok)
Aug 20 20:19:13.615: vmx| scsi0:0: Command WRITE(10) took 4.405 seconds (ok)
Aug 20 20:19:16.461: vmx| scsi0:0: Command WRITE(10) took 1.466 seconds (ok)
Aug 20 20:19:17.150: vmx| scsi0:0: Command WRITE(10) took 2.155 seconds (ok)
Aug 20 20:19:17.870: vmx| scsi0:0: Command WRITE(10) took 2.875 seconds (ok)
Aug 20 20:19:18.557: vmx| scsi0:0: Command WRITE(10) took 2.810 seconds (ok)
Aug 20 20:19:23.167: vmx| scsi0:0: Command WRITE(10) took 1.411 seconds (ok)
Aug 20 20:19:23.892: vmx| scsi0:0: Command WRITE(10) took 1.897 seconds (ok)
Aug 20 20:19:24.578: vmx| scsi0:0: Command WRITE(10) took 2.099 seconds (ok)
Aug 20 20:19:25.301: vmx| scsi0:0: Command WRITE(10) took 2.822 seconds (ok)
Aug 20 20:19:28.138: vmx| scsi0:0: Command WRITE(10) took 1.420 seconds (ok)
Aug 20 20:19:28.784: vmx| scsi0:0: Command WRITE(10) took 1.376 seconds (ok)
Aug 20 20:19:31.615: vmx| scsi0:0: Command WRITE(10) took 1.400 seconds (ok)
Aug 20 20:19:32.357: vmx| scsi0:0: Command WRITE(10) took 1.442 seconds (ok)
Aug 20 20:19:33.058: vmx| scsi0:0: Command WRITE(10) took 2.142 seconds (ok)
Aug 20 20:19:38.263: vmx| scsi0:0: Command WRITE(10) took 1.490 seconds (ok)
Aug 20 20:19:38.981: vmx| scsi0:0: Command WRITE(10) took 1.443 seconds (ok)
Aug 20 20:19:42.326: vmx| scsi0:0: Command WRITE(10) took 1.503 seconds (ok)
Aug 20 20:19:46.050: vmx| scsi0:0: Command WRITE(10) took 5.226 seconds (ok)
Aug 20 20:19:46.770: vmx| scsi0:0: Command WRITE(10) took 5.946 seconds (ok)
Aug 20 20:19:47.493: vmx| scsi0:0: Command WRITE(10) took 5.938 seconds (ok)
Aug 20 20:19:50.949: vmx| scsi0:0: Command WRITE(10) took 2.727 seconds (ok)
Aug 20 20:19:51.745: vmx| scsi0:0: Command WRITE(10) took 3.509 seconds (ok)
Aug 20 20:19:52.550: vmx| scsi0:0: Command WRITE(10) took 3.571 seconds (ok)
Aug 20 20:19:56.237: vmx| scsi0:0: Command WRITE(10) took 2.897 seconds (ok)
Aug 20 20:19:56.939: vmx| scsi0:0: Command WRITE(10) took 3.600 seconds (ok)
Aug 20 20:19:57.682: vmx| scsi0:0: Command WRITE(10) took 4.342 seconds (ok)
Aug 20 20:19:58.427: vmx| scsi0:0: Command WRITE(10) took 5.087 seconds (ok)
Aug 20 20:20:00.791: vmx| scsi0:0: Command WRITE(10) took 1.576 seconds (ok)
Aug 20 20:20:03.307: vmx| scsi0:0: Command WRITE(10) took 4.092 seconds (ok)
Aug 20 20:20:04.097: vmx| scsi0:0: Command WRITE(10) took 4.428 seconds (ok)
Aug 20 20:20:04.911: vmx| scsi0:0: Command WRITE(10) took 3.332 seconds (ok)
Aug 20 20:20:05.727: vmx| scsi0:0: Command WRITE(10) took 4.147 seconds (ok)
Aug 20 20:20:06.447: vmx| scsi0:0: Command WRITE(10) took 2.353 seconds (ok)
Aug 20 20:20:07.262: vmx| scsi0:0: Command WRITE(10) took 1.537 seconds (ok)
Aug 20 20:20:13.419: vmx| scsi0:0: Command WRITE(10) took 1.629 seconds (ok)
Aug 20 20:20:14.216: vmx| scsi0:0: Command WRITE(10) took 2.426 seconds (ok)
Aug 20 20:20:15.005: vmx| scsi0:0: Command WRITE(10) took 2.405 seconds (ok)
Aug 20 20:20:21.068: vmx| scsi0:0: Command WRITE(10) took 2.031 seconds (ok)
Aug 20 20:20:21.890: vmx| scsi0:0: Command WRITE(10) took 2.852 seconds (ok)
Aug 20 20:20:22.720: vmx| scsi0:0: Command WRITE(10) took 2.898 seconds (ok)
Aug 20 20:20:25.138: vmx| scsi0:0: Command WRITE(10) took 1.636 seconds (ok)
Aug 20 20:20:25.946: vmx| scsi0:0: Command WRITE(10) took 2.444 seconds (ok)
Aug 20 20:20:26.792: vmx| scsi0:0: Command WRITE(10) took 2.571 seconds (ok)
Aug 20 20:20:27.649: vmx| scsi0:0: Command WRITE(10) took 1.753 seconds (ok)
Aug 20 20:20:28.510: vmx| scsi0:0: Command WRITE(10) took 2.613 seconds (ok)
Aug 20 20:20:31.072: vmx| scsi0:0: Command WRITE(10) took 1.758 seconds (ok)
Aug 20 20:20:31.935: vmx| scsi0:0: Command WRITE(10) took 1.775 seconds (ok)
Aug 20 20:20:39.118: vmx| scsi0:0: Command WRITE(10) took 3.384 seconds (ok)
Aug 20 20:20:39.910: vmx| scsi0:0: Command WRITE(10) took 4.176 seconds (ok)
Aug 20 20:20:40.749: vmx| scsi0:0: Command WRITE(10) took 5.013 seconds (ok)
Aug 20 20:20:43.199: vmx| scsi0:0: Command WRITE(10) took 1.651 seconds (ok)
Aug 20 20:20:43.994: vmx| scsi0:0: Command WRITE(10) took 2.447 seconds (ok)
Aug 20 20:20:44.837: vmx| scsi0:0: Command WRITE(10) took 3.202 seconds (ok)
Aug 20 20:20:45.633: vmx| scsi0:0: Command WRITE(10) took 3.451 seconds (ok)
Aug 20 20:20:46.430: vmx| scsi0:0: Command WRITE(10) took 4.084 seconds (ok)
Aug 20 20:20:47.224: vmx| scsi0:0: Command WRITE(10) took 4.878 seconds (ok)
Aug 20 20:20:50.970: vmx| scsi0:0: Command WRITE(10) took 2.104 seconds (ok)
Aug 20 20:20:51.785: vmx| scsi0:0: Command WRITE(10) took 2.065 seconds (ok)
Aug 20 20:20:59.624: vmx| scsi0:0: Command WRITE(10) took 5.216 seconds (ok)
Aug 20 20:21:00.420: vmx| scsi0:0: Command WRITE(10) took 6.012 seconds (ok)
Aug 20 20:21:01.265: vmx| scsi0:0: Command WRITE(10) took 6.857 seconds (ok)
Aug 20 20:21:02.116: vmx| scsi0:0: Command WRITE(10) took 7.708 seconds (ok)
Aug 20 20:21:02.959: vmx| scsi0:0: Command WRITE(10) took 6.750 seconds (ok)
Aug 20 20:21:07.082: vmx| scsi0:0: Command WRITE(10) took 1.670 seconds (ok)
Aug 20 20:21:07.958: vmx| scsi0:0: Command WRITE(10) took 2.546 seconds (ok)
Aug 20 20:21:08.769: vmx| scsi0:0: Command WRITE(10) took 2.547 seconds (ok)
Aug 20 20:21:09.649: vmx| scsi0:0: Command WRITE(10) took 3.427 seconds (ok)
Aug 20 20:21:12.920: vmx| scsi0:0: Command WRITE(10) took 1.620 seconds (ok)
Aug 20 20:21:13.783: vmx| scsi0:0: Command WRITE(10) took 2.483 seconds (ok)
Aug 20 20:21:14.643: vmx| scsi0:0: Command WRITE(10) took 2.533 seconds (ok)
Aug 20 20:21:15.796: vmx| scsi0:0: Command WRITE(10) took 3.686 seconds (ok)
Aug 20 20:21:18.382: vmx| scsi0:0: Command WRITE(10) took 1.718 seconds (ok)
Aug 20 20:21:19.237: vmx| scsi0:0: Command WRITE(10) took 1.775 seconds (ok)
Aug 20 20:21:20.081: vmx| scsi0:0: Command WRITE(10) took 2.619 seconds (ok)
Aug 20 20:21:28.080: vmx| scsi0:0: Command WRITE(10) took 1.607 seconds (ok)
Aug 20 20:21:28.967: vmx| scsi0:0: Command WRITE(10) took 2.494 seconds (ok)
Aug 20 20:21:29.845: vmx| scsi0:0: Command WRITE(10) took 2.596 seconds (ok)
Aug 20 20:21:32.451: vmx| scsi0:0: Command WRITE(10) took 1.350 seconds (ok)
Aug 20 20:21:33.289: vmx| scsi0:0: Command WRITE(10) took 1.678 seconds (ok)
Aug 20 20:21:35.787: vmx| scsi0:0: Command WRITE(10) took 1.710 seconds (ok)
Aug 20 20:21:36.679: vmx| scsi0:0: Command WRITE(10) took 2.602 seconds (ok)
Aug 20 20:21:37.528: vmx| scsi0:0: Command WRITE(10) took 3.451 seconds (ok)
Aug 20 20:21:38.417: vmx| scsi0:0: Command WRITE(10) took 3.704 seconds (ok)
Aug 20 20:21:39.302: vmx| scsi0:0: Command WRITE(10) took 4.376 seconds (ok)
Aug 20 20:21:42.907: vmx| scsi0:0: Command WRITE(10) took 1.824 seconds (ok)
Aug 20 20:21:47.115: vmx| scsi0:0: Command WRITE(10) took 3.285 seconds (ok)
Aug 20 20:21:52.551: vmx| scsi0:0: Command WRITE(10) took 1.408 seconds (ok)
Aug 20 20:21:53.173: vmx| scsi0:0: Command WRITE(10) took 2.030 seconds (ok)
Aug 20 20:21:54.101: vmx| scsi0:0: Command WRITE(10) took 2.327 seconds (ok)
Aug 20 20:21:54.101: vmx| scsi0:0: Command WRITE(10) took 2.171 seconds (ok)
Aug 20 20:21:55.958: vmx| scsi0:0: Command WRITE(10) took 1.161 seconds (ok)
Aug 20 20:22:11.507: vcpu-0| UHCI: HCReset
Aug 20 20:22:11.550: mks| MKS switching absolute mouse off
Aug 20 20:22:11.579: vcpu-0| UHCI: Global Reset
Aug 20 20:22:13.517: mks| MKS switching absolute mouse on
Aug 20 20:22:15.049: mks| MKS switching absolute mouse off
Aug 20 20:22:16.697: mks| MKS switching absolute mouse on
Aug 20 20:22:19.432: mks| MKS switching absolute mouse off
Aug 20 20:22:19.647: mks| MKS switching absolute mouse on
Aug 20 20:22:23.025: vcpu-0| CDROM: Mode Sense for Unsupported Page 0x1B
Aug 20 20:22:23.026: vcpu-0| SCSI DEVICE (ide1:0): MODE SENSE(10) for unsupported page 0x1b
Aug 20 20:22:25.030: vcpu-0| CDROM: Mode Sense for Unsupported Page 0x1B
Aug 20 20:22:25.030: vcpu-0| SCSI DEVICE (ide1:0): MODE SENSE(10) for unsupported page 0x1b
Aug 20 20:22:29.631: vmx| scsi0:0: Command WRITE(10) took 2.500 seconds (ok)
Aug 20 20:22:30.509: vmx| scsi0:0: Command WRITE(10) took 3.378 seconds (ok)
Aug 20 20:22:31.381: vmx| scsi0:0: Command WRITE(10) took 3.064 seconds (ok)
Aug 20 20:22:36.904: vmx| scsi0:0: Command WRITE(10) took 4.589 seconds (ok)
Aug 20 20:22:39.828: vmx| scsi0:0: Command WRITE(10) took 1.031 seconds (ok)
Aug 20 20:22:43.907: vmx| scsi0:0: Command WRITE(10) took 3.130 seconds (ok)
Aug 20 20:22:50.246: vmx| scsi0:0: Command WRITE(10) took 1.840 seconds (ok)
Aug 20 20:22:53.077: vmx| scsi0:0: Command WRITE(10) took 1.883 seconds (ok)
Aug 20 20:22:54.003: vmx| scsi0:0: Command WRITE(10) took 1.900 seconds (ok)
Aug 20 20:22:56.200: vmx| scsi0:0: Command WRITE(10) took 1.309 seconds (ok)
Aug 20 20:22:57.142: vmx| scsi0:0: Command WRITE(10) took 2.251 seconds (ok)
Aug 20 20:22:58.074: vmx| scsi0:0: Command WRITE(10) took 3.183 seconds (ok)
Aug 20 20:22:59.012: vmx| scsi0:0: Command WRITE(10) took 1.874 seconds (ok)
Aug 20 20:23:06.630: vmx| scsi0:0: Command WRITE(10) took 1.050 seconds (ok)
Aug 20 20:23:07.510: vmx| scsi0:0: Command WRITE(10) took 1.711 seconds (ok)
Aug 20 20:23:11.076: vmx| scsi0:0: Command WRITE(10) took 1.785 seconds (ok)
Aug 20 20:23:12.002: vmx| scsi0:0: Command WRITE(10) took 2.712 seconds (ok)
Aug 20 20:23:12.931: vmx| scsi0:0: Command WRITE(10) took 3.640 seconds (ok)
Aug 20 20:23:14.828: vmx| scsi0:0: Command WRITE(10) took 4.875 seconds (ok)
Aug 20 20:23:15.718: vmx| scsi0:0: Command WRITE(10) took 4.864 seconds (ok)
Aug 20 20:23:18.381: vmx| scsi0:0: Command WRITE(10) took 1.706 seconds (ok)
Aug 20 20:23:19.284: vmx| scsi0:0: Command WRITE(10) took 1.782 seconds (ok)
Aug 20 20:23:26.770: vmx| scsi0:0: Command WRITE(10) took 6.191 seconds (ok)
Aug 20 20:23:27.668: vmx| scsi0:0: Command WRITE(10) took 5.169 seconds (ok)
Aug 20 20:23:28.513: vmx| scsi0:0: Command WRITE(10) took 5.507 seconds (ok)
Aug 20 20:23:36.344: vmx| scsi0:0: Command WRITE(10) took 2.317 seconds (ok)
Aug 20 20:23:37.307: vmx| scsi0:0: Command WRITE(10) took 3.280 seconds (ok)
Aug 20 20:23:38.255: vmx| scsi0:0: Command WRITE(10) took 3.241 seconds (ok)
Aug 20 20:23:41.105: vmx| scsi0:0: Command WRITE(10) took 1.890 seconds (ok)
Aug 20 20:23:42.077: vmx| scsi0:0: Command WRITE(10) took 1.916 seconds (ok)
Aug 20 20:23:47.972: vmx| scsi0:0: Command WRITE(10) took 4.937 seconds (ok)
Aug 20 20:23:48.979: vmx| scsi0:0: Command WRITE(10) took 5.945 seconds (ok)
Aug 20 20:23:52.706: vmx| scsi0:0: Command WRITE(10) took 2.757 seconds (ok)
Aug 20 20:23:53.654: vmx| scsi0:0: Command WRITE(10) took 1.852 seconds (ok)
Aug 20 20:23:54.549: vmx| scsi0:0: Command WRITE(10) took 2.154 seconds (ok)
Aug 20 20:24:00.626: vmx| scsi0:0: Command WRITE(10) took 1.867 seconds (ok)
Aug 20 20:24:01.586: vmx| scsi0:0: Command WRITE(10) took 2.432 seconds (ok)
Aug 20 20:24:02.494: vmx| scsi0:0: Command WRITE(10) took 2.749 seconds (ok)
Aug 20 20:24:08.754: vmx| scsi0:0: Command WRITE(10) took 4.799 seconds (ok)
Aug 20 20:24:09.652: vmx| scsi0:0: Command WRITE(10) took 4.245 seconds (ok)
Aug 20 20:24:14.249: vmx| scsi0:0: Command WRITE(10) took 1.797 seconds (ok)
Aug 20 20:24:15.199: vmx| scsi0:0: Command WRITE(10) took 2.746 seconds (ok)
Aug 20 20:24:16.092: vmx| scsi0:0: Command WRITE(10) took 2.102 seconds (ok)
Aug 20 20:24:19.286: vmx| scsi0:0: Command WRITE(10) took 2.236 seconds (ok)
Aug 20 20:24:20.188: vmx| scsi0:0: Command WRITE(10) took 2.284 seconds (ok)
Aug 20 20:24:21.090: vmx| scsi0:0: Command WRITE(10) took 3.186 seconds (ok)
Aug 20 20:24:22.050: vmx| scsi0:0: Command WRITE(10) took 4.144 seconds (ok)
Aug 20 20:24:22.957: vmx| scsi0:0: Command WRITE(10) took 5.050 seconds (ok)
Aug 20 20:24:32.696: vmx| scsi0:0: Command WRITE(10) took 1.816 seconds (ok)
Aug 20 20:24:34.100: vmx| scsi0:0: Command WRITE(10) took 2.257 seconds (ok)
Aug 20 20:24:35.077: vmx| scsi0:0: Command WRITE(10) took 3.234 seconds (ok)
Aug 20 20:24:37.083: vmx| scsi0:0: Command WRITE(10) took 1.025 seconds (ok)
Aug 20 20:24:38.048: vmx| scsi0:0: Command WRITE(10) took 1.990 seconds (ok)
Aug 20 20:24:38.909: vmx| scsi0:0: Command WRITE(10) took 2.850 seconds (ok)
Aug 20 20:24:40.792: vmx| scsi0:0: Command WRITE(10) took 1.022 seconds (ok)
Aug 20 20:24:43.748: vmx| scsi0:0: Command WRITE(10) took 2.021 seconds (ok)
Aug 20 20:24:44.733: vmx| scsi0:0: Command WRITE(10) took 2.028 seconds (ok)
Aug 20 20:24:47.503: vmx| scsi0:0: Command WRITE(10) took 1.840 seconds (ok)
Aug 20 20:24:48.481: vmx| scsi0:0: Command WRITE(10) took 2.805 seconds (ok)
Aug 20 20:24:49.364: vmx| scsi0:0: Command WRITE(10) took 2.750 seconds (ok)
Aug 20 20:24:58.560: vmx| scsi0:0: Command WRITE(10) took 1.009 seconds (ok)
Aug 20 20:24:59.567: vmx| scsi0:0: Command WRITE(10) took 2.016 seconds (ok)
Aug 20 20:25:01.783: vmx| scsi0:0: Command WRITE(10) took 1.170 seconds (ok)
Aug 20 20:25:04.840: vmx| scsi0:0: Command WRITE(10) took 2.095 seconds (ok)
Aug 20 20:25:05.881: vmx| scsi0:0: Command WRITE(10) took 3.136 seconds (ok)
Aug 20 20:25:06.916: vmx| scsi0:0: Command WRITE(10) took 4.170 seconds (ok)
Aug 20 20:25:07.947: vmx| scsi0:0: Command WRITE(10) took 3.180 seconds (ok)
Aug 20 20:25:10.017: vmx| scsi0:0: Command WRITE(10) took 1.030 seconds (ok)
Aug 20 20:25:10.984: vmx| scsi0:0: Command WRITE(10) took 1.996 seconds (ok)
Aug 20 20:25:12.033: vmx| scsi0:0: Command WRITE(10) took 1.058 seconds (ok)
Aug 20 20:25:13.058: vmx| scsi0:0: Command WRITE(10) took 2.074 seconds (ok)
Aug 20 20:25:14.075: vmx| scsi0:0: Command WRITE(10) took 2.043 seconds (ok)
Aug 20 20:25:18.318: vmx| scsi0:0: Command WRITE(10) took 3.245 seconds (ok)
Aug 20 20:25:19.401: vmx| scsi0:0: Command WRITE(10) took 4.328 seconds (ok)
Aug 20 20:25:23.454: vmx| scsi0:0: Command WRITE(10) took 3.050 seconds (ok)
Aug 20 20:25:26.139: vmx| scsi0:0: Command WRITE(10) took 1.105 seconds (ok)
Aug 20 20:25:27.161: vmx| scsi0:0: Command WRITE(10) took 2.128 seconds (ok)
Aug 20 20:25:29.454: vmx| scsi0:0: Command WRITE(10) took 1.055 seconds (ok)
Aug 20 20:25:30.466: vmx| scsi0:0: Command READ(10) took 1.493 seconds (ok)
Aug 20 20:25:32.649: vmx| scsi0:0: Command WRITE(10) took 1.167 seconds (ok)
Aug 20 20:25:34.866: vmx| scsi0:0: Command WRITE(10) took 1.143 seconds (ok)
Aug 20 20:25:35.964: vmx| scsi0:0: Command WRITE(10) took 2.241 seconds (ok)
Aug 20 20:25:37.078: vmx| scsi0:0: Command WRITE(10) took 3.317 seconds (ok)
Aug 20 20:25:38.054: vmx| scsi0:0: Command WRITE(10) took 3.786 seconds (ok)
Aug 20 20:25:39.143: vmx| scsi0:0: Command WRITE(10) took 4.541 seconds (ok)
Aug 20 20:25:49.949: vmx| scsi0:0: Command WRITE(10) took 2.129 seconds (ok)
Aug 20 20:25:51.029: vmx| scsi0:0: Command WRITE(10) took 3.201 seconds (ok)
Aug 20 20:25:53.705: vmx| scsi0:0: Command WRITE(10) took 1.640 seconds (ok)
Aug 20 20:25:54.755: vmx| scsi0:0: Command WRITE(10) took 2.691 seconds (ok)
Aug 20 20:25:55.837: vmx| scsi0:0: Command WRITE(10) took 3.772 seconds (ok)
Aug 20 20:25:56.904: vmx| scsi0:0: Command WRITE(10) took 4.839 seconds (ok)
Aug 20 20:25:59.008: vmx| scsi0:0: Command WRITE(10) took 1.111 seconds (ok)
Aug 20 20:26:01.237: vmx| scsi0:0: Command WRITE(10) took 1.123 seconds (ok)
Aug 20 20:26:02.275: vmx| scsi0:0: Command WRITE(10) took 1.841 seconds (ok)
Aug 20 20:26:08.936: vmx| scsi0:0: Command WRITE(10) took 4.551 seconds (ok)
Aug 20 20:26:09.750: vmx| scsi0:0: Command WRITE(10) took 5.331 seconds (ok)
Aug 20 20:26:12.558: vmx| scsi0:0: Command WRITE(10) took 1.421 seconds (ok)
Aug 20 20:26:14.742: vmx| scsi0:0: Command WRITE(10) took 1.122 seconds (ok)
Aug 20 20:26:15.853: vmx| scsi0:0: Command WRITE(10) took 2.228 seconds (ok)
Aug 20 20:26:18.789: vmx| scsi0:0: Command WRITE(10) took 1.215 seconds (ok)
Aug 20 20:26:19.675: vmx| scsi0:0: Command WRITE(10) took 2.101 seconds (ok)
Aug 20 20:26:20.724: vmx| scsi0:0: Command WRITE(10) took 2.762 seconds (ok)
Aug 20 20:26:21.842: vmx| scsi0:0: Command WRITE(10) took 3.627 seconds (ok)
Aug 20 20:26:24.063: vmx| scsi0:0: Command WRITE(10) took 1.112 seconds (ok)
Aug 20 20:26:26.306: vmx| scsi0:0: Command WRITE(10) took 1.113 seconds (ok)
Aug 20 20:26:28.563: vmx| scsi0:0: Command WRITE(10) took 1.132 seconds (ok)
Aug 20 20:26:33.288: vmx| scsi0:0: Command WRITE(10) took 3.577 seconds (ok)
Aug 20 20:26:40.006: vmx| scsi0:0: Command WRITE(10) took 1.106 seconds (ok)
Aug 20 20:26:42.283: vmx| scsi0:0: Command WRITE(10) took 1.146 seconds (ok)
Aug 20 20:26:44.534: vmx| scsi0:0: Command WRITE(10) took 1.107 seconds (ok)
Aug 20 20:26:46.758: vmx| scsi0:0: Command WRITE(10) took 1.078 seconds (ok)
Aug 20 20:26:47.902: vmx| scsi0:0: Command WRITE(10) took 2.221 seconds (ok)
Aug 20 20:26:49.050: vmx| scsi0:0: Command WRITE(10) took 3.370 seconds (ok)
Aug 20 20:26:50.132: vmx| scsi0:0: Command WRITE(10) took 4.451 seconds (ok)
Aug 20 20:26:51.865: vmx| scsi0:0: Command WRITE(10) took 6.184 seconds (ok)
Aug 20 20:26:53.009: vmx| scsi0:0: Command WRITE(10) took 1.719 seconds (ok)
Aug 20 20:26:59.471: vmx| scsi0:0: Command WRITE(10) took 5.307 seconds (ok)
Aug 20 20:27:00.627: vmx| scsi0:0: Command WRITE(10) took 6.462 seconds (ok)
Aug 20 20:27:07.093: vmx| scsi0:0: Command WRITE(10) took 1.214 seconds (ok)
Aug 20 20:27:09.377: vmx| scsi0:0: Command WRITE(10) took 1.247 seconds (ok)
Aug 20 20:27:10.579: vmx| scsi0:0: Command WRITE(10) took 2.449 seconds (ok)
Aug 20 20:27:11.758: vmx| scsi0:0: Command WRITE(10) took 3.627 seconds (ok)
Aug 20 20:27:13.995: vmx| scsi0:0: Command WRITE(10) took 1.190 seconds (ok)
Aug 20 20:27:16.339: vmx| scsi0:0: Command WRITE(10) took 1.126 seconds (ok)
Aug 20 20:27:18.700: vmx| scsi0:0: Command WRITE(10) took 1.185 seconds (ok)
Aug 20 20:27:19.887: vmx| scsi0:0: Command WRITE(10) took 2.372 seconds (ok)
Aug 20 20:27:21.020: vmx| scsi0:0: Command WRITE(10) took 3.293 seconds (ok)
Aug 20 20:27:31.400: vmx| scsi0:0: Command WRITE(10) took 1.215 seconds (ok)
Aug 20 20:27:33.136: vmx| scsi0:0: Command WRITE(10) took 2.631 seconds (ok)
Aug 20 20:27:35.447: vmx| scsi0:0: Command WRITE(10) took 1.125 seconds (ok)
Aug 20 20:27:37.737: vmx| scsi0:0: Command WRITE(10) took 1.183 seconds (ok)
Aug 20 20:27:39.813: vmx| scsi0:0: Command WRITE(10) took 1.216 seconds (ok)
Aug 20 20:27:41.790: vmx| scsi0:0: Command WRITE(10) took 1.244 seconds (ok)
Aug 20 20:29:14.507: vcpu-0| scsi0:0: Command WRITE(10) took 93.959 seconds (ok)
Aug 20 20:29:14.508: vcpu-0| scsi0:0: Command WRITE(10) took 90.729 seconds (ok)
Aug 20 20:29:14.508: vcpu-0| scsi0:0: Command WRITE(10) took 93.959 seconds (ok)
Aug 20 20:29:14.509: vcpu-0| scsi0:0: Command WRITE(10) took 93.960 seconds (ok)
Aug 20 20:29:14.509: vcpu-0| scsi0:0: Command WRITE(10) took 93.960 seconds (ok)
Aug 20 20:29:14.512: vcpu-0| scsi0:0: Command WRITE(10) took 93.963 seconds (ok)
Aug 20 20:29:14.513: vcpu-0| scsi0:0: Command WRITE(10) took 93.964 seconds (ok)
Aug 20 20:29:14.516: vcpu-0| scsi0:0: Command WRITE(10) took 93.967 seconds (ok)
Aug 20 20:29:14.517: vcpu-0| scsi0:0: Command WRITE(10) took 93.968 seconds (ok)
Aug 20 20:29:14.517: vcpu-0| scsi0:0: Command WRITE(10) took 93.968 seconds (ok)
Aug 20 20:29:14.518: vcpu-0| scsi0:0: Command WRITE(10) took 93.969 seconds (ok)
Aug 20 20:29:14.519: vcpu-0| scsi0:0: Command WRITE(10) took 93.969 seconds (ok)
Aug 20 20:29:14.519: vcpu-0| scsi0:0: Command WRITE(10) took 93.970 seconds (ok)
Aug 20 20:29:14.520: vcpu-0| scsi0:0: Command WRITE(10) took 93.970 seconds (ok)
Aug 20 20:29:14.520: vcpu-0| scsi0:0: Command WRITE(10) took 93.971 seconds (ok)
Aug 20 20:29:14.521: vcpu-0| scsi0:0: Command WRITE(10) took 93.971 seconds (ok)
Aug 20 20:29:14.521: vcpu-0| scsi0:0: Command WRITE(10) took 93.971 seconds (ok)
Aug 20 20:29:14.521: vcpu-0| scsi0:0: Command WRITE(10) took 92.075 seconds (ok)
Aug 20 20:29:14.522: vcpu-0| scsi0:0: Command WRITE(10) took 92.075 seconds (ok)
Aug 20 20:29:14.522: vcpu-0| scsi0:0: Command WRITE(10) took 91.581 seconds (ok)
Aug 20 20:29:14.522: vcpu-0| SCSI0: RESET BUS
Aug 20 20:29:20.825: vmx| DISKLIB-LIB   : numIOs = 50000 numMergedIOs = 1077 numSplitIOs = 342
Aug 20 20:29:25.502: vcpu-0| CDROM: Mode Sense for Unsupported Page 0x1B
Aug 20 20:29:25.503: vcpu-0| SCSI DEVICE (ide1:0): MODE SENSE(10) for unsupported page 0x1b
Aug 20 20:30:40.949: vcpu-0| scsi0:0: Command WRITE(10) took 54.449 seconds (ok)
Aug 20 20:30:42.274: vcpu-0| scsi0:0: Command WRITE(10) took 55.520 seconds (ok)
Aug 20 20:30:43.603: vcpu-0| scsi0:0: Command WRITE(10) took 56.103 seconds (ok)
Aug 20 20:30:44.868: vcpu-0| scsi0:0: Command WRITE(10) took 57.368 seconds (ok)
Aug 20 20:30:45.986: vcpu-0| scsi0:0: Command WRITE(10) took 57.767 seconds (ok)
Aug 20 20:30:47.358: vcpu-0| scsi0:0: Command WRITE(10) took 58.811 seconds (ok)
Aug 20 20:30:48.627: vcpu-0| SCSI0: RESET BUS
Aug 20 20:30:57.439: mks| MKS lost grab
Aug 20 20:31:03.620: vmx| scsi0:0: Command WRITE(10) took 1.342 seconds (ok)
Aug 20 20:31:04.897: mks| MKS lost grab
Aug 20 20:31:07.632: vmx| scsi0:0: Command WRITE(10) took 1.364 seconds (ok)
Aug 20 20:31:10.368: vmx| scsi0:0: Command WRITE(10) took 1.372 seconds (ok)
Aug 20 20:31:29.204: vcpu-0| scsi0:0: Command WRITE(10) took 11.976 seconds (ok)
Aug 20 20:31:30.522: vcpu-0| SCSI0: RESET BUS
Aug 20 20:31:45.013: vcpu-0| scsi0:0: Command WRITE(10) took 11.798 seconds (ok)
Aug 20 20:31:46.353: vcpu-0| SCSI0: RESET BUS
Aug 20 20:31:54.866: vmx| scsi0:0: Command WRITE(10) took 1.227 seconds (ok)
Aug 20 20:32:03.007: vmx| scsi0:0: Command WRITE(10) took 6.696 seconds (ok)
Aug 20 20:32:05.219: mks| MKS lost grab
Aug 20 20:32:06.675: vmx| scsi0:0: Command WRITE(10) took 2.289 seconds (ok)
Aug 20 20:32:21.110: vcpu-0| scsi0:0: Command WRITE(10) took 12.961 seconds (ok)
Aug 20 20:32:22.580: vcpu-0| SCSI0: RESET BUS
Aug 20 20:32:36.702: vmx| scsi0:0: Command WRITE(10) took 1.354 seconds (ok)
Aug 20 20:32:39.710: vmx| scsi0:0: Command WRITE(10) took 1.499 seconds (ok)
Aug 20 20:32:42.693: vmx| scsi0:0: Command WRITE(10) took 1.495 seconds (ok)
Aug 20 20:32:45.682: vmx| scsi0:0: Command WRITE(10) took 1.499 seconds (ok)
Aug 20 20:32:49.432: vmx| scsi0:0: Command WRITE(10) took 1.517 seconds (ok)
Aug 20 20:33:01.714: vmx| scsi0:0: Command WRITE(10) took 1.438 seconds (ok)
Aug 20 20:33:06.284: vmx| scsi0:0: Command WRITE(10) took 3.057 seconds (ok)
Aug 20 20:33:25.607: vcpu-0| scsi0:0: Command WRITE(10) took 16.460 seconds (ok)
Aug 20 20:33:27.147: vcpu-0| SCSI0: RESET BUS
Aug 20 20:33:43.417: vmx| scsi0:0: Command WRITE(10) took 1.560 seconds (ok)
Aug 20 20:33:57.641: vcpu-0| scsi0:0: Command WRITE(10) took 12.749 seconds (ok)
Aug 20 20:33:59.118: vcpu-0| SCSI0: RESET BUS
Aug 20 20:34:17.674: vmx| scsi0:0: Command WRITE(10) took 1.522 seconds (ok)
Aug 20 20:34:20.809: vmx| scsi0:0: Command WRITE(10) took 1.523 seconds (ok)
Aug 20 20:34:23.935: vmx| scsi0:0: Command WRITE(10) took 1.526 seconds (ok)
Aug 20 20:34:27.004: vmx| scsi0:0: Command WRITE(10) took 1.642 seconds (ok)
Aug 20 20:34:42.803: vmx| scsi0:0: Command WRITE(10) took 1.560 seconds (ok)
Aug 20 20:34:59.080: vcpu-0| scsi0:0: Command WRITE(10) took 14.635 seconds (ok)
Aug 20 20:35:00.755: vcpu-0| SCSI0: RESET BUS
Aug 20 20:35:16.958: vmx| scsi0:0: Command WRITE(10) took 1.492 seconds (ok)
Aug 20 20:35:30.020: vcpu-0| scsi0:0: Command WRITE(10) took 12.314 seconds (ok)
Aug 20 20:35:31.743: vcpu-0| SCSI0: RESET BUS
Aug 20 20:35:48.236: vmx| scsi0:0: Command WRITE(10) took 1.648 seconds (ok)
Aug 20 20:35:51.440: vmx| scsi0:0: Command WRITE(10) took 1.651 seconds (ok)
Aug 20 20:35:54.852: vmx| scsi0:0: Command WRITE(10) took 1.659 seconds (ok)
Aug 20 20:35:58.283: vmx| scsi0:0: Command WRITE(10) took 1.671 seconds (ok)
Aug 20 20:36:01.412: vmx| scsi0:0: Command WRITE(10) took 1.574 seconds (ok)
Aug 20 20:36:17.812: vmx| scsi0:0: Command WRITE(10) took 1.687 seconds (ok)
Aug 20 20:36:34.766: vcpu-0| scsi0:0: Command WRITE(10) took 15.264 seconds (ok)
Aug 20 20:36:36.466: vcpu-0| SCSI0: RESET BUS
Aug 20 20:37:08.673: vcpu-0| scsi0:0: Command WRITE(10) took 15.368 seconds (ok)
Aug 20 20:37:10.423: vcpu-0| SCSI0: RESET BUS
Aug 20 20:37:27.661: mks| MKS lost grab
Aug 20 20:37:29.687: mks| MKS lost grab
Aug 20 20:37:34.145: vmx| scsi0:0: Command WRITE(10) took 1.667 seconds (ok)
Aug 20 20:37:38.674: vmx| scsi0:0: Command WRITE(10) took 2.835 seconds (ok)
Aug 20 20:37:49.984: vmx| scsi0:0: Command WRITE(10) took 9.595 seconds (ok)
Aug 20 20:37:59.548: vmx| scsi0:0: Command WRITE(10) took 1.953 seconds (ok)
Aug 20 20:38:03.376: vmx| scsi0:0: Command WRITE(10) took 1.926 seconds (ok)
Aug 20 20:38:07.231: vmx| scsi0:0: Command WRITE(10) took 1.936 seconds (ok)
Aug 20 20:38:10.857: vmx| scsi0:0: Command WRITE(10) took 1.830 seconds (ok)
Aug 20 20:38:31.390: vmx| scsi0:0: Command WRITE(10) took 2.120 seconds (ok)
Aug 20 20:38:35.087: vmx| scsi0:0: Command WRITE(10) took 1.805 seconds (ok)
Aug 20 20:38:38.797: vmx| scsi0:0: Command WRITE(10) took 1.928 seconds (ok)
Aug 20 20:38:49.669: vmx| scsi0:0: Command WRITE(10) took 8.829 seconds (ok)
Aug 20 20:39:01.442: vmx| scsi0:0: Command WRITE(10) took 2.004 seconds (ok)
Aug 20 20:39:05.408: vmx| scsi0:0: Command WRITE(10) took 2.002 seconds (ok)
Aug 20 20:39:09.439: vmx| scsi0:0: Command WRITE(10) took 1.993 seconds (ok)
Aug 20 20:39:29.579: vmx| scsi0:0: Command WRITE(10) took 2.079 seconds (ok)
Aug 20 20:39:33.663: vmx| scsi0:0: Command WRITE(10) took 2.136 seconds (ok)
Aug 20 20:39:37.817: vmx| scsi0:0: Command WRITE(10) took 2.144 seconds (ok)
Aug 20 20:39:48.412: vmx| scsi0:0: Command WRITE(10) took 8.505 seconds (ok)
Aug 20 20:39:59.263: vmx| scsi0:0: Command WRITE(10) took 1.869 seconds (ok)
Aug 20 20:40:03.673: vmx| scsi0:0: Command WRITE(10) took 2.239 seconds (ok)
Aug 20 20:40:07.912: vmx| scsi0:0: Command WRITE(10) took 2.135 seconds (ok)
Aug 20 20:40:30.597: vmx| scsi0:0: Command WRITE(10) took 1.927 seconds (ok)
Aug 20 20:40:34.786: vmx| scsi0:0: Command WRITE(10) took 2.063 seconds (ok)
Aug 20 20:40:39.154: vmx| scsi0:0: Command WRITE(10) took 2.222 seconds (ok)
Aug 20 20:40:59.103: vmx| scsi0:0: Command WRITE(10) took 2.103 seconds (ok)
Aug 20 20:41:03.343: vmx| scsi0:0: Command WRITE(10) took 2.183 seconds (ok)
Aug 20 20:41:08.346: vmx| scsi0:0: Command WRITE(10) took 2.119 seconds (ok)
Aug 20 20:41:17.658: vmx| scsi0:0: Command WRITE(10) took 7.260 seconds (ok)
Aug 20 20:41:30.621: vmx| scsi0:0: Command WRITE(10) took 2.128 seconds (ok)
Aug 20 20:41:34.957: vmx| scsi0:0: Command WRITE(10) took 2.129 seconds (ok)
Aug 20 20:41:48.116: vmx| scsi0:0: Command WRITE(10) took 11.073 seconds (ok)
Aug 20 20:41:59.821: vmx| scsi0:0: Command WRITE(10) took 2.160 seconds (ok)
Aug 20 20:42:03.967: vmx| scsi0:0: Command WRITE(10) took 2.158 seconds (ok)
Aug 20 20:42:07.853: vmx| scsi0:0: Command WRITE(10) took 1.900 seconds (ok)
Aug 20 20:42:29.938: vmx| scsi0:0: Command WRITE(10) took 2.298 seconds (ok)
Aug 20 20:42:34.259: vmx| scsi0:0: Command WRITE(10) took 2.310 seconds (ok)
Aug 20 20:42:38.836: vmx| scsi0:0: Command WRITE(10) took 2.316 seconds (ok)
Aug 20 20:42:49.449: vmx| scsi0:0: Command WRITE(10) took 8.597 seconds (ok)
Aug 20 20:43:02.513: vmx| scsi0:0: Command WRITE(10) took 2.105 seconds (ok)
Aug 20 20:43:07.059: vmx| scsi0:0: Command WRITE(10) took 2.364 seconds (ok)
Aug 20 20:43:20.888: vmx| scsi0:0: Command WRITE(10) took 11.643 seconds (ok)
Aug 20 20:43:31.991: vmx| scsi0:0: Command WRITE(10) took 2.269 seconds (ok)
Aug 20 20:43:36.613: vmx| scsi0:0: Command WRITE(10) took 2.401 seconds (ok)
Aug 20 20:43:41.240: vmx| scsi0:0: Command WRITE(10) took 2.406 seconds (ok)
Aug 20 20:44:05.064: vmx| scsi0:0: Command WRITE(10) took 2.436 seconds (ok)
Aug 20 20:44:09.750: vmx| scsi0:0: Command WRITE(10) took 2.298 seconds (ok)
Aug 20 20:44:14.456: vmx| scsi0:0: Command WRITE(10) took 2.449 seconds (ok)
Aug 20 20:44:35.042: vmx| scsi0:0: Command WRITE(10) took 2.481 seconds (ok)
Aug 20 20:44:39.937: vmx| scsi0:0: Command WRITE(10) took 2.481 seconds (ok)
Aug 20 20:44:44.842: vmx| scsi0:0: Command WRITE(10) took 2.484 seconds (ok)
Aug 20 20:48:41.509: vmx| scsi0:0: Command WRITE(10) took 2.460 seconds (ok)
Aug 20 20:48:46.710: vmx| scsi0:0: Command WRITE(10) took 2.788 seconds (ok)
Aug 20 20:49:00.955: vmx| scsi0:0: Command WRITE(10) took 11.982 seconds (ok)
Aug 20 20:49:17.486: vmx| scsi0:0: Command WRITE(10) took 2.040 seconds (ok)
Aug 20 20:49:21.549: vmx| scsi0:0: Command WRITE(10) took 2.844 seconds (ok)
Aug 20 20:49:47.378: vmx| scsi0:0: Command WRITE(10) took 2.999 seconds (ok)
Aug 20 20:49:52.929: vmx| scsi0:0: Command WRITE(10) took 2.903 seconds (ok)
Aug 20 20:50:07.827: vmx| scsi0:0: Command WRITE(10) took 12.397 seconds (ok)
Aug 20 20:50:23.934: vmx| scsi0:0: Command WRITE(10) took 2.783 seconds (ok)
Aug 20 20:54:50.361: vmx| scsi0:0: Command WRITE(10) took 263.746 seconds (ok)
Aug 20 20:55:10.575: vmx| scsi0:0: Command WRITE(10) took 3.255 seconds (ok)
Aug 20 20:55:40.339: vcpu-0| scsi0:0: Command WRITE(10) took 3.317 seconds (ok)
Aug 20 20:55:43.579: vcpu-0| SCSI0: RESET BUS
Aug 20 20:56:16.301: vmx| scsi0:0: Command WRITE(10) took 2.946 seconds (ok)
Aug 20 20:56:36.178: vmx| scsi0:0: Command WRITE(10) took 16.811 seconds (ok)
Aug 20 20:56:53.437: vmx| scsi0:0: Command WRITE(10) took 3.329 seconds (ok)
Aug 20 20:57:11.685: vmx| scsi0:0: Command WRITE(10) took 15.164 seconds (ok)
Aug 20 20:57:32.720: vcpu-0| scsi0:0: Command WRITE(10) took 3.395 seconds (ok)
Aug 20 20:57:35.897: vcpu-0| SCSI0: RESET BUS
Aug 20 20:58:27.553: vmx| scsi0:0: Command WRITE(10) took 13.204 seconds (ok)
Aug 20 20:58:44.018: vmx| scsi0:0: Command WRITE(10) took 12.900 seconds (ok)
Aug 20 20:59:03.242: vmx| scsi0:0: Command WRITE(10) took 15.765 seconds (ok)
Aug 20 20:59:23.124: vcpu-0| scsi0:0: Command WRITE(10) took 3.527 seconds (ok)
Aug 20 21:04:09.199: vcpu-0| SCSI0: RESET BUS
Aug 20 21:04:39.091: vmx| scsi0:0: Command WRITE(10) took 1.057 seconds (ok)
Aug 20 21:04:43.737: vmx| scsi0:0: Command WRITE(10) took 1.719 seconds (ok)
Aug 20 21:04:57.726: vmx| scsi0:0: Command WRITE(10) took 11.252 seconds (ok)
Aug 20 21:05:06.606: vmx| scsi0:0: Command WRITE(10) took 1.506 seconds (ok)
Aug 20 21:05:09.351: vmx| scsi0:0: Command WRITE(10) took 1.904 seconds (ok)
Aug 20 21:05:13.992: vmx| scsi0:0: Command WRITE(10) took 2.179 seconds (ok)
Aug 20 21:05:33.984: vmx| scsi0:0: Command WRITE(10) took 15.834 seconds (ok)
Aug 20 21:06:10.908: vmx| scsi0:0: Command WRITE(10) took 16.550 seconds (ok)
Aug 20 21:06:28.550: vmx| scsi0:0: Command WRITE(10) took 3.415 seconds (ok)
Aug 20 21:06:48.832: vmx| scsi0:0: Command WRITE(10) took 17.160 seconds (ok)
Aug 20 21:07:08.343: vcpu-0| scsi0:0: Command WRITE(10) took 3.771 seconds (ok)
Aug 20 21:07:11.560: vcpu-0| SCSI0: RESET BUS
Aug 20 21:13:03.616: vmx| scsi0:0: Command WRITE(10) took 174.795 seconds (ok)
Aug 20 21:13:27.648: vmx| scsi0:0: Command WRITE(10) took 20.161 seconds (ok)
Aug 20 21:14:06.745: vmx| scsi0:0: Command WRITE(10) took 18.696 seconds (ok)
Aug 20 21:14:28.063: vmx| scsi0:0: Command WRITE(10) took 17.401 seconds (ok)
Aug 20 21:15:04.211: vcpu-0| scsi0:0: Command WRITE(10) took 3.602 seconds (ok)
Aug 20 21:15:07.881: vcpu-0| SCSI0: RESET BUS
Aug 20 21:15:44.005: vmx| scsi0:0: Command WRITE(10) took 4.098 seconds (ok)
Aug 20 21:16:05.165: vmx| scsi0:0: Command WRITE(10) took 17.198 seconds (ok)
Aug 20 21:16:24.034: mks| MKS lost grab
Aug 20 21:16:44.060: vmx| scsi0:0: Command WRITE(10) took 4.542 seconds (ok)
Aug 20 21:17:26.683: vcpu-0| scsi0:0: Command WRITE(10) took 40.216 seconds (ok)
Aug 20 21:17:30.552: vcpu-0| SCSI0: RESET BUS
Aug 20 21:19:08.857: vcpu-0| scsi0:0: Command WRITE(10) took 62.334 seconds (ok)
Aug 20 21:19:13.073: vcpu-0| SCSI0: RESET BUS
Aug 20 21:19:53.655: vcpu-0| scsi0:0: Command WRITE(10) took 3.741 seconds (ok)
Aug 20 21:19:56.294: vcpu-0| SCSI0: RESET BUS
Aug 20 21:20:31.284: mks| MKS lost grab
Aug 20 21:21:13.765: mks| MKS lost grab
Aug 20 21:22:29.013: vmx| scsi0:0: Command WRITE(10) took 31.936 seconds (ok)
Aug 20 21:29:04.792: vmx| scsi0:0: Command WRITE(10) took 391.319 seconds (ok)
Aug 20 21:29:42.650: vmx| Caught signal 15 -- tid 10584 (eip 0xb80c5430)

```
The above is log of a file vmware.log

---

### Post by jamesbon on 2010-08-26
Also one more file 
```

[2010-08-20 16:53:02,586] 
[2010-08-20 16:53:02,587] 
[2010-08-20 16:53:02,587] Installer running.
[2010-08-20 16:53:02,587] Command Line Arguments:
[2010-08-20 16:53:02,587] ['/tmp/vmis.fQGYZb/install/vmware-installer/vmware-installer.py', '--set-setting', 'vmware-installer', 'libconf', '/tmp/vmis.fQGYZb/install/vmware-installer/lib/libconf', '--install-component', '/tmp/vmis.fQGYZb/install/vmware-installer', '--install-bundle', '/media/disk/Softwares/VMwareLinux/./VMware-Workstation-Full-7.1.1-282343.i386.bundle', '']
xprop:  unable to open display ''
xprop:  unable to open display ''
[2010-08-20 16:53:03,419] /tmp/vmis.fQGYZb/install/vmware-installer/python/pygtk/gtk/__init__.py:69: GtkWarning: could not open display
  warnings.warn(str(e), _gtk.Warning)
[2010-08-20 16:53:03,420] Unable to initialize gtk: could not open display
[2010-08-20 16:53:03,470] Using UI type console
[2010-08-20 16:53:03,603] Opening database file /etc/vmware-installer/database
[2010-08-20 16:53:04,037] Could not locate installer App Control.
[2010-08-20 16:53:04,115] destination /tmp/tmpSVJCCi/.installer/8.4.3/__init__.py already exists, overwriting.
[2010-08-20 16:53:04,117] destination /tmp/tmpSVJCCi/.installer/8.4.3/include/update.py already exists, overwriting.
[2010-08-20 16:53:04,126] destination /tmp/tmpSVJCCi/.installer/8.4.3/__init__.py already exists, overwriting.
[2010-08-20 16:53:04,127] destination /tmp/tmpSVJCCi/.installer/8.4.3/include/update.py already exists, overwriting.
[2010-08-20 16:53:04,182] destination /tmp/tmpSVJCCi/.installer/8.4.3/__init__.py already exists, overwriting.
[2010-08-20 16:53:04,183] destination /tmp/tmpSVJCCi/.installer/8.4.3/include/update.py already exists, overwriting.
[2010-08-20 16:53:04,192] destination /tmp/tmpSVJCCi/.installer/8.4.3/__init__.py already exists, overwriting.
[2010-08-20 16:53:04,194] destination /tmp/tmpSVJCCi/.installer/8.4.3/include/update.py already exists, overwriting.
[2010-08-20 16:53:04,265] destination /tmp/tmpSVJCCi/.installer/8.4.3/__init__.py already exists, overwriting.
[2010-08-20 16:53:04,267] destination /tmp/tmpSVJCCi/.installer/8.4.3/include/update.py already exists, overwriting.
[2010-08-20 16:53:04,304] destination /tmp/tmpSVJCCi/.installer/3.1.1/__init__.py already exists, overwriting.
[2010-08-20 16:53:04,308] destination /tmp/tmpSVJCCi/.installer/3.1.1/include/update.py already exists, overwriting.
[2010-08-20 16:53:04,484] destination /tmp/tmpSVJCCi/.installer/7.1.1/include/update.py already exists, overwriting.
[2010-08-20 16:53:04,488] destination /tmp/tmpSVJCCi/.installer/7.1.1/__init__.py already exists, overwriting.
[2010-08-20 16:53:04,492] destination /tmp/tmpSVJCCi/.installer/7.1.1/vmware-workstation.py already exists, overwriting.
[2010-08-20 16:53:04,757] 1024
[2010-08-20 16:53:14,202] Cannot use vmware-app-control to shut down open VMs, defaulting to fallback message.
[2010-08-20 16:53:14,215] Ignored execution error: [Errno 2] No such file or directory when running command: [None, 'stoppable']
[2010-08-20 16:54:43,750] 2.6.28-11-generic
[2010-08-20 16:55:17,619] Attempting to change symlink /usr/lib/vmware/bin/vmplayer to permission 493. Operation is not allowed, skipping.
[2010-08-20 16:55:17,619] Attempting to change symlink /usr/lib/vmware/bin/vmware-acetool to permission 493. Operation is not allowed, skipping.
[2010-08-20 16:55:17,619] Attempting to change symlink /usr/lib/vmware/bin/vmware-unity-helper to permission 493. Operation is not allowed, skipping.
[2010-08-20 16:55:17,620] Attempting to change symlink /usr/lib/vmware/bin/vmware-modconfig to permission 493. Operation is not allowed, skipping.
[2010-08-20 16:55:17,620] Attempting to change symlink /usr/lib/vmware/bin/vmware-modconfig-console to permission 493. Operation is not allowed, skipping.
[2010-08-20 16:55:17,620] Attempting to change symlink /usr/lib/vmware/bin/vmplayer-daemon to permission 493. Operation is not allowed, skipping.
[2010-08-20 16:55:17,621] Attempting to change symlink /usr/lib/vmware/bin/vmware-gksu to permission 493. Operation is not allowed, skipping.
[2010-08-20 16:55:17,621] Attempting to change symlink /usr/lib/vmware/bin/vmware-fuseUI to permission 493. Operation is not allowed, skipping.
[2010-08-20 16:55:17,621] Attempting to change symlink /usr/lib/vmware/bin/vmware-app-control to permission 493. Operation is not allowed, skipping.
[2010-08-20 16:55:19,786] GNOME gnome-panel 2.26.0
[2010-08-20 16:55:22,275] Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Unknown media type in type 'uri/mms'
Unknown media type in type 'uri/mmst'
Unknown media type in type 'uri/mmsu'
Unknown media type in type 'uri/pnm'
Unknown media type in type 'uri/rtspt'
Unknown media type in type 'uri/rtspu'
Unknown media type in type 'fonts/package'
Unknown media type in type 'interface/x-winamp-skin'
 
[2010-08-20 16:55:26,725] Configuring Bridged network vmnet0
Configuring hostonly network vmnet1, probing for unused subnet ...
Configuring NAT network vmnet8, probing for unused subnet ...
Configured default networks - Bridged, Hostonly, NAT
[2010-08-20 16:55:26,827]  * Restarting Common Unix Printing System: cupsd
   ...done.
[2010-08-20 16:55:26,831] Prelink not present, skipping configuration.
[2010-08-20 16:55:27,094] Stopping VMware services:
   VMware USB Arbitrator[71G done
   VM communication interface socket family[71G done
   Virtual machine communication interface[71G done
   Virtual machine monitor[71G done
   Blocking file system[71G done
[2010-08-20 16:55:27,290] Starting VMware services:
   VMware USB Arbitrator[71G done
   Virtual machine monitor[71Gfailed
   Virtual machine communication interface[71Gfailed
   VM communication interface socket family[71Gfailed
   Blocking file system[71Gfailed
   Virtual ethernet[71Gfailed
[2010-08-20 16:55:27,469]  * Setting kernel variables (/etc/sysctl.conf)...
   ...done.
 * Setting kernel variables (/etc/sysctl.d/10-console-messages.conf)...
   ...done.
 * Setting kernel variables (/etc/sysctl.d/10-network-security.conf)...
   ...done.
 * Setting kernel variables (/etc/sysctl.d/30-wine.conf)...
   ...done.
[2010-08-20 16:55:28,066] 
[2010-08-20 16:55:28,066] 
[2010-08-20 16:55:28,066] Installer running.
[2010-08-20 16:55:28,066] Command Line Arguments:
[2010-08-20 16:55:28,066] ['/tmp/vmis.fQGYZb/install/vmware-installer/vmware-installer.py', '--register-file', 'vmware-player-app', 'regular', '/lib/modules/2.6.28-11-generic/misc/vmmon.o']
xprop:  unable to open display ''
xprop:  unable to open display ''
[2010-08-20 16:55:28,522] /tmp/vmis.fQGYZb/install/vmware-installer/python/pygtk/gtk/__init__.py:69: GtkWarning: could not open display
  warnings.warn(str(e), _gtk.Warning)
[2010-08-20 16:55:28,523] Unable to initialize gtk: could not open display
[2010-08-20 16:55:28,527] Using UI type console
[2010-08-20 16:55:28,531] Opening database file /etc/vmware-installer/database
[2010-08-20 16:55:28,677] 
[2010-08-20 16:55:28,677] 
[2010-08-20 16:55:28,677] Installer running.
[2010-08-20 16:55:28,677] Command Line Arguments:
[2010-08-20 16:55:28,678] ['/tmp/vmis.fQGYZb/install/vmware-installer/vmware-installer.py', '--register-file', 'vmware-player-app', 'regular', '/lib/modules/2.6.28-11-generic/misc/vmmon.ko']
xprop:  unable to open display ''
xprop:  unable to open display ''
[2010-08-20 16:55:29,161] /tmp/vmis.fQGYZb/install/vmware-installer/python/pygtk/gtk/__init__.py:69: GtkWarning: could not open display
  warnings.warn(str(e), _gtk.Warning)
[2010-08-20 16:55:29,162] Unable to initialize gtk: could not open display
[2010-08-20 16:55:29,165] Using UI type console
[2010-08-20 16:55:29,169] Opening database file /etc/vmware-installer/database
[2010-08-20 16:55:36,695] 
[2010-08-20 16:55:36,695] 
[2010-08-20 16:55:36,695] Installer running.
[2010-08-20 16:55:36,695] Command Line Arguments:
[2010-08-20 16:55:36,695] ['/tmp/vmis.fQGYZb/install/vmware-installer/vmware-installer.py', '--register-file', 'vmware-player-app', 'regular', '/lib/modules/2.6.28-11-generic/misc/vmnet.o']
xprop:  unable to open display ''
xprop:  unable to open display ''
[2010-08-20 16:55:37,151] /tmp/vmis.fQGYZb/install/vmware-installer/python/pygtk/gtk/__init__.py:69: GtkWarning: could not open display
  warnings.warn(str(e), _gtk.Warning)
[2010-08-20 16:55:37,152] Unable to initialize gtk: could not open display
[2010-08-20 16:55:37,158] Using UI type console
[2010-08-20 16:55:37,163] Opening database file /etc/vmware-installer/database
[2010-08-20 16:55:37,368] 
[2010-08-20 16:55:37,368] 
[2010-08-20 16:55:37,369] Installer running.
[2010-08-20 16:55:37,369] Command Line Arguments:
[2010-08-20 16:55:37,369] ['/tmp/vmis.fQGYZb/install/vmware-installer/vmware-installer.py', '--register-file', 'vmware-player-app', 'regular', '/lib/modules/2.6.28-11-generic/misc/vmnet.ko']
xprop:  unable to open display ''
xprop:  unable to open display ''
[2010-08-20 16:55:37,815] /tmp/vmis.fQGYZb/install/vmware-installer/python/pygtk/gtk/__init__.py:69: GtkWarning: could not open display
  warnings.warn(str(e), _gtk.Warning)
[2010-08-20 16:55:37,816] Unable to initialize gtk: could not open display
[2010-08-20 16:55:37,820] Using UI type console
[2010-08-20 16:55:37,825] Opening database file /etc/vmware-installer/database
[2010-08-20 16:55:38,353] 
[2010-08-20 16:55:38,353] 
[2010-08-20 16:55:38,353] Installer running.
[2010-08-20 16:55:38,354] Command Line Arguments:
[2010-08-20 16:55:38,354] ['/tmp/vmis.fQGYZb/install/vmware-installer/vmware-installer.py', '--register-file', 'vmware-player-app', 'regular', '/lib/modules/2.6.28-11-generic/misc/vmblock.o']
xprop:  unable to open display ''
xprop:  unable to open display ''
[2010-08-20 16:55:38,802] /tmp/vmis.fQGYZb/install/vmware-installer/python/pygtk/gtk/__init__.py:69: GtkWarning: could not open display
  warnings.warn(str(e), _gtk.Warning)
[2010-08-20 16:55:38,803] Unable to initialize gtk: could not open display
[2010-08-20 16:55:38,808] Using UI type console
[2010-08-20 16:55:38,811] Opening database file /etc/vmware-installer/database
[2010-08-20 16:55:38,973] 
[2010-08-20 16:55:38,974] 
[2010-08-20 16:55:38,974] Installer running.
[2010-08-20 16:55:38,974] Command Line Arguments:
[2010-08-20 16:55:38,974] ['/tmp/vmis.fQGYZb/install/vmware-installer/vmware-installer.py', '--register-file', 'vmware-player-app', 'regular', '/lib/modules/2.6.28-11-generic/misc/vmblock.ko']
xprop:  unable to open display ''
xprop:  unable to open display ''
[2010-08-20 16:55:39,417] /tmp/vmis.fQGYZb/install/vmware-installer/python/pygtk/gtk/__init__.py:69: GtkWarning: could not open display
  warnings.warn(str(e), _gtk.Warning)
[2010-08-20 16:55:39,418] Unable to initialize gtk: could not open display
[2010-08-20 16:55:39,421] Using UI type console
[2010-08-20 16:55:39,425] Opening database file /etc/vmware-installer/database
[2010-08-20 16:55:39,957] 
[2010-08-20 16:55:39,957] 
[2010-08-20 16:55:39,957] Installer running.
[2010-08-20 16:55:39,958] Command Line Arguments:
[2010-08-20 16:55:39,958] ['/tmp/vmis.fQGYZb/install/vmware-installer/vmware-installer.py', '--register-file', 'vmware-player-app', 'regular', '/lib/modules/2.6.28-11-generic/misc/vmci.o']
xprop:  unable to open display ''
xprop:  unable to open display ''
[2010-08-20 16:55:40,404] /tmp/vmis.fQGYZb/install/vmware-installer/python/pygtk/gtk/__init__.py:69: GtkWarning: could not open display
  warnings.warn(str(e), _gtk.Warning)
[2010-08-20 16:55:40,405] Unable to initialize gtk: could not open display
[2010-08-20 16:55:40,408] Using UI type console
[2010-08-20 16:55:40,412] Opening database file /etc/vmware-installer/database
[2010-08-20 16:55:40,615] 
[2010-08-20 16:55:40,615] 
[2010-08-20 16:55:40,615] Installer running.
[2010-08-20 16:55:40,615] Command Line Arguments:
[2010-08-20 16:55:40,615] ['/tmp/vmis.fQGYZb/install/vmware-installer/vmware-installer.py', '--register-file', 'vmware-player-app', 'regular', '/lib/modules/2.6.28-11-generic/misc/vmci.ko']
xprop:  unable to open display ''
xprop:  unable to open display ''
[2010-08-20 16:55:41,057] /tmp/vmis.fQGYZb/install/vmware-installer/python/pygtk/gtk/__init__.py:69: GtkWarning: could not open display
  warnings.warn(str(e), _gtk.Warning)
[2010-08-20 16:55:41,058] Unable to initialize gtk: could not open display
[2010-08-20 16:55:41,061] Using UI type console
[2010-08-20 16:55:41,065] Opening database file /etc/vmware-installer/database
[2010-08-20 16:55:41,556] 
[2010-08-20 16:55:41,557] 
[2010-08-20 16:55:41,557] Installer running.
[2010-08-20 16:55:41,557] Command Line Arguments:
[2010-08-20 16:55:41,557] ['/tmp/vmis.fQGYZb/install/vmware-installer/vmware-installer.py', '--register-file', 'vmware-player-app', 'regular', '/lib/modules/2.6.28-11-generic/misc/vsock.o']
xprop:  unable to open display ''
xprop:  unable to open display ''
[2010-08-20 16:55:42,000] /tmp/vmis.fQGYZb/install/vmware-installer/python/pygtk/gtk/__init__.py:69: GtkWarning: could not open display
  warnings.warn(str(e), _gtk.Warning)
[2010-08-20 16:55:42,001] Unable to initialize gtk: could not open display
[2010-08-20 16:55:42,005] Using UI type console
[2010-08-20 16:55:42,009] Opening database file /etc/vmware-installer/database
[2010-08-20 16:55:42,197] 
[2010-08-20 16:55:42,197] 
[2010-08-20 16:55:42,197] Installer running.
[2010-08-20 16:55:42,197] Command Line Arguments:
[2010-08-20 16:55:42,198] ['/tmp/vmis.fQGYZb/install/vmware-installer/vmware-installer.py', '--register-file', 'vmware-player-app', 'regular', '/lib/modules/2.6.28-11-generic/misc/vsock.ko']
xprop:  unable to open display ''
xprop:  unable to open display ''
[2010-08-20 16:55:42,630] /tmp/vmis.fQGYZb/install/vmware-installer/python/pygtk/gtk/__init__.py:69: GtkWarning: could not open display
  warnings.warn(str(e), _gtk.Warning)
[2010-08-20 16:55:42,630] Unable to initialize gtk: could not open display
[2010-08-20 16:55:42,634] Using UI type console
[2010-08-20 16:55:42,638] Opening database file /etc/vmware-installer/database
[2010-08-20 16:55:45,349] Stopping VMware services:
   VMware USB Arbitrator[71G done
   VM communication interface socket family[71G done
   Virtual machine communication interface[71G done
   Virtual machine monitor[71G done
   Blocking file system[71G done
Starting VMware services:
   VMware USB Arbitrator[71G done
   Virtual machine monitor[71G done
   Virtual machine communication interface[71G done
   VM communication interface socket family[71G done
   Blocking file system[71G done
   Virtual ethernet[71G done
   Shared Memory Available[71G done
Installed vmmon pre-built module
Installed vmnet pre-built module
Installed vmblock pre-built module
Installed vmci pre-built module
Installed vsock pre-built module
[2010-08-20 16:55:45,353] Successfully installed kernel modules
[2010-08-20 16:55:59,281] Attempting to change symlink /usr/lib/vmware/bin/vmware to permission 493. Operation is not allowed, skipping.
[2010-08-20 16:55:59,282] Attempting to change symlink /usr/lib/vmware/bin/vmware-tray to permission 493. Operation is not allowed, skipping.
[2010-08-20 16:55:59,282] Attempting to change symlink /usr/lib/vmware/bin/vmware-netcfg to permission 493. Operation is not allowed, skipping.
[2010-08-20 16:55:59,283] Attempting to change symlink /usr/lib/vmware/bin/vmware-gdb-proxy to permission 493. Operation is not allowed, skipping.
[2010-08-20 16:56:01,191] GNOME gnome-panel 2.26.0
[2010-08-20 16:56:01,936] Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Unknown media type in type 'uri/mms'
Unknown media type in type 'uri/mmst'
Unknown media type in type 'uri/mmsu'
Unknown media type in type 'uri/pnm'
Unknown media type in type 'uri/rtspt'
Unknown media type in type 'uri/rtspu'
Unknown media type in type 'fonts/package'
Unknown media type in type 'interface/x-winamp-skin'
 
[2010-08-20 16:56:04,778] Stopping VMware services:
   VMware USB Arbitrator[71G done
   VM communication interface socket family[71G done
   Virtual machine communication interface[71G done
   Virtual machine monitor[71G done
   Blocking file system[71G done
Starting VMware services:
   VMware USB Arbitrator[71G done
   Virtual machine monitor[71G done
   Virtual machine communication interface[71G done
   VM communication interface socket family[71G done
   Blocking file system[71G done
   Virtual ethernet[71G done
   Shared Memory Available[71G done
 

```

---

