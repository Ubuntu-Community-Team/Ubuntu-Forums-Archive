---
title: "Nextcloud server locks up with no discernable cause."
date: 2021-03-06
forum: Server Platforms
---

### Post by DuckHook on 2021-03-06
My Nextcloud server keeps hard locking on me. Once every few days with no discernible pattern. All times of day, sometimes a couple of days elapsing, sometimes longer than a week. Due to simultaneous log death, triage is proving especially challenging. For security/isolation, I feel that I must jail it within a LXD container—which is commonly done—but it's otherwise pretty much a default install. It is a component install: LAMP stack then the latest NC directly from the official site. I did not use the NC snap. The things I've already tried are:

[list=1]
[*]Upgraded RAM to 16 GB (replaced all RAM modules with new, so problem is unlikely memory related)
[*]Updated to most recent BIOS (so if it's CPU or MOBO, I have no further recourse other than new HW)
[*]Added 90 GB ZFS ARC cache
[*]Constrained Nextcloud container to only 2 of 4 CPU threads.
[/list]
By constraining CPU threads, the last failure at least did not freeze up the whole server. But I couldn't kill the LXD container, nor could I reach the Nextcloud instance. I could log into container directly (SSH didn't work), but no commands would execute, returning just a continually blinking cursor that had to be killed (vis SSH into the server). Logs were again frustratingly unhelpful. Web searches, likewise. There are hints that the problem could be a combo of kernel bugs and ZFS. Or perhaps my server is just too Mickey Mouse to handle such infrastructure, though that doesn't seem likely since many successfully run their NC instances from an RPi.

I should add that NC is the only container running on it. Though at one point I had plans to multitask the server, given the above, it is not used for anything else.

I am thinking of replacing ZFS with LVM. Also considering physically isolating the server and running LAMP+NC on a base install with no containment but also sans fancy file system, though this would be far from ideal and only a last resort.

HW description:

