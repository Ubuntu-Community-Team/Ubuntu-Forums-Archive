---
title: "Ethernet only works if the computer is started with the cable plugged in."
date: 2013-03-20
forum: Ubuntu Development Version
---

### Post by IYII3r41n on 2013-03-20
Ethernet only works if the computer is started with the cable plugged in. If I unplug it after starting and plug it back in, Ethernet does not work. 
```
ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:26:b9:d0:40:66  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Memory:e9600000-e9620000 



```

```
sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 82577LM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 05
       serial: 00:26:b9:d0:40:66
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi cap_list ethernet physical
       configuration: broadcast=yes driver=e1000e latency=0 multicast=yes
       resources: irq:20 memory:e9600000-e961ffff memory:e9680000-e9680fff ioport:8040(size=32)



```

```
LSB Version:	core-2.0-amd64:core-2.0-noarch:core-3.0-amd64:core-3.0-noarch:core-3.1-amd64:core-3.1-noarch:core-3.2-amd64:core-3.2-noarch:core-4.0-amd64:core-4.0-noarch
Distributor ID:	Ubuntu
Description:	Ubuntu Raring Ringtail (development branch)
Release:	13.04
Codename:	raring

```



This is the same output for  when ethernet works and when it does not work. 

any suggestions?

---

### Post by howefield on 2013-03-20
Thread moved to the Ubuntu =1 (Raring Ringtail) forum.

---

### Post by grahammechanical on 2013-03-20
This is not a problem on my machine. I have just tested this and ethernet reconnects in a couple of seconds. I do not even need to enable networking. This might be nothing to do with Ubuntu and everything to do with the peculiarities of your hardware. Is it a Laptop or mobile device that would power down certain parts of hardware to reduce battery consumption?

Regards.

---

### Post by IYII3r41n on 2013-03-20
> **grahammechanical said:**
> This is not a problem on my machine. I have just tested this and ethernet reconnects in a couple of seconds. I do not even need to enable networking. This might be nothing to do with Ubuntu and everything to do with the peculiarities of your hardware. Is it a Laptop or mobile device that would power down certain parts of hardware to reduce battery consumption?

Regards.


I'm using a laptop Dell Latitude E6510. 

Thanks for the help, it is a power down thing. It seems to work fine when plugged in. When i'm on battery power, that's when i experience the issues. I didnt' even think to try...

---

### Post by grahammechanical on 2013-03-20
We will see more of this kind of thing over the coming year as part of the push to get Ubuntu on mobile devices. Various system services are being looked at to see if they need to be running all the time. There is a drive to reduce memory usage and power consumption. As desktop machines and laptops have become more and more powerful developers have become a bit casual in their approach to using system resources. In Ubuntu that is being examined. Improvements that benefit Ubuntu on mobile devices will also improve things on the desktop/laptop.

---

### Post by cariboo on 2013-03-20
To help diagnose your problem, what does the output of dmesg look like when you plug the network cable in? To check open a termina and type:

```
dmesg | tail -n15
```

---

