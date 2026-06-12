---
title: "vmware-server Guest crashes on high I/O"
date: 2009-12-06
forum: Virtualisation
---

### Post by cu8164kp on 2009-12-06
Ubuntu 9.10 32bit
Kernel: 2.6.31-16-generic-pae
VMware-server-2.0.2-203138
Guest: Win2003
Guest image created with VMWare-Converter

Problem is Windows guest crashes, and by crash I mean the process dies.  VMWare itself is still running but the guest dies like somebody pulled the plug.

I can make it crash everytime by doing a backup inside of the Window VM, but any high disk I/0 seems to cause the problem.  I"ve also had the guest crash from doing a simple "cp -Rp /vmguest /backup/." in the host, it'll crash weather the guest system is running or is sent to pause.  

Below is my VMX and a log dump from VMWare at the time of the crash.  I've tried turning on and off every setting I can think of.  I've change the disk image to a disk sepearte than the OS, I've tried various controllers using SCSI and IDE both with the same results.  Initially I was 64bit Ubuntu and 64bit VMware but I thought that might have been the problem so I re-loaded as 32bit all around.

The machine is fast, responsive, and reliable except for the high I/O stuff which always causes the crashing.   I've been trying to figure this problem out for over a week and haven't had any luck with anything I've tried.  Thanks for any help or advise:


### VMX ####

#!/usr/bin/vmware
.encoding = "UTF-8"
config.version = "8"
virtualHW.version = "7"
memsize = "2048"
MemAllowAutoScaleDown = "FALSE"
displayName = "notes03"
guestOS = "winnetstandard"
floppy0.present = "TRUE"
floppy0.autodetect = "TRUE"
floppy0.filename = "auto detect"
usb.present = "TRUE"
serial0.present = "TRUE"
serial0.fileType = "device"
serial0.fileName = "auto-detect"
serial0.autodetect = "true"
parallel0.present = "TRUE"
parallel0.fileType = "device"
parallel0.fileName = "auto-detect"
parallel0.autodetect = "true"
ethernet0.present = "TRUE"
ethernet0.addressType = "generated"
ethernet0.connectionType = "bridged"
ethernet0.startConnected = "TRUE"
ide0:0.present = "TRUE"
ide0:0.fileName = "notes03.vmdk"
ide0:1.present = "TRUE"
ide0:1.fileName = "notes03-0.vmdk"
ide1:0.present = "TRUE"
ide1:0.autodetect = "TRUE"
ide1:0.filename = "auto detect"
ide1:0.deviceType = "cdrom-raw"
ide1:1.present = "TRUE"
ide1:1.autodetect = "TRUE"
ide1:1.filename = "auto detect"
ide1:1.deviceType = "cdrom-raw"
buslogic.noDriver = "false"
virtualHW.productCompatibility = "hosted"
scsi0:0.redo = ""
scsi0:1.redo = ""
vmotion.checkpointFBSize = "16777216"
tools.syncTime = "false"
mainMem.useNamedFile = "FALSE"
extendedConfigFile = "notes03.vmxf"
tools.upgrade.policy = "manual"
ide1:1.startConnected = "FALSE"
uuid.location = "56 4d ea b0 c6 55 02 83-8a ed 72 eb 01 15 fd ec"
uuid.bios = "56 4d ea b0 c6 55 02 83-8a ed 72 eb 01 15 fd ec"
ide0:0.redo = ""
ide0:1.redo = ""
ethernet0.generatedAddressOffset = "0"
floppy0.startConnected = "FALSE"