```
duckhook@charon:~$ sudo lshw -sanitize
computer                    
    description: Desktop Computer
    product: To Be Filled By O.E.M. (To Be Filled By O.E.M.)
    vendor: To Be Filled By O.E.M.
    version: To Be Filled By O.E.M.
    serial: [REMOVED]
    width: 64 bits
    capabilities: smbios-2.8 dmi-2.8 smp vsyscall32
    configuration: boot=normal chassis=desktop family=To Be Filled By O.E.M. sku=To Be Filled By O.E.M. uuid=[REMOVED]
  *-core
       description: Motherboard
       product: Q1900B-ITX
       vendor: ASRock
       physical id: 0
       serial: [REMOVED]
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: P2.20
          date: 02/12/2019
          size: 64KiB
          capacity: 8MiB
          capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer acpi usb biosbootspecification uefi
     *-memory
          description: System Memory
          physical id: a
          slot: System board or motherboard
          size: 16GiB
        *-bank:0
             description: DIMM DDR3 1333 MHz (0.8 ns)
             product: HMT41GS6AFR8A-PB
             vendor: Hynix Semiconduc
             physical id: 0
             serial: [REMOVED]
             slot: A1_DIMM0
             size: 8GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:1
             description: DIMM DDR3 1333 MHz (0.8 ns)
             product: HMT41GS6AFR8A-PB
             vendor: Hynix Semiconduc
             physical id: 1
             serial: [REMOVED]
             slot: A1_DIMM1
             size: 8GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
     *-cache:0
          description: L1 cache
          physical id: 11
          slot: CPU Internal L1
          size: 224KiB
          capacity: 224KiB
          capabilities: internal write-back
          configuration: level=1
     *-cache:1
          description: L2 cache
          physical id: 12
          slot: CPU Internal L2
          size: 2MiB
          capacity: 2MiB
          capabilities: internal write-back unified
          configuration: level=2
     *-cpu
          description: CPU
          product: Intel(R) Celeron(R) CPU  J1900  @ 1.99GHz
          vendor: Intel Corp.
          physical id: 13
          bus info: cpu@0
          version: Intel(R) Celeron(R) CPU J1900 @ 1.99GHz
          slot: CPUSocket
          size: 2317MHz
          capacity: 2416MHz
          width: 64 bits
          clock: 83MHz
          capabilities: lm fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp x86-64 constant_tsc arch_perfmon pebs bts rep_good nopl xtopology tsc_reliable nonstop_tsc cpuid aperfmperf tsc_known_freq pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 movbe popcnt tsc_deadline_timer rdrand lahf_lm 3dnowprefetch epb pti ibrs ibpb stibp tpr_shadow vnmi flexpriority ept vpid tsc_adjust smep erms dtherm ida arat cpufreq
          configuration: cores=4 enabledcores=4 threads=4
     *-pci
          description: Host bridge
          product: Atom Processor Z36xxx/Z37xxx Series SoC Transaction Register
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 0c
          width: 32 bits
          clock: 33MHz
          configuration: driver=iosf_mbi_pci
          resources: irq:0
        *-display
             description: VGA compatible controller
             product: Atom Processor Z36xxx/Z37xxx Series Graphics & Display
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 0c
             width: 32 bits
             clock: 33MHz
             capabilities: pm msi vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:94 memory:d0000000-d03fffff memory:c0000000-cfffffff ioport:f080(size=8) memory:c0000-dffff
        *-sata
             description: SATA controller
             product: Atom Processor E3800 Series SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 0c
             width: 32 bits
             clock: 66MHz
             capabilities: sata msi pm ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:92 ioport:f070(size=8) ioport:f060(size=4) ioport:f050(size=8) ioport:f040(size=4) ioport:f020(size=32) memory:d0716000-d07167ff
        *-usb
             description: USB controller
             product: Atom Processor Z36xxx/Z37xxx, Celeron N2000 Series USB xHCI
             vendor: Intel Corporation
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 0c
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:91 memory:d0700000-d070ffff
           *-usbhost:0
                product: xHCI Host Controller
                vendor: Linux 5.8.0-44-generic xhci-hcd
                physical id: 0
                bus info: usb@1
                logical name: usb1
                version: 5.08
                capabilities: usb-2.00
                configuration: driver=hub slots=6 speed=480Mbit/s
              *-usb
                   description: USB hub
                   product: USB2.0 Hub
                   vendor: Genesys Logic, Inc.
                   physical id: 2
                   bus info: usb@1:2
                   version: 85.37
                   capabilities: usb-2.00
                   configuration: driver=hub maxpower=100mA slots=3 speed=480Mbit/s
           *-usbhost:1
                product: xHCI Host Controller
                vendor: Linux 5.8.0-44-generic xhci-hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 5.08
                capabilities: usb-3.00
                configuration: driver=hub slots=1 speed=5000Mbit/s
        *-generic
             description: Encryption controller
             product: Atom Processor Z36xxx/Z37xxx Series Trusted Execution Engine
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 0c
             width: 32 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei_txe latency=0
             resources: irq:95 memory:d0500000-d05fffff memory:d0400000-d04fffff
        *-multimedia
             description: Audio device
             product: Atom Processor Z36xxx/Z37xxx Series High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 0c
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:96 memory:d0710000-d0713fff
        *-pci:0
             description: PCI bridge
             product: Atom Processor E3800 Series PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 0c
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:87 ioport:1000(size=4096)
        *-pci:1
             description: PCI bridge
             product: Atom Processor E3800 Series PCI Express Root Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 0c
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:88 ioport:e000(size=4096) memory:d0600000-d06fffff
           *-network
                description: Ethernet interface
                product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: enp2s0
                version: 11
                serial: [REMOVED]
                size: 1Gbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=5.8.0-44-generic duplex=full firmware=rtl8168g-2_0.0.1 02/06/13 ip=[REMOVED] latency=0 link=yes multicast=yes port=MII speed=1Gbit/s
                resources: irq:17 ioport:e000(size=256) memory:d0604000-d0604fff memory:d0600000-d0603fff
        *-pci:2
             description: PCI bridge
             product: Atom Processor E3800 Series PCI Express Root Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 0c
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:89 ioport:2000(size=4096)
        *-pci:3
             description: PCI bridge
             product: Atom Processor E3800 Series PCI Express Root Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: 0c
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:90 ioport:3000(size=4096)
        *-isa
             description: ISA bridge
             product: Atom Processor Z36xxx/Z37xxx Series Power Control Unit
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 0c
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-serial
             description: SMBus
             product: Atom Processor E3800 Series SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 0c
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: driver=i801_smbus latency=0
             resources: irq:18 memory:d0714000-d071401f ioport:f000(size=32)
     *-pnp00:00
          product: PnP device PNP0b00
          physical id: 1
          capabilities: pnp
          configuration: driver=rtc_cmos
     *-pnp00:01
          product: PnP device PNP0c02
          physical id: 2
          capabilities: pnp
          configuration: driver=system
     *-pnp00:02
          product: PnP device PNP0c02
          physical id: 3
          capabilities: pnp
          configuration: driver=system
     *-pnp00:03
          product: PnP device PNP0400
          physical id: 4
          capabilities: pnp
          configuration: driver=parport_pc
     *-pnp00:04
          product: PnP device PNP0501
          physical id: 5
          capabilities: pnp
          configuration: driver=serial
     *-pnp00:05
          product: PnP device PNP0501
          physical id: 6
          capabilities: pnp
          configuration: driver=serial
     *-pnp00:06
          product: PnP device PNP0c02
          physical id: 7
          capabilities: pnp
          configuration: driver=system
     *-scsi:0
          physical id: 8
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: KINGSTON SV300S3
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: BBF0
             serial: [REMOVED]
             size: 111GiB (120GB)
             capabilities: gpt-1.00 partitioned partitioned:gpt
             configuration: ansiversion=5 guid=81ee0c35-8d76-46cf-8046-2c6c24b48acb logicalsectorsize=512 sectorsize=512
           *-volume:0
                description: Windows FAT volume
                vendor: mkfs.fat
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                logical name: /boot/efi
                version: FAT32
                serial: [REMOVED]
                size: 510MiB
                capacity: 511MiB
                capabilities: boot fat initialized
                configuration: FATs=2 filesystem=fat label=UEFI mount.fstype=vfat mount.options=rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro name=EFI System Partition state=mounted
           *-volume:1
                description: EXT4 volume
                vendor: Linux
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                logical name: /
                version: 1.0
                serial: [REMOVED]
                size: 30GiB
                capabilities: journaled extended_attributes large_files huge_files dir_nlink recover 64bit extents ext4 ext2 initialized
                configuration: created=2021-01-04 20:28:14 filesystem=ext4 lastmountpoint=/ modified=2021-01-04 20:59:45 mount.fstype=ext4 mount.options=rw,relatime mounted=2021-03-06 00:53:22 name=root state=mounted
           *-volume:2
                description: OS X ZFS partition or Solaris /usr partition
                vendor: Solaris
                physical id: 3
                bus info: scsi@0:0.0.0,3
                logical name: /dev/sda3
                serial: [REMOVED]
                capacity: 79GiB
                configuration: name=Solaris /usr & Mac ZFS
     *-scsi:1
          physical id: 9
          logical name: scsi1
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: WDC WD30EZRX-00M
             vendor: Western Digital
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/sdb
             version: 0A80
             serial: [REMOVED]
             size: 2794GiB (3TB)
             capabilities: gpt-1.00 partitioned partitioned:gpt
             configuration: ansiversion=5 guid=2b1d0253-3039-1240-b2bf-a3241670f547 logicalsectorsize=512 sectorsize=4096
           *-volume:0
                description: OS X ZFS partition or Solaris /usr partition
                vendor: Solaris
                physical id: 1
                bus info: scsi@1:0.0.0,1
                logical name: /dev/sdb1
                serial: [REMOVED]
                capacity: 2794GiB
                configuration: name=zfs-2ac91fd99ba76c71
           *-volume:1
                description: reserved partition
                vendor: Solaris
                physical id: 9
                bus info: scsi@1:0.0.0,9
                logical name: /dev/sdb9
                serial: [REMOVED]
                capacity: 8191KiB
  *-network
       description: Ethernet interface
       physical id: 1
       logical name: veth8eaf1df1
       serial: [REMOVED]
       size: 10Gbit/s
       capabilities: ethernet physical
       configuration: autonegotiation=off broadcast=yes driver=veth driverversion=1.0 duplex=full link=yes multicast=yes port=twisted pair speed=10Gbit/s
```
I can pastebin the logs if anyone feels it to be necessary, but they are massive and unrevealing, with different and unrelated processes being called before each lockup. The logging daemons always die along with the kernel.

