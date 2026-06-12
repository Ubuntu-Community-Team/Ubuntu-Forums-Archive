---
title: "Ubuntu Server 14.04 Java/Minecraft entire server crash problem"
date: 2014-12-08
forum: Server Platforms
---

### Post by Erlpil on 2014-12-08
I have an issue with an Ubuntu 14.04 server. I am running a Minecraft network, which uses java. The server works fine for around 12 to 18 hours before it shuts the entire Ubuntu server down. I have tired to change the version of Java, formatting the server with a clean Ubuntu 14.04 server install with no luck. It can crash when there is no one using the minecraft network and the system is almost not demanding any data power from components.


This server used to run a windows server for several months with no errors. The problems started when Ubuntu 14.04 was installed.


The solution as of now is to reboot the server every 12 hours to make sure it does not crash. It’s worth noting that this is a server rented at a hosting company.


Does anyone know what causes these crashes, or know a way to prevent them so my server can stay online without needing a reboot every 12 hours?

*I have made the company name anonymous in the log.*

Server specifications:
```
System:    Host: companyname-Ubuntu-1404 Kernel: 3.13.0-36-generic x86_64 (64 bit, gcc: 4.8.2) 
           Console: tty 0 Distro: Ubuntu 14.04 trusty
Machine:   Mobo: MSI model: H87-G43 (MS-7816) version: 1.0 Bios: American Megatrends version: V2.14B6 date: 08/23/2013
CPU:       Quad core Intel Core i7-4770 CPU (-HT-MCP-) cache: 8192 KB flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 27200.8 
           Clock Speeds: 1: 3805.875 MHz 2: 3805.875 MHz 3: 3752.750 MHz 4: 3699.625 MHz 5: 3699.625 MHz 6: 3805.875 MHz 7: 3752.750 MHz 8: 3752.750 MHz
Graphics:  Card: Intel Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller bus-ID: 00:02.0 
           X-Vendor: N/A driver: N/A tty size: 270x76 Advanced Data: N/A for root out of X
Network:   Card: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller 
           driver: r8169 ver: 2.3LK-NAPI port: e000 bus-ID: 02:00.0
           IF: eth0 state: up speed: 1000 Mbps duplex: full mac: <filter>
Drives:    HDD Total Size: 480.1GB (5.5% used) 1: id: /dev/sda model: INTEL_SSDSC2CW24 size: 240.1GB temp: 0C 
           2: id: /dev/sdb model: INTEL_SSDSC2CW24 size: 240.1GB temp: 0C 
Partition: ID: / size: 204G used: 25G (13%) fs: ext4 ID: /boot size: 488M used: 39M (9%) fs: ext3 
           ID: swap-1 size: 17.17GB used: 0.00GB (0%) fs: swap 
RAID:      Device-1: /dev/md2 - active components: online: sdb3[1] sda3[0]
           Info: raid: 1 report: 2/2 blocks: 216994240 chunk size: N/A
           Device-2: /dev/md0 - active components: online: sdb1[1] sda1[0]
           Info: raid: 1 report: 2/2 blocks: 16768896 chunk size: N/A
           Device-3: /dev/md1 - active components: online: sdb2[1] sda2[0]
           Info: raid: 1 report: 2/2 blocks: 523968 chunk size: N/A
Sensors:   System Temperatures: cpu: 29.8C mobo: 27.8C 
           Fan Speeds (in rpm): cpu: N/A 
Info:      Processes: 186 Uptime: 1:20 Memory: 18162.0/32039.2MB Runlevel: 2 Gcc sys: N/A 
           Client: Shell (bash 4.3.11) inxi: 1.9.17 
```



Java version:
```
java version "1.8.0_25"
Java(TM) SE Runtime Environment (build 1.8.0_25-b17)
Java HotSpot(TM) 64-Bit Server VM (build 25.25-b02, mixed mode)
```


