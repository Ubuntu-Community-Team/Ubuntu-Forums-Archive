---
title: "Installing VirtualBox 4.3 on Ubuntu 14.04"
date: 2014-05-28
forum: Virtualisation
---

### Post by wavingerwin on 2014-05-28
Hi

I'm having trouble installing **VirtualBox 4.3.12** on my **Ubuntu 14.04**. I installed it manually by running the .deb file downloaded from the official VirtualBox website: [https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads)

The problem is, during the installation process, [FONT=courier new]sudo /etc/init.d/vboxdrv setup[/FONT] fails.

Running sudo /etc/init.d/vboxdrv setup manually via terminal returns
```
Stopping VirtualBox kernel modules ...done.
Uninstalling old VirtualBox DKMS kernel modules ...done.
Trying to register the VirtualBox kernel modules using DKMS ...done.
Starting VirtualBox kernel modules ...failed!
  (modprobe vboxdrv failed. Please use 'dmesg' to find out why)

```
[FONT=courier new]dmesg[/FONT] returns a long output, around the end the prompts which potentially reveal the cause of problems is:
```

[    3.497255] Bluetooth: BNEP socket layer initialized
[    3.535439] init: cups main process (910) killed by HUP signal
[    3.535447] init: cups main process ended, respawning
[    3.814971] e1000e 0000:00:19.0: irq 44 for MSI/MSI-X
[    3.916540] e1000e 0000:00:19.0: irq 44 for MSI/MSI-X
[    3.916763] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    3.916969] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    3.991579] init: Failed to spawn atd main process: unable to execute: No such file or directory
[    4.223696] vboxdrv: module verification failed: signature and/or  required key missing - tainting kernel
[    4.223784] vboxdrv: Unknown symbol mcount (err 0)
[    4.445045] [drm] Enabling RC6 states: RC6 on, RC6p on, RC6pp off
[    4.503004] init: plymouth-upstart-bridge respawning too fast, stopped
[    6.823304] e1000e: eth0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: Rx
[    6.823347] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   33.594336] audit_printk_skb: 189 callbacks suppressed
[   33.594338] type=1400 audit(1401255642.850:74): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=2665 comm="apparmor_parser"
[   33.594342] type=1400 audit(1401255642.850:75): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=2665 comm="apparmor_parser"
[   33.594616] type=1400 audit(1401255642.850:76): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=2665 comm="apparmor_parser"
[   86.308004] vboxdrv: Unknown symbol mcount (err 0)
[  551.076403] warning: `VirtualBox' uses 32-bit capabilities (legacy support in use)
[  565.238707] vboxdrv: Unknown symbol mcount (err 0)

```
Can somebody please help?
Many thanks in advance.

---

### Post by jdarby1983 on 2014-05-28
Hi, can you confirm you have downloaded the correct version for your chipset? 32/64-bit???

---

### Post by wavingerwin on 2014-05-28
Yes. Im with 64 bit ubuntu, and I downloaded the AMD64 version of VirtualBox.

(I actually tried installing the i386 version too, but it somehow removed Unity and Gnome Terminal, so this is a no-no I guess).

---

### Post by jdeca57 on 2014-05-29
What I did is:
1. Uninstall the Ubuntu version.
2. Add to /etc/apt/sources.list
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) trusty contrib
3 Add the key
wget -q [http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc](http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc) -O- | sudo apt-key add -
4 sudo apt-get update and upgrade
5 sudo apt-get install virtualbox-4.3
And during that installation process:
```

Setting up virtualbox-4.3 (4.3.12-93733~Ubuntu~raring) ...
addgroup: The group `vboxusers' already exists as a system group. Exiting.
Stopping VirtualBox kernel modules ...done.
Uninstalling old VirtualBox DKMS kernel modules ...done.
Trying to register the VirtualBox kernel modules using DKMS ...done.
Starting VirtualBox kernel modules ...done.
Setting up dkms (2.2.0.3-1.1ubuntu5) ...
Processing triggers for libc-bin (2.19-0ubuntu6) ...
Processing triggers for ureadahead (0.100.0-16) ...

```
Note that during this install dkms was added, so I suggest you try the apt way. On a reasonably clean installation of 14.04 it works.

---

### Post by wavingerwin on 2014-05-29
> **jdeca57 said:**
> What I did is:
1. Uninstall the Ubuntu version.

What do you mean by "Uninstall the Ubuntu version"?

I'm assuming it meant "uninstall the current VirtualBox version".

Assuming that, I followed the instructions. And on step 3, "wget -q [http://download.virtualbox.org/virtu...racle_vbox.asc](http://download.virtualbox.org/virtu...racle_vbox.asc) -O- | sudo apt-key add -" returns:
```
gpg: no valid OpenPGP data found.
```

---

### Post by jdeca57 on 2014-05-30
For your first question, there exists a version of Virtualbox in the Ubuntu repositories. It's 4.3.10, a recent version that's tested and works without problems. In that version dkms is not necessary, it works out of the box.
But you write about 4.3.12, the very latest. So you want the Oracle version. If you installed the version of the repositories, uninstall it first.
The second point is my bad: paste shortened the link.
```

wget -q http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc -O- | sudo apt-key add -

```
By the way, I didn't invent anything here: It's on the link you provided, [https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads) but a bit further on.

---

### Post by wavingerwin on 2014-05-30
During the installation process, it goes:

```
Setting up virtualbox-4.3 (4.3.12-93733~Ubuntu~raring) ...
addgroup: The group `vboxusers' already exists as a system group. Exiting.
Stopping VirtualBox kernel modules ...done.
Uninstalling old VirtualBox DKMS kernel modules ...done.
Trying to register the VirtualBox kernel modules using DKMS ...done.
Starting VirtualBox kernel modules ...failed!
  (modprobe vboxdrv failed. Please use 'dmesg' to find out why)