I welcome hearing from all of you about your NC triumphs/travails and especially your implementation strategies/recommendations.

---

### Post by LHammonds on 2021-03-07
I only use LVM and ext4 so I have no ZFS-related recommendations.  I also do not use containers or LAMP stacks since I dedicated a server for database work separate from all other web services...which means I install NextCloud manually and not through a package (which forces a silo database).

Have you booted with a DVD and run health checks against the drives and RAM?  (I know you replaced RAM but the mobo connecting to the RAM might have issue so best to test it all)

It could be helpful to document what version you are using of Ubuntu Server, MariaDB, PHP and NextCloud.

LHammonds

---

### Post by TheFu on 2021-03-07
The entire machine is locking up?
or is it just the LXD container?
or is it just the Nextcloud webapp?

For troubleshooting, be certain the logs are persistent across reboots - whether that is the LXD or whole machine.
Is it safe to assume the RAM is all good?

I run nextcloud inside a KVM VM with an LVM LV provided as raw block storage to the VM.
My VM doesn't get nearly as many resources.
[LIST]
[*]vCPU = 1
[*]RAM = 1GB
[*]Storage:
```
$ df -Th
Filesystem                  Type      Size  Used Avail Use% Mounted on
/dev/vda1                   ext4       19G   11G  6.7G  62% / 
romulus:/raid/media/Music   nfs4      1.8T  1.7T  7.7G 100% /M
romulus:/export/www/gallery nfs4      151G  107G   36G  76% /P
istar:/d/D1/ebooks/Library  nfs4      3.5T  3.5T   44G  99% /B
```
[/LIST]
The NFS is all read-only, since I don't trust NC not to delete everything.

