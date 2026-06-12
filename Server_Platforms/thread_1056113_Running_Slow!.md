---
title: "Running Slow!"
date: 2009-01-31
forum: Server Platforms
---

### Post by timma on 2009-01-31
Hi All,

I have a server running Ubuntu (2.6.24-21-openvz)

When I run "top" it says the process "top" is using about 15% CPU. If I run htop (a nicer version of top) the htop process uses about 25% CPU ! running them both at the same time results in the same effect.

On top of this, my system takes about 20 mins to boot!

I have spent a long time trying to work out why including trying to check the swap disk. Nothing I have done has helped. :(

Also, when I try to install bootchart to try to assess the cause it hangs for about 15 mins with this:

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.24-23-openvz


Anyone got any advice?

---

### Post by kerry_s on 2009-01-31
> Anyone got any advice? 

sure, when you want help with a problem, include as much info as you can.
specs?
post the /var/log/dmesg.log

---

### Post by HermanAB on 2009-01-31
Top lies about top.  It is a quirk - don't worry about it.

Look at your system logs to figure out why the system is slow to boot. It is likely a DNS problem, but you need to scroll through /var/log/messages using tail -n , to figure it out.

I'm also wondering why you reboot.  Unless it is a laptop pc, don't reboot.

Cheers,

Herman

---

### Post by timma on 2009-01-31
Well, I did wonder if top was misreporting, which is why I ran top and htop at the same time.. htop would still report that top was using 15% so it must actually be using the processor!

The whole system is generally sluggish.

You mentioned it could be a DNS issue? what DNS problem could it be?

Its a server machine in a server centre.

Generally it doesnt get rebooted but its running so slow at the moment I have been trying to fix it.

Its just rebooting at the moment and will post more info from logs when its finished

Thanks for the initial replies

---

### Post by timma on 2009-01-31
Ok,

Some extracts from dmesg log where its taking a lit of time:

> 
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] mapped IOAPIC to ffff9000 (fecc0000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1995.004 MHz processor.
[   13.914156] Console: colour VGA+ 80x25
[   13.914161] console [tty0] enabled
[   13.917700] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   13.917981] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   14.003565] Memory: 2032292k/2064000k available (2212k kernel code, 30448k reserved, 1047k data, 384k init, 1146496k highmem)

...
> [   16.364541] BIOS EDD facility v0.16 2004-Jun-25, 6 devices found
[   16.364952] Freeing unused kernel memory: 384k freed
[   16.383277] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   64.718352] fuse init (API version 7.9)
[   66.727559] ACPI: SSDT 7DFAE0B0, 0214 (r1    AMI   CPU1PM        1 INTL 20051117)
[   66.727914] ACPI: Processor [CPU1] (supports 16 throttling states)
[   66.728297] ACPI: SSDT 7DFAE2D0, 0143 (r1    AMI   CPU2PM        1 INTL 20051117)
[   66.728641] ACPI: Processor [CPU2] (supports 16 throttling states)
[   66.728787] ACPI Exception (processor_core-0822): AE_NOT_FOUND, Processor Device is not present [20070126]
[   66.728939] ACPI Exception (processor_core-0822): AE_NOT_FOUND, Processor Device is not present [20070126]
[  158.995314] SCSI subsystem initialized
[  159.502257] libata version 3.00 loaded.
[  164.362053] sata_via 0000:00:0f.0: version 2.3

...
> [  179.783301] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[  179.783361] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[  261.017433] Floppy drive(s): fd0 is 1.44M
[  261.038749] FDC 0 is a post-1991 82077
[  312.218226] Driver 'sd' needs updating - please use bus_type methods
[  312.218538] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)