### Post by ft_ on 2013-03-21
maybe related to
[http://ubuntuforums.org/showthread.php?t=2125994](http://ubuntuforums.org/showthread.php?t=2125994)
and the bug report
[https://bugs.launchpad.net/ubuntu/+bug/1112652](https://bugs.launchpad.net/ubuntu/+bug/1112652)

---

### Post by alfsagen on 2013-05-08
Hello,
I'm using a ThinkPad T500 and have been running Ubuntu since v10 with appropriate upgrade to new versions along the road. Currently on 13.04 and realising the same problem as reported here;
 - When plugging the ethernet cable, the HW detects it, and the link indicator is flashing. However, Ubuntu is not detecting the ethernet cable being plugged.

I have tried disabling and re-enabling networking, but to now avail. (Also by using ThinkPad's HW button, which is basically setting "Airplane Mode" for networking.)

From dmesg, it seems that the eth0 network adapter is completely gone:

```
alfs@Miraculix-Linux:~$ dmesg | tail -n15
[86075.387089] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[86075.387090] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[86075.387092] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[86084.827380] wlan0: authenticate with 00:0f:61:bb:22:21
[86084.831596] wlan0: send auth to 00:0f:61:bb:22:21 (try 1/3)
[86085.032028] wlan0: send auth to 00:0f:61:bb:22:21 (try 2/3)
[86085.039846] wlan0: authenticated
[86085.044046] wlan0: associate with 00:0f:61:bb:22:21 (try 1/3)
[86085.044806] wlan0: RX AssocResp from 00:0f:61:bb:22:21 (capab=0x801 status=0 aid=4)
[86085.046911] wlan0: associated
[86309.519486] SGI XFS with ACLs, security attributes, realtime, large block/inode numbers, no debug enabled
[86309.549247] JFS: nTxBlock = 8192, nTxLock = 65536
[86309.575919] NTFS driver 2.1.30 [Flags: R/O MODULE].
[86309.613131] QNX4 filesystem 0.2.3 registered.
[86309.641554] Btrfs loaded
alfs@Miraculix-Linux:~$

```

From syslog (please see comments pre-fixed with ## in-line):


##
## Closing lid of laptop and moving to the office.
##

```

May  8 08:36:54 Miraculix-Linux NetworkManager[1064]: <info> (wlan0): cleaning up...
May  8 08:36:54 Miraculix-Linux NetworkManager[1064]: <info> (wlan0): taking down device.
May  8 08:36:54 Miraculix-Linux NetworkManager[1064]: <info> (wwan0): device state change: disconnected -> unmanaged (reason 'sleeping') [30 10 37]
May  8 08:36:54 Miraculix-Linux NetworkManager[1064]: <info> (wwan0): cleaning up...
May  8 08:36:54 Miraculix-Linux dbus[711]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
May  8 08:36:54 Miraculix-Linux dbus[711]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
May  8 08:36:54 Miraculix-Linux anacron[17718]: Anacron 2.3 started on 2013-05-08
May  8 08:36:54 Miraculix-Linux anacron[17718]: Normal exit (0 jobs run)
May  8 08:36:55 Miraculix-Linux kernel: [85395.084997] PM: Syncing filesystems ... done.

```


##
## Re-opening laptop in office
##

```

May  8 08:58:41 Miraculix-Linux kernel: [85395.193859] Freezing user space processes ... (elapsed 0.01 seconds) done.
May  8 08:58:41 Miraculix-Linux kernel: [85395.208250] Freezing remaining freezable tasks ... (elapsed 0.01 seconds) done.
May  8 08:58:41 Miraculix-Linux kernel: [85395.224299] Suspending console(s) (use no_console_suspend to debug)
May  8 08:58:41 Miraculix-Linux kernel: [85395.224851] hdaps: setting ec_rate=0, filter_order=1
May  8 08:58:41 Miraculix-Linux kernel: [85395.382549] sd 1:0:0:0: [sdb] Synchronizing SCSI cache
May  8 08:58:41 Miraculix-Linux kernel: [85395.382678] sd 0:0:0:0: [sda] Synchronizing SCSI cache
May  8 08:58:41 Miraculix-Linux kernel: [85395.382723] sd 1:0:0:0: [sdb] Stopping disk
May  8 08:58:41 Miraculix-Linux kernel: [85395.383349] sd 0:0:0:0: [sda] Stopping disk
May  8 08:58:41 Miraculix-Linux kernel: [85395.464328] pciehp 0000:00:1c.4:pcie04: pciehp_suspend ENTRY
May  8 08:58:41 Miraculix-Linux kernel: [85395.464330] pciehp 0000:00:1c.3:pcie04: pciehp_suspend ENTRY
May  8 08:58:41 Miraculix-Linux kernel: [85395.464343] pciehp 0000:00:1c.1:pcie04: pciehp_suspend ENTRY
May  8 08:58:41 Miraculix-Linux kernel: [85395.464345] pciehp 0000:00:1c.0:pcie04: pciehp_suspend ENTRY
May  8 08:58:41 Miraculix-Linux kernel: [85395.464582] e1000e 0000:00:19.0: System wakeup enabled by ACPI
May  8 08:58:41 Miraculix-Linux kernel: [85395.784123] i915 0000:00:02.0: power state changed by ACPI to D3hot
May  8 08:58:41 Miraculix-Linux kernel: [85395.784186] PM: suspend of devices complete after 559.463 msecs
May  8 08:58:41 Miraculix-Linux kernel: [85395.784421] PM: late suspend of devices complete after 0.232 msecs
May  8 08:58:41 Miraculix-Linux kernel: [85395.832178] ehci-pci 0000:00:1d.7: System wakeup enabled by ACPI
May  8 08:58:41 Miraculix-Linux kernel: [85395.848018] ehci-pci 0000:00:1d.7: power state changed by ACPI to D3hot
May  8 08:58:41 Miraculix-Linux kernel: [85395.848127] uhci_hcd 0000:00:1d.0: System wakeup enabled by ACPI
May  8 08:58:41 Miraculix-Linux kernel: [85395.848130] uhci_hcd 0000:00:1d.0: power state changed by ACPI to D2
May  8 08:58:41 Miraculix-Linux kernel: [85395.848330] ehci-pci 0000:00:1a.7: System wakeup enabled by ACPI
May  8 08:58:41 Miraculix-Linux kernel: [85395.864018] ehci-pci 0000:00:1a.7: power state changed by ACPI to D3hot
May  8 08:58:41 Miraculix-Linux kernel: [85395.864067] uhci_hcd 0000:00:1a.2: System wakeup enabled by ACPI
May  8 08:58:41 Miraculix-Linux kernel: [85395.864070] uhci_hcd 0000:00:1a.2: power state changed by ACPI to D2
May  8 08:58:41 Miraculix-Linux kernel: [85395.864140] uhci_hcd 0000:00:1a.0: System wakeup enabled by ACPI
May  8 08:58:41 Miraculix-Linux kernel: [85395.864143] uhci_hcd 0000:00:1a.0: power state changed by ACPI to D2
May  8 08:58:41 Miraculix-Linux kernel: [85395.880066] PM: noirq suspend of devices complete after 95.642 msecs
May  8 08:58:41 Miraculix-Linux kernel: [85395.880403] ACPI: Preparing to enter system sleep state S3
May  8 08:58:41 Miraculix-Linux kernel: [85396.060054] PM: Saving platform NVS memory
May  8 08:58:41 Miraculix-Linux kernel: [85396.062086] Disabling non-boot CPUs ...
May  8 08:58:41 Miraculix-Linux kernel: [85396.164016] smpboot: CPU 1 is now offline
May  8 08:58:41 Miraculix-Linux kernel: [85396.164436] Extended CMOS year: 2000
May  8 08:58:41 Miraculix-Linux kernel: [85396.164436] ACPI: Low-level resume complete
May  8 08:58:41 Miraculix-Linux kernel: [85396.164436] PM: Restoring platform NVS memory
May  8 08:58:41 Miraculix-Linux kernel: [85396.164436] Extended CMOS year: 2000
May  8 08:58:41 Miraculix-Linux kernel: [85396.164436] Enabling non-boot CPUs ...
May  8 08:58:41 Miraculix-Linux kernel: [85396.164436] smpboot: Booting Node 0 Processor 1 APIC 0x1
May  8 08:58:41 Miraculix-Linux kernel: [85396.063425] Disabled fast string operations
May  8 08:58:41 Miraculix-Linux kernel: [85396.192475] CPU1 is up
May  8 08:58:41 Miraculix-Linux kernel: [85396.194600] ACPI: Waking up from system sleep state S3
May  8 08:58:41 Miraculix-Linux kernel: [85396.401977] thinkpad_acpi: EC reports that Thermal Table has changed
May  8 08:58:41 Miraculix-Linux kernel: [85396.604230] i915 0000:00:02.0: power state changed by ACPI to D0
May  8 08:58:41 Miraculix-Linux kernel: [85396.652142] uhci_hcd 0000:00:1a.0: power state changed by ACPI to D0
May  8 08:58:41 Miraculix-Linux kernel: [85396.652200] uhci_hcd 0000:00:1a.0: System wakeup disabled by ACPI
May  8 08:58:41 Miraculix-Linux kernel: [85396.652239] uhci_hcd 0000:00:1a.2: power state changed by ACPI to D0
May  8 08:58:41 Miraculix-Linux kernel: [85396.652291] uhci_hcd 0000:00:1a.2: System wakeup disabled by ACPI
May  8 08:58:41 Miraculix-Linux kernel: [85396.652295] ehci-pci 0000:00:1a.7: power state changed by ACPI to D0
May  8 08:58:41 Miraculix-Linux kernel: [85396.668147] ehci-pci 0000:00:1a.7: System wakeup disabled by ACPI
May  8 08:58:41 Miraculix-Linux kernel: [85396.684419] uhci_hcd 0000:00:1d.0: power state changed by ACPI to D0
May  8 08:58:41 Miraculix-Linux kernel: [85396.684461] uhci_hcd 0000:00:1d.0: System wakeup disabled by ACPI
May  8 08:58:41 Miraculix-Linux kernel: [85396.684521] ehci-pci 0000:00:1d.7: power state changed by ACPI to D0
May  8 08:58:41 Miraculix-Linux kernel: [85396.700146] ehci-pci 0000:00:1d.7: System wakeup disabled by ACPI
May  8 08:58:41 Miraculix-Linux kernel: [85396.796460] PM: noirq resume of devices complete after 192.340 msecs
May  8 08:58:41 Miraculix-Linux kernel: [85396.796640] PM: early resume of devices complete after 0.129 msecs
May  8 08:58:41 Miraculix-Linux kernel: [85396.796722] i915 0000:00:02.0: setting latency timer to 64
May  8 08:58:41 Miraculix-Linux kernel: [85396.796806] mei 0000:00:03.0: irq 44 for MSI/MSI-X
May  8 08:58:41 Miraculix-Linux kernel: [85396.796826] e1000e 0000:00:19.0: System wakeup disabled by ACPI
May  8 08:58:41 Miraculix-Linux kernel: [85396.796899] e1000e 0000:00:19.0: irq 47 for MSI/MSI-X
May  8 08:58:41 Miraculix-Linux kernel: [85396.799017] uhci_hcd 0000:00:1a.0: setting latency timer to 64
May  8 08:58:41 Miraculix-Linux kernel: [85396.799043] usb usb3: root hub lost power or was reset
May  8 08:58:41 Miraculix-Linux kernel: [85396.799059] uhci_hcd 0000:00:1a.1: setting latency timer to 64
May  8 08:58:41 Miraculix-Linux kernel: [85396.799084] usb usb4: root hub lost power or was reset
May  8 08:58:41 Miraculix-Linux kernel: [85396.799099] uhci_hcd 0000:00:1a.2: setting latency timer to 64
May  8 08:58:41 Miraculix-Linux kernel: [85396.799124] usb usb5: root hub lost power or was reset
May  8 08:58:41 Miraculix-Linux kernel: [85396.799140] ehci-pci 0000:00:1a.7: setting latency timer to 64
May  8 08:58:41 Miraculix-Linux kernel: [85396.799202] snd_hda_intel 0000:00:1b.0: irq 49 for MSI/MSI-X
May  8 08:58:41 Miraculix-Linux kernel: [85396.799256] pciehp 0000:00:1c.0:pcie04: pciehp_resume ENTRY
May  8 08:58:41 Miraculix-Linux kernel: [85396.799274] pciehp 0000:00:1c.1:pcie04: pciehp_resume ENTRY
May  8 08:58:41 Miraculix-Linux kernel: [85396.799296] pciehp 0000:00:1c.3:pcie04: pciehp_resume ENTRY
May  8 08:58:41 Miraculix-Linux kernel: [85396.799312] pciehp 0000:00:1c.4:pcie04: pciehp_resume ENTRY
May  8 08:58:41 Miraculix-Linux kernel: [85396.799329] uhci_hcd 0000:00:1d.0: setting latency timer to 64
May  8 08:58:41 Miraculix-Linux kernel: [85396.799354] usb usb6: root hub lost power or was reset
May  8 08:58:41 Miraculix-Linux kernel: [85396.799368] uhci_hcd 0000:00:1d.1: setting latency timer to 64
May  8 08:58:41 Miraculix-Linux kernel: [85396.799393] usb usb7: root hub lost power or was reset
May  8 08:58:41 Miraculix-Linux kernel: [85396.799407] uhci_hcd 0000:00:1d.2: setting latency timer to 64
May  8 08:58:41 Miraculix-Linux kernel: [85396.799431] usb usb8: root hub lost power or was reset
May  8 08:58:41 Miraculix-Linux kernel: [85396.799448] ehci-pci 0000:00:1d.7: setting latency timer to 64
May  8 08:58:41 Miraculix-Linux kernel: [85396.799465] pci 0000:00:1e.0: setting latency timer to 64
May  8 08:58:41 Miraculix-Linux kernel: [85396.799477] ahci 0000:00:1f.2: setting latency timer to 64
May  8 08:58:41 Miraculix-Linux kernel: [85396.799519] sdhci-pci 0000:15:00.2: Will use DMA mode even though HW doesn't fully claim to support it.
May  8 08:58:41 Miraculix-Linux kernel: [85396.800525] sdhci-pci 0000:15:00.2: Will use DMA mode even though HW doesn't fully claim to support it.
May  8 08:58:41 Miraculix-Linux kernel: [85396.900061] pciehp 0000:00:1c.1:pcie04: Device 0000:03:00.0 already exists at 0000:03:00, cannot hot-add
May  8 08:58:41 Miraculix-Linux kernel: [85396.900063] pciehp 0000:00:1c.1:pcie04: Cannot add device at 0000:03:00
May  8 08:58:41 Miraculix-Linux kernel: [85397.020848] dpm_run_callback(): pnp_bus_resume+0x0/0x80 returns -19
May  8 08:58:41 Miraculix-Linux kernel: [85397.020849] PM: Device 00:09 failed to resume: error -19
May  8 08:58:41 Miraculix-Linux kernel: [85397.023650] Extended CMOS year: 2000
May  8 08:58:41 Miraculix-Linux kernel: [85397.120059] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
May  8 08:58:41 Miraculix-Linux kernel: [85397.120091] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
May  8 08:58:41 Miraculix-Linux kernel: [85397.121985] ata2.00: ACPI cmd ef/02:00:00:00:00:a0 (SET FEATURES) succeeded
May  8 08:58:41 Miraculix-Linux kernel: [85397.121989] ata2.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
May  8 08:58:41 Miraculix-Linux kernel: [85397.122069] ata2.00: ACPI cmd ef/5f:00:00:00:00:a0 (SET FEATURES) succeeded
May  8 08:58:41 Miraculix-Linux kernel: [85397.122072] ata2.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
May  8 08:58:41 Miraculix-Linux kernel: [85397.136051] usb 1-6: reset high-speed USB device number 3 using ehci-pci
May  8 08:58:41 Miraculix-Linux kernel: [85397.171394] ata2.00: ACPI cmd ef/02:00:00:00:00:a0 (SET FEATURES) succeeded
May  8 08:58:41 Miraculix-Linux kernel: [85397.171397] ata2.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
May  8 08:58:41 Miraculix-Linux kernel: [85397.171483] ata2.00: ACPI cmd ef/5f:00:00:00:00:a0 (SET FEATURES) succeeded
May  8 08:58:41 Miraculix-Linux kernel: [85397.171486] ata2.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
May  8 08:58:41 Miraculix-Linux kernel: [85397.174292] ata2.00: configured for UDMA/133
May  8 08:58:41 Miraculix-Linux kernel: [85397.188118] sd 1:0:0:0: [sdb] Starting disk
May  8 08:58:41 Miraculix-Linux kernel: [85397.201422] ata1.00: ACPI cmd ef/02:00:00:00:00:a0 (SET FEATURES) succeeded
May  8 08:58:41 Miraculix-Linux kernel: [85397.201425] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
May  8 08:58:41 Miraculix-Linux kernel: [85397.201427] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
May  8 08:58:41 Miraculix-Linux kernel: [85397.354338] ata1.00: ACPI cmd ef/02:00:00:00:00:a0 (SET FEATURES) succeeded
May  8 08:58:41 Miraculix-Linux kernel: [85397.354341] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
May  8 08:58:41 Miraculix-Linux kernel: [85397.354344] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
May  8 08:58:41 Miraculix-Linux kernel: [85397.380056] usb 4-1: reset full-speed USB device number 2 using uhci_hcd
May  8 08:58:41 Miraculix-Linux kernel: [85397.452972] ata1.00: configured for UDMA/133
May  8 08:58:41 Miraculix-Linux kernel: [85397.468069] sd 0:0:0:0: [sda] Starting disk
May  8 08:58:41 Miraculix-Linux kernel: [85397.504074] firewire_core 0000:15:00.1: rediscovered device fw0
May  8 08:58:41 Miraculix-Linux kernel: [85397.608127] hdaps: initial mode latch is 0x05
May  8 08:58:41 Miraculix-Linux kernel: [85397.608261] hdaps: setting ec_rate=250, filter_order=2
May  8 08:58:41 Miraculix-Linux kernel: [85397.608535] PM: resume of devices complete after 811.891 msecs
May  8 08:58:41 Miraculix-Linux acpid: client 1635[0:0] has disconnected
May  8 08:58:41 Miraculix-Linux kernel: [85397.608991] Restarting tasks ... done.
May  8 08:58:41 Miraculix-Linux kernel: [85397.628727] video LNXVIDEO:00: Restoring backlight state
May  8 08:58:41 Miraculix-Linux acpid: client connected from 1635[0:0]
May  8 08:58:41 Miraculix-Linux acpid: 1 client rule loaded
May  8 08:58:41 Miraculix-Linux kernel: [85397.691132] sdhci-pci 0000:15:00.2: Will use DMA mode even though HW doesn't fully claim to support it.
May  8 08:58:41 Miraculix-Linux kernel: [85397.737333] usb 2-4: USB disconnect, device number 5
May  8 08:58:41 Miraculix-Linux kernel: [85397.739116] cdc_ether 2-4:1.7 wwan0: unregister 'cdc_ether' usb-0000:00:1d.7-4, Mobile Broadband Network Device
May  8 08:58:41 Miraculix-Linux avahi-daemon[725]: Withdrawing workstation service for wwan0.
May  8 08:58:41 Miraculix-Linux modem-manager[1047]: <info>  (tty/ttyACM1): released by modem /sys/devices/pci0000:00/0000:00:1d.7/usb2/2-4
May  8 08:58:41 Miraculix-Linux kernel: [85397.762941] sdhci-pci 0000:15:00.2: Will use DMA mode even though HW doesn't fully claim to support it.
May  8 08:58:41 Miraculix-Linux NetworkManager[1064]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/pci0000:00/0000:00:1d.7/usb2/2-4/2-4:1.7/net/wwan0, iface: wwan0)
May  8 08:58:41 Miraculix-Linux NetworkManager[1064]: <warn> sysctl: failed to open '/proc/sys/net/ipv6/conf/wwan0/accept_ra': (2) No such file or directory
May  8 08:58:41 Miraculix-Linux NetworkManager[1064]: <warn> sysctl: failed to open '/proc/sys/net/ipv6/conf/wwan0/use_tempaddr': (2) No such file or directory
May  8 08:58:41 Miraculix-Linux modem-manager[1047]: <info>  (tty/ttyACM0): released by modem /sys/devices/pci0000:00/0000:00:1d.7/usb2/2-4
May  8 08:58:41 Miraculix-Linux kernel: [85397.824872] sdhci-pci 0000:15:00.2: Will use DMA mode even though HW doesn't fully claim to support it.
May  8 08:58:42 Miraculix-Linux kernel: [85397.888946] sdhci-pci 0000:15:00.2: Will use DMA mode even though HW doesn't fully claim to support it.
May  8 08:58:42 Miraculix-Linux kernel: [85398.008046] usb 2-4: new high-speed USB device number 7 using ehci-pci
May  8 08:58:42 Miraculix-Linux anacron[18112]: Anacron 2.3 started on 2013-05-08
May  8 08:58:42 Miraculix-Linux anacron[18112]: Normal exit (0 jobs run)
May  8 08:58:42 Miraculix-Linux NetworkManager[1064]: <info> wake requested (sleeping: yes  enabled: yes)
May  8 08:58:42 Miraculix-Linux NetworkManager[1064]: <info> waking up and re-enabling...
May  8 08:58:42 Miraculix-Linux NetworkManager[1064]: <info> WWAN now enabled by management service

```


## NOTE this part:

```

May  8 08:58:42 Miraculix-Linux NetworkManager[1064]: <info> (eth0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
May  8 08:58:42 Miraculix-Linux NetworkManager[1064]: <info> (eth0): bringing up device.
May  8 08:58:42 Miraculix-Linux kernel: [85398.626552] e1000e 0000:00:19.0: irq 47 for MSI/MSI-X
May  8 08:58:42 Miraculix-Linux kernel: [85398.726799] usb 2-4: New USB device found, idVendor=0bdb, idProduct=1900
May  8 08:58:42 Miraculix-Linux kernel: [85398.726804] usb 2-4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
May  8 08:58:42 Miraculix-Linux kernel: [85398.726806] usb 2-4: Product: Ericsson F3507g Mobile Broadband Minicard Composite Device
May  8 08:58:42 Miraculix-Linux kernel: [85398.726809] usb 2-4: Manufacturer: Ericsson
May  8 08:58:42 Miraculix-Linux kernel: [85398.726811] usb 2-4: SerialNumber: 3541430243515200
May  8 08:58:42 Miraculix-Linux kernel: [85398.728379] e1000e 0000:00:19.0: irq 47 for MSI/MSI-X
May  8 08:58:42 Miraculix-Linux kernel: [85398.728504] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
May  8 08:58:42 Miraculix-Linux kernel: [85398.729509] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
May  8 08:58:42 Miraculix-Linux NetworkManager[1064]: <info> (eth0): preparing device.
May  8 08:58:42 Miraculix-Linux NetworkManager[1064]: <info> (eth0): deactivating device (reason 'managed') [2]

```


## So to me it seems that the ethernet adaptor is deactivated again, and the only clue/reason I can find is the line above
## saying   "IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready".


## I think that bug # 191889 is irrelevant for my issue;
## [MASTER] [WORKAROUND] "Offline Mode" feature fails to detect proper online state for networks that are managed outside of network manager. 
## This is about networks not detected if handled outside Network Manager.
## (However note that the nm-app in the system tray is often stopping working for me, and I have to bring up the "Network" application
## iself to be able to administrate/connect, e.g. when I need to connect to VPN.

## After this, there is no more hits when searching for "eth0" in syslog.

```

May  8 08:58:42 Miraculix-Linux NetworkManager[1064]: <info> Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889))
May  8 08:58:42 Miraculix-Linux NetworkManager[1064]: <info> Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889))
May  8 08:58:42 Miraculix-Linux NetworkManager[1064]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
May  8 08:58:42 Miraculix-Linux NetworkManager[1064]: <info> (wlan0): bringing up device.
May  8 08:58:42 Miraculix-Linux kernel: [85398.733975] iwlwifi 0000:03:00.0: Radio type=0x0-0x2-0x0

```

---

### Post by grahammechanical on 2013-05-08
@alf

My guess in all of this is that this is a clue for you:

> May 8 08:58:42 Miraculix-Linux NetworkManager [1064]: <info> (eth0): deactivating (reason 'managed') [2]

Is this a conflict between 2 network managers?  What is Miraculix-Linux? I cannot find any clear information about that. There are references to an incomplete and discontinued Russian Linux version. Could Miraculix-Linux kernel be an embedded Linux? Another clue, your own comment:

> [COLOR=#000000] "Offline Mode" feature fails to detect proper online state for networks that are managed _outside of network manager_.[/COLOR]

This should be the expected behaviour from an OS whose Network Manager is not managing the networks.

Regards.

---

### Post by alfsagen on 2013-05-08
@grahammechanical,
Thanks a lot for looking into this!

Miraculix-Linux is just my hostname, nothing interesting!
To my knowledge, I don't have more than one network manager, i.e. the default Ubuntu distro one. (Checking within synaptic/aptitude, I cannot find any other, and I am not aware that I have installed any other....i.e. not don it consciously.) Regarding the incomplete and discontinued Russian version, I'm a bit puzzled...maybe it's just something related to language support? (I have always run the plain vanilla international (i.e. English) standard desktop version of Ubuntu, however have changed "Regional Formats" to 'English (Denmark)'. I'm working from Norway, and in order to support local currency & metrics, I'm running en_dk (Danish locale with English language) because there is no en_no available. I'm not sure where you are reading that reference to a Russian cersion, but I'm indeed having support for Russian keyboard installed.

The strange thing on networking, however, is that after a couple of hours this morning I moved into a conference room where I plugged the ethernet cable again. This time....voila...it all worked nicely and fully automatic. (There is nothing wrong with the ethernet cable or network -- moving back to my desk and re-plugging the initial cable, it auto-detected and switched on automatically again.)

Now, dmesg is showing this (only the last 2 lines found by grep being amongst the last 100 dmesg lines):

```

alfs@Miraculix-Linux:~$ dmesg | grep eth0
[89110.530639] e1000e 0000:00:19.0 eth0: MAC Wakeup cause - Link Status Change
[94985.788903] e1000e: eth0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: None
[94985.788940] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[96059.620182] e1000e: eth0 NIC Link is Down
[96064.203113] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[96074.888943] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: None
[96074.888950] e1000e 0000:00:19.0 eth0: 10/100 speed: disabling TSO
[96074.888984] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[97398.644148] e1000e: eth0 NIC Link is Down
[97403.204199] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[97437.242594] e1000e 0000:00:19.0 eth0: MAC Wakeup cause - Link Status Change
[97443.108452] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[98481.848954] e1000e: eth0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: None
[98481.848997] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
alfs@Miraculix-Linux:~$ 

```


grep'ing for eth0 in syslog gives this:

```

alfs@Miraculix-Linux:~$ less ~/Desktop/tmp_eth0 | grep eth0
May  8 08:36:53 Miraculix-Linux NetworkManager[1064]: <info> (eth0): device state change: unavailable -> unmanaged (reason 'sleeping') [20 10 37]
May  8 08:36:53 Miraculix-Linux NetworkManager[1064]: <info> (eth0): cleaning up...
May  8 08:36:53 Miraculix-Linux NetworkManager[1064]: <info> (eth0): taking down device.
May  8 08:58:42 Miraculix-Linux NetworkManager[1064]: <info> (eth0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
May  8 08:58:42 Miraculix-Linux NetworkManager[1064]: <info> (eth0): bringing up device.
May  8 08:58:42 Miraculix-Linux kernel: [85398.728504] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
May  8 08:58:42 Miraculix-Linux NetworkManager[1064]: <info> (eth0): preparing device.
May  8 08:58:42 Miraculix-Linux NetworkManager[1064]: <info> (eth0): deactivating device (reason 'managed') [2]
May  8 10:00:34 Miraculix-Linux kernel: [89110.530639] e1000e 0000:00:19.0 eth0: MAC Wakeup cause - Link Status Change
May  8 11:38:29 Miraculix-Linux NetworkManager[1064]: <info> (eth0): carrier now ON (device state 20)
May  8 11:38:29 Miraculix-Linux kernel: [94985.788903] e1000e: eth0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: None
May  8 11:38:29 Miraculix-Linux kernel: [94985.788940] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
May  8 11:38:29 Miraculix-Linux NetworkManager[1064]: <info> (eth0): device state change: unavailable -> disconnected (reason 'carrier-changed') [20 30 40]
May  8 11:38:29 Miraculix-Linux NetworkManager[1064]: <info> Activation (eth0) starting connection 'Auto Ethernet'
May  8 11:38:29 Miraculix-Linux NetworkManager[1064]: <info> (eth0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
May  8 11:38:29 Miraculix-Linux NetworkManager[1064]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
May  8 11:38:29 Miraculix-Linux NetworkManager[1064]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) started...
May  8 11:38:29 Miraculix-Linux NetworkManager[1064]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
May  8 11:38:29 Miraculix-Linux NetworkManager[1064]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
May  8 11:38:29 Miraculix-Linux NetworkManager[1064]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) starting...
May  8 11:38:29 Miraculix-Linux NetworkManager[1064]: <info> (eth0): device state change: prepare -> config (reason 'none') [40 50 0]
May  8 11:38:29 Miraculix-Linux NetworkManager[1064]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) successful.
May  8 11:38:29 Miraculix-Linux NetworkManager[1064]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
May  8 11:38:29 Miraculix-Linux NetworkManager[1064]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) complete.
May  8 11:38:29 Miraculix-Linux NetworkManager[1064]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
May  8 11:38:29 Miraculix-Linux NetworkManager[1064]: <info> (eth0): device state change: config -> ip-config (reason 'none') [50 70 0]
May  8 11:38:29 Miraculix-Linux NetworkManager[1064]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
May  8 11:38:29 Miraculix-Linux NetworkManager[1064]: <info> Activation (eth0) Beginning IP6 addrconf.
May  8 11:38:29 Miraculix-Linux NetworkManager[1064]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
May  8 11:38:30 Miraculix-Linux NetworkManager[1064]: <info> (eth0): DHCPv4 state changed nbi -> preinit
May  8 11:38:30 Miraculix-Linux dhclient: Listening on LPF/eth0/00:24:7e:14:7c:41
May  8 11:38:30 Miraculix-Linux dhclient: Sending on   LPF/eth0/00:24:7e:14:7c:41
May  8 11:38:30 Miraculix-Linux dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3 (xid=0x6c1e02d7)
May  8 11:38:31 Miraculix-Linux avahi-daemon[725]: Joining mDNS multicast group on interface eth0.IPv6 with address fe80::224:7eff:fe14:7c41.
May  8 11:38:31 Miraculix-Linux avahi-daemon[725]: New relevant interface eth0.IPv6 for mDNS.
May  8 11:38:31 Miraculix-Linux avahi-daemon[725]: Registering new address record for fe80::224:7eff:fe14:7c41 on eth0.*.
May  8 11:38:33 Miraculix-Linux dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7 (xid=0x6c1e02d7)
May  8 11:38:38 Miraculix-Linux dhclient: DHCPREQUEST of 10.20.87.96 on eth0 to 255.255.255.255 port 67 (xid=0x6c1e02d7)
May  8 11:38:38 Miraculix-Linux NetworkManager[1064]: <info> (eth0): DHCPv4 state changed preinit -> bound
May  8 11:38:38 Miraculix-Linux NetworkManager[1064]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
May  8 11:38:38 Miraculix-Linux NetworkManager[1064]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) started...
May  8 11:38:38 Miraculix-Linux avahi-daemon[725]: Joining mDNS multicast group on interface eth0.IPv4 with address 10.20.87.96.
May  8 11:38:38 Miraculix-Linux avahi-daemon[725]: New relevant interface eth0.IPv4 for mDNS.
May  8 11:38:38 Miraculix-Linux avahi-daemon[725]: Registering new address record for 10.20.87.96 on eth0.IPv4.
May  8 11:38:39 Miraculix-Linux NetworkManager[1064]: <info> (eth0): device state change: ip-config -> secondaries (reason 'none') [70 90 0]
May  8 11:38:39 Miraculix-Linux NetworkManager[1064]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) complete.
May  8 11:38:39 Miraculix-Linux NetworkManager[1064]: <info> (eth0): device state change: secondaries -> activated (reason 'none') [90 100 0]
May  8 11:38:39 Miraculix-Linux NetworkManager[1064]: <info> Policy set 'Auto Ethernet' (eth0) as default for IPv4 routing and DNS.
May  8 11:38:39 Miraculix-Linux NetworkManager[1064]: <info> Activation (eth0) successful, device activated.
May  8 11:38:49 Miraculix-Linux NetworkManager[1064]: <info> (eth0): IP6 addrconf timed out or failed.
May  8 11:38:49 Miraculix-Linux NetworkManager[1064]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
May  8 11:38:49 Miraculix-Linux NetworkManager[1064]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) started...
May  8 11:38:49 Miraculix-Linux NetworkManager[1064]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
May  8 11:56:23 Miraculix-Linux NetworkManager[1064]: <info> (eth0): carrier now OFF (device state 100, deferring action for 4 seconds)
May  8 11:56:23 Miraculix-Linux kernel: [96059.620182] e1000e: eth0 NIC Link is Down
May  8 11:56:27 Miraculix-Linux NetworkManager[1064]: <info> (eth0): device state change: activated -> unavailable (reason 'carrier-changed') [100 20 40]
May  8 11:56:27 Miraculix-Linux NetworkManager[1064]: <info> (eth0): deactivating device (reason 'carrier-changed') [40]
May  8 11:56:27 Miraculix-Linux NetworkManager[1064]: <info> (eth0): canceled DHCP transaction, DHCP client pid 17404
May  8 11:56:27 Miraculix-Linux kernel: [96064.203113] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
May  8 11:56:27 Miraculix-Linux avahi-daemon[725]: Withdrawing address record for fe80::224:7eff:fe14:7c41 on eth0.
May  8 11:56:27 Miraculix-Linux avahi-daemon[725]: Leaving mDNS multicast group on interface eth0.IPv6 with address fe80::224:7eff:fe14:7c41.
May  8 11:56:27 Miraculix-Linux avahi-daemon[725]: Interface eth0.IPv6 no longer relevant for mDNS.
May  8 11:56:27 Miraculix-Linux avahi-daemon[725]: Withdrawing address record for 10.20.87.96 on eth0.
May  8 11:56:27 Miraculix-Linux avahi-daemon[725]: Leaving mDNS multicast group on interface eth0.IPv4 with address 10.20.87.96.
May  8 11:56:27 Miraculix-Linux avahi-daemon[725]: Interface eth0.IPv4 no longer relevant for mDNS.
May  8 11:56:38 Miraculix-Linux NetworkManager[1064]: <info> (eth0): carrier now ON (device state 20)
May  8 11:56:38 Miraculix-Linux NetworkManager[1064]: <info> (eth0): device state change: unavailable -> disconnected (reason 'carrier-changed') [20 30 40]
May  8 11:56:38 Miraculix-Linux NetworkManager[1064]: <info> Activation (eth0) starting connection 'Auto Ethernet'
May  8 11:56:38 Miraculix-Linux NetworkManager[1064]: <info> (eth0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
May  8 11:56:38 Miraculix-Linux NetworkManager[1064]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
May  8 11:56:38 Miraculix-Linux kernel: [96074.888943] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: None
May  8 11:56:38 Miraculix-Linux kernel: [96074.888950] e1000e 0000:00:19.0 eth0: 10/100 speed: disabling TSO
May  8 11:56:38 Miraculix-Linux kernel: [96074.888984] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
May  8 11:56:38 Miraculix-Linux NetworkManager[1064]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) started...
May  8 11:56:38 Miraculix-Linux NetworkManager[1064]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
May  8 11:56:38 Miraculix-Linux NetworkManager[1064]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
May  8 11:56:38 Miraculix-Linux NetworkManager[1064]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) starting...
May  8 11:56:38 Miraculix-Linux NetworkManager[1064]: <info> (eth0): device state change: prepare -> config (reason 'none') [40 50 0]
May  8 11:56:38 Miraculix-Linux NetworkManager[1064]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) successful.
May  8 11:56:38 Miraculix-Linux NetworkManager[1064]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
May  8 11:56:38 Miraculix-Linux NetworkManager[1064]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) complete.
May  8 11:56:38 Miraculix-Linux NetworkManager[1064]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
May  8 11:56:38 Miraculix-Linux NetworkManager[1064]: <info> (eth0): device state change: config -> ip-config (reason 'none') [50 70 0]
May  8 11:56:38 Miraculix-Linux NetworkManager[1064]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
May  8 11:56:39 Miraculix-Linux avahi-daemon[725]: Joining mDNS multicast group on interface eth0.IPv6 with address fe80::224:7eff:fe14:7c41.
May  8 11:56:39 Miraculix-Linux avahi-daemon[725]: New relevant interface eth0.IPv6 for mDNS.
May  8 11:56:39 Miraculix-Linux avahi-daemon[725]: Registering new address record for fe80::224:7eff:fe14:7c41 on eth0.*.
May  8 11:56:40 Miraculix-Linux NetworkManager[1064]: <info> Activation (eth0) Beginning IP6 addrconf.
May  8 11:56:40 Miraculix-Linux avahi-daemon[725]: Withdrawing address record for fe80::224:7eff:fe14:7c41 on eth0.
May  8 11:56:40 Miraculix-Linux avahi-daemon[725]: Leaving mDNS multicast group on interface eth0.IPv6 with address fe80::224:7eff:fe14:7c41.
May  8 11:56:40 Miraculix-Linux avahi-daemon[725]: Interface eth0.IPv6 no longer relevant for mDNS.
May  8 11:56:40 Miraculix-Linux NetworkManager[1064]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
May  8 11:56:40 Miraculix-Linux dhclient: Listening on LPF/eth0/00:24:7e:14:7c:41
May  8 11:56:40 Miraculix-Linux dhclient: Sending on   LPF/eth0/00:24:7e:14:7c:41
May  8 11:56:40 Miraculix-Linux dhclient: DHCPREQUEST of 10.20.87.96 on eth0 to 255.255.255.255 port 67 (xid=0x217b7893)
May  8 11:56:40 Miraculix-Linux NetworkManager[1064]: <info> (eth0): DHCPv4 state changed nbi -> preinit
May  8 11:56:40 Miraculix-Linux NetworkManager[1064]: <info> (eth0): DHCPv4 state changed preinit -> reboot
May  8 11:56:40 Miraculix-Linux NetworkManager[1064]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
May  8 11:56:40 Miraculix-Linux NetworkManager[1064]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) started...
May  8 11:56:40 Miraculix-Linux avahi-daemon[725]: Joining mDNS multicast group on interface eth0.IPv4 with address 10.20.87.96.
May  8 11:56:40 Miraculix-Linux avahi-daemon[725]: New relevant interface eth0.IPv4 for mDNS.
May  8 11:56:40 Miraculix-Linux avahi-daemon[725]: Registering new address record for 10.20.87.96 on eth0.IPv4.
May  8 11:56:41 Miraculix-Linux NetworkManager[1064]: <info> (eth0): device state change: ip-config -> secondaries (reason 'none') [70 90 0]
May  8 11:56:41 Miraculix-Linux NetworkManager[1064]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) complete.
May  8 11:56:41 Miraculix-Linux NetworkManager[1064]: <info> (eth0): device state change: secondaries -> activated (reason 'none') [90 100 0]
May  8 11:56:41 Miraculix-Linux NetworkManager[1064]: <info> Policy set 'Auto Ethernet' (eth0) as default for IPv4 routing and DNS.
May  8 11:56:41 Miraculix-Linux NetworkManager[1064]: <info> Activation (eth0) successful, device activated.
May  8 11:56:41 Miraculix-Linux avahi-daemon[725]: Joining mDNS multicast group on interface eth0.IPv6 with address fe80::224:7eff:fe14:7c41.
May  8 11:56:41 Miraculix-Linux avahi-daemon[725]: New relevant interface eth0.IPv6 for mDNS.
May  8 11:56:41 Miraculix-Linux avahi-daemon[725]: Registering new address record for fe80::224:7eff:fe14:7c41 on eth0.*.
May  8 11:57:00 Miraculix-Linux NetworkManager[1064]: <info> (eth0): IP6 addrconf timed out or failed.
May  8 11:57:00 Miraculix-Linux NetworkManager[1064]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
May  8 11:57:00 Miraculix-Linux NetworkManager[1064]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) started...
May  8 11:57:00 Miraculix-Linux NetworkManager[1064]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
May  8 12:18:42 Miraculix-Linux NetworkManager[1064]: <info> (eth0): carrier now OFF (device state 100, deferring action for 4 seconds)
May  8 12:18:42 Miraculix-Linux kernel: [97398.644148] e1000e: eth0 NIC Link is Down
May  8 12:18:46 Miraculix-Linux NetworkManager[1064]: <info> (eth0): device state change: activated -> unavailable (reason 'carrier-changed') [100 20 40]
May  8 12:18:46 Miraculix-Linux NetworkManager[1064]: <info> (eth0): deactivating device (reason 'carrier-changed') [40]
May  8 12:18:46 Miraculix-Linux NetworkManager[1064]: <info> (eth0): canceled DHCP transaction, DHCP client pid 17748
May  8 12:18:46 Miraculix-Linux avahi-daemon[725]: Withdrawing address record for fe80::224:7eff:fe14:7c41 on eth0.
May  8 12:18:46 Miraculix-Linux avahi-daemon[725]: Leaving mDNS multicast group on interface eth0.IPv6 with address fe80::224:7eff:fe14:7c41.
May  8 12:18:46 Miraculix-Linux avahi-daemon[725]: Interface eth0.IPv6 no longer relevant for mDNS.
May  8 12:18:46 Miraculix-Linux avahi-daemon[725]: Withdrawing address record for 10.20.87.96 on eth0.
May  8 12:18:46 Miraculix-Linux avahi-daemon[725]: Leaving mDNS multicast group on interface eth0.IPv4 with address 10.20.87.96.
May  8 12:18:46 Miraculix-Linux avahi-daemon[725]: Interface eth0.IPv4 no longer relevant for mDNS.
May  8 12:18:46 Miraculix-Linux kernel: [97403.204199] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
May  8 12:19:20 Miraculix-Linux NetworkManager[1064]: <info> (eth0): device state change: unavailable -> unmanaged (reason 'sleeping') [20 10 37]
May  8 12:19:20 Miraculix-Linux NetworkManager[1064]: <info> (eth0): cleaning up...
May  8 12:19:20 Miraculix-Linux NetworkManager[1064]: <info> (eth0): taking down device.
May  8 12:19:20 Miraculix-Linux kernel: [97437.242594] e1000e 0000:00:19.0 eth0: MAC Wakeup cause - Link Status Change
May  8 13:32:46 Miraculix-Linux NetworkManager[1064]: <info> (eth0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
May  8 13:32:46 Miraculix-Linux NetworkManager[1064]: <info> (eth0): bringing up device.
May  8 13:32:46 Miraculix-Linux kernel: [97443.108452] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
May  8 13:32:46 Miraculix-Linux NetworkManager[1064]: <info> (eth0): preparing device.
May  8 13:32:46 Miraculix-Linux NetworkManager[1064]: <info> (eth0): deactivating device (reason 'managed') [2]
May  8 13:50:05 Miraculix-Linux NetworkManager[1064]: <info> (eth0): carrier now ON (device state 20)
May  8 13:50:05 Miraculix-Linux NetworkManager[1064]: <info> (eth0): device state change: unavailable -> disconnected (reason 'carrier-changed') [20 30 40]
May  8 13:50:05 Miraculix-Linux kernel: [98481.848954] e1000e: eth0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: None
May  8 13:50:05 Miraculix-Linux kernel: [98481.848997] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
May  8 13:50:05 Miraculix-Linux NetworkManager[1064]: <info> Activation (eth0) starting connection 'Auto Ethernet'
May  8 13:50:05 Miraculix-Linux NetworkManager[1064]: <info> (eth0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
May  8 13:50:05 Miraculix-Linux NetworkManager[1064]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
May  8 13:50:05 Miraculix-Linux NetworkManager[1064]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) started...
May  8 13:50:05 Miraculix-Linux NetworkManager[1064]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
May  8 13:50:05 Miraculix-Linux NetworkManager[1064]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
May  8 13:50:05 Miraculix-Linux NetworkManager[1064]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) starting...
May  8 13:50:05 Miraculix-Linux NetworkManager[1064]: <info> (eth0): device state change: prepare -> config (reason 'none') [40 50 0]
May  8 13:50:05 Miraculix-Linux NetworkManager[1064]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) successful.
May  8 13:50:05 Miraculix-Linux NetworkManager[1064]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
May  8 13:50:05 Miraculix-Linux NetworkManager[1064]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) complete.
May  8 13:50:05 Miraculix-Linux NetworkManager[1064]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
May  8 13:50:05 Miraculix-Linux NetworkManager[1064]: <info> (eth0): device state change: config -> ip-config (reason 'none') [50 70 0]
May  8 13:50:05 Miraculix-Linux NetworkManager[1064]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
May  8 13:50:05 Miraculix-Linux NetworkManager[1064]: <info> Activation (eth0) Beginning IP6 addrconf.
May  8 13:50:05 Miraculix-Linux NetworkManager[1064]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
May  8 13:50:05 Miraculix-Linux NetworkManager[1064]: <info> (eth0): DHCPv4 state changed nbi -> preinit
May  8 13:50:05 Miraculix-Linux dhclient: Listening on LPF/eth0/00:24:7e:14:7c:41
May  8 13:50:05 Miraculix-Linux dhclient: Sending on   LPF/eth0/00:24:7e:14:7c:41
May  8 13:50:05 Miraculix-Linux dhclient: DHCPREQUEST of 10.20.87.96 on eth0 to 255.255.255.255 port 67 (xid=0x5ad93210)
May  8 13:50:07 Miraculix-Linux avahi-daemon[725]: Joining mDNS multicast group on interface eth0.IPv6 with address fe80::224:7eff:fe14:7c41.
May  8 13:50:07 Miraculix-Linux avahi-daemon[725]: New relevant interface eth0.IPv6 for mDNS.
May  8 13:50:07 Miraculix-Linux avahi-daemon[725]: Registering new address record for fe80::224:7eff:fe14:7c41 on eth0.*.
May  8 13:50:08 Miraculix-Linux dhclient: DHCPREQUEST of 10.20.87.96 on eth0 to 255.255.255.255 port 67 (xid=0x5ad93210)
May  8 13:50:08 Miraculix-Linux NetworkManager[1064]: <info> (eth0): DHCPv4 state changed preinit -> reboot
May  8 13:50:08 Miraculix-Linux NetworkManager[1064]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
May  8 13:50:08 Miraculix-Linux NetworkManager[1064]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) started...
May  8 13:50:08 Miraculix-Linux avahi-daemon[725]: Joining mDNS multicast group on interface eth0.IPv4 with address 10.20.87.96.
May  8 13:50:08 Miraculix-Linux avahi-daemon[725]: New relevant interface eth0.IPv4 for mDNS.
May  8 13:50:08 Miraculix-Linux avahi-daemon[725]: Registering new address record for 10.20.87.96 on eth0.IPv4.
May  8 13:50:09 Miraculix-Linux NetworkManager[1064]: <info> (eth0): device state change: ip-config -> secondaries (reason 'none') [70 90 0]
May  8 13:50:09 Miraculix-Linux NetworkManager[1064]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) complete.
May  8 13:50:09 Miraculix-Linux NetworkManager[1064]: <info> (eth0): device state change: secondaries -> activated (reason 'none') [90 100 0]
May  8 13:50:09 Miraculix-Linux NetworkManager[1064]: <info> Policy set 'Auto Ethernet' (eth0) as default for IPv4 routing and DNS.
May  8 13:50:12 Miraculix-Linux NetworkManager[1064]: <info> Activation (eth0) successful, device activated.
May  8 13:50:25 Miraculix-Linux NetworkManager[1064]: <info> (eth0): IP6 addrconf timed out or failed.
May  8 13:50:25 Miraculix-Linux NetworkManager[1064]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
May  8 13:50:25 Miraculix-Linux NetworkManager[1064]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) started...
May  8 13:50:25 Miraculix-Linux NetworkManager[1064]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
alfs@Miraculix-Linux:~$

```


I'm not sure whether the lack of stability is caused by upgrade to Ubuntu 13.04 or whether it's cause by something different.
Worth noting is that I have experienced lots of trouble using PPTP type VPN (i.e. connecting to Microsoft Windows VPN service) as well, and due to this I manually upgraded network manager to version 0.9.8.0-1 (the network-manager-gnome systray applet is now v0.9.8.0-1ubuntu2). Until today, I have been able to connect both to ethernet cabled network and PPTP VPN networking (even after upgrade to 13.04).

A general error that has been present as far back as I can remember (I believe from Ubuntu v10) is that the nm-applet (now 'network-manager-gnome' systray applet) is "un-linked" to the network manager after some time, especially after suspending/awakening the laptop a few times. Symptoms include that VPN networks are disappearing from the 2nd level menu (i.e. when clicking VPN networks in the main dropdown, the 2nd level dropdown shows only a narrow grey stripe showing that a menu should be present, but now contents are found). Also, clicking on WiFi networks or Mobile broadband has no effect, and the status is sometimes shown erroneously. When opening the Network Manager application in a separat application window, it's still working correctly and showing all networsk + activating correctly what is selected.


From my side, this is no big deal, but I've seen many others struggling with the same type of problems. Less experienced users who are not able to maunally opening the Network Manager in a separate window will have to restart the laptop in order to fix this problem, which is a lot of hassle for many users.


Best regards
:-) alfs

---

### Post by dino99 on 2013-05-08
it should be interesting to know about the network chipset (using lshw), then glancing at the kernel module  (with modprobe). Maybe an issue with the kernel driver.

is there something usefull inside /var/log/dmesg about the network ?

---

### Post by grahammechanical on 2013-05-08
I did recognise it as your host name but then I got to thinking (silly me) and I found this

[http://ru.wikipedia.org/wiki/Miraculix](http://ru.wikipedia.org/wiki/Miraculix)

Now there is a coincidence! I am now guessing that this could be happening as the device moves from a IPv6 netwrok to an IPV4 network or the other way around. Or, (another silly thought) at the boundary between the two different networks.

Regards.

---

### Post by ventrical on 2013-05-08
> **alf.sagen@gmail.com said:**
> @grahammechanical,


The strange thing on networking, however, is that after a couple of hours this morning I moved into a conference room where I plugged the ethernet cable again. This time....voila...it all worked nicely and fully automatic. (There is nothing wrong with the ethernet cable or network -- moving back to my desk and re-plugging the initial cable, it auto-detected and switched on automatically again.)



  I had this problem while doing setups with Ubuntu in general on customers machines. Believe it or not, if you install Ubuntu via one service provider and then attempt to  switch to another service provider (here in Canada that would be COGECO)  there is a blocking protocol that will not allow Ubuntu on the network. This has also happened with the Live  USBs. On some networks  there is a wait-gate when a new MAC address is detected. So the new machine will force an election on the network and if the ISP is gated then that anomoly could happen.

my 2cents.

---

### Post by malchir on 2013-06-02
Just adding my 2 cents here that my T510i is having the same problem. If the machine is booted without a cable plugged in, it won't see any network connection although the less on the connector show a physical link. This machine has been running several Linux Mint versions (11(u11.04),12 (u11.10),13 (u12.04) and now 15 (u13.04 based)) and this is the first time I have problems with this.

[edit]
found another thread with a possible sollution:

[http://ubuntuforums.org/showthread.php?t=2140927&page=3](http://ubuntuforums.org/showthread.php?t=2140927&page=3)

in short : add pci=nomsi to the linux default line in Grub

---