On that system, the real hardware is a dualCore Pentium G3258 ($50 in 2015). It runs no other VMs, but is the main NFS server for the network. Just moved from 16.04 to 18.04 last month for both the VM and the hostOS. Also installed the HWE kernel - so it runs 5.4.0-66-generic currently. Don't know why ZFS would be an issue, but I've never put a DBMS onto ZFS storage. I know that LXD really prefers ZFS be used.  I use it for my piholes running in LXD. No issues there.  I've considered moving my NC to LXD. Just never got around to it.

Upgraded to Nextcloud 20.0.8 last week.  A few of the addons didn't have compatible versions, but the most important ones did, so I moved from x.x.5. I've had to use the CLI upgrade process for over a year. The web 1-click updates always time out and fail.  I did force a php version upgrade last fall.   v21 of Nextcloud requires a new DBMS release. 
Before I make any upgrades, I create an LVM snapshot. If it doesn't go well, I just shutdown the system and revert to the snapshot. Instantaneously back to the pre-snapshot bits.  ZFS can do that too.  Of course, daily, automatic, backups happen ... er ... daily.
Some upgrades don't go cleanly. This is almost always due to DB table updates that weren't automatically run - don't forget to run those manually - or incompatible addons.  I need to create a safe SQL task to do what VACUUM does. Some of my addons will churn through thousands of new records every day.  The how-to for the addons often says how to reclaim the unused DBMS storage. I haven't seen similar for the NC tables.

Don't forget to clean up the pre-upgrade backups in $nc-data/updater-*/backups/  Every upgrade can eat 1G-3G of stuff there.  I check for updates about once every month or two. If the system were on the internet, I'd check weekly.  Nextcloud is LAN-only here. Remote access is only allowed via VPN or ssh-socks proxy.

Last week, the nextcloud log was growing to fill all available storage.  I keep NC data in /opt/, so a solution would be to just create another LV for the VM and mount it on /opt/.  That would make moving to a pre-package version easier.

Without logs of some sort, I don't know where to start.  
[LIST]
[*]dmesg
[*]syslog
[*]nextcloud.log
[/LIST]
Just the last 20 lines probably.

---