...
> [  335.200701] EXT3-fs: mounted filesystem with ordered data mode.
[  635.633152] Linux agpgart interface v0.102
[  636.065445] agpgart: Detected VIA P4M900 chipset
[  636.078438] agpgart: AGP aperture is 32M @ 0xfc000000
[  644.821366] input: PC Speaker as /devices/platform/pcspkr/input/input2
[  652.126331] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[  652.287118] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[  770.060744] loop: module loaded
[  789.149122] udev: renamed network interface eth0 to eth1
[  792.407824] eth1: link up, 100Mbps, full-duplex, lpa 0x41E1
[  809.384919] ip_tables: (C) 2000-2006 Netfilter Core Team
[  816.414364] input: Power Button (FF) as /devices/virtual/input/input3

...
> [  873.079014] parport_pc 00:05: reported by Plug and Play ACPI
[  873.079189] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[  873.423469] lp0: using parport0 (interrupt-driven).
[ 1005.966651] Adding 2650684k swap on /dev/sda5.  Priority:-1 extents:1 across:2650684k
[ 1028.800890] EXT3 FS on sda1, internal journal
[ 1095.922401] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input6
[ 1231.137690] NET: Registered protocol family 10
[ 1241.523156] eth1: no IPv6 routers present
[ 1252.158155] ACPI: PCI Interrupt 0000:80:01.0[A] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
[ 1252.158202] PCI: Setting latency timer of device 0000:80:01.0 to 64
[ 1252.244893] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-openvz/sound/alsa-driver/pci/hda/../../alsa-kernel/pci/hda/hda_intel$
[ 1252.245028] ACPI: PCI interrupt for device 0000:80:01.0 disabled
[ 1310.431720] NET: Registered protocol family 17
[ 1331.412368] tun: Universal TUN/TAP device driver, 1.6
[ 1331.412389] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[ 1352.250591] CT: 601: started


---

### Post by timma on 2009-01-31
This is result from htop (i have stopped most stuff running)
```

  1  [|||||||                                   13.0%]     Tasks: 22 total, 2 running
  2  [||||||||                                  15.2%]     Load average: 0.22 0.39 1.75
  Mem[|||||||||                             38/1992MB]     Uptime: 01:02:01
  Swp[                                       0/2588MB]

  PID USER     PRI  NI  VIRT   RES   SHR S CPU% MEM%   TIME+  Command
    1 root      20   0  2844  1684   540 S  0.0  0.1  0:10.46 /sbin/init
18151 root      20   0  1888   580   488 S  0.0  0.0  0:02.48  `- /sbin/udevadm monitor -e
18140 root      16  -4  2228   780   384 S  0.0  0.0  1:12.15  `- /sbin/udevd --daemon
 7614 root      20   0  1716   504   436 S  0.0  0.0  0:00.04  `- /sbin/getty 38400 tty1
 7604 root      20   0 10388  6348  1432 S  0.0  0.3  0:00.14  `- /usr/bin/perl /usr/share/webmin/miniserv.pl /etc/
 6689 root      20   0  2104   884   708 S  0.0  0.0  0:00.22  `- /usr/sbin/cron
 6571 daemon    20   0  1984   424   300 S  0.0  0.0  0:00.00  `- /usr/sbin/atd
 2752 root      20   0  5316  1012   664 S  0.0  0.0  0:00.02  `- /usr/sbin/sshd
 7876 root      20   0  8056  2504  2044 S  0.0  0.1  0:01.26  |   `- sshd: root@pts/1
 7899 root      20   0  4204  1856  1396 S  0.0  0.1  0:03.87  |   |   `- -bash
 7988 root      20   0  2344  1144   912 R 16.3  0.1  0:13.07  |   |       `- htop
 7488 root      20   0  8056  2512  2044 S  0.0  0.1  0:01.55  |   `- sshd: root@pts/0
 7490 root      20   0  4204  1860  1400 S  0.0  0.1  0:07.42  |       `- -bash
 7989 root      20   0  2308  1076   848 R 23.1  0.1  0:12.61  |           `- top
 1206 klog      20   0  3292  2156   424 S  0.0  0.1  0:29.12  `- /sbin/klogd -P /var/run/klogd/kmsg
 1199 root      20   0  1872   536   440 S  0.0  0.0  0:00.28  `- /bin/dd bs 1 if /proc/kmsg of /var/run/klogd/kmsg
 1112 syslog    20   0  1936   644   508 S  0.0  0.0  0:00.97  `- /sbin/syslogd -u syslog
  937 root      20   0  1716   504   436 S  0.0  0.0  0:00.04  `- /sbin/getty 38400 tty6
  933 root      20   0  1716   500   436 S  0.0  0.0  0:00.04  `- /sbin/getty 38400 tty3
  922 root      20   0  1716   508   436 S  0.0  0.0  0:00.04  `- /sbin/getty 38400 tty2
  917 root      20   0  1716   504   436 S  0.0  0.0  0:00.04  `- /sbin/getty 38400 tty5
  916 root      20   0  1716   508   436 S  0.0  0.0  0:00.04  `- /sbin/getty 38400 tty4