System log:
```
Dec  8 00:08:14 companyname-Ubuntu-1404 dbus[505]: [system] Reloaded configuration
Dec  8 00:17:01 companyname-Ubuntu-1404 CRON[15465]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Dec  8 01:06:18 companyname-Ubuntu-1404 rsyslogd: [origin software="rsyslogd" swVersion="7.4.4" x-pid="561" x-info="http://www.rsyslog.com"] exiting on signal 15.
Dec  8 01:06:57 companyname-Ubuntu-1404 rsyslogd: [origin software="rsyslogd" swVersion="7.4.4" x-pid="586" x-info="http://www.rsyslog.com"] start
Dec  8 01:06:57 companyname-Ubuntu-1404 rsyslogd: rsyslogd's groupid changed to 104
Dec  8 01:06:57 companyname-Ubuntu-1404 rsyslogd: rsyslogd's userid changed to 101
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] Initializing cgroup subsys cpuset
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] Initializing cgroup subsys cpu
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] Initializing cgroup subsys cpuacct
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] Linux version 3.13.0-36-generic (buildd@toyol) (gcc version 4.8.2 (Ubuntu 4.8.2-19ubuntu1) ) #63-Ubuntu SMP Wed Sep 3 21:30:07 UTC 2014 (Ubuntu 3.13.0-36.63-generic 3.13.11.6)
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] Command line: BOOT_IMAGE=/vmlinuz-3.13.0-36-generic root=UUID=33347b6f-1460-4085-855b-4bba83e35b42 ro nomodeset intel_pstate=enable nomdmonddf nomdmonisw
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] KERNEL supported cpus:
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000]   Intel GenuineIntel
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000]   AMD AuthenticAMD
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000]   Centaur CentaurHauls
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] e820: BIOS-provided physical RAM map:
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009d7ff] usable
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] BIOS-e820: [mem 0x000000000009d800-0x000000000009ffff] reserved
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000c6989fff] usable
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] BIOS-e820: [mem 0x00000000c698a000-0x00000000c6990fff] ACPI NVS
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] BIOS-e820: [mem 0x00000000c6991000-0x00000000c6dd6fff] usable
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] BIOS-e820: [mem 0x00000000c6dd7000-0x00000000c7367fff] reserved
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] BIOS-e820: [mem 0x00000000c7368000-0x00000000d8dacfff] usable
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] BIOS-e820: [mem 0x00000000d8dad000-0x00000000d8e36fff] reserved
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] BIOS-e820: [mem 0x00000000d8e37000-0x00000000d8e90fff] usable
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] BIOS-e820: [mem 0x00000000d8e91000-0x00000000d8fc8fff] ACPI NVS
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] BIOS-e820: [mem 0x00000000d8fc9000-0x00000000d9ffefff] reserved
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] BIOS-e820: [mem 0x00000000d9fff000-0x00000000d9ffffff] usable
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] BIOS-e820: [mem 0x00000000db000000-0x00000000df1fffff] reserved
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] BIOS-e820: [mem 0x00000000f8000000-0x00000000fbffffff] reserved
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] BIOS-e820: [mem 0x00000000fed00000-0x00000000fed03fff] reserved
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] BIOS-e820: [mem 0x00000000fed1c000-0x00000000fed1ffff] reserved
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] BIOS-e820: [mem 0x00000000ff000000-0x00000000ffffffff] reserved
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000081edfffff] usable
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] NX (Execute Disable) protection: active
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] SMBIOS 2.7 present.
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] DMI: MSI MS-7816/H87-G43 (MS-7816), BIOS V2.14B6 08/23/2013
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] No AGP bridge found
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] e820: last_pfn = 0x81ee00 max_arch_pfn = 0x400000000
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] MTRR default type: uncachable
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] MTRR fixed ranges enabled:
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000]   00000-9FFFF write-back
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000]   A0000-BFFFF uncachable
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000]   C0000-CFFFF write-protect
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000]   D0000-E7FFF uncachable
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000]   E8000-FFFFF write-protect
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] MTRR variable ranges enabled:
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000]   0 base 0000000000 mask 7800000000 write-back
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000]   1 base 0800000000 mask 7FE0000000 write-back
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000]   2 base 00E0000000 mask 7FE0000000 uncachable
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000]   3 base 00DC000000 mask 7FFC000000 uncachable
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000]   4 base 00DB000000 mask 7FFF000000 uncachable
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000]   5 base 081F000000 mask 7FFF000000 uncachable
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000]   6 base 081EE00000 mask 7FFFE00000 uncachable
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000]   7 disabled
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000]   8 disabled
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000]   9 disabled
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] original variable MTRRs
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] reg 0, base: 0GB, range: 32GB, type WB
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] reg 1, base: 32GB, range: 512MB, type WB
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] reg 2, base: 3584MB, range: 512MB, type UC
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] reg 3, base: 3520MB, range: 64MB, type UC
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] reg 4, base: 3504MB, range: 16MB, type UC
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] reg 5, base: 33264MB, range: 16MB, type UC
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] reg 6, base: 33262MB, range: 2MB, type UC
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] total RAM covered: 32670M
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000]  gran_size: 64K     chunk_size: 64K     num_reg: 10      lose cover RAM: 238M
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000]  gran_size: 64K     chunk_size: 128K     num_reg: 10      lose cover RAM: 238M
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000]  gran_size: 64K     chunk_size: 256K     num_reg: 10      lose cover RAM: 238M
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000]  gran_size: 64K     chunk_size: 512K     num_reg: 10      lose cover RAM: 238M
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000]  gran_size: 64K     chunk_size: 1M     num_reg: 10      lose cover RAM: 238M
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000]  gran_size: 64K     chunk_size: 2M     num_reg: 10      lose cover RAM: 238M
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000]  gran_size: 64K     chunk_size: 4M     num_reg: 10      lose cover RAM: 238M
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000]  gran_size: 64K     chunk_size: 8M     num_reg: 10      lose cover RAM: 238M
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000]  gran_size: 64K     chunk_size: 16M     num_reg: 10      lose cover RAM: 238M
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] *BAD*gran_size: 64K     chunk_size: 32M     num_reg: 10      lose cover RAM: -18M
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] *BAD*gran_size: 64K     chunk_size: 64M     num_reg: 10      lose cover RAM: -18M
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] *BAD*gran_size: 64K     chunk_size: 128M     num_reg: 10      lose cover RAM: -16M
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] *BAD*gran_size: 64K     chunk_size: 256M     num_reg: 10      lose cover RAM: -16M
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] *BAD*gran_size: 64K     chunk_size: 512M     num_reg: 10      lose cover RAM: -16M
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] *BAD*gran_size: 64K     chunk_size: 1G     num_reg: 10      lose cover RAM: -512M
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] *BAD*gran_size: 64K     chunk_size: 2G     num_reg: 10      lose cover RAM: -1536M
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000]  gran_size: 128K     chunk_size: 128K     num_reg: 10      lose cover RAM: 238M
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000]  gran_size: 128K     chunk_size: 256K     num_reg: 10      lose cover RAM: 238M
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000]  gran_size: 128K     chunk_size: 512K     num_reg: 10      lose cover RAM: 238M
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000]  gran_size: 128K     chunk_size: 1M     num_reg: 10      lose cover RAM: 238M
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000]  gran_size: 128K     chunk_size: 2M     num_reg: 10      lose cover RAM: 238M
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000]  gran_size: 128K     chunk_size: 4M     num_reg: 10      lose cover RAM: 238M
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000]  gran_size: 128K     chunk_size: 8M     num_reg: 10      lose cover RAM: 238M
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000]  gran_size: 128K     chunk_size: 16M     num_reg: 10      lose cover RAM: 238M
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] *BAD*gran_size: 128K     chunk_size: 32M     num_reg: 10      lose cover RAM: -18M
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] *BAD*gran_size: 128K     chunk_size: 64M     num_reg: 10      lose cover RAM: -18M
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] *BAD*gran_size: 128K     chunk_size: 128M     num_reg: 10      lose cover RAM: -16M
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] *BAD*gran_size: 128K     chunk_size: 256M     num_reg: 10      lose cover RAM: -16M
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] *BAD*gran_size: 128K     chunk_size: 512M     num_reg: 10      lose cover RAM: -16M
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] *BAD*gran_size: 128K     chunk_size: 1G     num_reg: 10      lose cover RAM: -512M
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] *BAD*gran_size: 128K     chunk_size: 2G     num_reg: 10      lose cover RAM: -1536M
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000]  gran_size: 256K     chunk_size: 256K     num_reg: 10      lose cover RAM: 238M
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000]  gran_size: 256K     chunk_size: 512K     num_reg: 10      lose cover RAM: 238M
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000]  gran_size: 256K     chunk_size: 1M     num_reg: 10      lose cover RAM: 238M
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000]  gran_size: 256K     chunk_size: 2M     num_reg: 10      lose cover RAM: 238M
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000]  gran_size: 256K     chunk_size: 4M     num_reg: 10      lose cover RAM: 238M
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000]  gran_size: 256K     chunk_size: 8M     num_reg: 10      lose cover RAM: 238M
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000]  gran_size: 256K     chunk_size: 16M     num_reg: 10      lose cover RAM: 238M
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] *BAD*gran_size: 256K     chunk_size: 32M     num_reg: 10      lose cover RAM: -18M
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] *BAD*gran_size: 256K     chunk_size: 64M     num_reg: 10      lose cover RAM: -18M
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] *BAD*gran_size: 256K     chunk_size: 128M     num_reg: 10      lose cover RAM: -16M
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] *BAD*gran_size: 256K     chunk_size: 256M     num_reg: 10      lose cover RAM: -16M
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] *BAD*gran_size: 256K     chunk_size: 512M     num_reg: 10      lose cover RAM: -16M
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] *BAD*gran_size: 256K     chunk_size: 1G     num_reg: 10      lose cover RAM: -512M
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] *BAD*gran_size: 256K     chunk_size: 2G     num_reg: 10      lose cover RAM: -1536M
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000]  gran_size: 512K     chunk_size: 512K     num_reg: 10      lose cover RAM: 238M
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000]  gran_size: 512K     chunk_size: 1M     num_reg: 10      lose cover RAM: 238M
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000]  gran_size: 512K     chunk_size: 2M     num_reg: 10      lose cover RAM: 238M
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000]  gran_size: 512K     chunk_size: 4M     num_reg: 10      lose cover RAM: 238M
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000]  gran_size: 512K     chunk_size: 8M     num_reg: 10      lose cover RAM: 238M
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000]  gran_size: 512K     chunk_size: 16M     num_reg: 10      lose cover RAM: 238M
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] *BAD*gran_size: 512K     chunk_size: 32M     num_reg: 10      lose cover RAM: -18M
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] *BAD*gran_size: 512K     chunk_size: 64M     num_reg: 10      lose cover RAM: -18M
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] *BAD*gran_size: 512K     chunk_size: 128M     num_reg: 10      lose cover RAM: -16M
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] *BAD*gran_size: 512K     chunk_size: 256M     num_reg: 10      lose cover RAM: -16M
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] *BAD*gran_size: 512K     chunk_size: 512M     num_reg: 10      lose cover RAM: -16M
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] *BAD*gran_size: 512K     chunk_size: 1G     num_reg: 10      lose cover RAM: -512M
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] *BAD*gran_size: 512K     chunk_size: 2G     num_reg: 10      lose cover RAM: -1536M
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000]  gran_size: 1M     chunk_size: 1M     num_reg: 10      lose cover RAM: 238M
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000]  gran_size: 1M     chunk_size: 2M     num_reg: 10      lose cover RAM: 238M
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000]  gran_size: 1M     chunk_size: 4M     num_reg: 10      lose cover RAM: 238M
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000]  gran_size: 1M     chunk_size: 8M     num_reg: 10      lose cover RAM: 238M
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000]  gran_size: 1M     chunk_size: 16M     num_reg: 10      lose cover RAM: 238M
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] *BAD*gran_size: 1M     chunk_size: 32M     num_reg: 10      lose cover RAM: -18M
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] *BAD*gran_size: 1M     chunk_size: 64M     num_reg: 10      lose cover RAM: -18M
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] *BAD*gran_size: 1M     chunk_size: 128M     num_reg: 10      lose cover RAM: -16M
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] *BAD*gran_size: 1M     chunk_size: 256M     num_reg: 10      lose cover RAM: -16M
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] *BAD*gran_size: 1M     chunk_size: 512M     num_reg: 10      lose cover RAM: -16M
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] *BAD*gran_size: 1M     chunk_size: 1G     num_reg: 10      lose cover RAM: -512M
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] *BAD*gran_size: 1M     chunk_size: 2G     num_reg: 10      lose cover RAM: -1536M
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000]  gran_size: 2M     chunk_size: 2M     num_reg: 10      lose cover RAM: 238M
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000]  gran_size: 2M     chunk_size: 4M     num_reg: 10      lose cover RAM: 238M
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000]  gran_size: 2M     chunk_size: 8M     num_reg: 10      lose cover RAM: 238M
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000]  gran_size: 2M     chunk_size: 16M     num_reg: 10      lose cover RAM: 238M
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] *BAD*gran_size: 2M     chunk_size: 32M     num_reg: 10      lose cover RAM: -18M
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] *BAD*gran_size: 2M     chunk_size: 64M     num_reg: 10      lose cover RAM: -18M
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] *BAD*gran_size: 2M     chunk_size: 128M     num_reg: 10      lose cover RAM: -16M
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] *BAD*gran_size: 2M     chunk_size: 256M     num_reg: 10      lose cover RAM: -16M
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] *BAD*gran_size: 2M     chunk_size: 512M     num_reg: 10      lose cover RAM: -16M
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] *BAD*gran_size: 2M     chunk_size: 1G     num_reg: 10      lose cover RAM: -512M
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] *BAD*gran_size: 2M     chunk_size: 2G     num_reg: 10      lose cover RAM: -1536M
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000]  gran_size: 4M     chunk_size: 4M     num_reg: 10      lose cover RAM: 238M
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000]  gran_size: 4M     chunk_size: 8M     num_reg: 10      lose cover RAM: 238M
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000]  gran_size: 4M     chunk_size: 16M     num_reg: 10      lose cover RAM: 238M
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] *BAD*gran_size: 4M     chunk_size: 32M     num_reg: 10      lose cover RAM: -18M
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] *BAD*gran_size: 4M     chunk_size: 64M     num_reg: 10      lose cover RAM: -18M
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] *BAD*gran_size: 4M     chunk_size: 128M     num_reg: 10      lose cover RAM: -14M
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] *BAD*gran_size: 4M     chunk_size: 256M     num_reg: 10      lose cover RAM: -14M
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] *BAD*gran_size: 4M     chunk_size: 512M     num_reg: 10      lose cover RAM: -14M
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] *BAD*gran_size: 4M     chunk_size: 1G     num_reg: 10      lose cover RAM: -510M
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] *BAD*gran_size: 4M     chunk_size: 2G     num_reg: 10      lose cover RAM: -1534M
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000]  gran_size: 8M     chunk_size: 8M     num_reg: 10      lose cover RAM: 238M
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000]  gran_size: 8M     chunk_size: 16M     num_reg: 10      lose cover RAM: 238M
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] *BAD*gran_size: 8M     chunk_size: 32M     num_reg: 10      lose cover RAM: -18M
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] *BAD*gran_size: 8M     chunk_size: 64M     num_reg: 10      lose cover RAM: -18M
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] *BAD*gran_size: 8M     chunk_size: 128M     num_reg: 10      lose cover RAM: -10M
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] *BAD*gran_size: 8M     chunk_size: 256M     num_reg: 10      lose cover RAM: -10M
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] *BAD*gran_size: 8M     chunk_size: 512M     num_reg: 10      lose cover RAM: -10M
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] *BAD*gran_size: 8M     chunk_size: 1G     num_reg: 10      lose cover RAM: -506M
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] *BAD*gran_size: 8M     chunk_size: 2G     num_reg: 10      lose cover RAM: -1530M
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000]  gran_size: 16M     chunk_size: 16M     num_reg: 10      lose cover RAM: 238M
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000]  gran_size: 16M     chunk_size: 32M     num_reg: 10      lose cover RAM: 238M
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] *BAD*gran_size: 16M     chunk_size: 64M     num_reg: 10      lose cover RAM: -18M
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000]  gran_size: 16M     chunk_size: 128M     num_reg: 10      lose cover RAM: 14M
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000]  gran_size: 16M     chunk_size: 256M     num_reg: 10      lose cover RAM: 14M
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000]  gran_size: 16M     chunk_size: 512M     num_reg: 10      lose cover RAM: 14M
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000]  gran_size: 16M     chunk_size: 1G     num_reg: 10      lose cover RAM: 14M
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] *BAD*gran_size: 16M     chunk_size: 2G     num_reg: 10      lose cover RAM: -1010M
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000]  gran_size: 32M     chunk_size: 32M     num_reg: 10      lose cover RAM: 126M
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] *BAD*gran_size: 32M     chunk_size: 64M     num_reg: 10      lose cover RAM: -2M
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000]  gran_size: 32M     chunk_size: 128M     num_reg: 10      lose cover RAM: 30M
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000]  gran_size: 32M     chunk_size: 256M     num_reg: 10      lose cover RAM: 30M
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000]  gran_size: 32M     chunk_size: 512M     num_reg: 10      lose cover RAM: 30M
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000]  gran_size: 32M     chunk_size: 1G     num_reg: 10      lose cover RAM: 30M
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] *BAD*gran_size: 32M     chunk_size: 2G     num_reg: 10      lose cover RAM: -994M
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000]  gran_size: 64M     chunk_size: 64M     num_reg: 10      lose cover RAM: 94M
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000]  gran_size: 64M     chunk_size: 128M     num_reg: 9      lose cover RAM: 94M
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000]  gran_size: 64M     chunk_size: 256M     num_reg: 9      lose cover RAM: 94M
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000]  gran_size: 64M     chunk_size: 512M     num_reg: 9      lose cover RAM: 94M
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000]  gran_size: 64M     chunk_size: 1G     num_reg: 9      lose cover RAM: 94M
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000]  gran_size: 64M     chunk_size: 2G     num_reg: 10      lose cover RAM: 94M
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000]  gran_size: 128M     chunk_size: 128M     num_reg: 9      lose cover RAM: 158M
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000]  gran_size: 128M     chunk_size: 256M     num_reg: 9      lose cover RAM: 158M
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000]  gran_size: 128M     chunk_size: 512M     num_reg: 9      lose cover RAM: 158M
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000]  gran_size: 128M     chunk_size: 1G     num_reg: 9      lose cover RAM: 158M
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000]  gran_size: 128M     chunk_size: 2G     num_reg: 10      lose cover RAM: 158M
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000]  gran_size: 256M     chunk_size: 256M     num_reg: 7      lose cover RAM: 414M
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000]  gran_size: 256M     chunk_size: 512M     num_reg: 9      lose cover RAM: 414M
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000]  gran_size: 256M     chunk_size: 1G     num_reg: 9      lose cover RAM: 414M
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000]  gran_size: 256M     chunk_size: 2G     num_reg: 10      lose cover RAM: 414M
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000]  gran_size: 512M     chunk_size: 512M     num_reg: 5      lose cover RAM: 926M
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000]  gran_size: 512M     chunk_size: 1G     num_reg: 5      lose cover RAM: 926M
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000]  gran_size: 512M     chunk_size: 2G     num_reg: 5      lose cover RAM: 926M
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000]  gran_size: 1G     chunk_size: 1G     num_reg: 5      lose cover RAM: 926M
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000]  gran_size: 1G     chunk_size: 2G     num_reg: 5      lose cover RAM: 926M
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000]  gran_size: 2G     chunk_size: 2G     num_reg: 4      lose cover RAM: 1950M
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] mtrr_cleanup: can not find optimal value
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] please specify mtrr_gran_size/mtrr_chunk_size
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] e820: update [mem 0xdb000000-0xffffffff] usable ==> reserved
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] e820: last_pfn = 0xda000 max_arch_pfn = 0x400000000
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] found SMP MP-table at [mem 0x000fd720-0x000fd72f] mapped at [ffff8800000fd720]
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] Scanning 1 areas for low memory corruption
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] Base memory trampoline at [ffff880000097000] 97000 size 24576
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] Using GB pages for direct mapping
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000]  [mem 0x00000000-0x000fffff] page 4k
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] BRK [0x01fdf000, 0x01fdffff] PGTABLE
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] BRK [0x01fe0000, 0x01fe0fff] PGTABLE
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] BRK [0x01fe1000, 0x01fe1fff] PGTABLE
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] init_memory_mapping: [mem 0x81ec00000-0x81edfffff]
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000]  [mem 0x81ec00000-0x81edfffff] page 2M
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] BRK [0x01fe2000, 0x01fe2fff] PGTABLE
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] init_memory_mapping: [mem 0x81c000000-0x81ebfffff]
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000]  [mem 0x81c000000-0x81ebfffff] page 2M
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] init_memory_mapping: [mem 0x800000000-0x81bffffff]
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000]  [mem 0x800000000-0x81bffffff] page 2M
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] init_memory_mapping: [mem 0x00100000-0xc6989fff]
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000]  [mem 0x00100000-0x001fffff] page 4k
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000]  [mem 0x00200000-0x3fffffff] page 2M
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000]  [mem 0x40000000-0xbfffffff] page 1G
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000]  [mem 0xc0000000-0xc67fffff] page 2M
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000]  [mem 0xc6800000-0xc6989fff] page 4k
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] init_memory_mapping: [mem 0xc6991000-0xc6dd6fff]
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000]  [mem 0xc6991000-0xc69fffff] page 4k
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000]  [mem 0xc6a00000-0xc6bfffff] page 2M
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000]  [mem 0xc6c00000-0xc6dd6fff] page 4k
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] BRK [0x01fe3000, 0x01fe3fff] PGTABLE
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] init_memory_mapping: [mem 0xc7368000-0xd8dacfff]
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000]  [mem 0xc7368000-0xc73fffff] page 4k
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000]  [mem 0xc7400000-0xd8bfffff] page 2M
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000]  [mem 0xd8c00000-0xd8dacfff] page 4k
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] BRK [0x01fe4000, 0x01fe4fff] PGTABLE
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] init_memory_mapping: [mem 0xd8e37000-0xd8e90fff]
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000]  [mem 0xd8e37000-0xd8e90fff] page 4k
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] init_memory_mapping: [mem 0xd9fff000-0xd9ffffff]
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000]  [mem 0xd9fff000-0xd9ffffff] page 4k
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] init_memory_mapping: [mem 0x100000000-0x7ffffffff]
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000]  [mem 0x100000000-0x7ffffffff] page 1G
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] RAMDISK: [mem 0x3586e000-0x36c2efff]
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] ACPI: RSDP 00000000000f0490 000024 (v02 ALASKA)
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] ACPI: XSDT 00000000d8f99080 000084 (v01 ALASKA    A M I 01072009 AMI  00010013)
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] ACPI: FACP 00000000d8fa8178 00010C (v05 ALASKA    A M I 01072009 AMI  00010013)
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] ACPI: DSDT 00000000d8f991a0 00EFD1 (v02 ALASKA    A M I 00000028 INTL 20120711)
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] ACPI: FACS 00000000d8fc7080 000040
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] ACPI: APIC 00000000d8fa8288 000092 (v03 ALASKA    A M I 01072009 AMI  00010013)
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] ACPI: FPDT 00000000d8fa8320 000044 (v01 ALASKA    A M I 01072009 AMI  00010013)
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] ACPI: LPIT 00000000d8fa8368 00005C (v01 ALASKA    A M I 00000000 AMI. 00000005)
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] ACPI: SSDT 00000000d8fa83c8 000539 (v01  PmRef  Cpu0Ist 00003000 INTL 20120711)
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] ACPI: SSDT 00000000d8fa8908 000AD8 (v01  PmRef    CpuPm 00003000 INTL 20120711)
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] ACPI: MCFG 00000000d8fa93e0 00003C (v01 ALASKA    A M I 01072009 MSFT 00000097)
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] ACPI: HPET 00000000d8fa9420 000038 (v01 ALASKA    A M I 01072009 AMI. 00000005)
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] ACPI: SSDT 00000000d8fa9458 00036D (v01 SataRe SataTabl 00001000 INTL 20120711)
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] ACPI: SSDT 00000000d8fa97c8 003406 (v01 SaSsdt  SaSsdt  00003000 INTL 20091112)
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] ACPI: ASF! 00000000d8facbd0 0000A5 (v32 INTEL       HCG 00000001 TFSM 000F4240)
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] ACPI: DMAR 00000000d8facc78 0000B8 (v01 INTEL      HSW  00000001 INTL 00000001)
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] No NUMA configuration found
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] Faking a node at [mem 0x0000000000000000-0x000000081edfffff]
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] Initmem setup node 0 [mem 0x00000000-0x81edfffff]
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000]   NODE_DATA [mem 0x81edf6000-0x81edfafff]
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000]  [ffffea0000000000-ffffea00207fffff] PMD -> [ffff8807fe400000-ffff88081e3fffff] on node 0
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] Zone ranges:
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000]   DMA      [mem 0x00001000-0x00ffffff]
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000]   Normal   [mem 0x100000000-0x81edfffff]
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] Movable zone start for each node
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] Early memory node ranges
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000]   node   0: [mem 0x00001000-0x0009cfff]
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000]   node   0: [mem 0x00100000-0xc6989fff]
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000]   node   0: [mem 0xc6991000-0xc6dd6fff]
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000]   node   0: [mem 0xc7368000-0xd8dacfff]
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000]   node   0: [mem 0xd8e37000-0xd8e90fff]
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000]   node   0: [mem 0xd9fff000-0xd9ffffff]
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000]   node   0: [mem 0x100000000-0x81edfffff]
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] On node 0 totalpages: 8353292
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000]   DMA zone: 64 pages used for memmap
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000]   DMA zone: 21 pages reserved
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000]   DMA zone: 3996 pages, LIFO batch:0
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000]   DMA32 zone: 13794 pages used for memmap
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000]   DMA32 zone: 882800 pages, LIFO batch:31
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000]   Normal zone: 116664 pages used for memmap
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000]   Normal zone: 7466496 pages, LIFO batch:31
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1808
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x04] enabled)
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x06] enabled)
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x01] enabled)
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x03] enabled)
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x05] enabled)
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x07] enabled)
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0xff] high edge lint[0x1])
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] ACPI: IRQ0 used by override.
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] ACPI: IRQ2 used by override.
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] ACPI: IRQ9 used by override.
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] ACPI: HPET id: 0x8086a701 base: 0xfed00000
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] smpboot: Allowing 8 CPUs, 0 hotplug CPUs
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] nr_irqs_gsi: 40
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009d000-0x0009dfff]
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009e000-0x0009ffff]
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dffff]
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000e0000-0x000fffff]
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] PM: Registered nosave memory: [mem 0xc698a000-0xc6990fff]
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] PM: Registered nosave memory: [mem 0xc6dd7000-0xc7367fff]
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] PM: Registered nosave memory: [mem 0xd8dad000-0xd8e36fff]
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] PM: Registered nosave memory: [mem 0xd8e91000-0xd8fc8fff]
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] PM: Registered nosave memory: [mem 0xd8fc9000-0xd9ffefff]
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] PM: Registered nosave memory: [mem 0xda000000-0xdaffffff]
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] PM: Registered nosave memory: [mem 0xdb000000-0xdf1fffff]
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] PM: Registered nosave memory: [mem 0xdf200000-0xf7ffffff]
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] PM: Registered nosave memory: [mem 0xf8000000-0xfbffffff]
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfc000000-0xfebfffff]
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xfec00fff]
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec01000-0xfecfffff]
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed00000-0xfed03fff]
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed04000-0xfed1bfff]
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed1c000-0xfed1ffff]
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed20000-0xfedfffff]
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfee00000-0xfee00fff]
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfee01000-0xfeffffff]
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] PM: Registered nosave memory: [mem 0xff000000-0xffffffff]
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] e820: [mem 0xdf200000-0xf7ffffff] available for PCI devices
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:8 nr_node_ids:1
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] PERCPU: Embedded 29 pages/cpu @ffff88081ea00000 s86336 r8192 d24256 u262144
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] pcpu-alloc: s86336 r8192 d24256 u262144 alloc=1*2097152
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 8222749
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] Policy zone: Normal
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/vmlinuz-3.13.0-36-generic root=UUID=33347b6f-1460-4085-855b-4bba83e35b42 ro nomodeset intel_pstate=enable nomdmonddf nomdmonisw
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] xsave: enabled xstate_bv 0x7, cntxt size 0x340
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] Checking aperture...
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] No AGP bridge found
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] Calgary: detecting Calgary via BIOS EBDA area
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] Memory: 32785008K/33413168K available (7373K kernel code, 1144K rwdata, 3404K rodata, 1336K init, 1440K bss, 628160K reserved)
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] Hierarchical RCU implementation.
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000]     RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=8.
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000]     Offload RCU callbacks from all CPUs
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000]     Offload RCU callbacks from CPUs: 0-7.
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] NR_IRQS:16640 nr_irqs:744 16
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] Console: colour VGA+ 80x25
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] console [tty0] enabled
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] allocated 134217728 bytes of page_cgroup
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] hpet clockevent registered
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000000] tsc: Fast TSC calibration using PIT
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.004000] tsc: Detected 3400.030 MHz processor
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000002] Calibrating delay loop (skipped), value calculated using timer frequency.. 6800.06 BogoMIPS (lpj=13600120)
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000107] pid_max: default: 32768 minimum: 301
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000172] Security Framework initialized
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000234] AppArmor: AppArmor initialized
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.000284] Yama: becoming mindful.
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.001664] Dentry cache hash table entries: 4194304 (order: 13, 33554432 bytes)
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.005773] Inode-cache hash table entries: 2097152 (order: 12, 16777216 bytes)
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.007555] Mount-cache hash table entries: 65536 (order: 7, 524288 bytes)
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.007632] Mountpoint-cache hash table entries: 65536 (order: 7, 524288 bytes)
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.007913] Initializing cgroup subsys memory
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.007966] Initializing cgroup subsys devices
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.008017] Initializing cgroup subsys freezer
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.008068] Initializing cgroup subsys blkio
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.008118] Initializing cgroup subsys perf_event
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.008170] Initializing cgroup subsys hugetlb
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.008235] CPU: Physical Processor ID: 0
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.008285] CPU: Processor Core ID: 0
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.009074] mce: CPU supports 9 MCE banks
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.009134] CPU0: Thermal monitoring enabled (TM1)
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.009193] Last level iTLB entries: 4KB 0, 2MB 0, 4MB 0
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.009193] Last level dTLB entries: 4KB 64, 2MB 0, 4MB 0
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.009193] tlb_flushall_shift: 6
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.009356] Freeing SMP alternatives memory: 32K (ffffffff81e6d000 - ffffffff81e75000)
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.010097] ACPI: Core revision 20131115
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.015127] ACPI: All ACPI Tables successfully acquired
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.023727] ftrace: allocating 28537 entries in 112 pages
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.032006] dmar: Host address width 39
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.032056] dmar: DRHD base: 0x000000fed90000 flags: 0x0
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.032112] dmar: IOMMU 0: reg_base_addr fed90000 ver 1:0 cap c0000020660462 ecap f0101a
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.032179] dmar: DRHD base: 0x000000fed91000 flags: 0x1
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.032234] dmar: IOMMU 1: reg_base_addr fed91000 ver 1:0 cap d2008020660462 ecap f010da
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.032301] dmar: RMRR base: 0x000000d9ea8000 end: 0x000000d9eb6fff
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.032355] dmar: RMRR base: 0x000000db000000 end: 0x000000df1fffff
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.032471] IOAPIC id 2 under DRHD base  0xfed91000 IOMMU 1
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.032523] HPET id 0 under DRHD base 0xfed91000
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.032679] Enabled IRQ remapping in x2apic mode
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.032730] Enabling x2apic
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.032778] Enabled x2apic
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.032828] Switched APIC routing to cluster x2apic.
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.033276] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.072989] smpboot: CPU0: Intel(R) Core(TM) i7-4770 CPU @ 3.40GHz (fam: 06, model: 3c, stepping: 03)
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.073157] TSC deadline timer enabled
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.073163] Performance Events: PEBS fmt2+, 16-deep LBR, Haswell events, full-width counters, Intel PMU driver.
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.073393] ... version:                3
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.073443] ... bit width:              48
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.073493] ... generic registers:      4
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.073542] ... value mask:             0000ffffffffffff
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.073594] ... max period:             0000ffffffffffff
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.073646] ... fixed-purpose events:   3
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.073695] ... event mask:             000000070000000f
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.074779] x86: Booting SMP configuration:
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.088697] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.074830] .... node  #0, CPUs:      #1 #2 #3 #4 #5 #6 #7
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.171829] x86: Booted up 1 node, 8 CPUs
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.171924] smpboot: Total of 8 processors activated (54400.48 BogoMIPS)
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.178509] devtmpfs: initialized
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.180857] EVM: security.selinux
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.180906] EVM: security.SMACK64
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.180954] EVM: security.ima
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.181002] EVM: security.capability
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.181079] PM: Registering ACPI NVS region [mem 0xc698a000-0xc6990fff] (28672 bytes)
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.181149] PM: Registering ACPI NVS region [mem 0xd8e91000-0xd8fc8fff] (1277952 bytes)
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.181681] pinctrl core: initialized pinctrl subsystem
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.181767] regulator-dummy: no parameters
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.181841] RTC time:  0:06:51, date: 12/08/14
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.181912] NET: Registered protocol family 16
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.182023] cpuidle: using governor ladder
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.182072] cpuidle: using governor menu
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.182146] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.182214] ACPI: bus type PCI registered
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.182264] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.182354] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf8000000-0xfbffffff] (base 0xf8000000)
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.182425] PCI: MMCONFIG at [mem 0xf8000000-0xfbffffff] reserved in E820
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.186686] PCI: Using configuration type 1 for base access
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.187417] bio: create slab <bio-0> at 0
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.187565] ACPI: Added _OSI(Module Device)
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.187616] ACPI: Added _OSI(Processor Device)
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.187666] ACPI: Added _OSI(3.0 _SCP Extensions)
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.187717] ACPI: Added _OSI(Processor Aggregator Device)
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.190215] ACPI: Executed 1 blocks of module-level executable AML code
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.191932] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.194408] ACPI: SSDT 00000000d8e2cc18 0003D3 (v01  PmRef  Cpu0Cst 00003001 INTL 20120711)
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.194823] ACPI: Dynamic OEM Table Load:
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.194935] ACPI: SSDT           (null) 0003D3 (v01  PmRef  Cpu0Cst 00003001 INTL 20120711)
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.198505] ACPI: SSDT 00000000d8e2c618 0005AA (v01  PmRef    ApIst 00003000 INTL 20120711)
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.198965] ACPI: Dynamic OEM Table Load:
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.199079] ACPI: SSDT           (null) 0005AA (v01  PmRef    ApIst 00003000 INTL 20120711)
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.202397] ACPI: SSDT 00000000d8e2bd98 000119 (v01  PmRef    ApCst 00003000 INTL 20120711)
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.202810] ACPI: Dynamic OEM Table Load:
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.202923] ACPI: SSDT           (null) 000119 (v01  PmRef    ApCst 00003000 INTL 20120711)
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.207115] ACPI: Interpreter enabled
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.207168] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20131115/hwxface-580)
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.207304] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20131115/hwxface-580)
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.207445] ACPI: (supports S0 S3 S4 S5)
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.207495] ACPI: Using IOAPIC for interrupt routing
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.207563] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.209197] ACPI: No dock devices found.
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.214199] ACPI: Power Resource [FN00] (off)
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.214290] ACPI: Power Resource [FN01] (off)
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.214380] ACPI: Power Resource [FN02] (off)
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.214468] ACPI: Power Resource [FN03] (off)
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.214555] ACPI: Power Resource [FN04] (off)
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.215063] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-3e])
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.215119] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.215330] acpi PNP0A08:00: _OSC: platform does not support [PCIeHotplug PME]
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.215470] acpi PNP0A08:00: _OSC: OS now controls [AER PCIeCapability]
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.215856] PCI host bridge to bus 0000:00
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.215907] pci_bus 0000:00: root bus resource [bus 00-3e]
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.215960] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.216014] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.216067] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.216122] pci_bus 0000:00: root bus resource [mem 0x000d0000-0x000d3fff]
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.216176] pci_bus 0000:00: root bus resource [mem 0x000d4000-0x000d7fff]
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.216231] pci_bus 0000:00: root bus resource [mem 0x000d8000-0x000dbfff]
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.216286] pci_bus 0000:00: root bus resource [mem 0x000dc000-0x000dffff]
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.216341] pci_bus 0000:00: root bus resource [mem 0x000e0000-0x000e3fff]
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.216395] pci_bus 0000:00: root bus resource [mem 0x000e4000-0x000e7fff]
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.216450] pci_bus 0000:00: root bus resource [mem 0xdf200000-0xfeafffff]
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.216509] pci 0000:00:00.0: [8086:0c00] type 00 class 0x060000
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.216563] pci 0000:00:02.0: [8086:0412] type 00 class 0x030000
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.216570] pci 0000:00:02.0: reg 0x10: [mem 0xf7800000-0xf7bfffff 64bit]
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.216575] pci 0000:00:02.0: reg 0x18: [mem 0xe0000000-0xefffffff 64bit pref]
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.216578] pci 0000:00:02.0: reg 0x20: [io  0xf000-0xf03f]
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.216644] pci 0000:00:14.0: [8086:8c31] type 00 class 0x0c0330
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.216660] pci 0000:00:14.0: reg 0x10: [mem 0xf7c00000-0xf7c0ffff 64bit]
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.216711] pci 0000:00:14.0: PME# supported from D3hot D3cold
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.216737] pci 0000:00:14.0: System wakeup disabled by ACPI
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.216810] pci 0000:00:16.0: [8086:8c3a] type 00 class 0x078000
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.216827] pci 0000:00:16.0: reg 0x10: [mem 0xf7c16000-0xf7c1600f 64bit]
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.216881] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.216934] pci 0000:00:1a.0: [8086:8c2d] type 00 class 0x0c0320
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.216951] pci 0000:00:1a.0: reg 0x10: [mem 0xf7c14000-0xf7c143ff]
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.217029] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.217066] pci 0000:00:1a.0: System wakeup disabled by ACPI
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.217136] pci 0000:00:1c.0: [8086:8c10] type 01 class 0x060400
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.217191] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.217220] pci 0000:00:1c.0: System wakeup disabled by ACPI
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.217290] pci 0000:00:1c.1: [8086:8c12] type 01 class 0x060400
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.217344] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.217373] pci 0000:00:1c.1: System wakeup disabled by ACPI
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.217443] pci 0000:00:1c.3: [8086:244e] type 01 class 0x060401
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.217497] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.217526] pci 0000:00:1c.3: System wakeup disabled by ACPI
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.217603] pci 0000:00:1d.0: [8086:8c26] type 00 class 0x0c0320
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.217620] pci 0000:00:1d.0: reg 0x10: [mem 0xf7c13000-0xf7c133ff]
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.217695] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.217731] pci 0000:00:1d.0: System wakeup disabled by ACPI
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.217804] pci 0000:00:1f.0: [8086:8c4a] type 00 class 0x060100
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.217934] pci 0000:00:1f.2: [8086:8c02] type 00 class 0x010601
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.217946] pci 0000:00:1f.2: reg 0x10: [io  0xf0b0-0xf0b7]
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.217952] pci 0000:00:1f.2: reg 0x14: [io  0xf0a0-0xf0a3]
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.217958] pci 0000:00:1f.2: reg 0x18: [io  0xf090-0xf097]
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.217964] pci 0000:00:1f.2: reg 0x1c: [io  0xf080-0xf083]
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.217970] pci 0000:00:1f.2: reg 0x20: [io  0xf060-0xf07f]
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.217977] pci 0000:00:1f.2: reg 0x24: [mem 0xf7c12000-0xf7c127ff]
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.218008] pci 0000:00:1f.2: PME# supported from D3hot
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.218046] pci 0000:00:1f.3: [8086:8c22] type 00 class 0x0c0500
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.218058] pci 0000:00:1f.3: reg 0x10: [mem 0xf7c11000-0xf7c110ff 64bit]
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.218075] pci 0000:00:1f.3: reg 0x20: [io  0xf040-0xf05f]
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.218170] acpiphp: Slot [1] registered
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.218223] pci 0000:00:1c.0: PCI bridge to [bus 01]
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.218341] pci 0000:02:00.0: [10ec:8168] type 00 class 0x020000
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.218356] pci 0000:02:00.0: reg 0x10: [io  0xe000-0xe0ff]
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.218383] pci 0000:02:00.0: reg 0x18: [mem 0xf0004000-0xf0004fff 64bit pref]
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.218399] pci 0000:02:00.0: reg 0x20: [mem 0xf0000000-0xf0003fff 64bit pref]
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.218469] pci 0000:02:00.0: supports D1 D2
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.218470] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.218497] pci 0000:02:00.0: System wakeup disabled by ACPI
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.226615] pci 0000:00:1c.1: PCI bridge to [bus 02]
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.226668] pci 0000:00:1c.1:   bridge window [io  0xe000-0xefff]
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.226673] pci 0000:00:1c.1:   bridge window [mem 0xf0000000-0xf00fffff 64bit pref]
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.226739] pci 0000:03:00.0: [1b21:1080] type 01 class 0x060400
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.226856] pci 0000:03:00.0: supports D1 D2
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.226857] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.226884] pci 0000:03:00.0: System wakeup disabled by ACPI
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.234609] pci 0000:00:1c.3: PCI bridge to [bus 03-04] (subtractive decode)
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.234669] pci 0000:00:1c.3:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.234670] pci 0000:00:1c.3:   bridge window [io  0x0d00-0xffff] (subtractive decode)
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.234671] pci 0000:00:1c.3:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.234672] pci 0000:00:1c.3:   bridge window [mem 0x000d0000-0x000d3fff] (subtractive decode)
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.234673] pci 0000:00:1c.3:   bridge window [mem 0x000d4000-0x000d7fff] (subtractive decode)
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.234674] pci 0000:00:1c.3:   bridge window [mem 0x000d8000-0x000dbfff] (subtractive decode)
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.234675] pci 0000:00:1c.3:   bridge window [mem 0x000dc000-0x000dffff] (subtractive decode)
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.234676] pci 0000:00:1c.3:   bridge window [mem 0x000e0000-0x000e3fff] (subtractive decode)
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.234677] pci 0000:00:1c.3:   bridge window [mem 0x000e4000-0x000e7fff] (subtractive decode)
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.234678] pci 0000:00:1c.3:   bridge window [mem 0xdf200000-0xfeafffff] (subtractive decode)
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.234800] pci 0000:03:00.0: PCI bridge to [bus 04]
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.234891] acpi PNP0A08:00: Disabling ASPM (FADT indicates it is unsupported)
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.235438] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 10 *11 12 14 15)
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.235868] ACPI: PCI Interrupt Link [LNKB] (IRQs *3 4 5 6 10 11 12 14 15)
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.236296] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 *10 11 12 14 15)
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.236723] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 *10 11 12 14 15)
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.237150] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.237655] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.238159] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.238665] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 10 *11 12 14 15)
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.239299] ACPI: Enabled 6 GPEs in block 00 to 3F
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.239416] ACPI: \_SB_.PCI0: notify handler is installed
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.239458] Found 1 acpi root devices
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.239509] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.239579] vgaarb: loaded
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.239626] vgaarb: bridge control possible 0000:00:02.0
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.239765] SCSI subsystem initialized
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.239840] libata version 3.00 loaded.
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.239850] ACPI: bus type USB registered
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.239907] usbcore: registered new interface driver usbfs
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.239963] usbcore: registered new interface driver hub
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.240035] usbcore: registered new device driver usb
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.240146] PCI: Using ACPI for IRQ routing
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.241380] PCI: pci_cache_line_size set to 64 bytes
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.241417] e820: reserve RAM buffer [mem 0x0009d800-0x0009ffff]
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.241418] e820: reserve RAM buffer [mem 0xc698a000-0xc7ffffff]
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.241419] e820: reserve RAM buffer [mem 0xc6dd7000-0xc7ffffff]
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.241419] e820: reserve RAM buffer [mem 0xd8dad000-0xdbffffff]
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.241420] e820: reserve RAM buffer [mem 0xd8e91000-0xdbffffff]
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.241421] e820: reserve RAM buffer [mem 0xda000000-0xdbffffff]
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.241422] e820: reserve RAM buffer [mem 0x81ee00000-0x81fffffff]
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.241464] NetLabel: Initializing
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.241513] NetLabel:  domain hash size = 128
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.241563] NetLabel:  protocols = UNLABELED CIPSOv4
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.241621] NetLabel:  unlabeled traffic allowed by default
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.241705] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.242043] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.244118] Switched to clocksource hpet
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.246780] AppArmor: AppArmor Filesystem Enabled
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.246840] pnp: PnP ACPI init
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.246892] ACPI: bus type PNP registered
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.246975] system 00:00: [mem 0xfed40000-0xfed44fff] has been reserved
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.247031] system 00:00: Plug and Play ACPI device, IDs PNP0c01 (active)
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.247037] pnp 00:01: [dma 4]
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.247043] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.247053] pnp 00:02: Plug and Play ACPI device, IDs INT0800 (active)
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.247122] pnp 00:03: Plug and Play ACPI device, IDs PNP0103 (active)
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.247150] pnp 00:04: Plug and Play ACPI device, IDs PNP0c04 (active)
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.247208] system 00:05: [io  0x0680-0x069f] has been reserved
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.247262] system 00:05: [io  0xffff] has been reserved
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.247314] system 00:05: [io  0xffff] has been reserved
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.247366] system 00:05: [io  0xffff] has been reserved
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.247418] system 00:05: [io  0x1c00-0x1cfe] has been reserved
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.247472] system 00:05: [io  0x1d00-0x1dfe] has been reserved
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.247525] system 00:05: [io  0x1e00-0x1efe] has been reserved
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.247578] system 00:05: [io  0x1f00-0x1ffe] has been reserved
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.247632] system 00:05: [io  0x1800-0x18fe] could not be reserved
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.247686] system 00:05: [io  0x164e-0x164f] has been reserved
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.247739] system 00:05: Plug and Play ACPI device, IDs PNP0c02 (active)
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.247753] pnp 00:06: Plug and Play ACPI device, IDs PNP0b00 (active)
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.247774] system 00:07: [io  0x1854-0x1857] has been reserved
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.247827] system 00:07: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.247885] system 00:08: [io  0x0a00-0x0a0f] has been reserved
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.247938] system 00:08: [io  0x0a10-0x0a1f] has been reserved
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.247992] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.248015] pnp 00:09: Plug and Play ACPI device, IDs PNP0303 PNP030b (active)
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.248102] pnp 00:0a: [dma 0 disabled]
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.248132] pnp 00:0a: Plug and Play ACPI device, IDs PNP0501 (active)
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.248275] pnp 00:0b: [dma 0 disabled]
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.248325] pnp 00:0b: Plug and Play ACPI device, IDs PNP0400 (active)
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.248347] system 00:0c: [io  0x04d0-0x04d1] has been reserved
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.248401] system 00:0c: Plug and Play ACPI device, IDs PNP0c02 (active)
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.248645] system 00:0d: [mem 0xfed1c000-0xfed1ffff] has been reserved
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.248700] system 00:0d: [mem 0xfed10000-0xfed17fff] has been reserved
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.248754] system 00:0d: [mem 0xfed18000-0xfed18fff] has been reserved
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.248809] system 00:0d: [mem 0xfed19000-0xfed19fff] has been reserved
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.248863] system 00:0d: [mem 0xf8000000-0xfbffffff] has been reserved
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.248918] system 00:0d: [mem 0xfed20000-0xfed3ffff] has been reserved
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.248972] system 00:0d: [mem 0xfed90000-0xfed93fff] could not be reserved
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.249028] system 00:0d: [mem 0xfed45000-0xfed8ffff] has been reserved
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.249082] system 00:0d: [mem 0xff000000-0xffffffff] has been reserved
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.249137] system 00:0d: [mem 0xfee00000-0xfeefffff] could not be reserved
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.249192] system 00:0d: [mem 0xf7fdf000-0xf7fdffff] has been reserved
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.249246] system 00:0d: [mem 0xf7fe0000-0xf7feffff] has been reserved
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.249301] system 00:0d: Plug and Play ACPI device, IDs PNP0c02 (active)
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.249431] pnp: PnP ACPI: found 14 devices
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.249481] ACPI: bus type PNP unregistered
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.255090] pci 0000:00:1c.0: bridge window [io  0x1000-0x0fff] to [bus 01] add_size 1000
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.255092] pci 0000:00:1c.0: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 01] add_size 200000
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.255093] pci 0000:00:1c.0: bridge window [mem 0x00100000-0x000fffff] to [bus 01] add_size 200000
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.255116] pci 0000:00:1c.0: res[14]=[mem 0x00100000-0x000fffff] get_res_add_size add_size 200000
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.255117] pci 0000:00:1c.0: res[15]=[mem 0x00100000-0x000fffff 64bit pref] get_res_add_size add_size 200000
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.255118] pci 0000:00:1c.0: res[13]=[io  0x1000-0x0fff] get_res_add_size add_size 1000
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.255120] pci 0000:00:1c.0: BAR 14: assigned [mem 0xdf200000-0xdf3fffff]
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.255176] pci 0000:00:1c.0: BAR 15: assigned [mem 0xdf400000-0xdf5fffff 64bit pref]
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.255244] pci 0000:00:1c.0: BAR 13: assigned [io  0x2000-0x2fff]
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.255298] pci 0000:00:1c.0: PCI bridge to [bus 01]
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.255350] pci 0000:00:1c.0:   bridge window [io  0x2000-0x2fff]
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.255406] pci 0000:00:1c.0:   bridge window [mem 0xdf200000-0xdf3fffff]
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.255462] pci 0000:00:1c.0:   bridge window [mem 0xdf400000-0xdf5fffff 64bit pref]
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.255533] pci 0000:00:1c.1: PCI bridge to [bus 02]
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.255586] pci 0000:00:1c.1:   bridge window [io  0xe000-0xefff]
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.255643] pci 0000:00:1c.1:   bridge window [mem 0xf0000000-0xf00fffff 64bit pref]
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.255714] pci 0000:03:00.0: PCI bridge to [bus 04]
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.255780] pci 0000:00:1c.3: PCI bridge to [bus 03-04]
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.255839] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.255840] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.255841] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.255842] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000d3fff]
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.255843] pci_bus 0000:00: resource 8 [mem 0x000d4000-0x000d7fff]
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.255844] pci_bus 0000:00: resource 9 [mem 0x000d8000-0x000dbfff]
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.255845] pci_bus 0000:00: resource 10 [mem 0x000dc000-0x000dffff]
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.255846] pci_bus 0000:00: resource 11 [mem 0x000e0000-0x000e3fff]
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.255847] pci_bus 0000:00: resource 12 [mem 0x000e4000-0x000e7fff]
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.255847] pci_bus 0000:00: resource 13 [mem 0xdf200000-0xfeafffff]
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.255848] pci_bus 0000:01: resource 0 [io  0x2000-0x2fff]
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.255849] pci_bus 0000:01: resource 1 [mem 0xdf200000-0xdf3fffff]
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.255850] pci_bus 0000:01: resource 2 [mem 0xdf400000-0xdf5fffff 64bit pref]
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.255851] pci_bus 0000:02: resource 0 [io  0xe000-0xefff]
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.255852] pci_bus 0000:02: resource 2 [mem 0xf0000000-0xf00fffff 64bit pref]
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.255853] pci_bus 0000:03: resource 4 [io  0x0000-0x0cf7]
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.255854] pci_bus 0000:03: resource 5 [io  0x0d00-0xffff]
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.255855] pci_bus 0000:03: resource 6 [mem 0x000a0000-0x000bffff]
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.255856] pci_bus 0000:03: resource 7 [mem 0x000d0000-0x000d3fff]
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.255857] pci_bus 0000:03: resource 8 [mem 0x000d4000-0x000d7fff]
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.255858] pci_bus 0000:03: resource 9 [mem 0x000d8000-0x000dbfff]
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.255858] pci_bus 0000:03: resource 10 [mem 0x000dc000-0x000dffff]
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.255859] pci_bus 0000:03: resource 11 [mem 0x000e0000-0x000e3fff]
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.255860] pci_bus 0000:03: resource 12 [mem 0x000e4000-0x000e7fff]
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.255861] pci_bus 0000:03: resource 13 [mem 0xdf200000-0xfeafffff]
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.255877] NET: Registered protocol family 2
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.256075] TCP established hash table entries: 262144 (order: 9, 2097152 bytes)
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.256383] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.256534] TCP: Hash tables configured (established 262144 bind 65536)
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.256598] TCP: reno registered
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.256668] UDP hash table entries: 16384 (order: 7, 524288 bytes)
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.256787] UDP-Lite hash table entries: 16384 (order: 7, 524288 bytes)
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.256919] NET: Registered protocol family 1
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.256975] pci 0000:00:02.0: Boot video device
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.257260] PCI: CLS 64 bytes, default 64
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.257290] Trying to unpack rootfs image as initramfs...
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.463520] Freeing initrd memory: 20228K (ffff88003586e000 - ffff880036c2f000)
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.463594] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.463649] software IO TLB [mem 0xd4dad000-0xd8dad000] (64MB) mapped at [ffff8800d4dad000-ffff8800d8dacfff]
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.463889] microcode: CPU0 sig=0x306c3, pf=0x2, revision=0x12
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.463947] microcode: CPU1 sig=0x306c3, pf=0x2, revision=0x12
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.464008] microcode: CPU2 sig=0x306c3, pf=0x2, revision=0x12
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.464065] microcode: CPU3 sig=0x306c3, pf=0x2, revision=0x12
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.464123] microcode: CPU4 sig=0x306c3, pf=0x2, revision=0x12
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.464180] microcode: CPU5 sig=0x306c3, pf=0x2, revision=0x12
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.464237] microcode: CPU6 sig=0x306c3, pf=0x2, revision=0x12
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.464295] microcode: CPU7 sig=0x306c3, pf=0x2, revision=0x12
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.464375] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.464445] Scanning for low memory corruption every 60 seconds
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.464657] Initialise system trusted keyring
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.464732] audit: initializing netlink socket (disabled)
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.464790] type=2000 audit(1417997211.448:1): initialized
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.482457] HugeTLB registered 2 MB page size, pre-allocated 0 pages
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.483441] zbud: loaded
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.483576] VFS: Disk quotas dquot_6.5.2
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.483648] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.483921] fuse init (API version 7.22)
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.484019] msgmni has been set to 32768
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.484097] Key type big_key registered
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.484459] Key type asymmetric registered
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.484510] Asymmetric key parser 'x509' registered
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.484575] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.484675] io scheduler noop registered
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.484727] io scheduler deadline registered (default)
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.484789] io scheduler cfq registered
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.485042] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.485101] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.485177] intel_idle: MWAIT substates: 0x42120
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.485178] intel_idle: v0.4 model 0x3C
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.485179] intel_idle: lapic_timer_reliable_states 0xffffffff
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.485281] ipmi message handler version 39.2
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.485374] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.485445] ACPI: Power Button [PWRB]
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.485511] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.485578] ACPI: Power Button [PWRF]
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.485660] ACPI: Fan [FAN0] (off)
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.485720] ACPI: Fan [FAN1] (off)
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.485781] ACPI: Fan [FAN2] (off)
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.485840] ACPI: Fan [FAN3] (off)
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.485902] ACPI: Fan [FAN4] (off)
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.486192] thermal LNXTHERM:00: registered as thermal_zone0
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.486246] ACPI: Thermal Zone [TZ00] (28 C)
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.486411] thermal LNXTHERM:01: registered as thermal_zone1
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.486463] ACPI: Thermal Zone [TZ01] (30 C)
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.486526] GHES: HEST is not enabled!
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.486631] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.507039] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4, base_baud = 115200) is a 16550A
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.509370] Linux agpgart interface v0.103
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.510069] brd: module loaded
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.510445] loop: module loaded
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.510679] libphy: Fixed MDIO Bus: probed
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.510771] tun: Universal TUN/TAP device driver, 1.6
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.510823] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.510898] PPP generic driver version 2.4.2
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.510969] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.511025] ehci-pci: EHCI PCI platform driver
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.511142] ehci-pci 0000:00:1a.0: EHCI Host Controller
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.511197] ehci-pci 0000:00:1a.0: new USB bus registered, assigned bus number 1
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.511274] ehci-pci 0000:00:1a.0: debug port 2
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.515221] ehci-pci 0000:00:1a.0: cache line size of 64 is not supported
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.515235] ehci-pci 0000:00:1a.0: irq 16, io mem 0xf7c14000
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.523963] ehci-pci 0000:00:1a.0: USB 2.0 started, EHCI 1.00
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.524047] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.524102] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.524168] usb usb1: Product: EHCI Host Controller
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.524220] usb usb1: Manufacturer: Linux 3.13.0-36-generic ehci_hcd
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.524273] usb usb1: SerialNumber: 0000:00:1a.0
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.524378] hub 1-0:1.0: USB hub found
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.524431] hub 1-0:1.0: 2 ports detected
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.524588] ehci-pci 0000:00:1d.0: EHCI Host Controller
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.524641] ehci-pci 0000:00:1d.0: new USB bus registered, assigned bus number 2
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.524717] ehci-pci 0000:00:1d.0: debug port 2
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.528670] ehci-pci 0000:00:1d.0: cache line size of 64 is not supported
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.528682] ehci-pci 0000:00:1d.0: irq 23, io mem 0xf7c13000
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.539952] ehci-pci 0000:00:1d.0: USB 2.0 started, EHCI 1.00
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.540027] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.540082] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.540149] usb usb2: Product: EHCI Host Controller
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.540200] usb usb2: Manufacturer: Linux 3.13.0-36-generic ehci_hcd
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.540254] usb usb2: SerialNumber: 0000:00:1d.0
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.540353] hub 2-0:1.0: USB hub found
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.540405] hub 2-0:1.0: 2 ports detected
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.540509] ehci-platform: EHCI generic platform driver
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.540565] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.540618] ohci-pci: OHCI PCI platform driver
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.540672] ohci-platform: OHCI generic platform driver
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.540726] uhci_hcd: USB Universal Host Controller Interface driver
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.540849] xhci_hcd 0000:00:14.0: xHCI Host Controller
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.540903] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 3
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.541046] xhci_hcd 0000:00:14.0: cache line size of 64 is not supported
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.541061] xhci_hcd 0000:00:14.0: irq 42 for MSI/MSI-X
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.541098] usb usb3: New USB device found, idVendor=1d6b, idProduct=0002
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.541152] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.541219] usb usb3: Product: xHCI Host Controller
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.541270] usb usb3: Manufacturer: Linux 3.13.0-36-generic xhci_hcd
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.541324] usb usb3: SerialNumber: 0000:00:14.0
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.541436] hub 3-0:1.0: USB hub found
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.541499] hub 3-0:1.0: 14 ports detected
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.543723] xhci_hcd 0000:00:14.0: xHCI Host Controller
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.543776] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 4
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.543868] usb usb4: New USB device found, idVendor=1d6b, idProduct=0003
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.543923] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.543996] usb usb4: Product: xHCI Host Controller
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.544047] usb usb4: Manufacturer: Linux 3.13.0-36-generic xhci_hcd
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.544101] usb usb4: SerialNumber: 0000:00:14.0
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.544216] hub 4-0:1.0: USB hub found
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.544274] hub 4-0:1.0: 6 ports detected
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.551987] i8042: PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.552043] i8042: PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.552801] serio: i8042 KBD port at 0x60,0x64 irq 1
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.552920] mousedev: PS/2 mouse device common for all mice
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.553073] rtc_cmos 00:06: RTC can wake from S4
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.553228] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.553304] rtc_cmos 00:06: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.553403] device-mapper: uevent: version 1.0.3
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.553500] device-mapper: ioctl: 4.27.0-ioctl (2013-10-30) initialised: dm-devel@redhat.com
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.553572] Intel P-state driver initializing.
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.553629] Intel pstate controlling: cpu 0
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.553687] Intel pstate controlling: cpu 1
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.553753] Intel pstate controlling: cpu 2
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.553810] Intel pstate controlling: cpu 3
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.553886] Intel pstate controlling: cpu 4
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.553943] Intel pstate controlling: cpu 5
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.554000] Intel pstate controlling: cpu 6
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.554057] Intel pstate controlling: cpu 7
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.554140] Consider also installing thermald for improved thermal control.
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.554195] ledtrig-cpu: registered to indicate activity on CPUs
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.554294] TCP: cubic registered
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.554381] NET: Registered protocol family 10
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.554515] NET: Registered protocol family 17
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.554568] Key type dns_resolver registered
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.554807] Loading compiled-in X.509 certificates
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.555336] Loaded X.509 cert 'Magrathea: Glacier signing key: 38f3b6c63a85affdfbbe0e53339df8e0c6b6c9d5'
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.555431] registered taskstats version 1
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.557359] Key type trusted registered
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.558814] Key type encrypted registered
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.560229] AppArmor: AppArmor sha1 policy hashing enabled
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.560281] IMA: No TPM chip found, activating TPM-bypass!
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.560560] regulator-dummy: disabling
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.560750]   Magic number: 10:697:101
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.560855] memory memory250: hash matches
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.560982] rtc_cmos 00:06: setting system clock to 2014-12-08 00:06:51 UTC (1417997211)
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.561219] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.561283] EDD information not available.
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.561353] PM: Hibernation image not present or could not be loaded.
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.561865] Freeing unused kernel memory: 1336K (ffffffff81d1f000 - ffffffff81e6d000)
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.561932] Write protecting the kernel read-only data: 12288k
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.563199] Freeing unused kernel memory: 808K (ffff880001736000 - ffff880001800000)
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.564207] Freeing unused kernel memory: 692K (ffff880001b53000 - ffff880001c00000)
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.570892] systemd-udevd[141]: starting version 204
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.580877] md: linear personality registered for level -1
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.582265] md: multipath personality registered for level -4
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.583649] md: raid0 personality registered for level 0
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.584498] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.584569] r8169 0000:02:00.0: can't disable ASPM; OS doesn't have ASPM control
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.584687] ahci 0000:00:1f.2: version 3.0
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.584793] ahci 0000:00:1f.2: irq 43 for MSI/MSI-X
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.584848] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 6 Gbps 0x3 impl SATA mode
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.584886] r8169 0000:02:00.0: irq 44 for MSI/MSI-X
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.584966] ahci 0000:00:1f.2: flags: 64bit ncq led clo pio slum part ems apst 
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.584998] r8169 0000:02:00.0 eth0: RTL8168evl/8111evl at 0xffffc90003148000, d4:3d:7e:d8:bc:9e, XID 0c900880 IRQ 44
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.584998] r8169 0000:02:00.0 eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.585409] md: raid1 personality registered for level 1
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.592464] scsi0 : ahci
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.592635] scsi1 : ahci
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.592758] scsi2 : ahci
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.592874] scsi3 : ahci
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.592974] scsi4 : ahci
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.593083] scsi5 : ahci
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.593161] ata1: SATA max UDMA/133 abar m2048@0xf7c12000 port 0xf7c12100 irq 43
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.593245] ata2: SATA max UDMA/133 abar m2048@0xf7c12000 port 0xf7c12180 irq 43
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.593331] ata3: DUMMY
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.593380] ata4: DUMMY
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.593428] ata5: DUMMY
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.593481] ata6: DUMMY
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.613910] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.651882] raid6: sse2x1   12194 MB/s
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.719843] raid6: sse2x2   15272 MB/s
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.787801] raid6: sse2x4   17824 MB/s
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.835785] usb 1-1: new high-speed USB device number 2 using ehci-pci
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.855761] raid6: avx2x1   23685 MB/s
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.911765] ata1: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.911832] ata2: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.913713] ata2.00: ATA-9: INTEL SSDSC2CW240A3, 400i, max UDMA/133
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.913766] ata2.00: 468862128 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.922747] ata1.00: ATA-9: INTEL SSDSC2CW240A3, 400i, max UDMA/133
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.922800] ata1.00: 468862128 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.923665] ata2.00: configured for UDMA/133
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.923721] raid6: avx2x2   27203 MB/s
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.932686] ata1.00: configured for UDMA/133
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.932857] scsi 0:0:0:0: Direct-Access     ATA      INTEL SSDSC2CW24 400i PQ: 0 ANSI: 5
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.933042] sd 0:0:0:0: Attached scsi generic sg0 type 0
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.933048] sd 0:0:0:0: [sda] 468862128 512-byte logical blocks: (240 GB/223 GiB)
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.933323] sd 0:0:0:0: [sda] Write Protect is off
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.933406] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.933415] scsi 1:0:0:0: Direct-Access     ATA      INTEL SSDSC2CW24 400i PQ: 0 ANSI: 5
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.933436] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.933722] sd 1:0:0:0: Attached scsi generic sg1 type 0
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.933723]  sda: sda1 sda2 sda3
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.933874] sd 1:0:0:0: [sdb] 468862128 512-byte logical blocks: (240 GB/223 GiB)
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.933995] sd 0:0:0:0: [sda] Attached SCSI disk
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.934182] sd 1:0:0:0: [sdb] Write Protect is off
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.934233] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.934253] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.936119]  sdb: sdb1 sdb2 sdb3
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.936420] sd 1:0:0:0: [sdb] Attached SCSI disk
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.951222] md: bind<sda3>
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.952044] md: bind<sda1>
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.952791] md: bind<sdb3>
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.953562] md/raid1:md2: active with 2 out of 2 mirrors
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.953623] md2: detected capacity change from 0 to 222202101760
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.954311] md: bind<sdb1>
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.954757]  md2: unknown partition table
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.955263] md/raid1:md0: active with 2 out of 2 mirrors
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.955354] md0: detected capacity change from 0 to 17171349504
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.956043] md: bind<sda2>
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.956550]  md0: unknown partition table
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.957090] md: bind<sdb2>
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.958060] md/raid1:md1: active with 2 out of 2 mirrors
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.958135] md1: detected capacity change from 0 to 536543232
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.959274]  md1: unknown partition table
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.968059] usb 1-1: New USB device found, idVendor=8087, idProduct=8008
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.968113] usb 1-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.968333] hub 1-1:1.0: USB hub found
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.968431] hub 1-1:1.0: 6 ports detected
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.991693] raid6: avx2x4   29874 MB/s
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.991753] raid6: using algorithm avx2x4 (29874 MB/s)
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.991804] raid6: using avx2x2 recovery algorithm
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    0.992635] xor: automatically using best checksumming function:
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    1.031658]    avx       : 36693.000 MB/sec
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    1.032388] async_tx: api initialized (async)
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    1.036118] md: raid6 personality registered for level 6
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    1.036178] md: raid5 personality registered for level 5
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    1.036234] md: raid4 personality registered for level 4
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    1.038977] md: raid10 personality registered for level 10
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    1.051568] bio: create slab <bio-1> at 1
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    1.051801] Btrfs loaded
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    1.079702] usb 2-1: new high-speed USB device number 2 using ehci-pci
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    1.211944] usb 2-1: New USB device found, idVendor=8087, idProduct=8000
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    1.211998] usb 2-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    1.212333] hub 2-1:1.0: USB hub found
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    1.212565] hub 2-1:1.0: 8 ports detected
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    1.459443] tsc: Refined TSC clocksource calibration: 3399.997 MHz
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    2.458991] Switched to clocksource tsc
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    6.061101] EXT4-fs (md2): mounted filesystem with ordered data mode. Opts: (null)
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    6.092787] random: init urandom read with 59 bits of entropy available
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    6.104924] init: plymouth-upstart-bridge main process (276) terminated with status 1
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    6.105015] init: plymouth-upstart-bridge main process ended, respawning
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    6.107840] init: plymouth-upstart-bridge main process (286) terminated with status 1
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    6.107920] init: plymouth-upstart-bridge main process ended, respawning
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    6.110009] init: plymouth-upstart-bridge main process (289) terminated with status 1
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    6.110090] init: plymouth-upstart-bridge main process ended, respawning
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    6.111053] init: plymouth-upstart-bridge main process (292) terminated with status 1
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    6.111143] init: plymouth-upstart-bridge main process ended, respawning
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    6.112299] init: plymouth-upstart-bridge main process (294) terminated with status 1
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    6.112379] init: plymouth-upstart-bridge main process ended, respawning
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    6.235518] Adding 16768892k swap on /dev/md0.  Priority:-1 extents:1 across:16768892k FS
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    6.238169] EXT4-fs (md2): re-mounted. Opts: (null)
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    6.257639] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    6.266202] EXT4-fs (md1): mounting ext3 file system using the ext4 subsystem
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    6.267924] EXT4-fs (md1): mounted filesystem with ordered data mode. Opts: (null)
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    6.268096] systemd-udevd[400]: starting version 204
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    6.286973] wmi: Mapper loaded
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    6.290040] lp: driver loaded but no devices found
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    6.290779] parport_pc 00:0b: reported by Plug and Play ACPI
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    6.290822] parport0: PC-style at 0x378, irq 5 [PCSPP]
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    6.304295] ACPI Warning: 0x0000000000001828-0x000000000000182f SystemIO conflicts with Region \PMIO 1 (20131115/utaddress-251)
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    6.304301] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    6.304304] ACPI Warning: 0x0000000000001c30-0x0000000000001c3f SystemIO conflicts with Region \GPRL 1 (20131115/utaddress-251)
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    6.304307] ACPI Warning: 0x0000000000001c30-0x0000000000001c3f SystemIO conflicts with Region \GPR_ 2 (20131115/utaddress-251)
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    6.304309] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    6.304310] ACPI Warning: 0x0000000000001c00-0x0000000000001c2f SystemIO conflicts with Region \GPRL 1 (20131115/utaddress-251)
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    6.304312] ACPI Warning: 0x0000000000001c00-0x0000000000001c2f SystemIO conflicts with Region \GPR_ 2 (20131115/utaddress-251)
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    6.304315] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    6.304315] lpc_ich: Resource conflict(s) found affecting gpio_ich
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    6.304443] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    6.341534] type=1400 audit(1417997217.281:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=532 comm="apparmor_parser"
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    6.341538] type=1400 audit(1417997217.281:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=532 comm="apparmor_parser"
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    6.341541] type=1400 audit(1417997217.281:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=532 comm="apparmor_parser"
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    6.341872] type=1400 audit(1417997217.281:5): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=532 comm="apparmor_parser"
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    6.341877] type=1400 audit(1417997217.281:6): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=532 comm="apparmor_parser"
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    6.342048] type=1400 audit(1417997217.281:7): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=532 comm="apparmor_parser"
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    6.344481] type=1400 audit(1417997217.281:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/ntpd" pid=538 comm="apparmor_parser"
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    6.356969] ppdev: user-space parallel port driver
Dec  8 01:06:57 companyname-Ubuntu-1404 rsyslogd-2039: Could no open output pipe '/dev/xconsole': No such file or directory [try http://www.rsyslog.com/e/2039 ]
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    6.368605] lp0: using parport0 (interrupt-driven).
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    6.494527] r8169 0000:02:00.0 eth0: link down
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    6.494567] r8169 0000:02:00.0 eth0: link down
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    6.494581] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Dec  8 01:06:57 companyname-Ubuntu-1404 failsafe: Failsafe of 120 seconds reached.
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    6.511507] init: failsafe main process (730) killed by TERM signal
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    6.532612] type=1400 audit(1417997217.473:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/mysqld" pid=857 comm="apparmor_parser"
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    6.532629] type=1400 audit(1417997217.473:10): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/ntpd" pid=858 comm="apparmor_parser"
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    6.532861] type=1400 audit(1417997217.473:11): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=856 comm="apparmor_parser"
Dec  8 01:06:57 companyname-Ubuntu-1404 acpid: starting up with netlink and the input layer
Dec  8 01:06:57 companyname-Ubuntu-1404 acpid: 1 rule loaded
Dec  8 01:06:57 companyname-Ubuntu-1404 acpid: waiting for events: event logging is off
Dec  8 01:06:57 companyname-Ubuntu-1404 cron[909]: (CRON) INFO (pidfile fd = 3)
Dec  8 01:06:57 companyname-Ubuntu-1404 cron[943]: (CRON) STARTUP (fork ok)
Dec  8 01:06:57 companyname-Ubuntu-1404 cron[943]: (CRON) INFO (Running @reboot jobs)
Dec  8 01:06:57 companyname-Ubuntu-1404 haveged: haveged starting up
Dec  8 01:06:57 companyname-Ubuntu-1404 ntpd[1115]: ntpd 4.2.6p5@1.2349-o Wed Oct  9 19:08:06 UTC 2013 (1)
Dec  8 01:06:57 companyname-Ubuntu-1404 ntpd[1116]: proto: precision = 0.149 usec
Dec  8 01:06:57 companyname-Ubuntu-1404 ntpd[1116]: ntp_io: estimated max descriptors: 1024, initial socket boundary: 16
Dec  8 01:06:57 companyname-Ubuntu-1404 ntpd[1116]: Listen and drop on 0 v4wildcard 0.0.0.0 UDP 123
Dec  8 01:06:57 companyname-Ubuntu-1404 ntpd[1116]: Listen and drop on 1 v6wildcard :: UDP 123
Dec  8 01:06:57 companyname-Ubuntu-1404 ntpd[1116]: Listen normally on 2 lo 127.0.0.1 UDP 123
Dec  8 01:06:57 companyname-Ubuntu-1404 ntpd[1116]: Listen normally on 3 eth0 ip.ip.ip.ip.ip UDP 123
Dec  8 01:06:57 companyname-Ubuntu-1404 ntpd[1116]: Listen normally on 4 lo ::1 UDP 123
Dec  8 01:06:57 companyname-Ubuntu-1404 ntpd[1116]: peers refreshed
Dec  8 01:06:57 companyname-Ubuntu-1404 ntpd[1116]: Listening on routing socket on fd #21 for interface updates
Dec  8 01:06:57 companyname-Ubuntu-1404 kernel: [    6.691813] random: nonblocking pool is initialized
Dec  8 01:06:59 companyname-Ubuntu-1404 kernel: [    8.589301] init: plymouth-upstart-bridge main process ended, respawning
Dec  8 01:06:59 companyname-Ubuntu-1404 /etc/mysql/debian-start[1279]: Upgrading MySQL tables if necessary.
Dec  8 01:06:59 companyname-Ubuntu-1404 /etc/mysql/debian-start[1283]: /usr/bin/mysql_upgrade: the '--basedir' option is always ignored
Dec  8 01:06:59 companyname-Ubuntu-1404 /etc/mysql/debian-start[1283]: Looking for 'mysql' as: /usr/bin/mysql
Dec  8 01:06:59 companyname-Ubuntu-1404 /etc/mysql/debian-start[1283]: Looking for 'mysqlcheck' as: /usr/bin/mysqlcheck
Dec  8 01:06:59 companyname-Ubuntu-1404 /etc/mysql/debian-start[1283]: This installation of MySQL is already upgraded to 5.5.40, use --force if you still need to run mysql_upgrade
Dec  8 01:06:59 companyname-Ubuntu-1404 /etc/mysql/debian-start[1294]: Checking for insecure root accounts.
Dec  8 01:06:59 companyname-Ubuntu-1404 /etc/mysql/debian-start[1299]: WARNING: mysql.user contains 4 root accounts without password!
Dec  8 01:06:59 companyname-Ubuntu-1404 /etc/mysql/debian-start[1300]: Triggering myisam-recover for all MyISAM tables
Dec  8 01:07:00 companyname-Ubuntu-1404 kernel: [    9.569911] r8169 0000:02:00.0 eth0: link up
Dec  8 01:07:00 companyname-Ubuntu-1404 kernel: [    9.569916] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Dec  8 01:07:04 companyname-Ubuntu-1404 ntpd[1116]: Listen normally on 5 eth0 fe80::d63d:7eff:fed8:bc9e UDP 123
Dec  8 01:07:04 companyname-Ubuntu-1404 ntpd[1116]: Listen normally on 6 eth0 2a01:4f8:192:63a7::2 UDP 123
Dec  8 01:07:04 companyname-Ubuntu-1404 ntpd[1116]: peers refreshed
Dec  8 01:07:04 companyname-Ubuntu-1404 ntpd[1116]: new interface(s) found: waking up resolver
Dec  8 01:17:01 companyname-Ubuntu-1404 CRON[2783]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Dec  8 02:17:01 companyname-Ubuntu-1404 CRON[4366]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Dec  8 03:17:01 companyname-Ubuntu-1404 CRON[6203]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Dec  8 04:17:01 companyname-Ubuntu-1404 CRON[8032]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Dec  8 05:17:01 companyname-Ubuntu-1404 CRON[9923]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Dec  8 05:19:26 companyname-Ubuntu-1404 kernel: [15146.352094] UDP: bad checksum. From 66.240.192.138:45118 to 148.251.225.138:64738 ulen 20
Dec  8 05:39:13 companyname-Ubuntu-1404 kernel: [16332.582082] UDP: bad checksum. From 66.240.192.138:45118 to 148.251.225.138:4500 ulen 348
Dec  8 06:17:01 companyname-Ubuntu-1404 CRON[11682]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Dec  8 06:25:01 companyname-Ubuntu-1404 CRON[11843]: (root) CMD (test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily ))
Dec  8 06:25:05 companyname-Ubuntu-1404 rsyslogd: [origin software="rsyslogd" swVersion="7.4.4" x-pid="586" x-info="http://www.rsyslog.com"] rsyslogd was HUPed
```

---