### Post by DuckHook on 2021-03-07
Thanks kindly @LHammonds @TheFu for your responses. I will have to delay posting logs until tonight. It's tax prep day today and I've promised The Boss that it will get done before any other project (else she'll send me to bed with no dinner).

Will likely pastebin them. They are massive in their raw state. Or would you prefer them prefiltered with "err", "warn", "fatal", etc?

---

### Post by TheFu on 2021-03-07
I wouldn't want more than the last 50 lines, only the interesting stuff, clearly labeled for which log goes which which system / host or container.
If the host is locking up, I don't think this is a container issue.  Can you recreate the problem without NC running?

---

### Post by DuckHook on 2021-03-08
> **LHammonds said:**
> Have you booted with a DVD
Not yet but will do so in the coming week.
> …and run health checks against the drives
Am now running: ```
smartctl -t long
```It's a 3 TB HDD. Will take overnight to complete.
> and RAM? (I know you replaced RAM but the mobo connecting to the RAM might have issue so best to test it all)
Will do a memtest as soon as smartctl finishes. There are 16GB so this also will take a while.
> It could be helpful to document what version you are using of Ubuntu Server, MariaDB, PHP and NextCloud
Of course. I should have posted this info at the start:

[list=1]
[*]Server:
```
duckhook@charon:~$ uname -a
Linux charon 5.8.0-44-generic #50~20.04.1-Ubuntu SMP Wed Feb 10 21:07:30 UTC 2021 x86_64 x86_64 x86_64 GNU/Linux
```
```
duckhook@charon:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 20.04.2 LTS
Release:	20.04
Codename:	focal
```
[*]Container:
```
ubuntu@next:~$ uname -a
Linux next 5.8.0-44-generic #50~20.04.1-Ubuntu SMP Wed Feb 10 21:07:30 UTC 2021 x86_64 x86_64 x86_64 GNU/Linux
```
```
ubuntu@next:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 20.04.2 LTS
Release:	20.04
Codename:	focal
```
[*]```
ubuntu@next:~$ dpkg -l | grep mariadb
ii  mariadb-client                 1:10.3.25-0ubuntu0.20.04.1        all          MariaDB database client (metapackage depending on the latest version)

```
[*]```
ubuntu@next:~$ dpkg -l | grep php
…
ii  php7.4                         7.4.3-4ubuntu2.4                  all          server-side, HTML-embedded scripting language (metapackage)
```
[*]```
ubuntu@next:~$ dpkg -l | grep apache2
ii  apache2                        2.4.41-4ubuntu3.1                 amd64        Apache HTTP Server
```
[*]```
ubuntu@next:~$ sudo -u www-data php /var/www/nextcloud/occ
Nextcloud 20.0.8
```
[/list]
Thanks so much, LHammonds. I always highly value your input.

---

### Post by DuckHook on 2021-03-08
> **TheFu said:**
> The entire machine is locking up?
Prior to confining the container to just two threads (of four), the entire server locked up. Even sysrq (REISUB) was helpless. Forced to do a hard power reset.
> or is it just the LXD container?
Post confinement, the container locked up but not the server. However, trying to kill the container was no go. Server continued to run, but shutdown would not complete. Final entries from server journalctl: ```
…
Mar 03 21:45:11 charon systemd[1]: Shutting down.
Mar 03 21:45:11 charon systemd-shutdown[1]: Syncing filesystems and block devices.
Mar 03 21:45:41 charon systemd-shutdown[1]: Syncing filesystems and block devices - timed out, issuing SIGKILL to PID 559769.
Mar 03 21:45:41 charon systemd-shutdown[1]: Sending SIGTERM to remaining processes...
Mar 03 21:45:41 charon systemd-journald[367]: Journal stopped
```
However, this time, sysrq did work because I still had an operable and semi-stable server, though I had to use the physical console as SSH had been shut down. The above hints at a filesystem/ZFS issue.
> or is it just the Nextcloud webapp?
Not just the webapp. As already described, on the last occasion, I could log into the container but could do nothing within it. I tried a variety of commands. All commands, even a simple cat /var/log/… resulted in blinking cursor forever. I could kill that process by SSH-ing into the server and killing the prior SSH process, but commands within the container were all broken.
> For troubleshooting, be certain the logs are persistent across reboots - whether that is the LXD or whole machine.
I believe this is already set to be so.
> Is it safe to assume the RAM is all good?
I was quite sure of this until LHammonds advised a doublecheck anyway. I intend to do so just to make sure, but memtest takes a long time. Cannot confirm that right away.
> I run nextcloud inside a KVM VM…
One of the options I have already thought about was to go the VM route after nixing ZFS. But I did not want to go there until I had chased down as many gremlins as I could.
> Don't forget to clean up the pre-upgrade backups in $nc-data/updater-*/backups/ Every upgrade can eat 1G-3G of stuff there.
Good advice. Thanks for the heads&#8209;up. As an infant just starting out with NC, this would not have occurred to me.
>  Nextcloud is LAN-only here. Remote access is only allowed via VPN or ssh-socks proxy.
I was aware of your high security bar with NC. I will think further on the security front after I get the damn thing shaken out and working properly. FWIW, I have fail2ban and firewalls fencing it in for now. The whole point in LXD was to add further containment. I might also go LHammond's route and segment the whole server off to its own VLAN. But this bear is only capable of chewing on one issue at a time.
> Without logs of some sort, I don't know where to start.
I'll need more time to reconstruct anything that would be useful to you. The last lockup occurred a few days ago and these days, with my mind like a sieve, I can't recall the precise time. I will have to parse the logs around an approximation of last lockup to post only relevant stuff, else I would be wasting your time.

Though Mrs DH has released me from tax prep purgatory, it's getting late here, so I will leave that for tomorrow's project.

Thanks so much for your always considerable care and help!

---

### Post by TheFu on 2021-03-08
5.8.0-44-generic 
Bleeding edge much?

Can you go back the a 5.4 kernel?  The interactions between ZFS, LXD and 5.8 kernels ... hummmm.
Which version of lxd?  I'm using 3.0.3 for my piholes. I have it set to stay stable - or at least I think I have that set. ;)

BTW, the best practice for running any container is to run them inside a VM.  Businesses run multiple containers inside the same VM, which reduces the total overhead that having separate VMs would incur.

---

### Post by LHammonds on 2021-03-08
> **DuckHook said:**
> 
```
Linux charon 5.8.0-44-generic
```

My 20.04.2 LTS machines are all on 5.4.0-66.  I wonder if the 5.8 kernel is the culprit.  If possible, run a 5.4 kernel and see if the lockups continue.

> **DuckHook said:**
> 
```
ubuntu@next:~$ dpkg -l | grep mariadb
ii  mariadb-client                 1:10.3.25-0ubuntu0.20.04.1        all          MariaDB database client (metapackage depending on the latest version)
```

I would expect to see about 7 or so mariadb entries here if you were running MariaDB as the database.  Are you instead running MySQL perhaps?

Try this command instead:
```
mysql --version
mysql  Ver 15.1 Distrib 10.4.18-MariaDB, for debian-linux-gnu (x86_64) using readline 5.2
```

**EDIT:** TheFu ninja'd me. LoL

LHammonds

---

### Post by TheFu on 2021-03-08
> **LHammonds said:**
>  
**EDIT:** TheFu ninja'd me. LoL


You usually ninja me with better answers. ;)