```

---

### Post by HermanAB on 2009-01-31
Some tips:
If you have desktop search crapware running eg. 'beagle', uninstall it.
Type 'ps -e' to see everything that is running.
Test your DNS speed with 'dig' and put the fastest server at the top in /etc/resolv.conf.

Hope that helps!

Herman

---

### Post by timma on 2009-01-31
This is output from ps -e

This is a server machine - not running much at the moment !

Doesnt seem to have any problems doing dig

```

  PID TTY          TIME CMD
    1 ?        00:00:10 init
    2 ?        00:00:00 kthreadd
    3 ?        00:00:00 migration/0
    4 ?        00:00:00 ksoftirqd/0
    5 ?        00:00:00 watchdog/0
    6 ?        00:00:00 migration/1
    7 ?        00:00:00 ksoftirqd/1
    8 ?        00:00:00 watchdog/1
    9 ?        00:00:00 events/0
   10 ?        00:00:00 events/1
   11 ?        00:00:00 khelper
   43 ?        00:00:00 kblockd/0
   44 ?        00:00:00 kblockd/1
   47 ?        00:00:00 kacpid
   48 ?        00:00:00 kacpi_notify
  145 ?        00:00:00 kseriod
  187 ?        00:00:00 ubstatd
  189 ?        00:00:00 pdflush
  190 ?        00:00:00 pdflush
  191 ?        00:00:00 kswapd0
  257 ?        00:00:00 aio/0
  258 ?        00:00:00 aio/1
  916 tty4     00:00:00 getty
  917 tty5     00:00:00 getty
  922 tty2     00:00:00 getty
  933 tty3     00:00:00 getty
  937 tty6     00:00:00 getty
 1112 ?        00:00:01 syslogd
 1199 ?        00:00:00 dd
 1206 ?        00:00:29 klogd
 2752 ?        00:00:00 sshd
 4279 ?        00:00:00 vzmond
 5898 ?        00:00:00 ata/0
 5901 ?        00:00:00 ata/1
 5904 ?        00:00:00 ata_aux
 6022 ?        00:00:00 scsi_eh_0
 6027 ?        00:00:00 scsi_eh_1
 6030 ?        00:00:00 ksuspend_usbd
 6034 ?        00:00:00 khubd
 6205 ?        00:00:00 scsi_eh_2
 6210 ?        00:00:00 scsi_eh_3
 6571 ?        00:00:00 atd
 6689 ?        00:00:00 cron
 7604 ?        00:00:00 miniserv.pl
 7614 tty1     00:00:00 getty
 8375 ?        00:00:01 sshd
 8377 pts/0    00:00:02 bash
 8392 pts/0    00:00:00 ps
11783 ?        00:00:00 kjournald
18140 ?        00:01:12 udevd
18151 ?        00:00:02 udevadm
28661 ?        00:00:00 kpsmoused
```

---

### Post by unixeducation on 2009-01-31
Is this a physical dedicated server or a virtual private server?

---

### Post by timma on 2009-02-01
its a phisical dedicated server.

Its got openVZ installed to run virtual servers on it but currently when doing the outputs above no virtual servers running on it.

---

### Post by timma on 2009-02-02
any ideas?
Thanks

---

