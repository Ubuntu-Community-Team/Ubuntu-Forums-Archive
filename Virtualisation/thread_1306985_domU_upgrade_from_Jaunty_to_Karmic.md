---
title: "domU upgrade from Jaunty to Karmic"
date: 2009-10-30
forum: Virtualisation
---

### Post by cocoa117 on 2009-10-30
hi, I am running a 64-bit Intrepid dom0 with Xen 3.3.0. I have one domU running Jaunty, it was using PV kernel /boot/vmlinuz-2.6.24-19-xen from dom0. After I upgraded the domU by using "do-release-upgrade", the domU no longer boot properly.

The following are the output, can anyone tell me why "mountall:/proc: unable to mount: Device or resource busy" this?

Does this mean the Karmic is not suitable for PV domU ubuntu, when running with Intrepid?

[    0.147395] Early unpacking initramfs... done
[    0.164170] Brought up 1 CPUs
[    0.164569] net_namespace: 120 bytes
[    0.164573] failed to set up cpufreq notifier
[    0.182475] Time: 165:165:165  Date: 165/165/65
[    0.182501] NET: Registered protocol family 16
[    0.194501] SMP alternatives: switching to SMP code
[    0.000006] Initializing CPU#1
[    0.000033] , L1 D cache: 32K
[    0.195122] Brought up 2 CPUs
[    0.000040] CPU: Physical Processor ID: 0
[    0.000041] CPU: Processor Core ID: 0
[    0.195603] PCI: Fatal: No config space access function found
[    0.195606] PCI: setting up Xen PCI frontend stub
[    0.196115] ACPI: Interpreter disabled.
[    0.196118] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.196143] pnp: PnP ACPI: disabled
[    0.196281] xen_mem: Initialising balloon driver.
[    0.198407] Setting mem allocation to 1048576 kiB
[    0.198612] PCI: System does not support PCI
[    0.198616] PCI: System does not support PCI
[    0.199048] pcifront pci-0: Installing PCI frontend
[    0.199125] pcifront pci-0: Creating PCI Frontend Bus 0000:00
[    0.206048] NET: Registered protocol family 8
[    0.206051] NET: Registered protocol family 20
[    0.206120] AppArmor: AppArmor Filesystem Enabled
[    0.206478] NET: Registered protocol family 2
[    0.209979] Time: xen clocksource has been installed.
[    0.241719] IP route cache hash table entries: 32768 (order: 6, 262144 bytes)
[    0.241939] TCP established hash table entries: 131072 (order: 9, 2097152 bytes)
[    0.242596] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.243017] TCP: Hash tables configured (established 131072 bind 65536)
[    0.243019] TCP reno registered
[    0.253657] checking if image is initramfs... it is
[    0.273501] Freeing initrd memory: 23096k freed
[    0.095869] audit: initializing netlink socket (disabled)
[    0.095901] audit(1256945585.612:1): initialized
[    0.096178] VFS: Disk quotas dquot_6.5.1
[    0.096205] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.096286] io scheduler noop registered
[    0.096289] io scheduler anticipatory registered
[    0.096290] io scheduler deadline registered
[    0.096319] io scheduler cfq registered (default)
[    0.096603] Xen virtual console successfully installed as xvc0
[    0.096663] Event-channel device installed.
[    0.102685] Successfully initialized TPM backend driver.
[    0.108639] netfront: Initialising virtual ethernet driver.
[    0.306503] xen-vbd: registered block device major 202
[    0.306519] blkfront: xvda1: barriers enabled
[    0.309676] blkfront: xvda2: barriers enabled
[    0.141506] rtc: IRQ 8 is not free.
[    0.141731] Linux agpgart interface v0.102
[    0.142302] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    0.142364] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    0.142482] PNP: No PS/2 controller found. Probing ports directly.
[    0.143305] i8042.c: No controller found.
[    0.157527] mice: PS/2 mouse device common for all mice
[    0.157567] cpuidle: using governor ladder
[    0.157638] NET: Registered protocol family 1
[    0.157680] registered taskstats version 1
[    0.157700] XENBUS: Device with no driver: device/console/0
[    0.157711]   Magic number: 1:252:3141
[    0.157765] /build/buildd/linux-2.6.24/debian/build/custom-source-xen/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[    0.157774] Freeing unused kernel memory: 220k freed
Loading, please wait...
Begin: Loading essential drivers... ...
[    0.341657] fuse init (API version 7.9)
[    0.400778] thermal: Unknown symbol acpi_processor_set_thermal_limit
[    0.609022] device-mapper: uevent: version 1.0.3
[    0.609068] device-mapper: ioctl: 4.12.0-ioctl (2007-10-02) initialised: [email]dm-devel@redhat.com[/email]
[    0.428837] md: linear personality registered for level -1
[    0.629166] md: multipath personality registered for level -4
[    0.437924] md: raid0 personality registered for level 0
[    0.638500] md: raid1 personality registered for level 1
[    0.447158] xor: automatically using best checksumming function: generic_sse
[    0.466890]    generic_sse:  5569.000 MB/sec
[    0.466893] xor: using function: generic_sse (5569.000 MB/sec)
[    0.467347] async_tx: api initialized (async)
[    0.534926] raid6: int64x1   2065 MB/s
[    0.602899] raid6: int64x2   2637 MB/s
[    0.670907] raid6: int64x4   2696 MB/s
[    0.738895] raid6: int64x8   2127 MB/s
[    0.806927] raid6: sse2x1    4058 MB/s
[    0.874870] raid6: sse2x2    4607 MB/s
[    0.942915] raid6: sse2x4    6830 MB/s
[    0.942917] raid6: using algorithm sse2x4 (6830 MB/s)
[    0.942920] md: raid6 personality registered for level 6
[    0.942922] md: raid5 personality registered for level 5
[    0.942924] md: raid4 personality registered for level 4
[    0.966254] md: raid10 personality registered for level 10
Done.
Begin: Running /scripts/init-premount ...
Done.
Begin: Mounting root file system... ...
Begin: Running /scripts/local-top ...
Setting up cryptographic volume md1_crypt (based on /dev/md1)
[    1.813158] usbcore: registered new interface driver usbfs
[    1.813180] usbcore: registered new interface driver hub
[    1.630013] PCI: Enabling device 0000:00:01.0 (0000 -> 0002)
[    1.816571] usbcore: registered new device driver usb
[    1.681431] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[19]  MMIO=[88000000-880007ff]  Max Packet=[2048]  IR/IT contexts=[8/8]
[    1.877066] USB Universal Host Controller Interface driver v3.0
[    1.877939] PCI: Enabling device 0000:00:00.2 (0000 -> 0002)
[    1.878045] ehci_hcd 0000:00:00.2: EHCI Host Controller
[    1.878253] ehci_hcd 0000:00:00.2: new USB bus registered, assigned bus number 1
[    1.878396] ehci_hcd 0000:00:00.2: irq 23, io mem 0x88001000
[    1.887663] ehci_hcd 0000:00:00.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    1.887765] usb usb1: configuration #1 chosen from 1 choice
[    1.887788] hub 1-0:1.0: USB hub found
[    1.887807] hub 1-0:1.0: 4 ports detected
[    1.991366] PCI: Enabling device 0000:00:00.0 (0000 -> 0001)
[    1.991462] uhci_hcd 0000:00:00.0: UHCI Host Controller
[    1.991483] uhci_hcd 0000:00:00.0: new USB bus registered, assigned bus number 2
[    1.991534] uhci_hcd 0000:00:00.0: irq 21, io base 0x00001020
[    1.991628] usb usb2: configuration #1 chosen from 1 choice
[    1.991644] hub 2-0:1.0: USB hub found
[    1.991652] hub 2-0:1.0: 2 ports detected
[    2.094150] PCI: Enabling device 0000:00:00.1 (0000 -> 0001)
[    2.094248] uhci_hcd 0000:00:00.1: UHCI Host Controller
[    2.094268] uhci_hcd 0000:00:00.1: new USB bus registered, assigned bus number 3
[    2.094323] uhci_hcd 0000:00:00.1: irq 22, io base 0x00001000
[    2.094420] usb usb3: configuration #1 chosen from 1 choice
[    2.094436] hub 3-0:1.0: USB hub found
[    2.094446] hub 3-0:1.0: 2 ports detected
[    2.227668] usb 1-1: new high speed USB device using ehci_hcd and address 2
cryptsetup: Source device /dev/md1 not found
Setting up cryptographic volume md1_crypt (based on /dev/md1)
cryptsetup: Source device /dev/md1 not found
Done.
Begin: Running /scripts/local-premount ...
Begin: Waiting for resume device... ...
[    2.358645] usb 1-1: configuration #1 chosen from 1 choice
Done.
Done.
[    7.521012] kjournald starting.  Commit interval 5 seconds
[    7.521023] EXT3-fs: mounted filesystem with ordered data mode.
Begin: Running /scripts/local-bottom ...
Done.
Done.
Begin: Running /scripts/init-bottom ...
Done.
mountall:/proc: unable to mount: Device or resource busy
mountall:/proc/self/mountinfo: No such file or directory
mountall: root filesystem isn't mounted
init: mountall main process (2399) terminated with status 1
General error mounting filesystems.
A maintenance shell will now be started.
CONTROL-D will terminate this shell and re-try.
Give root password for maintenance
(or type Control-D to continue):