OTOH, I have been looking at my nextcloud VM and the php stuff is a mess.  Because I was lazy, I run Wallabag on it too which is also LAMP, but the required php versions have split over the years. Wish I'd kept them separate.  Thanks  DuckHook for pointing out my less-than-great setup. ;) Reminders of failures is always good.

It also runs ZNC, but that's perl which I know how to keep segmented as needed.

---

### Post by DuckHook on 2021-03-08
Top of the morning to the both of you (from where I am)!

I now feel a fool for not checking LHammond's recommendations earlier. :redface: smartctl identifies a likely culprit: ```
duckhook@charon:~$ sudo smartctl -l selftest /dev/sdb
smartctl 7.1 2019-12-30 r5022 [x86_64-linux-5.8.0-44-generic] (local build)
Copyright (C) 2002-19, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF READ SMART DATA SECTION ===
SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed: read failure       20%      2917         4028400592
# 2  Short offline       Completed without error       00%     47968         -
# 3  Short offline       Aborted by host               60%     18193         -
# 4  Short offline       Completed without error       00%     18119         -
# 5  Short offline       Completed without error       00%     18119         -
# 6  Short offline       Completed without error       00%     18108         -
# 7  Short offline       Completed without error       00%     18066         -

```
I had run short tests before, but it took the long test to identify a real problem. I had always suspected something to do with ZFS, but if there's an underlying HDD issue, then of course, this could manifest as a file system problem (duh).

> **LHammonds said:**
> I would expect to see about 7 or so mariadb entries here if you were running MariaDB as the database.  Are you instead running MySQL perhaps?
I thought you just wanted the version reference, so pruned the prior results before posting. Here's the full output:
```
ubuntu@next:~$ dpkg -l | grep mariadb
ii  mariadb-client                 1:10.3.25-0ubuntu0.20.04.1        all          MariaDB database client (metapackage depending on the latest version)
ii  mariadb-client-10.3            1:10.3.25-0ubuntu0.20.04.1        amd64        MariaDB database client binaries
ii  mariadb-client-core-10.3       1:10.3.25-0ubuntu0.20.04.1        amd64        MariaDB database core client binaries
ii  mariadb-common                 1:10.3.25-0ubuntu0.20.04.1        all          MariaDB common metapackage
ii  mariadb-server                 1:10.3.25-0ubuntu0.20.04.1        all          MariaDB database server (metapackage depending on the latest version)
ii  mariadb-server-10.3            1:10.3.25-0ubuntu0.20.04.1        amd64        MariaDB database server binaries
ii  mariadb-server-core-10.3       1:10.3.25-0ubuntu0.20.04.1        amd64        MariaDB database core server files