###############
# vmware log a couple lines before it crashed:
###############
Dec 06 19:03:08.580: vcpu-0| DISKLIB-LIB   : numIOs = 200000 numMergedIOs = 10226 numSplitIOs = 0
Dec 06 19:04:38.426: vmx| DISKLIB-LIB   : numIOs = 250000 numMergedIOs = 10867 numSplitIOs = 0
Dec 06 19:04:54.445: Worker#4| Caught signal 6 -- tid 16082
Dec 06 19:04:54.445: Worker#4| SIGNAL: eip 0xb7887430 esp 0x4cdbc018 ebp 0x4cdbc030
Dec 06 19:04:54.445: Worker#4| SIGNAL: eax 0x0 ebx 0x3ecb ecx 0x3ed2 edx 0x6 esi 0x2 edi 0xb7817ff4
Dec 06 19:04:54.445: Worker#4| SIGNAL: stack 4CDBC018 : 0x4cdbc030 0x00000006 0x00003ed2 0xb77024d1
Dec 06 19:04:54.445: Worker#4| SIGNAL: stack 4CDBC028 : 0xb7817ff4 0x4cdbc150 0x4cdbc158 0xb7705932
Dec 06 19:04:54.445: Worker#4| SIGNAL: stack 4CDBC038 : 0x00000006 0x4cdbc0d0 0x00000000 0x00000000
Dec 06 19:04:54.445: Worker#4| SIGNAL: stack 4CDBC048 : 0x00000000 0x00000000 0x00000000 0x00000000
Dec 06 19:04:54.445: Worker#4| SIGNAL: stack 4CDBC058 : 0x00000000 0x00000000 0x00000000 0x00000000
Dec 06 19:04:54.445: Worker#4| SIGNAL: stack 4CDBC068 : 0x00000000 0x00000000 0x00000000 0x00000000
Dec 06 19:04:54.446: Worker#4| SIGNAL: stack 4CDBC078 : 0x00000000 0x00000000 0x00000000 0x00000000
Dec 06 19:04:54.446: Worker#4| SIGNAL: stack 4CDBC088 : 0x00000000 0x00000000 0x0a10e800 0x00000000
Dec 06 19:04:54.446: Worker#4| Backtrace:
Dec 06 19:04:54.446: Worker#4| Backtrace[0] 0x4cdbbbd8 eip 0x8052690 
Dec 06 19:04:54.446: Worker#4| Backtrace[1] 0x4cdbbc98 eip 0x80a71e0 
Dec 06 19:04:54.446: Worker#4| Backtrace[2] 0x4cdbc030 eip 0xb7887410 
Dec 06 19:04:54.446: Worker#4| Backtrace[3] 0x4cdbc158 eip 0xb7705932 
Dec 06 19:04:54.446: Worker#4| Backtrace[4] 0x4cdbc190 eip 0xb774301b 
Dec 06 19:04:54.446: Worker#4| Backtrace[5] 0x4cdbc1a8 eip 0xb7747806 
Dec 06 19:04:54.446: Worker#4| Backtrace[6] 0x4cdbc1f8 eip 0x80bd34f 
Dec 06 19:04:54.446: Worker#4| Backtrace[7] 0x4cdbc248 eip 0x819c39f 
Dec 06 19:04:54.446: Worker#4| Backtrace[8] 0x4cdbc288 eip 0x8139cff 
Dec 06 19:04:54.446: Worker#4| Backtrace[9] 0x4cdbc2b8 eip 0x8139f07 
Dec 06 19:04:54.446: Worker#4| Backtrace[10] 0x4cdbc398 eip 0x80c338d 
Dec 06 19:04:54.446: Worker#4| Backtrace[11] 0x4cdbc498 eip 0xb783780e 
Dec 06 19:04:54.446: Worker#4| Backtrace[12] 00000000 eip 0xb77a47ee 
Dec 06 19:04:54.446: Worker#4| SymBacktrace[0] 0x4cdbbbd8 eip 0x8052690 in function (null) in object /usr/lib/vmware/bin/vmware-vmx loaded at 0x8048000
Dec 06 19:04:54.446: Worker#4| SymBacktrace[1] 0x4cdbbc98 eip 0x80a71e0 in function (null) in object /usr/lib/vmware/bin/vmware-vmx loaded at 0x8048000
Dec 06 19:04:54.446: Worker#4| SymBacktrace[2] 0x4cdbc030 eip 0xb7887410 in function __kernel_rt_sigreturn in object  loaded at 0xb7887000
Dec 06 19:04:54.446: Worker#4| SymBacktrace[3] 0x4cdbc158 eip 0xb7705932 in function abort in object /lib/tls/i686/cmov/libc.so.6 loaded at 0xb76d8000
Dec 06 19:04:54.446: Worker#4| SymBacktrace[4] 0x4cdbc190 eip 0xb774301b in function (null) in object /lib/tls/i686/cmov/libc.so.6 loaded at 0xb76d8000
Dec 06 19:04:54.446: Worker#4| SymBacktrace[5] 0x4cdbc1a8 eip 0xb7747806 in function cfree in object /lib/tls/i686/cmov/libc.so.6 loaded at 0xb76d8000
Dec 06 19:04:54.446: Worker#4| SymBacktrace[6] 0x4cdbc1f8 eip 0x80bd34f in function (null) in object /usr/lib/vmware/bin/vmware-vmx loaded at 0x8048000
Dec 06 19:04:54.446: Worker#4| SymBacktrace[7] 0x4cdbc248 eip 0x819c39f in function (null) in object /usr/lib/vmware/bin/vmware-vmx loaded at 0x8048000
Dec 06 19:04:54.446: Worker#4| SymBacktrace[8] 0x4cdbc288 eip 0x8139cff in function (null) in object /usr/lib/vmware/bin/vmware-vmx loaded at 0x8048000
Dec 06 19:04:54.446: Worker#4| SymBacktrace[9] 0x4cdbc2b8 eip 0x8139f07 in function (null) in object /usr/lib/vmware/bin/vmware-vmx loaded at 0x8048000
Dec 06 19:04:54.446: Worker#4| SymBacktrace[10] 0x4cdbc398 eip 0x80c338d in function (null) in object /usr/lib/vmware/bin/vmware-vmx loaded at 0x8048000
Dec 06 19:04:54.446: Worker#4| SymBacktrace[11] 0x4cdbc498 eip 0xb783780e in function (null) in object /lib/tls/i686/cmov/libpthread.so.0 loaded at 0xb7832000
Dec 06 19:04:54.446: Worker#4| SymBacktrace[12] 00000000 eip 0xb77a47ee in function clone in object /lib/tls/i686/cmov/libc.so.6 loaded at 0xb76d8000
Dec 06 19:04:54.446: Worker#4| Unexpected signal: 6.
Dec 06 19:04:54.446: Worker#4| Core dump limit is 0 KB.
Dec 06 19:04:54.452: Worker#4| Child process 16329 failed to dump core (status 0x6).
Dec 06 19:04:54.452: Worker#4| Backtrace:
Dec 06 19:04:54.452: Worker#4| Backtrace[0] 0x4cdbb7a8 eip 0x8052690 
Dec 06 19:04:54.452: Worker#4| Backtrace[1] 0x4cdbbbd8 eip 0x8122356 
Dec 06 19:04:54.452: Worker#4| Backtrace[2] 0x4cdbbc98 eip 0x80a73d1 
Dec 06 19:04:54.452: Worker#4| Backtrace[3] 0x4cdbc030 eip 0xb7887410 
Dec 06 19:04:54.452: Worker#4| Backtrace[4] 0x4cdbc158 eip 0xb7705932 
Dec 06 19:04:54.452: Worker#4| Backtrace[5] 0x4cdbc190 eip 0xb774301b 
Dec 06 19:04:54.452: Worker#4| Backtrace[6] 0x4cdbc1a8 eip 0xb7747806 
Dec 06 19:04:54.452: Worker#4| Backtrace[7] 0x4cdbc1f8 eip 0x80bd34f 
Dec 06 19:04:54.452: Worker#4| Backtrace[8] 0x4cdbc248 eip 0x819c39f 
Dec 06 19:04:54.452: Worker#4| Backtrace[9] 0x4cdbc288 eip 0x8139cff 
Dec 06 19:04:54.452: Worker#4| Backtrace[10] 0x4cdbc2b8 eip 0x8139f07 
Dec 06 19:04:54.452: Worker#4| Backtrace[11] 0x4cdbc398 eip 0x80c338d 
Dec 06 19:04:54.452: Worker#4| Backtrace[12] 0x4cdbc498 eip 0xb783780e 
Dec 06 19:04:54.452: Worker#4| Backtrace[13] 00000000 eip 0xb77a47ee 
Dec 06 19:04:54.452: Worker#4| SymBacktrace[0] 0x4cdbb7a8 eip 0x8052690 in function (null) in object /usr/lib/vmware/bin/vmware-vmx loaded at 0x8048000
Dec 06 19:04:54.452: Worker#4| SymBacktrace[1] 0x4cdbbbd8 eip 0x8122356 in function (null) in object /usr/lib/vmware/bin/vmware-vmx loaded at 0x8048000
Dec 06 19:04:54.452: Worker#4| SymBacktrace[2] 0x4cdbbc98 eip 0x80a73d1 in function (null) in object /usr/lib/vmware/bin/vmware-vmx loaded at 0x8048000
Dec 06 19:04:54.452: Worker#4| SymBacktrace[3] 0x4cdbc030 eip 0xb7887410 in function __kernel_rt_sigreturn in object  loaded at 0xb7887000
Dec 06 19:04:54.452: Worker#4| SymBacktrace[4] 0x4cdbc158 eip 0xb7705932 in function abort in object /lib/tls/i686/cmov/libc.so.6 loaded at 0xb76d8000
Dec 06 19:04:54.452: Worker#4| SymBacktrace[5] 0x4cdbc190 eip 0xb774301b in function (null) in object /lib/tls/i686/cmov/libc.so.6 loaded at 0xb76d8000
Dec 06 19:04:54.452: Worker#4| SymBacktrace[6] 0x4cdbc1a8 eip 0xb7747806 in function cfree in object /lib/tls/i686/cmov/libc.so.6 loaded at 0xb76d8000
Dec 06 19:04:54.452: Worker#4| SymBacktrace[7] 0x4cdbc1f8 eip 0x80bd34f in function (null) in object /usr/lib/vmware/bin/vmware-vmx loaded at 0x8048000
Dec 06 19:04:54.452: Worker#4| SymBacktrace[8] 0x4cdbc248 eip 0x819c39f in function (null) in object /usr/lib/vmware/bin/vmware-vmx loaded at 0x8048000
Dec 06 19:04:54.452: Worker#4| SymBacktrace[9] 0x4cdbc288 eip 0x8139cff in function (null) in object /usr/lib/vmware/bin/vmware-vmx loaded at 0x8048000
Dec 06 19:04:54.452: Worker#4| SymBacktrace[10] 0x4cdbc2b8 eip 0x8139f07 in function (null) in object /usr/lib/vmware/bin/vmware-vmx loaded at 0x8048000
Dec 06 19:04:54.452: Worker#4| SymBacktrace[11] 0x4cdbc398 eip 0x80c338d in function (null) in object /usr/lib/vmware/bin/vmware-vmx loaded at 0x8048000
Dec 06 19:04:54.452: Worker#4| SymBacktrace[12] 0x4cdbc498 eip 0xb783780e in function (null) in object /lib/tls/i686/cmov/libpthread.so.0 loaded at 0xb7832000
Dec 06 19:04:54.452: Worker#4| SymBacktrace[13] 00000000 eip 0xb77a47ee in function clone in object /lib/tls/i686/cmov/libc.so.6 loaded at 0xb76d8000
Dec 06 19:04:54.467: Worker#4| Msg_Post: Error
Dec 06 19:04:54.467: Worker#4| [msg.log.error.unrecoverable] VMware Server unrecoverable error: (Worker#4)
Dec 06 19:04:54.467: Worker#4| Unexpected signal: 6.
Dec 06 19:04:54.467: Worker#4| [msg.panic.haveLog] A log file is available in "/vm/notes03/vmware.log".  [msg.panic.requestSupport.withLog] Please request support and include the contents of the log file.  [msg.panic.requestSupport.vmSupport.windowsOrLinux] 
Dec 06 19:04:54.467: Worker#4| To collect data to submit to VMware support, select Help > About and click "Collect Support Data". You can also run the "vm-support" script in the Workstation folder directly.
Dec 06 19:04:54.467: Worker#4| [msg.panic.response] We will respond on the basis of your support entitlement.
Dec 06 19:04:54.467: Worker#4| ----------------------------------------
Dec 06 19:04:54.548: vcpu-0| VTHREAD watched thread 40 "Worker#4" died
Dec 06 19:04:54.552: vmx| VTHREAD watched thread 4 "vcpu-0" died
Dec 06 19:04:54.555: mks| VTHREAD watched thread 0 "vmx" died
Dec 06 19:04:54.643: Worker#5| VTHREAD watched thread 4 "vcpu-0" died
Dec 06 19:04:54.644: Worker#1| VTHREAD watched thread 4 "vcpu-0" died
Dec 06 19:04:54.644: Worker#2| VTHREAD watched thread 4 "vcpu-0" died
Dec 06 19:04:54.644: Worker#6| VTHREAD watched thread 4 "vcpu-0" died
Dec 06 19:04:54.646: Worker#0| VTHREAD watched thread 0 "vmx" died
Dec 06 19:04:54.646: Worker#3| VTHREAD watched thread 0 "vmx" died