---

### Post by cocoa117 on 2009-10-30
It seems it is kernel related issue base on this article. [http://www.itkovian.net/base/xen_hypervisor_with_ubuntu_karmic_koala](http://www.itkovian.net/base/xen_hypervisor_with_ubuntu_karmic_koala)

The only solution is to upgrade the dom0 to Karmic, and recompile the new dom0-xen kernel to 2.6.31-xen, then run the domU guest.

---

### Post by kleinerdrache on 2009-10-31
The same thing here, I hope this will find a solution fast, like for me, I don't have access to the dom0, just to my instance.

---

### Post by kleinerdrache on 2009-10-31
cocoa117, how did you solve the prolem then?

---

### Post by cocoa117 on 2009-11-01
kleinerdrache, it seems the solution isn't easy if you don't have access to the dom0. I believe the problem is the PV kernel which still 2.6.24-xen, in Karmic they using 2.6.31. I am sure some of the feature for /proc require 2.6.31 features, and 2.6.24-xen don't have.

At the moment, I am thinking to run Linux domU in HVM mode if possible. But I haven't made any progress yet. Let me know if you figured out how.

---

### Post by kleinerdrache on 2009-11-03
As far as I understand the HVM mode, this is a dom0 issue, and I cannot switch that in domU.  But interesting what you said about the 2 different kernels... do you think there is a way to get another kernel for my karmic?  Or to disable the feature requirement from 2.6.31 for /proc?

Thanks,
Martin

---

### Post by kleinerdrache on 2009-11-04
I found out now, that the xen dom0 comes from a debian system, its only my xen instance which is a ubuntu.  I think that worked, because the kernel were simmilar, and now they are very different. 2.6.20 from the server, but my ubuntu wants to have a 2.6.31 on karmic I think.  So the mounting of /proc should be done different, right?

uname -a says now:                                
Linux storpersgard.net 2.6.20-xen-r6 #2 SMP Wed Apr 8 19:29:54 CEST 2009 x86_64 
GNU/Linux

---

### Post by cocoa117 on 2009-11-05
kleinerdrache, I still think there isn't much you can do when you only have access to paravirt domU. The 2.6.31 kernel in Karmic clearly have features that previous kernel does not have, this is why it failed to boot when using 2.6.24-19-xen kernel in my case.

I assume your service provider rent a OS to you which is domU running on top of Debian dom0 with Xen. I don't know what version of Xen they are running, but you might want to push them to get as latest as possible. The Xen before version 3.1 have many bugs when running HVM domU.

I have different situation as I have root access to dom0, but as Ubuntu not longer support Xen as their choice of VM, I am stacking with Xen 3.3. The options I have are 
(1) learn to build from source with latest Xen source and compile it under dom0 Karmic
(2) switch to KVM. 
To be honest, I am happy with neither of them.

---

### Post by __p1n__ on 2009-11-05
> **cocoa117 said:**
> 
(1) learn to build from source with latest Xen source and compile it under dom0 Karmic

That's what I did to get xen 3.4.1 running on netbsd 5.0.1.  Bridge-utils, iproute2, python, hotplug all had to be ported too.

It took about 3 days of on-and-off focus to get 'make world' to execute clean (and some mods to tools/check.)

---

### Post by cocoa117 on 2009-11-06
> **__p1n__ said:**
> That's what I did to get xen 3.4.1 running on netbsd 5.0.1.  Bridge-utils, iproute2, python, hotplug all had to be ported too.

It took about 3 days of on-and-off focus to get 'make world' to execute clean (and some mods to tools/check.)

I have to say I found "make world" in BSD world is easist way to compile source code and make it work. If it still take you three days to get it work, I won't imaging how long it took for Ubuntu.

---

### Post by cocoa117 on 2009-11-16
I found this link for people who are still wishing to use their Xen with Ubuntu as dom0 or domU.

[http://article.gmane.org/gmane.comp.emulators.xen.user/51999](http://article.gmane.org/gmane.comp.emulators.xen.user/51999)

Does anyone have any idea how to run ur Ubuntu as HVM in xen? What to change with your configure file?

---