```
> **TheFu said:**
> 5.8.0-44-generic 
Bleeding edge much?

Can you go back the a 5.4 kernel?
> **LHammonds said:**
> &#8230;I wonder if the 5.8 kernel is the culprit.
I did start out with the standard 5.4 kernel. It was when the lockups started that one of my gambits was to try the HWE kernel. Easy to revert, but since the problems started under the stabler kernel, I didn't think it a priority for now. Sorry&#8230; should'a clarified that at the outset.
> **TheFu said:**
> &#8230;Which version of lxd?
```
duckhook@charon:~$ sudo snap list lxd
Name  Version  Rev    Tracking       Publisher   Notes
lxd   4.11     19566  latest/stable  canonical&#10003;  -

```
I'm going to replace the HDD, then rebuild NC from scratch. Obviously, this will take some time, and it's turning out to be a full day ahead, so it may possibly be tomorrow before you hear back from me.

As always, thanks to the both of you for your expertise and guidance.

---

### Post by TheFu on 2021-03-08
Were it me, I'd replace the hdd/ssd then restore everything from backups.  Should take 45 min, at most.  Plus it is good to test the restores when the risks are zero.

The only thing I'd do if it isn't already done, would be to have a separate partition/LV for the NC-Data storage.

All the other stuff I posted was just guesses. The failing storage seems to be the issue.

---

### Post by DuckHook on 2021-03-08
> **TheFu said:**
> Were it me, I'd replace the hdd/ssd then restore everything from backups.  Should take 45 min, at most.  Plus it is good to test the restores when the risks are zero.

The only thing I'd do if it isn't already done, would be to have a separate partition/LV for the NC-Data storage.

All the other stuff I posted was just guesses. The failing storage seems to be the issue.
Thanks for the recommendations. I've already restored a few times, so know that they work. But there are other infrastructural changes I want to make—like your excellent suggestion to hive nc-data off entirely to it's own partition—that make more sense with a new build. I'm not DB-savvy enough to link/redirect all of the persnickty pointers to the new location, and the last thing I want are further unrelated failure points that will obfuscate the original problem. I think it better to do a rebuild that I know to be clean. But I appreciate the thought you are putting into this on my behalf. O:)

---

### Post by TheFu on 2021-03-08
It isn't the DBMS files. It is everything else:

Maybe this will help:
```
$ ll /opt/nc-data/
total 329464
drwxrwx---  9 www-data www-data      4096 Mar  7 06:26 ./
drwxr-xr-x  4 root     root          4096 Feb 20  2017 ../
drwxr-xr-x  5 www-data www-data      4096 Dec 17  2017 Ann/
drwxr-xr-x  5 www-data www-data      4096 Dec 17  2017 Dave/
drwxr-xr-x  5 www-data www-data      4096 Dec 17  2017 Don/
drwxr-xr-x  5 www-data www-data      4096 Dec 17  2017 Jim/
drwxr-xr-x  5 www-data www-data      4096 Dec 17  2017 Joanie/
drwxr-xr-x  5 www-data www-data      4096 Dec 17  2017 Julia/
drwxr-xr-x  5 www-data www-data      4096 Dec 17  2017 Kay/
drwxr-xr-x  5 www-data www-data      4096 Dec 17  2017 Eileen/
drwxr-xr-x  5 www-data www-data      4096 Dec 17  2017 Mike/
drwxr-xr-x  5 www-data www-data      4096 Dec 17  2017 Pete/
drwxr-xr-x  5 www-data www-data      4096 Dec 17  2017 Samatha/
drwxr-xr-x  5 www-data www-data      4096 Dec 17  2017 Thomas/
drwxr-xr-x  8 www-data www-data      4096 May  8  2020 thefu/
drwxr-xr-x 16 www-data www-data      4096 Jan  2 17:53 appdata_xyz1234kjsdiwerrandom/
-rw-r-----  1 www-data www-data   2167804 Mar  8 14:03 audit.log
-rw-r-----  1 www-data www-data  11441937 Mar  2 02:06 audit.log.1.gz
drwxr-xr-x  2 www-data www-data      4096 Mar  2 10:52 files_external/
drwxr-xr-x  2 www-data www-data      4096 Jan 26  2019 gpxpod/
-rw-r--r--  1 www-data www-data       542 Mar  2 10:52 .htaccess
-rw-r--r--  1 www-data www-data         0 Mar  2 10:52 index.html
drwxr-x---  4 www-data www-data      4096 Sep 14  2018 news/
-rw-r-----  1 www-data www-data  67400452 Mar  8 14:03 nextcloud.log
-rw-r-----  1 www-data www-data 255761227 Mar  7 06:26 nextcloud.log.1
-rw-rw-r--  1 www-data www-data         0 Mar  2 10:52 .ocdata
-rw-r--r--  1 www-data www-data      1928 Feb  7  2017 update.log
-rw-r--r--  1 www-data www-data    503925 Mar  2 10:54 updater.log
drwxr-xr-x  4 www-data www-data      4096 Mar  2 10:53 updater-xyz1234kjsdiwerrandom/
```

That's the NC-Data directory.  I think there are just 1-2 places in the nc init file with it.  I'll check.  Only 1.
```
/var/www/html/nextcloud/config$ egrep '/opt/nc-data' *
config.php:  'datadirectory' => '/opt/nc-data',