---

### Post by cu8164kp on 2009-12-06
Also, I'm not set on using VMware.  But VMWare Conveter is what I used to create the image.  

I tried using VirtualBox (3.0-OSE and 3.1 commercial), but no mater if I use the .vmdk or convert it to native .vdi format I always get the following error in the VirtualBox logs

vm00:00:18.115 Guest Log: BIOS: int13_harddisk: function 15, unmapped device for ELDL=81

I tried using IDE, SCSI, and SATA controllers and all give me that same error as above.

Creating a image from scratch isn't a option, it weird mission critical software that can only be installed by some 3rd party company and that would take days and cost alot in downtime and support.  That's the main reason I wanted to use vmware in the first place so I could have a image that was easier to move around and backup.

Thanks,

---

### Post by dcstar on 2009-12-07
> **cu8164kp said:**
> Also, I'm not set on using VMware.  But VMWare Conveter is what I used to create the image.  
.........

With all Windows conversions from real to VM environments, you should have created a new Hardware Profile, deleted all old physical devices in it and then let Windows boot up and autodetect the VMware drivers (in VMware tools) and install them.

---

### Post by cu8164kp on 2009-12-07
Maybe something to try for the next one, but not so helpfully for the current problem.  I've checked out the hardware and everything looks correct, no funky controller and anything like that.

