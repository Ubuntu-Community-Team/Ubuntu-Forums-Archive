---
title: "Hyper-V Server and TRIM (SSD)"
date: 2017-11-10
forum: Virtualisation
---

### Post by mr-glasspoole on 2017-11-10
Hi, new to Ubuntu.
I had Debian running a long time in Hyper-V (bare metal) but switched to 16.04 LTS because i want vRSS and SR-IOV.
I never really looked at TRIM in Hyper-V.

Now i wonder how it works. Who does the trimming? The VM (Ubuntu) or the host (Hyper-V)?
Does Hyper-V trim everything outside the virtual disk and Ubuntu inside the virtual disk?

How can i see if TRIM is working? Is there something i need to do?
lsblk says it is a spinning disk
```
~# lsblk -d -o name,rota
NAME ROTA
sda     1
sr0     1
```


Also how can i see if NCQ (command queueing) is enabled/working respectively to i need it inside the VM?
In FreeBSD i can do this and see NCQ enabled:
```
~# dmesg |grep da0
da0 at storvsc0 bus 0 scbus0 target 0 lun 0
da0: <Msft Virtual Disk 1.0> Fixed Direct Access SPC-3 SCSI device
da0: 300.000MB/s transfers
da0: Command Queueing enabled
da0: 20480MB (41943040 512 byte sectors)
```

But Ubuntu just says:
```
~# dmesg |grep sda
[    2.320154] sd 0:0:0:0: [sda] 41943040 512-byte logical blocks: (21.5 GB/20.0 GiB)
[    2.321162] sd 0:0:0:0: [sda] 4096-byte physical blocks
[    2.324794] sd 0:0:0:0: [sda] Write Protect is off
[    2.326795] sd 0:0:0:0: [sda] Mode Sense: 0f 00 00 00
[    2.327124] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.332761]  sda: sda1 sda2 sda3
[    2.336875] sd 0:0:0:0: [sda] Attached SCSI disk
[    4.450469] EXT4-fs (sda2): mounted filesystem with ordered data mode. Opts: (null)
[    5.416756] EXT4-fs (sda2): re-mounted. Opts: errors=remount-ro
[    5.920198] Adding 4395004k swap on /dev/sda3.  Priority:-1 extents:1 across:4395004k FS
```

---

### Post by efflandt on 2017-11-11
I would think that TRIM needs to be done by the host system. That would be meaningless for a system accessing virtual hardware, unless maybe it was configured to have full direct access to real hardware. For example if a host system is using WiFi, to a guest system virtual networking usually appears to be Ethernet. So a guest system using a virtual disk would not normally even see the real disk.

---

### Post by mr-glasspoole on 2017-11-11
The problem is that i can't really find something on that topic.

There must be a reason that some OS in a VM support it and some not.
Ubuntu has TRIM support since 12.04: [https://docs.microsoft.com/en-us/windows-server/virtualization/hyper-v/supported-ubuntu-virtual-machines-on-hyper-v](https://docs.microsoft.com/en-us/windows-server/virtualization/hyper-v/supported-ubuntu-virtual-machines-on-hyper-v)
FreeBSD just recently: [https://docs.microsoft.com/en-us/windows-server/virtualization/hyper-v/supported-freebsd-virtual-machines-on-hyper-v](https://docs.microsoft.com/en-us/windows-server/virtualization/hyper-v/supported-freebsd-virtual-machines-on-hyper-v)

I guess it is like defragmenting. That is also something you need to do in the VM because the host can't do it in the virtual disk.

---