```
Rock on!

---

### Post by DuckHook on 2021-03-09
> **TheFu said:**
> It isn't the DBMS files. It is everything else:

Maybe this will help:
&#8230;
Rock on!
My backups do not remotely approach your levels of finesse. I just do a weekly export of the entire container (it's not that big and is easily done in ZFS) to an eight week rotation of 1.5 TB USB drives&#8212;overkill, but so absurdly cheap these days ($40 each at Costco) that&#8230; well, what the heck?

Being weekly, they aren't as fine grained as yours, but as a retired couple, our NC instance is no more than a convenient repository for phone photos, some songs, news feeds and the odd file. Nothing is of earth&#8209;shattering importance. There are multiple redundancies already in play and the photos and songs are duplicated separately on yet another pair of mirrored servers anyway. The calendar/contacts/notes stuff is a bit more unique/time sensitive but again, as a retired couple we don't exactly live a life of hazard and high drama. Nothing much changes in a week.

Of course, if I open the NC instance up to friends and family, I may have to implement backups closer to your level, but it is the prospect of shouldering such responsibilities that acts as a brake on my ambitions.

It was [this quasi&#8209;official HowTo]("https://help.nextcloud.com/t/howto-change-move-data-directory-after-installation/17170/9") that had me deciding to reinstall from scratch, especially the following bit in big black freaking bold print: > **Changing data directory after installation is not officially supported. Consider re-installing Nextcloud with new data directory, if you did not use it too much/added users/created shares/tags/comments etc.**&#8230;that last part describes me to a "T", so why tempt fate?

***UPDATE:***

I lied. Rather than rebuild from scratch, I got horribly lazy and took the export &#8594; switch HDD &#8594; import route. Not ideal because if the problem is in the container build, then I've just packed it up and brought it along. I'm gambling that the problem was a bad HDD, in which case, a smoothly working clone would be confirmation. If it fails with the new HDD, next step will be building from scratch. So far, so good, but that's not saying much: it's always taken a few days for the gremlins to emerge.

I'm parking this thread for now. Should the new HW run problem free for more than a week, I will consider the matter solved and come back to mark it as such. Until then, I guess I will have to compose myself in patience.

I'm sounding like a broken record, but many thanks to the two of you for your kindness, time and help.

---

### Post by DuckHook on 2021-03-16
A week has passed with no further issues. The problem was clearly a bad HDD. Solved!

---