---

### Post by dmizer on 2009-12-07
I have been experiencing this problem as well. Only, I'm using a separate mounted HDD, and when the guest crashes, it takes out the whole IDE controller. This means that all disks on that controller are lost, so that's about 1.5TB of data gone. My guests are all Linux.
```
Dec 06 21:07:12.147: mks| SVGA: display status changed, using optimizations for local consoles.
Dec 06 21:15:52.061: vmx| TOOLS setting the tools version to '0'
Dec 06 21:17:06.339: vmx| scsi0:0: Command WRITE(10) took 1.099 seconds (ok)
Dec 06 21:17:06.501: vmx| scsi0:0: Command WRITE(10) took 1.263 seconds (ok)
Dec 06 21:17:06.666: vmx| scsi0:0: Command WRITE(10) took 1.427 seconds (ok)
Dec 06 21:17:06.887: vmx| scsi0:0: Command WRITE(10) took 1.648 seconds (ok)
Dec 06 21:17:07.072: vmx| scsi0:0: Command WRITE(10) took 1.833 seconds (ok)
Dec 06 21:17:10.864: vmx| scsi0:0: Command WRITE(10) took 1.365 seconds (ok)
Dec 06 21:17:26.338: vmx| scsi0:0: Command WRITE(10) took 1.270 seconds (ok)
Dec 06 21:17:26.363: vmx| scsi0:0: Command WRITE(10) took 1.295 seconds (ok)
Dec 06 21:17:26.546: vmx| scsi0:0: Command WRITE(10) took 1.478 seconds (ok)
Dec 06 21:17:26.570: vmx| scsi0:0: Command WRITE(10) took 1.501 seconds (ok)
Dec 06 21:17:26.593: vmx| scsi0:0: Command WRITE(10) took 1.522 seconds (ok)
Dec 06 21:18:34.820: vmx| scsi0:0: Command READ(10) took 3.951 seconds (ok)
Dec 06 21:20:07.280: vmx| scsi0:0: Command WRITE(10) took 2.170 seconds (ok)
Dec 06 21:39:28.100: vcpu-0| VCPU 0 RunVM failed: -2.
Dec 06 21:39:28.158: vcpu-0| Core dump limit is 0 KB.
Dec 06 21:39:29.159: vcpu-0| Child process 7431 failed to dump core (status 0x6).
Dec 06 21:39:29.171: vcpu-0| Backtrace:
Dec 06 21:39:29.176: vcpu-0| Backtrace[0] 00007fc900c1bae0 rip=000000000041521c rbx=0000000000000000 rbp=0000000000415500 r12=0000000000000082 r13=00007fc90333b940 r14=0000000002c70f90 r15=00007fff66754cb0
Dec 06 21:39:29.176: vcpu-0| Backtrace[1] 00007fc900c1bb00 rip=00000000004db650 rbx=00000000fffffffe rbp=0000000000000000 r12=0000000000000082 r13=00007fc90333b940 r14=0000000002c70f90 r15=00007fff66754cb0
Dec 06 21:39:29.178: vcpu-0| Backtrace[2] 00007fc900c1bfe0 rip=00000000007cf5a8 rbx=00000000fffffffe rbp=0000000000000000 r12=0000000000000082 r13=00007fc90333b940 r14=0000000002c70f90 r15=00007fff66754cb0
Dec 06 21:39:29.178: vcpu-0| Backtrace[3] 00007fc900c1c010 rip=00000000007effb9 rbx=0000000000edfea0 rbp=0000000000000000 r12=00007fff66754d30 r13=0000000000000000 r14=00007fc90571d040 r15=00007fff66754cb0
Dec 06 21:39:29.178: vcpu-0| Backtrace[4] 00007fc900c1c020 rip=000000000048542a rbx=0000000000edfea0 rbp=0000000000000000 r12=00007fff66754d30 r13=0000000000000000 r14=00007fc90571d040 r15=00007fff66754cb0
Dec 06 21:39:29.178: vcpu-0| Backtrace[5] 00007fc900c1c120 rip=00007fc904e5f3ba rbx=0000000000000000 rbp=0000000000000000 r12=0000000000000000 r13=0000000000000000 r14=00007fc90571d040 r15=00007fff66754cb0
Dec 06 21:39:29.189: vcpu-0| Backtrace[6] 00007fc900c1c260 rip=00007fc9047a6fcd rbx=00007fc900c1c950 rbp=0000000000000000 r12=0000000000000000 r13=0000000000000000 r14=00007fc90571d040 r15=00007fff66754cb0
Dec 06 21:39:29.199: vcpu-0| SymBacktrace[0] 00007fc900c1bae0 rip=000000000041521c in function (null) in object /usr/lib/vmware/bin/vmware-vmx loaded at 0000000000400000
Dec 06 21:39:29.199: vcpu-0| SymBacktrace[1] 00007fc900c1bb00 rip=00000000004db650 in function (null) in object /usr/lib/vmware/bin/vmware-vmx loaded at 0000000000400000
Dec 06 21:39:29.200: vcpu-0| SymBacktrace[2] 00007fc900c1bfe0 rip=00000000007cf5a8 in function (null) in object /usr/lib/vmware/bin/vmware-vmx loaded at 0000000000400000
Dec 06 21:39:29.200: vcpu-0| SymBacktrace[3] 00007fc900c1c010 rip=00000000007effb9 in function (null) in object /usr/lib/vmware/bin/vmware-vmx loaded at 0000000000400000
Dec 06 21:39:29.200: vcpu-0| SymBacktrace[4] 00007fc900c1c020 rip=000000000048542a in function (null) in object /usr/lib/vmware/bin/vmware-vmx loaded at 0000000000400000
Dec 06 21:39:29.200: vcpu-0| SymBacktrace[5] 00007fc900c1c120 rip=00007fc904e5f3ba in function (null) in object /lib/libpthread.so.0 loaded at 00007fc904e58000
Dec 06 21:39:29.200: vcpu-0| SymBacktrace[6] 00007fc900c1c260 rip=00007fc9047a6fcd in function clone in object /lib/libc.so.6 loaded at 00007fc9046c1000
Dec 06 21:39:29.207: vcpu-0| Msg_Post: Error
Dec 06 21:39:29.207: vcpu-0| [msg.log.error.unrecoverable] VMware Server unrecoverable error: (vcpu-0)
Dec 06 21:39:29.207: vcpu-0| VCPU 0 RunVM failed: -2.
Dec 06 21:39:29.207: vcpu-0| [msg.panic.haveLog] A log file is available in "/media/disk/virtual-machines/gutsy-current/vmware.log".  [msg.panic.requestSupport.withLog] Please request support and include the contents of the log file.  [msg.panic.requestSupport.vmSupport.windowsOrLinux] 
Dec 06 21:39:29.207: vcpu-0| To collect data to submit to VMware support, select Help > About and click "Collect Support Data". You can also run the "vm-support" script in the Workstation folder directly.
Dec 06 21:39:29.207: vcpu-0| [msg.panic.response] We will respond on the basis of your support entitlement.
Dec 06 21:39:29.207: vcpu-0| ----------------------------------------
Dec 06 21:39:29.497: Worker#16| VTHREAD watched thread 4 "vcpu-0" died
Dec 06 21:39:29.497: Worker#8| VTHREAD watched thread 4 "vcpu-0" died
Dec 06 21:39:29.503: Worker#7| VTHREAD watched thread 4 "vcpu-0" died
Dec 06 21:39:29.507: Worker#2| VTHREAD watched thread 4 "vcpu-0" died
Dec 06 21:39:29.508: Worker#0| VTHREAD watched thread 4 "vcpu-0" died
Dec 06 21:39:29.508: Worker#12| VTHREAD watched thread 4 "vcpu-0" died
Dec 06 21:39:29.514: Worker#9| VTHREAD watched thread 4 "vcpu-0" died
Dec 06 21:39:29.514: Worker#13| VTHREAD watched thread 4 "vcpu-0" died
Dec 06 21:39:29.531: vmx| VTHREAD watched thread 4 "vcpu-0" died
Dec 06 21:39:29.539: mks| VTHREAD watched thread 0 "vmx" died
Dec 06 21:39:29.565: Worker#10| VTHREAD watched thread 4 "vcpu-0" died
Dec 06 21:39:29.566: Worker#14| VTHREAD watched thread 4 "vcpu-0" died
Dec 06 21:39:29.569: Worker#15| VTHREAD watched thread 4 "vcpu-0" died
Dec 06 21:39:29.569: Worker#4| VTHREAD watched thread 4 "vcpu-0" died
Dec 06 21:39:29.580: Worker#3| VTHREAD watched thread 0 "vmx" died
Dec 06 21:39:29.584: Worker#5| VTHREAD watched thread 0 "vmx" died
Dec 06 21:39:29.594: Worker#6| VTHREAD watched thread 4 "vcpu-0" died
Dec 06 21:39:29.594: Worker#1| VTHREAD watched thread 4 "vcpu-0" died
Dec 06 21:39:29.594: Worker#11| VTHREAD watched thread 4 "vcpu-0" died
```

I moved to virtualbox for most of my virtual machines, and I'm waiting to see if that will solve some of my problems.

What kind of system specs do you have?

I am using VMware Server 2
I have a 64bit host, and the guest is 32bit.
I have a fairly large music collection mounted in the guest via NFS, and the NFS share is hosted by the virtual machine host.
I generally have at least 4 virtual guests running at most times.
I am using an ext3 filing system on the disk where the virtual machines are located.

Don't know how to solve this problem, but I have not been pleased with vmware server 2. I never had these kinds of problems with server 1.

Also, next time you experience this problem please post the output of dmesg as well.

---