```

dmesg returns a long output:

```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 3.13.0-27-generic (buildd@akateko) (gcc version 4.8.2 (Ubuntu 4.8.2-19ubuntu1) ) #50-Ubuntu SMP Thu May 15 18:06:16 UTC 2014 (Ubuntu 3.13.0-27.50-generic 3.13.11)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-27-generic root=UUID=89b5e051-1f88-402b-a634-846cab1ab777 ro quiet splash vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x0000000000091bff] usable
[    0.000000] BIOS-e820: [mem 0x0000000000091c00-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x000000001fffffff] usable
[    0.000000] BIOS-e820: [mem 0x0000000020000000-0x00000000201fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000020200000-0x0000000040003fff] usable
[    0.000000] BIOS-e820: [mem 0x0000000040004000-0x0000000040004fff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000040005000-0x00000000d6709fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000d670a000-0x00000000d67fffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000d6800000-0x00000000d6f55fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000d6f56000-0x00000000d6ffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000d7000000-0x00000000d77b3fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000d77b4000-0x00000000d77fffff] ACPI data
[    0.000000] BIOS-e820: [mem 0x00000000d7800000-0x00000000d8f1afff] usable
[    0.000000] BIOS-e820: [mem 0x00000000d8f1b000-0x00000000d8ffffff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000d9000000-0x00000000da6e6fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000da6e7000-0x00000000da8e5fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000da8e6000-0x00000000da928fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000da929000-0x00000000daffffff] usable
[    0.000000] BIOS-e820: [mem 0x00000000db800000-0x00000000df9fffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000f8000000-0x00000000fbffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed00000-0x00000000fed03fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed1c000-0x00000000fed1ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ff000000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000021e5fffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.7 present.
[    0.000000] DMI: Dell Inc. OptiPlex 9010/0KV62T, BIOS A08 09/19/2012
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] No AGP bridge found
[    0.000000] e820: last_pfn = 0x21e600 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-DBFFF write-protect
[    0.000000]   DC000-E7FFF uncachable
[    0.000000]   E8000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask E00000000 write-back
[    0.000000]   1 base 200000000 mask FE0000000 write-back
[    0.000000]   2 base 0E0000000 mask FE0000000 uncachable
[    0.000000]   3 base 0DC000000 mask FFC000000 uncachable
[    0.000000]   4 base 0DB800000 mask FFF800000 uncachable
[    0.000000]   5 base 21F000000 mask FFF000000 uncachable
[    0.000000]   6 base 21E800000 mask FFF800000 uncachable
[    0.000000]   7 base 21E600000 mask FFFE00000 uncachable
[    0.000000]   8 disabled
[    0.000000]   9 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 8GB, type WB
[    0.000000] reg 1, base: 8GB, range: 512MB, type WB
[    0.000000] reg 2, base: 3584MB, range: 512MB, type UC
[    0.000000] reg 3, base: 3520MB, range: 64MB, type UC
[    0.000000] reg 4, base: 3512MB, range: 8MB, type UC
[    0.000000] reg 5, base: 8688MB, range: 16MB, type UC
[    0.000000] reg 6, base: 8680MB, range: 8MB, type UC
[    0.000000] reg 7, base: 8678MB, range: 2MB, type UC
[    0.000000] total RAM covered: 8094M
[    0.000000]  gran_size: 64K     chunk_size: 64K     num_reg: 10      lose cover RAM: 102M
[    0.000000]  gran_size: 64K     chunk_size: 128K     num_reg: 10      lose cover RAM: 102M
[    0.000000]  gran_size: 64K     chunk_size: 256K     num_reg: 10      lose cover RAM: 102M
[    0.000000]  gran_size: 64K     chunk_size: 512K     num_reg: 10      lose cover RAM: 102M
[    0.000000]  gran_size: 64K     chunk_size: 1M     num_reg: 10      lose cover RAM: 102M
[    0.000000]  gran_size: 64K     chunk_size: 2M     num_reg: 10      lose cover RAM: 102M
[    0.000000]  gran_size: 64K     chunk_size: 4M     num_reg: 10      lose cover RAM: 102M
[    0.000000]  gran_size: 64K     chunk_size: 8M     num_reg: 10      lose cover RAM: 102M
[    0.000000]  gran_size: 64K     chunk_size: 16M     num_reg: 10      lose cover RAM: 38M
[    0.000000] *BAD*gran_size: 64K     chunk_size: 32M     num_reg: 10      lose cover RAM: -16M
[    0.000000] *BAD*gran_size: 64K     chunk_size: 64M     num_reg: 10      lose cover RAM: -16M
[    0.000000]  gran_size: 64K     chunk_size: 128M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 64K     chunk_size: 256M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 64K     chunk_size: 512M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 64K     chunk_size: 1G     num_reg: 10      lose cover RAM: 0G
[    0.000000] *BAD*gran_size: 64K     chunk_size: 2G     num_reg: 10      lose cover RAM: -1G
[    0.000000]  gran_size: 128K     chunk_size: 128K     num_reg: 10      lose cover RAM: 102M
[    0.000000]  gran_size: 128K     chunk_size: 256K     num_reg: 10      lose cover RAM: 102M
[    0.000000]  gran_size: 128K     chunk_size: 512K     num_reg: 10      lose cover RAM: 102M
[    0.000000]  gran_size: 128K     chunk_size: 1M     num_reg: 10      lose cover RAM: 102M
[    0.000000]  gran_size: 128K     chunk_size: 2M     num_reg: 10      lose cover RAM: 102M
[    0.000000]  gran_size: 128K     chunk_size: 4M     num_reg: 10      lose cover RAM: 102M
[    0.000000]  gran_size: 128K     chunk_size: 8M     num_reg: 10      lose cover RAM: 102M
[    0.000000]  gran_size: 128K     chunk_size: 16M     num_reg: 10      lose cover RAM: 38M
[    0.000000] *BAD*gran_size: 128K     chunk_size: 32M     num_reg: 10      lose cover RAM: -16M
[    0.000000] *BAD*gran_size: 128K     chunk_size: 64M     num_reg: 10      lose cover RAM: -16M
[    0.000000]  gran_size: 128K     chunk_size: 128M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 128K     chunk_size: 256M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 128K     chunk_size: 512M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 128K     chunk_size: 1G     num_reg: 10      lose cover RAM: 0G
[    0.000000] *BAD*gran_size: 128K     chunk_size: 2G     num_reg: 10      lose cover RAM: -1G
[    0.000000]  gran_size: 256K     chunk_size: 256K     num_reg: 10      lose cover RAM: 102M
[    0.000000]  gran_size: 256K     chunk_size: 512K     num_reg: 10      lose cover RAM: 102M
[    0.000000]  gran_size: 256K     chunk_size: 1M     num_reg: 10      lose cover RAM: 102M
[    0.000000]  gran_size: 256K     chunk_size: 2M     num_reg: 10      lose cover RAM: 102M
[    0.000000]  gran_size: 256K     chunk_size: 4M     num_reg: 10      lose cover RAM: 102M
[    0.000000]  gran_size: 256K     chunk_size: 8M     num_reg: 10      lose cover RAM: 102M
[    0.000000]  gran_size: 256K     chunk_size: 16M     num_reg: 10      lose cover RAM: 38M
[    0.000000] *BAD*gran_size: 256K     chunk_size: 32M     num_reg: 10      lose cover RAM: -16M
[    0.000000] *BAD*gran_size: 256K     chunk_size: 64M     num_reg: 10      lose cover RAM: -16M
[    0.000000]  gran_size: 256K     chunk_size: 128M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 256K     chunk_size: 256M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 256K     chunk_size: 512M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 256K     chunk_size: 1G     num_reg: 10      lose cover RAM: 0G
[    0.000000] *BAD*gran_size: 256K     chunk_size: 2G     num_reg: 10      lose cover RAM: -1G
[    0.000000]  gran_size: 512K     chunk_size: 512K     num_reg: 10      lose cover RAM: 102M
[    0.000000]  gran_size: 512K     chunk_size: 1M     num_reg: 10      lose cover RAM: 102M
[    0.000000]  gran_size: 512K     chunk_size: 2M     num_reg: 10      lose cover RAM: 102M
[    0.000000]  gran_size: 512K     chunk_size: 4M     num_reg: 10      lose cover RAM: 102M
[    0.000000]  gran_size: 512K     chunk_size: 8M     num_reg: 10      lose cover RAM: 102M
[    0.000000]  gran_size: 512K     chunk_size: 16M     num_reg: 10      lose cover RAM: 38M
[    0.000000] *BAD*gran_size: 512K     chunk_size: 32M     num_reg: 10      lose cover RAM: -16M
[    0.000000] *BAD*gran_size: 512K     chunk_size: 64M     num_reg: 10      lose cover RAM: -16M
[    0.000000]  gran_size: 512K     chunk_size: 128M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 512K     chunk_size: 256M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 512K     chunk_size: 512M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 512K     chunk_size: 1G     num_reg: 10      lose cover RAM: 0G
[    0.000000] *BAD*gran_size: 512K     chunk_size: 2G     num_reg: 10      lose cover RAM: -1G
[    0.000000]  gran_size: 1M     chunk_size: 1M     num_reg: 10      lose cover RAM: 102M
[    0.000000]  gran_size: 1M     chunk_size: 2M     num_reg: 10      lose cover RAM: 102M
[    0.000000]  gran_size: 1M     chunk_size: 4M     num_reg: 10      lose cover RAM: 102M
[    0.000000]  gran_size: 1M     chunk_size: 8M     num_reg: 10      lose cover RAM: 102M
[    0.000000]  gran_size: 1M     chunk_size: 16M     num_reg: 10      lose cover RAM: 38M
[    0.000000] *BAD*gran_size: 1M     chunk_size: 32M     num_reg: 10      lose cover RAM: -16M
[    0.000000] *BAD*gran_size: 1M     chunk_size: 64M     num_reg: 10      lose cover RAM: -16M
[    0.000000]  gran_size: 1M     chunk_size: 128M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 1M     chunk_size: 256M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 1M     chunk_size: 512M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 1M     chunk_size: 1G     num_reg: 10      lose cover RAM: 0G
[    0.000000] *BAD*gran_size: 1M     chunk_size: 2G     num_reg: 10      lose cover RAM: -1G
[    0.000000]  gran_size: 2M     chunk_size: 2M     num_reg: 10      lose cover RAM: 102M
[    0.000000]  gran_size: 2M     chunk_size: 4M     num_reg: 10      lose cover RAM: 102M
[    0.000000]  gran_size: 2M     chunk_size: 8M     num_reg: 10      lose cover RAM: 102M
[    0.000000]  gran_size: 2M     chunk_size: 16M     num_reg: 10      lose cover RAM: 38M
[    0.000000] *BAD*gran_size: 2M     chunk_size: 32M     num_reg: 10      lose cover RAM: -16M
[    0.000000] *BAD*gran_size: 2M     chunk_size: 64M     num_reg: 10      lose cover RAM: -16M
[    0.000000]  gran_size: 2M     chunk_size: 128M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 2M     chunk_size: 256M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 2M     chunk_size: 512M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 2M     chunk_size: 1G     num_reg: 10      lose cover RAM: 0G
[    0.000000] *BAD*gran_size: 2M     chunk_size: 2G     num_reg: 10      lose cover RAM: -1G
[    0.000000]  gran_size: 4M     chunk_size: 4M     num_reg: 10      lose cover RAM: 102M
[    0.000000]  gran_size: 4M     chunk_size: 8M     num_reg: 10      lose cover RAM: 102M
[    0.000000]  gran_size: 4M     chunk_size: 16M     num_reg: 10      lose cover RAM: 38M
[    0.000000] *BAD*gran_size: 4M     chunk_size: 32M     num_reg: 10      lose cover RAM: -14M
[    0.000000] *BAD*gran_size: 4M     chunk_size: 64M     num_reg: 10      lose cover RAM: -14M
[    0.000000]  gran_size: 4M     chunk_size: 128M     num_reg: 10      lose cover RAM: 2M
[    0.000000]  gran_size: 4M     chunk_size: 256M     num_reg: 10      lose cover RAM: 2M
[    0.000000]  gran_size: 4M     chunk_size: 512M     num_reg: 10      lose cover RAM: 2M
[    0.000000]  gran_size: 4M     chunk_size: 1G     num_reg: 10      lose cover RAM: 2M
[    0.000000] *BAD*gran_size: 4M     chunk_size: 2G     num_reg: 10      lose cover RAM: -1022M
[    0.000000]  gran_size: 8M     chunk_size: 8M     num_reg: 10      lose cover RAM: 102M
[    0.000000]  gran_size: 8M     chunk_size: 16M     num_reg: 10      lose cover RAM: 38M
[    0.000000]  gran_size: 8M     chunk_size: 32M     num_reg: 10      lose cover RAM: 38M
[    0.000000]  gran_size: 8M     chunk_size: 64M     num_reg: 9      lose cover RAM: 6M
[    0.000000]  gran_size: 8M     chunk_size: 128M     num_reg: 8      lose cover RAM: 6M
[    0.000000]  gran_size: 8M     chunk_size: 256M     num_reg: 8      lose cover RAM: 6M
[    0.000000]  gran_size: 8M     chunk_size: 512M     num_reg: 8      lose cover RAM: 6M
[    0.000000]  gran_size: 8M     chunk_size: 1G     num_reg: 8      lose cover RAM: 6M
[    0.000000]  gran_size: 8M     chunk_size: 2G     num_reg: 9      lose cover RAM: 6M
[    0.000000]  gran_size: 16M     chunk_size: 16M     num_reg: 10      lose cover RAM: 46M
[    0.000000]  gran_size: 16M     chunk_size: 32M     num_reg: 10      lose cover RAM: 46M
[    0.000000]  gran_size: 16M     chunk_size: 64M     num_reg: 9      lose cover RAM: 14M
[    0.000000]  gran_size: 16M     chunk_size: 128M     num_reg: 8      lose cover RAM: 14M
[    0.000000]  gran_size: 16M     chunk_size: 256M     num_reg: 8      lose cover RAM: 14M
[    0.000000]  gran_size: 16M     chunk_size: 512M     num_reg: 8      lose cover RAM: 14M
[    0.000000]  gran_size: 16M     chunk_size: 1G     num_reg: 8      lose cover RAM: 14M
[    0.000000]  gran_size: 16M     chunk_size: 2G     num_reg: 9      lose cover RAM: 14M
[    0.000000]  gran_size: 32M     chunk_size: 32M     num_reg: 10      lose cover RAM: 30M
[    0.000000]  gran_size: 32M     chunk_size: 64M     num_reg: 9      lose cover RAM: 30M
[    0.000000]  gran_size: 32M     chunk_size: 128M     num_reg: 8      lose cover RAM: 30M
[    0.000000]  gran_size: 32M     chunk_size: 256M     num_reg: 8      lose cover RAM: 30M
[    0.000000]  gran_size: 32M     chunk_size: 512M     num_reg: 8      lose cover RAM: 30M
[    0.000000]  gran_size: 32M     chunk_size: 1G     num_reg: 8      lose cover RAM: 30M
[    0.000000]  gran_size: 32M     chunk_size: 2G     num_reg: 9      lose cover RAM: 30M
[    0.000000]  gran_size: 64M     chunk_size: 64M     num_reg: 8      lose cover RAM: 94M
[    0.000000]  gran_size: 64M     chunk_size: 128M     num_reg: 7      lose cover RAM: 94M
[    0.000000]  gran_size: 64M     chunk_size: 256M     num_reg: 7      lose cover RAM: 94M
[    0.000000]  gran_size: 64M     chunk_size: 512M     num_reg: 7      lose cover RAM: 94M
[    0.000000]  gran_size: 64M     chunk_size: 1G     num_reg: 7      lose cover RAM: 94M
[    0.000000]  gran_size: 64M     chunk_size: 2G     num_reg: 8      lose cover RAM: 94M
[    0.000000]  gran_size: 128M     chunk_size: 128M     num_reg: 7      lose cover RAM: 158M
[    0.000000]  gran_size: 128M     chunk_size: 256M     num_reg: 7      lose cover RAM: 158M
[    0.000000]  gran_size: 128M     chunk_size: 512M     num_reg: 7      lose cover RAM: 158M
[    0.000000]  gran_size: 128M     chunk_size: 1G     num_reg: 7      lose cover RAM: 158M
[    0.000000]  gran_size: 128M     chunk_size: 2G     num_reg: 8      lose cover RAM: 158M
[    0.000000]  gran_size: 256M     chunk_size: 256M     num_reg: 5      lose cover RAM: 414M
[    0.000000]  gran_size: 256M     chunk_size: 512M     num_reg: 7      lose cover RAM: 414M
[    0.000000]  gran_size: 256M     chunk_size: 1G     num_reg: 7      lose cover RAM: 414M
[    0.000000]  gran_size: 256M     chunk_size: 2G     num_reg: 8      lose cover RAM: 414M
[    0.000000]  gran_size: 512M     chunk_size: 512M     num_reg: 3      lose cover RAM: 926M
[    0.000000]  gran_size: 512M     chunk_size: 1G     num_reg: 3      lose cover RAM: 926M
[    0.000000]  gran_size: 512M     chunk_size: 2G     num_reg: 3      lose cover RAM: 926M
[    0.000000]  gran_size: 1G     chunk_size: 1G     num_reg: 3      lose cover RAM: 926M
[    0.000000]  gran_size: 1G     chunk_size: 2G     num_reg: 3      lose cover RAM: 926M
[    0.000000]  gran_size: 2G     chunk_size: 2G     num_reg: 2      lose cover RAM: 1950M
[    0.000000] mtrr_cleanup: can not find optimal value
[    0.000000] please specify mtrr_gran_size/mtrr_chunk_size
[    0.000000] e820: update [mem 0xdb800000-0xffffffff] usable ==> reserved
[    0.000000] e820: last_pfn = 0xdb000 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [mem 0x000fd9d0-0x000fd9df] mapped at [ffff8800000fd9d0]
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] Base memory trampoline at [ffff88000008b000] 8b000 size 24576
[    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
[    0.000000]  [mem 0x00000000-0x000fffff] page 4k
[    0.000000] BRK [0x01fde000, 0x01fdefff] PGTABLE
[    0.000000] BRK [0x01fdf000, 0x01fdffff] PGTABLE
[    0.000000] BRK [0x01fe0000, 0x01fe0fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x21e400000-0x21e5fffff]
[    0.000000]  [mem 0x21e400000-0x21e5fffff] page 2M
[    0.000000] BRK [0x01fe1000, 0x01fe1fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x21c000000-0x21e3fffff]
[    0.000000]  [mem 0x21c000000-0x21e3fffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x200000000-0x21bffffff]
[    0.000000]  [mem 0x200000000-0x21bffffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x00100000-0x1fffffff]
[    0.000000]  [mem 0x00100000-0x001fffff] page 4k
[    0.000000]  [mem 0x00200000-0x1fffffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x20200000-0x40003fff]
[    0.000000]  [mem 0x20200000-0x3fffffff] page 2M
[    0.000000]  [mem 0x40000000-0x40003fff] page 4k
[    0.000000] BRK [0x01fe2000, 0x01fe2fff] PGTABLE
[    0.000000] BRK [0x01fe3000, 0x01fe3fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x40005000-0xd6709fff]
[    0.000000]  [mem 0x40005000-0x401fffff] page 4k
[    0.000000]  [mem 0x40200000-0xd65fffff] page 2M
[    0.000000]  [mem 0xd6600000-0xd6709fff] page 4k
[    0.000000] init_memory_mapping: [mem 0xd6800000-0xd6f55fff]
[    0.000000]  [mem 0xd6800000-0xd6dfffff] page 2M
[    0.000000]  [mem 0xd6e00000-0xd6f55fff] page 4k
[    0.000000] init_memory_mapping: [mem 0xd7000000-0xd77b3fff]
[    0.000000]  [mem 0xd7000000-0xd75fffff] page 2M
[    0.000000]  [mem 0xd7600000-0xd77b3fff] page 4k
[    0.000000] init_memory_mapping: [mem 0xd7800000-0xd8f1afff]
[    0.000000]  [mem 0xd7800000-0xd8dfffff] page 2M
[    0.000000]  [mem 0xd8e00000-0xd8f1afff] page 4k
[    0.000000] init_memory_mapping: [mem 0xd9000000-0xda6e6fff]
[    0.000000]  [mem 0xd9000000-0xda5fffff] page 2M
[    0.000000]  [mem 0xda600000-0xda6e6fff] page 4k
[    0.000000] init_memory_mapping: [mem 0xda929000-0xdaffffff]
[    0.000000]  [mem 0xda929000-0xda9fffff] page 4k
[    0.000000]  [mem 0xdaa00000-0xdaffffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x100000000-0x1ffffffff]
[    0.000000]  [mem 0x100000000-0x1ffffffff] page 2M
[    0.000000] RAMDISK: [mem 0x35b82000-0x36db8fff]
[    0.000000] ACPI: RSDP 00000000000f0490 000024 (v02 DELL  )
[    0.000000] ACPI: XSDT 00000000d77f4080 00007C (v01 DELL    CBX3    01072009 AMI  00010013)
[    0.000000] ACPI: FACP 00000000d77fd790 00010C (v05 DELL    CBX3    01072009 AMI  00010013)
[    0.000000] ACPI: DSDT 00000000d77f4188 009607 (v02 DELL    CBX3    00000022 INTL 20091112)
[    0.000000] ACPI: FACS 00000000d8ffe080 000040
[    0.000000] ACPI: APIC 00000000d77fd8a0 000092 (v03 DELL    CBX3    01072009 AMI  00010013)
[    0.000000] ACPI: FPDT 00000000d77fd938 000044 (v01 DELL    CBX3    01072009 AMI  00010013)
[    0.000000] ACPI: MCFG 00000000d77fd980 00003C (v01 DELL    CBX3    01072009 MSFT 00000097)
[    0.000000] ACPI: HPET 00000000d77fd9c0 000038 (v01 DELL    CBX3    01072009 AMI. 00000005)
[    0.000000] ACPI: SSDT 00000000d77fd9f8 000415 (v01 SataRe SataTabl 00001000 INTL 20091112)
[    0.000000] ACPI: SSDT 00000000d77fde10 0009B9 (v01  PmRef  Cpu0Ist 00003000 INTL 20051117)
[    0.000000] ACPI: SSDT 00000000d77fe7d0 000A92 (v01  PmRef    CpuPm 00003000 INTL 20051117)
[    0.000000] ACPI: DMAR 00000000d77ff268 0000B8 (v01 INTEL      SNB  00000001 INTL 00000001)
[    0.000000] ACPI: ASF! 00000000d77ff320 0000A5 (v32 INTEL       HCG 00000001 TFSM 000F4240)
[    0.000000] ACPI: SLIC 00000000d77ff3c8 000176 (v03 DELL    CBX3    01072009 MSFT 00010013)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x000000021e5fffff]
[    0.000000] Initmem setup node 0 [mem 0x00000000-0x21e5fffff]
[    0.000000]   NODE_DATA [mem 0x21e5ef000-0x21e5f3fff]
[    0.000000]  [ffffea0000000000-ffffea00087fffff] PMD -> [ffff880215c00000-ffff88021dbfffff] on node 0
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00001000-0x00ffffff]
[    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
[    0.000000]   Normal   [mem 0x100000000-0x21e5fffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00001000-0x00090fff]
[    0.000000]   node   0: [mem 0x00100000-0x1fffffff]
[    0.000000]   node   0: [mem 0x20200000-0x40003fff]
[    0.000000]   node   0: [mem 0x40005000-0xd6709fff]
[    0.000000]   node   0: [mem 0xd6800000-0xd6f55fff]
[    0.000000]   node   0: [mem 0xd7000000-0xd77b3fff]
[    0.000000]   node   0: [mem 0xd7800000-0xd8f1afff]
[    0.000000]   node   0: [mem 0xd9000000-0xda6e6fff]
[    0.000000]   node   0: [mem 0xda929000-0xdaffffff]
[    0.000000]   node   0: [mem 0x100000000-0x21e5fffff]
[    0.000000] On node 0 totalpages: 2068092
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 21 pages reserved
[    0.000000]   DMA zone: 3984 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 13924 pages used for memmap
[    0.000000]   DMA32 zone: 891116 pages, LIFO batch:31
[    0.000000]   Normal zone: 18328 pages used for memmap
[    0.000000]   Normal zone: 1172992 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x04] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x06] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x03] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x05] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x07] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0xff] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a701 base: 0xfed00000
[    0.000000] smpboot: Allowing 8 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: [mem 0x00091000-0x00091fff]
[    0.000000] PM: Registered nosave memory: [mem 0x00092000-0x0009ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000e0000-0x000fffff]
[    0.000000] PM: Registered nosave memory: [mem 0x20000000-0x201fffff]
[    0.000000] PM: Registered nosave memory: [mem 0x40004000-0x40004fff]
[    0.000000] PM: Registered nosave memory: [mem 0xd670a000-0xd67fffff]
[    0.000000] PM: Registered nosave memory: [mem 0xd6f56000-0xd6ffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xd77b4000-0xd77fffff]
[    0.000000] PM: Registered nosave memory: [mem 0xd8f1b000-0xd8ffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xda6e7000-0xda8e5fff]
[    0.000000] PM: Registered nosave memory: [mem 0xda8e6000-0xda928fff]
[    0.000000] PM: Registered nosave memory: [mem 0xdb000000-0xdb7fffff]
[    0.000000] PM: Registered nosave memory: [mem 0xdb800000-0xdf9fffff]
[    0.000000] PM: Registered nosave memory: [mem 0xdfa00000-0xf7ffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xf8000000-0xfbffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfc000000-0xfebfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xfec00fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec01000-0xfecfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed00000-0xfed03fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed04000-0xfed1bfff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed1c000-0xfed1ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed20000-0xfedfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfee00000-0xfee00fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfee01000-0xfeffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xff000000-0xffffffff]
[    0.000000] e820: [mem 0xdfa00000-0xf7ffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:8 nr_node_ids:1
[    0.000000] PERCPU: Embedded 29 pages/cpu @ffff88021e200000 s86336 r8192 d24256 u262144
[    0.000000] pcpu-alloc: s86336 r8192 d24256 u262144 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 2035755
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-27-generic root=UUID=89b5e051-1f88-402b-a634-846cab1ab777 ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] xsave: enabled xstate_bv 0x7, cntxt size 0x340
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 8038988K/8272368K available (7354K kernel code, 1142K rwdata, 3396K rodata, 1332K init, 1440K bss, 233380K reserved)
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=8.
[    0.000000]     Offload RCU callbacks from all CPUs
[    0.000000]     Offload RCU callbacks from CPUs: 0-7.
[    0.000000] NR_IRQS:16640 nr_irqs:744 16
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 33554432 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.004000] tsc: Detected 3392.048 MHz processor
[    0.000002] Calibrating delay loop (skipped), value calculated using timer frequency.. 6784.09 BogoMIPS (lpj=13568192)
[    0.000004] pid_max: default: 32768 minimum: 301
[    0.000019] Security Framework initialized
[    0.000033] AppArmor: AppArmor initialized
[    0.000034] Yama: becoming mindful.
[    0.000440] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.001890] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.002525] Mount-cache hash table entries: 16384 (order: 5, 131072 bytes)
[    0.002532] Mountpoint-cache hash table entries: 16384 (order: 5, 131072 bytes)
[    0.002674] Initializing cgroup subsys memory
[    0.002678] Initializing cgroup subsys devices
[    0.002679] Initializing cgroup subsys freezer
[    0.002680] Initializing cgroup subsys blkio
[    0.002681] Initializing cgroup subsys perf_event
[    0.002683] Initializing cgroup subsys hugetlb
[    0.002698] CPU: Physical Processor ID: 0
[    0.002699] CPU: Processor Core ID: 0
[    0.002702] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
[    0.002702] ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
[    0.002964] mce: CPU supports 9 MCE banks
[    0.002973] CPU0: Thermal monitoring enabled (TM1)
[    0.002980] Last level iTLB entries: 4KB 512, 2MB 0, 4MB 0
[    0.002980] Last level dTLB entries: 4KB 512, 2MB 32, 4MB 32
[    0.002980] tlb_flushall_shift: 2
[    0.003070] Freeing SMP alternatives memory: 32K (ffffffff81e6c000 - ffffffff81e74000)
[    0.003922] ACPI: Core revision 20131115
[    0.007297] ACPI: All ACPI Tables successfully acquired
[    0.007446] ftrace: allocating 28458 entries in 112 pages
[    0.017300] dmar: Host address width 36
[    0.017302] dmar: DRHD base: 0x000000fed90000 flags: 0x0
[    0.017307] dmar: IOMMU 0: reg_base_addr fed90000 ver 1:0 cap c0000020e60262 ecap f0101a
[    0.017308] dmar: DRHD base: 0x000000fed91000 flags: 0x1
[    0.017311] dmar: IOMMU 1: reg_base_addr fed91000 ver 1:0 cap c9008020660262 ecap f0105a
[    0.017312] dmar: RMRR base: 0x000000da85e000 end: 0x000000da884fff
[    0.017313] dmar: RMRR base: 0x000000db800000 end: 0x000000df9fffff
[    0.017385] IOAPIC id 2 under DRHD base  0xfed91000 IOMMU 1
[    0.017386] HPET id 0 under DRHD base 0xfed91000
[    0.017490] Enabled IRQ remapping in x2apic mode
[    0.017491] Enabling x2apic
[    0.017492] Enabled x2apic
[    0.017499] Switched APIC routing to cluster x2apic.
[    0.017932] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.057630] smpboot: CPU0: Intel(R) Core(TM) i7-3770 CPU @ 3.40GHz (fam: 06, model: 3a, stepping: 09)
[    0.057639] TSC deadline timer enabled
[    0.059208] Performance Events: PEBS fmt1+, 16-deep LBR, IvyBridge events, full-width counters, Intel PMU driver.
[    0.059213] ... version:                3
[    0.059214] ... bit width:              48
[    0.059214] ... generic registers:      4
[    0.059215] ... value mask:             0000ffffffffffff
[    0.059216] ... max period:             0000ffffffffffff
[    0.059217] ... fixed-purpose events:   3
[    0.059217] ... event mask:             000000070000000f
[    0.060374] x86: Booting SMP configuration:
[    0.073685] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.060375] .... node  #0, CPUs:      #1 #2 #3 #4 #5 #6 #7
[    0.154109] x86: Booted up 1 node, 8 CPUs
[    0.154111] smpboot: Total of 8 processors activated (54272.76 BogoMIPS)
[    0.160383] devtmpfs: initialized
[    0.162271] EVM: security.selinux
[    0.162272] EVM: security.SMACK64
[    0.162272] EVM: security.ima
[    0.162273] EVM: security.capability
[    0.162306] PM: Registering ACPI NVS region [mem 0xd8f1b000-0xd8ffffff] (937984 bytes)
[    0.162315] PM: Registering ACPI NVS region [mem 0xda8e6000-0xda928fff] (274432 bytes)
[    0.162851] pinctrl core: initialized pinctrl subsystem
[    0.162893] regulator-dummy: no parameters
[    0.162923] RTC time:  6:53:26, date: 05/28/14
[    0.162945] NET: Registered protocol family 16
[    0.163013] cpuidle: using governor ladder
[    0.163014] cpuidle: using governor menu
[    0.163038] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.163039] ACPI: bus type PCI registered
[    0.163040] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.163080] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf8000000-0xfbffffff] (base 0xf8000000)
[    0.163082] PCI: MMCONFIG at [mem 0xf8000000-0xfbffffff] reserved in E820
[    0.169026] PCI: Using configuration type 1 for base access
[    0.169031] dmi type 0xB1 record - unknown flag
[    0.169658] bio: create slab <bio-0> at 0
[    0.169766] ACPI: Added _OSI(Module Device)
[    0.169767] ACPI: Added _OSI(Processor Device)
[    0.169768] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.169769] ACPI: Added _OSI(Processor Aggregator Device)
[    0.171992] ACPI: Executed 1 blocks of module-level executable AML code
[    0.176531] ACPI: SSDT 00000000da88d018 00083B (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.176806] ACPI: Dynamic OEM Table Load:
[    0.176807] ACPI: SSDT           (null) 00083B (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.180387] ACPI: SSDT 00000000da88ea98 000303 (v01  PmRef    ApIst 00003000 INTL 20051117)
[    0.180676] ACPI: Dynamic OEM Table Load:
[    0.180678] ACPI: SSDT           (null) 000303 (v01  PmRef    ApIst 00003000 INTL 20051117)
[    0.184308] ACPI: SSDT 00000000da894c18 000119 (v01  PmRef    ApCst 00003000 INTL 20051117)
[    0.184577] ACPI: Dynamic OEM Table Load:
[    0.184578] ACPI: SSDT           (null) 000119 (v01  PmRef    ApCst 00003000 INTL 20051117)
[    0.189002] ACPI: Interpreter enabled
[    0.189006] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20131115/hwxface-580)
[    0.189009] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20131115/hwxface-580)
[    0.189018] ACPI: (supports S0 S3 S4 S5)
[    0.189019] ACPI: Using IOAPIC for interrupt routing
[    0.189038] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.189141] ACPI: No dock devices found.
[    0.214104] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-3e])
[    0.214108] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    0.214200] \_SB_.PCI0:_OSC invalid UUID
[    0.214201] _OSC request data:1 1f 0 
[    0.214204] acpi PNP0A08:00: _OSC failed (AE_ERROR); disabling ASPM
[    0.214677] PCI host bridge to bus 0000:00
[    0.214679] pci_bus 0000:00: root bus resource [bus 00-3e]
[    0.214680] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
[    0.214681] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
[    0.214683] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    0.214684] pci_bus 0000:00: root bus resource [mem 0x000dc000-0x000dffff]
[    0.214685] pci_bus 0000:00: root bus resource [mem 0x000e0000-0x000e3fff]
[    0.214686] pci_bus 0000:00: root bus resource [mem 0x000e4000-0x000e7fff]
[    0.214687] pci_bus 0000:00: root bus resource [mem 0xdfa00000-0xfeafffff]
[    0.214692] pci 0000:00:00.0: [8086:0150] type 00 class 0x060000
[    0.214764] pci 0000:00:02.0: [8086:0162] type 00 class 0x030000
[    0.214772] pci 0000:00:02.0: reg 0x10: [mem 0xf7800000-0xf7bfffff 64bit]
[    0.214776] pci 0000:00:02.0: reg 0x18: [mem 0xe0000000-0xefffffff 64bit pref]
[    0.214780] pci 0000:00:02.0: reg 0x20: [io  0xf000-0xf03f]
[    0.214863] pci 0000:00:14.0: [8086:1e31] type 00 class 0x0c0330
[    0.214883] pci 0000:00:14.0: reg 0x10: [mem 0xf7c20000-0xf7c2ffff 64bit]
[    0.214950] pci 0000:00:14.0: PME# supported from D3hot D3cold
[    0.214988] pci 0000:00:14.0: System wakeup disabled by ACPI
[    0.215015] pci 0000:00:16.0: [8086:1e3a] type 00 class 0x078000
[    0.215037] pci 0000:00:16.0: reg 0x10: [mem 0xf7c3c000-0xf7c3c00f 64bit]
[    0.215109] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    0.215171] pci 0000:00:16.3: [8086:1e3d] type 00 class 0x070002
[    0.215188] pci 0000:00:16.3: reg 0x10: [io  0xf0e0-0xf0e7]
[    0.215197] pci 0000:00:16.3: reg 0x14: [mem 0xf7c3a000-0xf7c3afff]
[    0.215327] pci 0000:00:19.0: [8086:1502] type 00 class 0x020000
[    0.215344] pci 0000:00:19.0: reg 0x10: [mem 0xf7c00000-0xf7c1ffff]
[    0.215352] pci 0000:00:19.0: reg 0x14: [mem 0xf7c39000-0xf7c39fff]
[    0.215361] pci 0000:00:19.0: reg 0x18: [io  0xf080-0xf09f]
[    0.215420] pci 0000:00:19.0: PME# supported from D0 D3hot D3cold
[    0.215458] pci 0000:00:19.0: System wakeup disabled by ACPI
[    0.215486] pci 0000:00:1a.0: [8086:1e2d] type 00 class 0x0c0320
[    0.215505] pci 0000:00:1a.0: reg 0x10: [mem 0xf7c38000-0xf7c383ff]
[    0.215590] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    0.215629] pci 0000:00:1a.0: System wakeup disabled by ACPI
[    0.215653] pci 0000:00:1b.0: [8086:1e20] type 00 class 0x040300
[    0.215667] pci 0000:00:1b.0: reg 0x10: [mem 0xf7c30000-0xf7c33fff 64bit]
[    0.215730] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.215770] pci 0000:00:1b.0: System wakeup disabled by ACPI
[    0.215797] pci 0000:00:1d.0: [8086:1e26] type 00 class 0x0c0320
[    0.215816] pci 0000:00:1d.0: reg 0x10: [mem 0xf7c37000-0xf7c373ff]
[    0.215901] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    0.215942] pci 0000:00:1d.0: System wakeup disabled by ACPI
[    0.215964] pci 0000:00:1e.0: [8086:244e] type 01 class 0x060401
[    0.216039] pci 0000:00:1e.0: System wakeup disabled by ACPI
[    0.216063] pci 0000:00:1f.0: [8086:1e47] type 00 class 0x060100
[    0.216216] pci 0000:00:1f.2: [8086:2822] type 00 class 0x010400
[    0.216232] pci 0000:00:1f.2: reg 0x10: [io  0xf0d0-0xf0d7]
[    0.216239] pci 0000:00:1f.2: reg 0x14: [io  0xf0c0-0xf0c3]
[    0.216250] pci 0000:00:1f.2: reg 0x18: [io  0xf0b0-0xf0b7]
[    0.216257] pci 0000:00:1f.2: reg 0x1c: [io  0xf0a0-0xf0a3]
[    0.216265] pci 0000:00:1f.2: reg 0x20: [io  0xf060-0xf07f]
[    0.216272] pci 0000:00:1f.2: reg 0x24: [mem 0xf7c36000-0xf7c367ff]
[    0.216314] pci 0000:00:1f.2: PME# supported from D3hot
[    0.216369] pci 0000:00:1f.3: [8086:1e22] type 00 class 0x0c0500
[    0.216383] pci 0000:00:1f.3: reg 0x10: [mem 0xf7c35000-0xf7c350ff 64bit]
[    0.216402] pci 0000:00:1f.3: reg 0x20: [io  0xf040-0xf05f]
[    0.216524] pci 0000:00:1e.0: PCI bridge to [bus 01] (subtractive decode)
[    0.216533] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.216534] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.216536] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.216537] pci 0000:00:1e.0:   bridge window [mem 0x000dc000-0x000dffff] (subtractive decode)
[    0.216538] pci 0000:00:1e.0:   bridge window [mem 0x000e0000-0x000e3fff] (subtractive decode)
[    0.216539] pci 0000:00:1e.0:   bridge window [mem 0x000e4000-0x000e7fff] (subtractive decode)
[    0.216540] pci 0000:00:1e.0:   bridge window [mem 0xdfa00000-0xfeafffff] (subtractive decode)
[    0.216920] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 10 *11 12 14 15)
[    0.216959] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.216997] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 *10 11 12 14 15)
[    0.217041] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 *10 11 12 14 15)
[    0.217081] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 *5 6 10 11 12 14 15)
[    0.217122] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.217164] ACPI: PCI Interrupt Link [LNKG] (IRQs *3 4 5 6 10 11 12 14 15)
[    0.217204] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 10 *11 12 14 15)
[    0.217374] ACPI: Enabled 4 GPEs in block 00 to 3F
[    0.217378] ACPI: \_SB_.PCI0: notify handler is installed
[    0.217417] Found 1 acpi root devices
[    0.217484] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.217486] vgaarb: loaded
[    0.217487] vgaarb: bridge control possible 0000:00:02.0
[    0.217582] SCSI subsystem initialized
[    0.217614] libata version 3.00 loaded.
[    0.217625] ACPI: bus type USB registered
[    0.217635] usbcore: registered new interface driver usbfs
[    0.217640] usbcore: registered new interface driver hub
[    0.217662] usbcore: registered new device driver usb
[    0.217730] PCI: Using ACPI for IRQ routing
[    0.219170] PCI: pci_cache_line_size set to 64 bytes
[    0.219202] e820: reserve RAM buffer [mem 0x00091c00-0x0009ffff]
[    0.219203] e820: reserve RAM buffer [mem 0x40004000-0x43ffffff]
[    0.219204] e820: reserve RAM buffer [mem 0xd670a000-0xd7ffffff]
[    0.219205] e820: reserve RAM buffer [mem 0xd6f56000-0xd7ffffff]
[    0.219206] e820: reserve RAM buffer [mem 0xd77b4000-0xd7ffffff]
[    0.219207] e820: reserve RAM buffer [mem 0xd8f1b000-0xdbffffff]
[    0.219209] e820: reserve RAM buffer [mem 0xda6e7000-0xdbffffff]
[    0.219210] e820: reserve RAM buffer [mem 0xdb000000-0xdbffffff]
[    0.219211] e820: reserve RAM buffer [mem 0x21e600000-0x21fffffff]
[    0.219260] NetLabel: Initializing
[    0.219261] NetLabel:  domain hash size = 128
[    0.219262] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.219270] NetLabel:  unlabeled traffic allowed by default
[    0.219309] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    0.219313] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    0.221345] Switched to clocksource hpet
[    0.224347] AppArmor: AppArmor Filesystem Enabled
[    0.224359] pnp: PnP ACPI init
[    0.224366] ACPI: bus type PNP registered
[    0.224408] system 00:00: [mem 0xfed40000-0xfed44fff] has been reserved
[    0.224410] system 00:00: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.224419] pnp 00:01: [dma 4]
[    0.224428] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.224439] pnp 00:02: Plug and Play ACPI device, IDs INT0800 (active)
[    0.224507] pnp 00:03: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.224529] system 00:04: [io  0x0680-0x069f] has been reserved
[    0.224530] system 00:04: [io  0x1000-0x100f] has been reserved
[    0.224531] system 00:04: [io  0xffff] has been reserved
[    0.224532] system 00:04: [io  0xffff] has been reserved
[    0.224534] system 00:04: [io  0x0400-0x0453] could not be reserved
[    0.224535] system 00:04: [io  0x0458-0x047f] has been reserved
[    0.224536] system 00:04: [io  0x0500-0x057f] has been reserved
[    0.224537] system 00:04: [io  0x164e-0x164f] has been reserved
[    0.224539] system 00:04: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.224562] pnp 00:05: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.224589] system 00:06: [io  0x0454-0x0457] has been reserved
[    0.224591] system 00:06: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
[    0.224649] system 00:07: [io  0x0a40-0x0a4f] has been reserved
[    0.224650] system 00:07: [io  0x0a00-0x0a3f] has been reserved
[    0.224652] system 00:07: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.224680] system 00:08: [io  0x04d0-0x04d1] has been reserved
[    0.224681] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.224700] pnp 00:09: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.225236] pnp 00:0a: [dma 0 disabled]
[    0.225262] pnp 00:0a: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.225419] system 00:0b: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.225420] system 00:0b: [mem 0xfed10000-0xfed17fff] has been reserved
[    0.225421] system 00:0b: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.225423] system 00:0b: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.225424] system 00:0b: [mem 0xf8000000-0xfbffffff] has been reserved
[    0.225425] system 00:0b: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.225427] system 00:0b: [mem 0xfed90000-0xfed93fff] could not be reserved
[    0.225428] system 00:0b: [mem 0xfed45000-0xfed8ffff] has been reserved
[    0.225429] system 00:0b: [mem 0xff000000-0xffffffff] has been reserved
[    0.225431] system 00:0b: [mem 0xfee00000-0xfeefffff] could not be reserved
[    0.225432] system 00:0b: [mem 0xdfa00000-0xdfa00fff] has been reserved
[    0.225433] system 00:0b: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.225540] system 00:0c: [mem 0x20000000-0x201fffff] has been reserved
[    0.225542] system 00:0c: [mem 0x40004000-0x40004fff] has been reserved
[    0.225543] system 00:0c: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.225552] pnp: PnP ACPI: found 13 devices
[    0.225552] ACPI: bus type PNP unregistered
[    0.231481] pci 0000:00:1e.0: PCI bridge to [bus 01]
[    0.231494] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.231495] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.231497] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.231498] pci_bus 0000:00: resource 7 [mem 0x000dc000-0x000dffff]
[    0.231499] pci_bus 0000:00: resource 8 [mem 0x000e0000-0x000e3fff]
[    0.231500] pci_bus 0000:00: resource 9 [mem 0x000e4000-0x000e7fff]
[    0.231501] pci_bus 0000:00: resource 10 [mem 0xdfa00000-0xfeafffff]
[    0.231502] pci_bus 0000:01: resource 4 [io  0x0000-0x0cf7]
[    0.231504] pci_bus 0000:01: resource 5 [io  0x0d00-0xffff]
[    0.231505] pci_bus 0000:01: resource 6 [mem 0x000a0000-0x000bffff]
[    0.231506] pci_bus 0000:01: resource 7 [mem 0x000dc000-0x000dffff]
[    0.231507] pci_bus 0000:01: resource 8 [mem 0x000e0000-0x000e3fff]
[    0.231508] pci_bus 0000:01: resource 9 [mem 0x000e4000-0x000e7fff]
[    0.231509] pci_bus 0000:01: resource 10 [mem 0xdfa00000-0xfeafffff]
[    0.231527] NET: Registered protocol family 2
[    0.231632] TCP established hash table entries: 65536 (order: 7, 524288 bytes)
[    0.231736] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.231832] TCP: Hash tables configured (established 65536 bind 65536)
[    0.231842] TCP: reno registered
[    0.231849] UDP hash table entries: 4096 (order: 5, 131072 bytes)
[    0.231869] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
[    0.231912] NET: Registered protocol family 1
[    0.231919] pci 0000:00:02.0: Boot video device
[    0.273469] PCI: CLS 64 bytes, default 64
[    0.273500] Trying to unpack rootfs image as initramfs...
[    0.474645] Freeing initrd memory: 18652K (ffff880035b82000 - ffff880036db9000)
[    0.474689] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.474691] software IO TLB [mem 0xd270a000-0xd670a000] (64MB) mapped at [ffff8800d270a000-ffff8800d6709fff]
[    0.474932] microcode: CPU0 sig=0x306a9, pf=0x2, revision=0x12
[    0.474937] microcode: CPU1 sig=0x306a9, pf=0x2, revision=0x12
[    0.474940] microcode: CPU2 sig=0x306a9, pf=0x2, revision=0x12
[    0.474946] microcode: CPU3 sig=0x306a9, pf=0x2, revision=0x12
[    0.474951] microcode: CPU4 sig=0x306a9, pf=0x2, revision=0x12
[    0.474955] microcode: CPU5 sig=0x306a9, pf=0x2, revision=0x12
[    0.474959] microcode: CPU6 sig=0x306a9, pf=0x2, revision=0x12
[    0.474967] microcode: CPU7 sig=0x306a9, pf=0x2, revision=0x12
[    0.475007] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.475009] Scanning for low memory corruption every 60 seconds
[    0.475196] Initialise system trusted keyring
[    0.475222] audit: initializing netlink socket (disabled)
[    0.475231] type=2000 audit(1401260006.464:1): initialized
[    0.493809] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.494548] zbud: loaded
[    0.494647] VFS: Disk quotas dquot_6.5.2
[    0.494672] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.494925] fuse init (API version 7.22)
[    0.494970] msgmni has been set to 15737
[    0.495000] Key type big_key registered
[    0.495371] Key type asymmetric registered
[    0.495373] Asymmetric key parser 'x509' registered
[    0.495389] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    0.495434] io scheduler noop registered
[    0.495435] io scheduler deadline registered (default)
[    0.495448] io scheduler cfq registered
[    0.495488] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.495496] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.495517] vesafb: mode is 1920x1080x32, linelength=7680, pages=0
[    0.495518] vesafb: scrolling: redraw
[    0.495519] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    0.496298] vesafb: framebuffer at 0xe0000000, mapped to 0xffffc90004e80000, using 8128k, total 8128k
[    0.602931] Console: switching to colour frame buffer device 240x67
[    0.709126] fb0: VESA VGA frame buffer device
[    0.709136] intel_idle: MWAIT substates: 0x1120
[    0.709136] intel_idle: v0.4 model 0x3A
[    0.709137] intel_idle: lapic_timer_reliable_states 0xffffffff
[    0.709237] ipmi message handler version 39.2
[    0.709278] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.709282] ACPI: Power Button [PWRB]
[    0.709304] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.709305] ACPI: Power Button [PWRF]
[    0.709493] ACPI: Invalid active0 threshold
[    0.709545] thermal LNXTHERM:00: registered as thermal_zone0
[    0.709546] ACPI: Thermal Zone [TZ00] (28 C)
[    0.709698] thermal LNXTHERM:01: registered as thermal_zone1
[    0.709699] ACPI: Thermal Zone [TZ01] (30 C)
[    0.709713] GHES: HEST is not enabled!
[    0.709762] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.730473] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4, base_baud = 115200) is a 16550A
[    0.751669] 0000:00:16.3: ttyS4 at I/O 0xf0e0 (irq = 19, base_baud = 115200) is a 16550A
[    0.751833] Linux agpgart interface v0.103
[    0.752616] brd: module loaded
[    0.753030] loop: module loaded
[    0.753234] libphy: Fixed MDIO Bus: probed
[    0.753281] tun: Universal TUN/TAP device driver, 1.6
[    0.753282] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.753310] PPP generic driver version 2.4.2
[    0.753338] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.753340] ehci-pci: EHCI PCI platform driver
[    0.753434] ehci-pci 0000:00:1a.0: EHCI Host Controller
[    0.753438] ehci-pci 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    0.753452] ehci-pci 0000:00:1a.0: debug port 2
[    0.757346] ehci-pci 0000:00:1a.0: cache line size of 64 is not supported
[    0.757360] ehci-pci 0000:00:1a.0: irq 16, io mem 0xf7c38000
[    0.765611] ehci-pci 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    0.765639] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    0.765641] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.765642] usb usb1: Product: EHCI Host Controller
[    0.765643] usb usb1: Manufacturer: Linux 3.13.0-27-generic ehci_hcd
[    0.765644] usb usb1: SerialNumber: 0000:00:1a.0
[    0.765712] hub 1-0:1.0: USB hub found
[    0.765717] hub 1-0:1.0: 3 ports detected
[    0.765873] ehci-pci 0000:00:1d.0: EHCI Host Controller
[    0.765877] ehci-pci 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.765890] ehci-pci 0000:00:1d.0: debug port 2
[    0.769772] ehci-pci 0000:00:1d.0: cache line size of 64 is not supported
[    0.769785] ehci-pci 0000:00:1d.0: irq 23, io mem 0xf7c37000
[    0.781615] ehci-pci 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    0.781637] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    0.781638] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.781640] usb usb2: Product: EHCI Host Controller
[    0.781641] usb usb2: Manufacturer: Linux 3.13.0-27-generic ehci_hcd
[    0.781642] usb usb2: SerialNumber: 0000:00:1d.0
[    0.781702] hub 2-0:1.0: USB hub found
[    0.781706] hub 2-0:1.0: 3 ports detected
[    0.781786] ehci-platform: EHCI generic platform driver
[    0.781791] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.781792] ohci-pci: OHCI PCI platform driver
[    0.781796] ohci-platform: OHCI generic platform driver
[    0.781800] uhci_hcd: USB Universal Host Controller Interface driver
[    0.781887] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    0.781890] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 3
[    0.781980] xhci_hcd 0000:00:14.0: cache line size of 64 is not supported
[    0.782002] xhci_hcd 0000:00:14.0: irq 42 for MSI/MSI-X
[    0.782052] usb usb3: New USB device found, idVendor=1d6b, idProduct=0002
[    0.782054] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.782055] usb usb3: Product: xHCI Host Controller
[    0.782056] usb usb3: Manufacturer: Linux 3.13.0-27-generic xhci_hcd
[    0.782057] usb usb3: SerialNumber: 0000:00:14.0
[    0.782140] hub 3-0:1.0: USB hub found
[    0.782150] hub 3-0:1.0: 4 ports detected
[    0.782377] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    0.782379] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 4
[    0.782407] usb usb4: New USB device found, idVendor=1d6b, idProduct=0003
[    0.782408] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.782409] usb usb4: Product: xHCI Host Controller
[    0.782410] usb usb4: Manufacturer: Linux 3.13.0-27-generic xhci_hcd
[    0.782411] usb usb4: SerialNumber: 0000:00:14.0
[    0.782495] hub 4-0:1.0: USB hub found
[    0.782505] hub 4-0:1.0: 4 ports detected
[    0.789674] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    0.792545] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.792550] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.792741] mousedev: PS/2 mouse device common for all mice
[    0.792997] rtc_cmos 00:05: RTC can wake from S4
[    0.793166] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    0.793197] rtc_cmos 00:05: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    0.793236] device-mapper: uevent: version 1.0.3
[    0.793307] device-mapper: ioctl: 4.27.0-ioctl (2013-10-30) initialised: dm-devel@redhat.com
[    0.793311] ledtrig-cpu: registered to indicate activity on CPUs
[    0.793374] TCP: cubic registered
[    0.793418] NET: Registered protocol family 10
[    0.793516] NET: Registered protocol family 17
[    0.793521] Key type dns_resolver registered
[    0.793815] Loading compiled-in X.509 certificates
[    0.794408] Loaded X.509 cert 'Magrathea: Glacier signing key: 23984ac203784325ccf7b95b51f6c119380eb933'
[    0.794414] registered taskstats version 1
[    0.796381] Key type trusted registered
[    0.798214] Key type encrypted registered
[    0.800011] AppArmor: AppArmor sha1 policy hashing enabled
[    0.800014] IMA: No TPM chip found, activating TPM-bypass!
[    0.800179] regulator-dummy: disabling
[    0.800323]   Magic number: 14:72:874
[    0.800430] rtc_cmos 00:05: setting system clock to 2014-05-28 06:53:27 UTC (1401260007)
[    0.801361] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.801362] EDD information not available.
[    0.801403] PM: Hibernation image not present or could not be loaded.
[    0.802045] Freeing unused kernel memory: 1332K (ffffffff81d1f000 - ffffffff81e6c000)
[    0.802047] Write protecting the kernel read-only data: 12288k
[    0.803431] Freeing unused kernel memory: 828K (ffff880001731000 - ffff880001800000)
[    0.804585] Freeing unused kernel memory: 700K (ffff880001b51000 - ffff880001c00000)
[    0.812713] systemd-udevd[143]: starting version 204
[    0.826913] pps_core: LinuxPPS API ver. 1 registered
[    0.826916] pps_core: Software ver. 5.3.6 - Copyright 2005-2007 Rodolfo Giometti <giometti@linux.it>
[    0.827741] PTP clock support registered
[    0.828319] ahci 0000:00:1f.2: version 3.0
[    0.828442] ahci 0000:00:1f.2: irq 43 for MSI/MSI-X
[    0.828484] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 6 Gbps 0x3 impl RAID mode
[    0.828486] ahci 0000:00:1f.2: flags: 64bit ncq pm led clo pio slum part ems apst 
[    0.830246] e1000e: Intel(R) PRO/1000 Network Driver - 2.3.2-k
[    0.830248] e1000e: Copyright(c) 1999 - 2013 Intel Corporation.
[    0.833971] scsi0 : ahci
[    0.834043] scsi1 : ahci
[    0.834110] scsi2 : ahci
[    0.834159] scsi3 : ahci
[    0.834220] scsi4 : ahci
[    0.834286] scsi5 : ahci
[    0.834317] ata1: SATA max UDMA/133 abar m2048@0xf7c36000 port 0xf7c36100 irq 43
[    0.834320] ata2: SATA max UDMA/133 abar m2048@0xf7c36000 port 0xf7c36180 irq 43
[    0.834322] ata3: DUMMY
[    0.834323] ata4: DUMMY
[    0.834324] ata5: DUMMY
[    0.834325] ata6: DUMMY
[    0.834498] e1000e 0000:00:19.0: Interrupt Throttling Rate (ints/sec) set to dynamic conservative mode
[    0.834526] e1000e 0000:00:19.0: irq 44 for MSI/MSI-X
[    1.041357] e1000e 0000:00:19.0 eth0: registered PHC clock
[    1.041359] e1000e 0000:00:19.0 eth0: (PCI Express:2.5GT/s:Width x1) 90:b1:1c:72:13:5c
[    1.041361] e1000e 0000:00:19.0 eth0: Intel(R) PRO/1000 Network Connection
[    1.041394] e1000e 0000:00:19.0 eth0: MAC: 10, PHY: 11, PBA No: 1011FF-0FF
[    1.077856] usb 1-1: new high-speed USB device number 2 using ehci-pci
[    1.153840] ata1: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    1.153878] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.154927] ata1.00: ACPI cmd ef/10:06:00:00:00:00 (SET FEATURES) succeeded
[    1.154933] ata1.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
[    1.154936] ata1.00: ACPI cmd b1/c1:00:00:00:00:00 (DEVICE CONFIGURATION OVERLAY) filtered out
[    1.155551] ata1.00: ACPI cmd 00/00:00:00:00:00:a0 (NOP) rejected by device (Stat=0x51 Err=0x04)
[    1.157095] ata1.00: ATA-8: ST500LX003-1AC15G, DEM4, max UDMA/133
[    1.157102] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    1.158072] ata2.00: ACPI cmd ef/10:06:00:00:00:00 (SET FEATURES) succeeded
[    1.158078] ata2.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
[    1.158081] ata2.00: ACPI cmd b1/c1:00:00:00:00:00 (DEVICE CONFIGURATION OVERLAY) filtered out
[    1.158511] ata2.00: ACPI cmd 00/00:00:00:00:00:a0 (NOP) rejected by device (Stat=0x51 Err=0x04)
[    1.159266] ata1.00: ACPI cmd ef/10:06:00:00:00:00 (SET FEATURES) succeeded
[    1.159271] ata1.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
[    1.159275] ata1.00: ACPI cmd b1/c1:00:00:00:00:00 (DEVICE CONFIGURATION OVERLAY) filtered out
[    1.159886] ata1.00: ACPI cmd 00/00:00:00:00:00:a0 (NOP) rejected by device (Stat=0x51 Err=0x04)
[    1.161458] ata1.00: configured for UDMA/133
[    1.161806] ata2.00: ATAPI: HL-DT-ST DVD+/-RW GHA2N, A103, max UDMA/133
[    1.166033] scsi 0:0:0:0: Direct-Access     ATA      ST500LX003-1AC15 DEM4 PQ: 0 ANSI: 5
[    1.166158] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.166167] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    1.166168] sd 0:0:0:0: [sda] 4096-byte physical blocks
[    1.166361] sd 0:0:0:0: [sda] Write Protect is off
[    1.166364] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.166459] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.166996] ata2.00: ACPI cmd ef/10:06:00:00:00:00 (SET FEATURES) succeeded
[    1.166999] ata2.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
[    1.167001] ata2.00: ACPI cmd b1/c1:00:00:00:00:00 (DEVICE CONFIGURATION OVERLAY) filtered out
[    1.167505] ata2.00: ACPI cmd 00/00:00:00:00:00:a0 (NOP) rejected by device (Stat=0x51 Err=0x04)
[    1.168805]  sda: sda1 sda2 sda3 < sda5 sda6 >
[    1.169608] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.170783] ata2.00: configured for UDMA/133
[    1.192854] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVD+-RW GHA2N    A103 PQ: 0 ANSI: 5
[    1.209056] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.209060] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.209172] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.209242] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.210118] usb 1-1: New USB device found, idVendor=8087, idProduct=0024
[    1.210120] usb 1-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.210257] hub 1-1:1.0: USB hub found
[    1.210372] hub 1-1:1.0: 6 ports detected
[    1.321901] usb 2-1: new high-speed USB device number 2 using ehci-pci
[    1.344686] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
[    1.454350] usb 2-1: New USB device found, idVendor=8087, idProduct=0024
[    1.454352] usb 2-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.454691] hub 2-1:1.0: USB hub found
[    1.454893] hub 2-1:1.0: 8 ports detected
[    1.473962] tsc: Refined TSC clocksource calibration: 3392.294 MHz
[    1.548146] random: init urandom read with 55 bits of entropy available
[    1.622051] usb 3-3: new high-speed USB device number 2 using xhci_hcd
[    1.622247] init: plymouth-upstart-bridge main process (223) terminated with status 1
[    1.622256] init: plymouth-upstart-bridge main process ended, respawning
[    1.624016] init: plymouth-upstart-bridge main process (234) terminated with status 1
[    1.624026] init: plymouth-upstart-bridge main process ended, respawning
[    1.625305] init: plymouth-upstart-bridge main process (236) terminated with status 1
[    1.625315] init: plymouth-upstart-bridge main process ended, respawning
[    1.627561] init: plymouth-upstart-bridge main process (237) terminated with status 1
[    1.627568] init: plymouth-upstart-bridge main process ended, respawning
[    1.628844] init: plymouth-upstart-bridge main process (239) terminated with status 1
[    1.628857] init: plymouth-upstart-bridge main process ended, respawning
[    1.631134] init: plymouth-upstart-bridge main process (240) terminated with status 1
[    1.631142] init: plymouth-upstart-bridge main process ended, respawning
[    1.633577] init: plymouth-upstart-bridge main process (242) terminated with status 1
[    1.633585] init: plymouth-upstart-bridge main process ended, respawning
[    1.634712] init: plymouth-upstart-bridge main process (245) terminated with status 1
[    1.634724] init: plymouth-upstart-bridge main process ended, respawning
[    1.636045] init: plymouth-upstart-bridge main process (246) terminated with status 1
[    1.636052] init: plymouth-upstart-bridge main process ended, respawning
[    1.638250] usb 3-3: New USB device found, idVendor=413c, idProduct=1010
[    1.638252] usb 3-3: New USB device strings: Mfr=0, Product=1, SerialNumber=0
[    1.638254] usb 3-3: Product: USB 2.0 Hub [MTT]
[    1.638468] hub 3-3:1.0: USB hub found
[    1.638491] hub 3-3:1.0: 4 ports detected
[    1.806166] usb 3-4: new high-speed USB device number 3 using xhci_hcd
[    1.822451] usb 3-4: New USB device found, idVendor=0424, idProduct=2514
[    1.822453] usb 3-4: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.822780] hub 3-4:1.0: USB hub found
[    1.822849] hub 3-4:1.0: 4 ports detected
[    1.910225] usb 3-3.4: new low-speed USB device number 4 using xhci_hcd
[    1.935590] usb 3-3.4: New USB device found, idVendor=413c, idProduct=2110
[    1.935592] usb 3-3.4: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.935593] usb 3-3.4: Product: Dell Wired Multimedia Keyboard
[    1.935594] usb 3-3.4: Manufacturer: Dell
[    1.935699] usb 3-3.4: ep 0x81 - rounding interval to 64 microframes, ep desc says 80 microframes
[    1.935702] usb 3-3.4: ep 0x82 - rounding interval to 64 microframes, ep desc says 80 microframes
[    2.094280] usb 3-4.1: new low-speed USB device number 5 using xhci_hcd
[    2.114446] usb 3-4.1: New USB device found, idVendor=04ca, idProduct=0061
[    2.114449] usb 3-4.1: New USB device strings: Mfr=0, Product=2, SerialNumber=0
[    2.114450] usb 3-4.1: Product: USB Optical Mouse
[    2.114548] usb 3-4.1: ep 0x81 - rounding interval to 64 microframes, ep desc says 80 microframes
[    2.474608] Switched to clocksource tsc
[    3.291621] random: nonblocking pool is initialized
[    4.042491] Adding 8269820k swap on /dev/sda6.  Priority:-1 extents:1 across:8269820k FS
[    4.051948] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    4.069627] systemd-udevd[354]: starting version 204
[    4.089402] lp: driver loaded but no devices found
[    4.093429] mei_me 0000:00:16.0: irq 45 for MSI/MSI-X
[    4.094258] [drm] Initialized drm 1.1.0 20060810
[    4.101391] ppdev: user-space parallel port driver
[    4.110241] [drm] Memory usable by graphics device = 2048M
[    4.110245] checking generic (e0000000 7f0000) vs hw (e0000000 10000000)
[    4.110247] fb: conflicting fb hw usage inteldrmfb vs VESA VGA - removing generic driver
[    4.110264] Console: switching to colour dummy device 80x25
[    4.124276] type=1400 audit(1401260010.817:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=426 comm="apparmor_parser"
[    4.124283] type=1400 audit(1401260010.817:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=426 comm="apparmor_parser"
[    4.124287] type=1400 audit(1401260010.817:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=426 comm="apparmor_parser"
[    4.124661] type=1400 audit(1401260010.817:5): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=426 comm="apparmor_parser"
[    4.124666] type=1400 audit(1401260010.817:6): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=426 comm="apparmor_parser"
[    4.124859] type=1400 audit(1401260010.817:7): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=426 comm="apparmor_parser"
[    4.145548] hidraw: raw HID events driver (C) Jiri Kosina
[    4.161119] usbcore: registered new interface driver usbhid
[    4.161121] usbhid: USB HID core driver
[    4.167733] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[    4.171212] i915 0000:00:02.0: irq 46 for MSI/MSI-X
[    4.171221] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[    4.171222] [drm] Driver supports precise vblank timestamp query.
[    4.171329] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[    4.201421] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro
[    4.201849] input: Dell Dell Wired Multimedia Keyboard as /devices/pci0000:00/0000:00:14.0/usb3/3-3/3-3.4/3-3.4:1.0/input/input5
[    4.202708] hid-generic 0003:413C:2110.0001: input,hidraw0: USB HID v1.10 Keyboard [Dell Dell Wired Multimedia Keyboard] on usb-0000:00:14.0-3.4/input0
[    4.202860] input: Dell Dell Wired Multimedia Keyboard as /devices/pci0000:00/0000:00:14.0/usb3/3-3/3-3.4/3-3.4:1.1/input/input6
[    4.202979] hid-generic 0003:413C:2110.0002: input,hiddev0,hidraw1: USB HID v1.10 Mouse [Dell Dell Wired Multimedia Keyboard] on usb-0000:00:14.0-3.4/input1
[    4.203070] input: USB Optical Mouse as /devices/pci0000:00/0000:00:14.0/usb3/3-4/3-4.1/3-4.1:1.0/input/input7
[    4.203151] hid-generic 0003:04CA:0061.0003: input,hidraw2: USB HID v1.11 Mouse [USB Optical Mouse] on usb-0000:00:14.0-4.1/input0
[    4.272492] fbcon: inteldrmfb (fb0) is primary device
[    4.330329] intel_rapl: domain uncore energy ctr 119784:119784 not working, skip
[    4.647494] Console: switching to colour frame buffer device 160x64
[    4.652150] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[    4.652152] i915 0000:00:02.0: registered panic notifier
[    4.666219] init: failsafe main process (683) killed by TERM signal
[    4.667639] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[    4.667943] acpi device:4a: registered as cooling_device9
[    4.668023] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input8
[    4.668094] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    4.668255] ACPI Warning: 0x0000000000000428-0x000000000000042f SystemIO conflicts with Region \PMIO 1 (20131115/utaddress-251)
[    4.668261] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    4.668267] ACPI Warning: 0x0000000000000530-0x000000000000053f SystemIO conflicts with Region \GPIO 1 (20131115/utaddress-251)
[    4.668270] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    4.668271] ACPI Warning: 0x0000000000000500-0x000000000000052f SystemIO conflicts with Region \GPIO 1 (20131115/utaddress-251)
[    4.668274] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    4.668275] lpc_ich: Resource conflict(s) found affecting gpio_ich
[    4.668713] snd_hda_intel 0000:00:1b.0: irq 47 for MSI/MSI-X
[    4.679123] hda_codec: ALC269VB: SKU not ready 0x411111f0
[    4.679722] autoconfig: line_outs=1 (0x1b/0x0/0x0/0x0/0x0) type:line
[    4.679724]    speaker_outs=1 (0x14/0x0/0x0/0x0/0x0)
[    4.679725]    hp_outs=1 (0x21/0x0/0x0/0x0/0x0)
[    4.679725]    mono: mono_out=0x0
[    4.679726]    inputs:
[    4.679727]      Rear Mic=0x19
[    4.679728]      Front Mic=0x18
[    4.679728] realtek: No valid SSID, checking pincfg 0x411111f0 for NID 0x1d
[    4.679729] realtek: Enable default setup for auto mode as fallback
[    4.689005] input: HDA Intel PCH HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input14
[    4.689068] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input13
[    4.689121] input: HDA Intel PCH Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[    4.689176] input: HDA Intel PCH Line Out as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[    4.689227] input: HDA Intel PCH Front Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[    4.689278] input: HDA Intel PCH Rear Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[    4.705534] Bluetooth: Core ver 2.17
[    4.705549] NET: Registered protocol family 31
[    4.705550] Bluetooth: HCI device and connection manager initialized
[    4.705556] Bluetooth: HCI socket layer initialized
[    4.705557] Bluetooth: L2CAP socket layer initialized
[    4.705560] Bluetooth: SCO socket layer initialized
[    4.707409] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    4.707411] Bluetooth: BNEP filters: protocol multicast
[    4.707422] Bluetooth: BNEP socket layer initialized
[    4.710174] Bluetooth: RFCOMM TTY layer initialized
[    4.710180] Bluetooth: RFCOMM socket layer initialized
[    4.710183] Bluetooth: RFCOMM ver 1.11
[    4.762841] type=1400 audit(1401260011.453:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=787 comm="apparmor_parser"
[    4.762846] type=1400 audit(1401260011.453:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cupsd" pid=787 comm="apparmor_parser"
[    4.763113] type=1400 audit(1401260011.453:10): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=787 comm="apparmor_parser"
[    4.811299] init: cups main process (794) killed by HUP signal
[    4.811308] init: cups main process ended, respawning
[    4.944208] e1000e 0000:00:19.0: irq 44 for MSI/MSI-X
[    5.047631] e1000e 0000:00:19.0: irq 44 for MSI/MSI-X
[    5.047851] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    5.048058] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    5.101327] init: Failed to spawn atd main process: unable to execute: No such file or directory
[    5.465549] init: plymouth-upstart-bridge main process ended, respawning
[    5.470303] init: plymouth-upstart-bridge main process (1213) terminated with status 1
[    5.470320] init: plymouth-upstart-bridge main process ended, respawning
[    5.828247] [drm] Enabling RC6 states: RC6 on, RC6p on, RC6pp off
[    8.562595] e1000e: eth0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: Rx
[    8.562628] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   34.828489] audit_printk_skb: 171 callbacks suppressed
[   34.828492] type=1400 audit(1401260041.006:68): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=2629 comm="apparmor_parser"
[   34.828496] type=1400 audit(1401260041.006:69): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=2629 comm="apparmor_parser"
[   34.828755] type=1400 audit(1401260041.006:70): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=2629 comm="apparmor_parser"
[  147.095997] vboxdrv: module verification failed: signature and/or  required key missing - tainting kernel
[  147.096163] vboxdrv: Unknown symbol mcount (err 0)
[  294.760149] vboxdrv: Unknown symbol mcount (err 0)
[  646.283419] vboxdrv: Unknown symbol mcount (err 0)
[ 1266.772769] warning: `VirtualBox' uses 32-bit capabilities (legacy support in use)
[ 2607.975427] usb 3-4: USB disconnect, device number 3
[ 2607.975446] usb 3-4.1: USB disconnect, device number 5
[40916.224404] perf samples too long (2514 > 2500), lowering kernel.perf_event_max_sample_rate to 50000
[52814.846238] usb 3-4: new high-speed USB device number 6 using xhci_hcd
[52814.862341] usb 3-4: New USB device found, idVendor=0424, idProduct=2514
[52814.862347] usb 3-4: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[52814.862692] hub 3-4:1.0: USB hub found
[52814.862727] hub 3-4:1.0: 4 ports detected
[52815.134373] usb 3-4.1: new low-speed USB device number 7 using xhci_hcd
[52815.154170] usb 3-4.1: New USB device found, idVendor=04ca, idProduct=0061
[52815.154175] usb 3-4.1: New USB device strings: Mfr=0, Product=2, SerialNumber=0
[52815.154178] usb 3-4.1: Product: USB Optical Mouse
[52815.154378] usb 3-4.1: ep 0x81 - rounding interval to 64 microframes, ep desc says 80 microframes
[52815.156712] input: USB Optical Mouse as /devices/pci0000:00/0000:00:14.0/usb3/3-4/3-4.1/3-4.1:1.0/input/input15
[52815.157140] hid-generic 0003:04CA:0061.0004: input,hidraw2: USB HID v1.11 Mouse [USB Optical Mouse] on usb-0000:00:14.0-4.1/input0
[53415.613226] type=1400 audit(1401313397.163:71): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=18902 comm="apparmor_parser"
[53415.613232] type=1400 audit(1401313397.163:72): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=18902 comm="apparmor_parser"
[53415.613549] type=1400 audit(1401313397.163:73): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=18902 comm="apparmor_parser"
[63868.686120] type=1400 audit(1401323845.415:74): apparmor="DENIED" operation="mknod" profile="/usr/sbin/cupsd" name="/var/cache/samba/gencache.tdb" pid=21677 comm="smb" requested_mask="c" denied_mask="c" fsuid=7 ouid=7
[63868.686407] type=1400 audit(1401323845.415:75): apparmor="DENIED" operation="mknod" profile="/usr/sbin/cupsd" name="/var/cache/samba/gencache.tdb" pid=21677 comm="smb" requested_mask="c" denied_mask="c" fsuid=7 ouid=7
[63869.178552] type=1400 audit(1401323845.903:76): apparmor="DENIED" operation="mknod" profile="/usr/sbin/cupsd" name="/var/cache/samba/gencache.tdb" pid=21677 comm="smb" requested_mask="c" denied_mask="c" fsuid=7 ouid=7
[76760.218544] [drm] stuck on render ring
[76760.218550] [drm] GPU crash dump saved to /sys/class/drm/card0/error
[76760.218551] [drm] GPU hangs can indicate a bug anywhere in the entire gfx stack, including userspace.
[76760.218552] [drm] Please file a _new_ bug report on bugs.freedesktop.org against DRI -> DRM/Intel
[76760.218553] [drm] drm/i915 developers can then reassign to the right component if it's not a kernel issue.
[76760.218553] [drm] The gpu crash dump is required to analyze gpu hangs, so please always attach it.
[85095.076255] [drm] stuck on render ring
[140233.923680] type=1400 audit(1401400175.416:77): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=3246 comm="apparmor_parser"
[140233.923686] type=1400 audit(1401400175.416:78): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=3246 comm="apparmor_parser"
[140233.924004] type=1400 audit(1401400175.416:79): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=3246 comm="apparmor_parser"
[147242.356466] type=1400 audit(1401407180.616:80): apparmor="DENIED" operation="mknod" profile="/usr/sbin/cupsd" name="/var/cache/samba/gencache.tdb" pid=3982 comm="smb" requested_mask="c" denied_mask="c" fsuid=7 ouid=7
[147242.356679] type=1400 audit(1401407180.616:81): apparmor="DENIED" operation="mknod" profile="/usr/sbin/cupsd" name="/var/cache/samba/gencache.tdb" pid=3982 comm="smb" requested_mask="c" denied_mask="c" fsuid=7 ouid=7
[147242.358162] type=1400 audit(1401407180.616:82): apparmor="DENIED" operation="mknod" profile="/usr/sbin/cupsd" name="/var/cache/samba/gencache.tdb" pid=3982 comm="smb" requested_mask="c" denied_mask="c" fsuid=7 ouid=7
[154527.272242] type=1400 audit(1401414462.169:83): apparmor="DENIED" operation="mknod" profile="/usr/sbin/cupsd" name="/var/cache/samba/gencache.tdb" pid=6555 comm="smb" requested_mask="c" denied_mask="c" fsuid=7 ouid=7
[154527.272583] type=1400 audit(1401414462.173:84): apparmor="DENIED" operation="mknod" profile="/usr/sbin/cupsd" name="/var/cache/samba/gencache.tdb" pid=6555 comm="smb" requested_mask="c" denied_mask="c" fsuid=7 ouid=7
[154527.273924] type=1400 audit(1401414462.173:85): apparmor="DENIED" operation="mknod" profile="/usr/sbin/cupsd" name="/var/cache/samba/gencache.tdb" pid=6555 comm="smb" requested_mask="c" denied_mask="c" fsuid=7 ouid=7
[154533.519488] type=1400 audit(1401414468.417:86): apparmor="DENIED" operation="mknod" profile="/usr/sbin/cupsd" name="/var/cache/samba/gencache.tdb" pid=6579 comm="smb" requested_mask="c" denied_mask="c" fsuid=7 ouid=7
[154533.519654] type=1400 audit(1401414468.417:87): apparmor="DENIED" operation="mknod" profile="/usr/sbin/cupsd" name="/var/cache/samba/gencache.tdb" pid=6579 comm="smb" requested_mask="c" denied_mask="c" fsuid=7 ouid=7
[154533.521010] type=1400 audit(1401414468.417:88): apparmor="DENIED" operation="mknod" profile="/usr/sbin/cupsd" name="/var/cache/samba/gencache.tdb" pid=6579 comm="smb" requested_mask="c" denied_mask="c" fsuid=7 ouid=7
[154841.227030] type=1400 audit(1401414775.981:89): apparmor="DENIED" operation="mknod" profile="/usr/sbin/cupsd" name="/var/cache/samba/gencache.tdb" pid=7063 comm="smb" requested_mask="c" denied_mask="c" fsuid=7 ouid=7
[154841.227159] type=1400 audit(1401414775.981:90): apparmor="DENIED" operation="mknod" profile="/usr/sbin/cupsd" name="/var/cache/samba/gencache.tdb" pid=7063 comm="smb" requested_mask="c" denied_mask="c" fsuid=7 ouid=7
[154841.228347] type=1400 audit(1401414775.981:91): apparmor="DENIED" operation="mknod" profile="/usr/sbin/cupsd" name="/var/cache/samba/gencache.tdb" pid=7063 comm="smb" requested_mask="c" denied_mask="c" fsuid=7 ouid=7
[155054.691449] type=1400 audit(1401414989.345:92): apparmor="DENIED" operation="mknod" profile="/usr/sbin/cupsd" name="/var/cache/samba/gencache.tdb" pid=7126 comm="smb" requested_mask="c" denied_mask="c" fsuid=7 ouid=7
[155054.691578] type=1400 audit(1401414989.345:93): apparmor="DENIED" operation="mknod" profile="/usr/sbin/cupsd" name="/var/cache/samba/gencache.tdb" pid=7126 comm="smb" requested_mask="c" denied_mask="c" fsuid=7 ouid=7
[155054.695228] type=1400 audit(1401414989.349:94): apparmor="DENIED" operation="mknod" profile="/usr/sbin/cupsd" name="/var/cache/samba/gencache.tdb" pid=7126 comm="smb" requested_mask="c" denied_mask="c" fsuid=7 ouid=7
[155430.485096] type=1400 audit(1401415364.965:95): apparmor="DENIED" operation="mknod" profile="/usr/sbin/cupsd" name="/var/cache/samba/gencache.tdb" pid=7179 comm="smb" requested_mask="c" denied_mask="c" fsuid=7 ouid=7
[155430.485304] type=1400 audit(1401415364.969:96): apparmor="DENIED" operation="mknod" profile="/usr/sbin/cupsd" name="/var/cache/samba/gencache.tdb" pid=7179 comm="smb" requested_mask="c" denied_mask="c" fsuid=7 ouid=7
[155430.486723] type=1400 audit(1401415364.969:97): apparmor="DENIED" operation="mknod" profile="/usr/sbin/cupsd" name="/var/cache/samba/gencache.tdb" pid=7179 comm="smb" requested_mask="c" denied_mask="c" fsuid=7 ouid=7
[155801.413962] type=1400 audit(1401415735.725:98): apparmor="DENIED" operation="mknod" profile="/usr/sbin/cupsd" name="/var/cache/samba/gencache.tdb" pid=7336 comm="smb" requested_mask="c" denied_mask="c" fsuid=7 ouid=7
[155801.414103] type=1400 audit(1401415735.725:99): apparmor="DENIED" operation="mknod" profile="/usr/sbin/cupsd" name="/var/cache/samba/gencache.tdb" pid=7336 comm="smb" requested_mask="c" denied_mask="c" fsuid=7 ouid=7
[155801.415482] type=1400 audit(1401415735.725:100): apparmor="DENIED" operation="mknod" profile="/usr/sbin/cupsd" name="/var/cache/samba/gencache.tdb" pid=7336 comm="smb" requested_mask="c" denied_mask="c" fsuid=7 ouid=7
[155818.221769] type=1400 audit(1401415752.525:101): apparmor="DENIED" operation="mknod" profile="/usr/sbin/cupsd" name="/var/cache/samba/gencache.tdb" pid=7375 comm="smb" requested_mask="c" denied_mask="c" fsuid=7 ouid=7
[155818.221947] type=1400 audit(1401415752.525:102): apparmor="DENIED" operation="mknod" profile="/usr/sbin/cupsd" name="/var/cache/samba/gencache.tdb" pid=7375 comm="smb" requested_mask="c" denied_mask="c" fsuid=7 ouid=7
[155818.223263] type=1400 audit(1401415752.525:103): apparmor="DENIED" operation="mknod" profile="/usr/sbin/cupsd" name="/var/cache/samba/gencache.tdb" pid=7375 comm="smb" requested_mask="c" denied_mask="c" fsuid=7 ouid=7
[155850.031431] type=1400 audit(1401415784.321:104): apparmor="DENIED" operation="mknod" profile="/usr/sbin/cupsd" name="/var/cache/samba/gencache.tdb" pid=7408 comm="smb" requested_mask="c" denied_mask="c" fsuid=7 ouid=7
[155850.031552] type=1400 audit(1401415784.321:105): apparmor="DENIED" operation="mknod" profile="/usr/sbin/cupsd" name="/var/cache/samba/gencache.tdb" pid=7408 comm="smb" requested_mask="c" denied_mask="c" fsuid=7 ouid=7
[155850.032681] type=1400 audit(1401415784.321:106): apparmor="DENIED" operation="mknod" profile="/usr/sbin/cupsd" name="/var/cache/samba/gencache.tdb" pid=7408 comm="smb" requested_mask="c" denied_mask="c" fsuid=7 ouid=7
[155889.259140] type=1400 audit(1401415823.529:107): apparmor="DENIED" operation="mknod" profile="/usr/sbin/cupsd" name="/var/cache/samba/gencache.tdb" pid=7471 comm="smb" requested_mask="c" denied_mask="c" fsuid=7 ouid=7
[155889.259327] type=1400 audit(1401415823.529:108): apparmor="DENIED" operation="mknod" profile="/usr/sbin/cupsd" name="/var/cache/samba/gencache.tdb" pid=7471 comm="smb" requested_mask="c" denied_mask="c" fsuid=7 ouid=7
[155889.260844] type=1400 audit(1401415823.533:109): apparmor="DENIED" operation="mknod" profile="/usr/sbin/cupsd" name="/var/cache/samba/gencache.tdb" pid=7471 comm="smb" requested_mask="c" denied_mask="c" fsuid=7 ouid=7
[175599.618731] vboxdrv: Unknown symbol mcount (err 0)
[175949.158215] vboxdrv: Unknown symbol mcount (err 0)

```

---

### Post by jdeca57 on 2014-05-30
I'm sorry but this is as far as I can help. 
Two remarks: on my system dmesg there are no lines like
```
[    0.000000] *BAD*gran_size: 1M     chunk_size: 2G     num_reg: 10      lose cover RAM: -1G
```
And also, I have no issue with the GPU:
```
[   12.104347] [drm] ib test on ring 5 succeeded
[   12.104642] [drm] Radeon Display Connectors
```
etc... where your output is 'stuck on render ring' and GPU crash dump saved to...

---

