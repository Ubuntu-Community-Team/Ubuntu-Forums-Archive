---
title: "random server lockups..."
date: 2007-07-11
forum: Server Platforms
---

### Post by Betelgeuse on 2007-07-11
Hi,

I have a ubuntu 6.06 server machine running on an ISP's datacenter. it's sometimes stops running and I have to call the ISP  co-location support and tell them to reset the machine. Yesterday, it stops again but this time I tried to ping it and it was responding to pings but I could not connect to the machine with ssh. I'm using ssh on a different port to administer the machine and all the services that the machine running are bind DNS server for may domains and vmware-server 1.03 with 3 virtual machines (windows 2000 server). 
What logs should I look to see the source of lockups? I do not have physical access to the machine and the box is on a rack without display so I can not see the error message on the screen. All I have is ssh to access it and vmware-server console to access the virtual machines.

---

### Post by kebes on 2007-07-11
First step is to check all the log files in /var/log/

Start with "syslog" and see what it says. However all the logs are useful, so I would check them all.

If possible, take note of the times when the server is available and the time when it suddenly becomes unavailable. Then when you next are able to log in (after a reboot I guess) see if there is any strange activity around that time in the logfiles.

---

### Post by Betelgeuse on 2007-07-11
I've checked the syslog, auth.log and messages but I could not find any strange activity, but I'm new to linux so I do not see myself fully capable of interpreting those logs...

---

### Post by rickyjones on 2007-07-11
> **Betelgeuse said:**
> I've checked the syslog, auth.log and messages but I could not find any strange activity, but I'm new to linux so I do not see myself fully capable of interpreting those logs...

I'm not as capable as others in the community but if you post the log files then someone here might be able to help you decipher them correctly.

Hope it helps!

-Richard

---

### Post by Betelgeuse on 2007-07-11
Thanks...
I'll post the log files right after the next crash... The server now seems to run good since yesterday morning. 
So, which log files should I have to post?

---

### Post by rickyjones on 2007-07-11
> **Betelgeuse said:**
> Thanks...
I'll post the log files right after the next crash... The server now seems to run good since yesterday morning. 
So, which log files should I have to post?

I would post all the log files - you might want to sanitize IP addresses/etc... but the experts here will definitely want to see as much info in all the logs as possible.

---

### Post by Betelgeuse on 2007-07-11
> **rickyjones said:**
> I would post all the log files - you might want to sanitize IP addresses/etc... but the experts here will definitely want to see as much info in all the logs as possible.

But there are lots of log files in the /var/log directory. Thats why I asked about which one is significant...
and there are several log files of vmware-server in the /var/log/vmware directory too.

---

### Post by kebes on 2007-07-12
> **Betelgeuse said:**
> But there are lots of log files in the /var/log directory. Thats why I asked about which one is significant...
and there are several log files of vmware-server in the /var/log/vmware directory too.

It's difficult to say which log file is "important" because it really depends on what the problem is (is it just net connectivity that is lost, or is the server completely crashed? etc.)

However, my guess is that the most important log files for this case would be:

syslog
kern.log
messages
user.log

auth.log may be important, too. However you may not want to post it since it contains real usernames and IP addresses, which you might want to reveal. You can replace those with other strings before posting, if you want. I would check through it and see if there are any error message or things like "failed login" ... it could be that your server is getting swamped with bogus login attempts or something. See if there is a long list of failed logins, which indicates someone trying to break into your system and/or a denial-of-service attack.

Other ones to look at, though probably less important:
acpid
apache2/error.log

(Note that if any of the logfiles are empty, check the most recent backup... e.g. if messages is empty, check messages.0)


The most useful thing, though, is to narrow down a time when the server died. If possible, open a terminal and login to the server. Then leave a command running that keeps updating the time (such as "top"). Leave the terminal running. When the server crashes (or whatever it is doing), you'll be logged out of the remote session, and the on-screen information (from "top" or whatever) will show you at exactly what moment the connection was lost.

Knowing this time makes it alot easier to search through the logfiles. Using "top" is also good because you'll have a snapshot of processes that were running just before the problem occurred. It may also give you other clues... for instance, when the server "goes bad", maybe it's only because it's refusing new connections? Maybe your old ssh connections will still work... that would be a useful clue.


P.S.: You mentioned VMWare... is the server running inside a VMWare session?

---

### Post by Betelgeuse on 2007-07-17
Hello !

My server had one of those lockups again...
I've looked at the log files but I do not see what caused the problem.
I've called the ISP datacenter techs and ask them if there was any error messages on the screen and he told me there was some strange message on the screen and he read me the normal console login prompt and he was expecting a windows login screen. I think this was the first time he saw a linux login prompt. 

here are the log files. I've put only the last several lines before the reboot.

/var/log/kern.log :
-------------------
```

Jul 16 13:45:50 evrimweb0 kernel: [43253446.780000] /dev/vmmon[4141]: host clock rate change request 101 -> 100
Jul 16 14:45:40 evrimweb0 kernel: [43257037.130000] /dev/vmmon[4141]: host clock rate change request 100 -> 101
Jul 16 14:45:50 evrimweb0 kernel: [43257047.140000] /dev/vmmon[4141]: host clock rate change request 101 -> 100
Jul 16 15:45:40 evrimweb0 kernel: [43260637.210000] /dev/vmmon[4141]: host clock rate change request 100 -> 101
Jul 16 15:45:50 evrimweb0 kernel: [43260647.210000] /dev/vmmon[4141]: host clock rate change request 101 -> 100
Jul 16 16:45:40 evrimweb0 kernel: [43264237.610000] /dev/vmmon[4141]: host clock rate change request 100 -> 101
Jul 16 16:45:50 evrimweb0 kernel: [43264247.610000] /dev/vmmon[4141]: host clock rate change request 101 -> 100
Jul 16 17:45:41 evrimweb0 kernel: [43267837.690000] /dev/vmmon[4141]: host clock rate change request 100 -> 101
Jul 16 17:45:51 evrimweb0 kernel: [43267847.680000] /dev/vmmon[4141]: host clock rate change request 101 -> 100
Jul 16 18:45:41 evrimweb0 kernel: [43271438.000000] /dev/vmmon[4141]: host clock rate change request 100 -> 101
Jul 16 18:45:51 evrimweb0 kernel: [43271447.990000] /dev/vmmon[4141]: host clock rate change request 101 -> 100
Jul 16 19:23:13 evrimweb0 kernel: [43273690.350000] KERNEL: assertion (!sk->sk_forward_alloc) failed at net/core/stream.c (279)
Jul 16 19:23:13 evrimweb0 kernel: [43273690.360000] KERNEL: assertion (!sk->sk_forward_alloc) failed at net/ipv4/af_inet.c (148)
Jul 16 19:45:41 evrimweb0 kernel: [43275038.110000] /dev/vmmon[4141]: host clock rate change request 100 -> 101
Jul 16 19:45:51 evrimweb0 kernel: [43275048.110000] /dev/vmmon[4141]: host clock rate change request 101 -> 100
Jul 16 20:45:41 evrimweb0 kernel: [43278638.360000] /dev/vmmon[4141]: host clock rate change request 100 -> 101
Jul 16 20:45:51 evrimweb0 kernel: [43278648.360000] /dev/vmmon[4141]: host clock rate change request 101 -> 100
Jul 16 21:45:42 evrimweb0 kernel: [43282238.710000] /dev/vmmon[4141]: host clock rate change request 100 -> 101
Jul 16 21:45:52 evrimweb0 kernel: [43282248.710000] /dev/vmmon[4141]: host clock rate change request 101 -> 100
Jul 16 22:45:42 evrimweb0 kernel: [43285839.130000] /dev/vmmon[4141]: host clock rate change request 100 -> 101
Jul 16 22:45:52 evrimweb0 kernel: [43285849.140000] /dev/vmmon[4141]: host clock rate change request 101 -> 100
Jul 16 23:43:09 evrimweb0 kernel: [43289286.030000] /dev/vmmon[4141]: host clock rate change request 100 -> 101
Jul 16 23:43:19 evrimweb0 kernel: [43289296.080000] /dev/vmmon[4141]: host clock rate change request 101 -> 83
Jul 16 23:43:28 evrimweb0 kernel: [43289304.970000] /dev/vmmon[4141]: host clock rate change request 83 -> 100
Jul 16 23:43:39 evrimweb0 kernel: [43289315.770000] /dev/vmmon[4141]: host clock rate change request 100 -> 101
Jul 16 23:43:49 evrimweb0 kernel: [43289325.780000] /dev/vmmon[4141]: host clock rate change request 101 -> 100
Jul 16 23:45:38 evrimweb0 kernel: [43289435.040000] /dev/vmmon[4141]: host clock rate change request 100 -> 101
Jul 16 23:45:48 evrimweb0 kernel: [43289445.030000] /dev/vmmon[4141]: host clock rate change request 101 -> 100
Jul 17 00:45:42 evrimweb0 kernel: [43293039.550000] /dev/vmmon[4141]: host clock rate change request 100 -> 101
Jul 17 00:45:52 evrimweb0 kernel: [43293049.540000] /dev/vmmon[4141]: host clock rate change request 101 -> 100
Jul 17 01:45:42 evrimweb0 kernel: [43296639.580000] /dev/vmmon[4141]: host clock rate change request 100 -> 101
Jul 17 01:45:52 evrimweb0 kernel: [43296649.580000] /dev/vmmon[4141]: host clock rate change request 101 -> 100
Jul 17 02:45:43 evrimweb0 kernel: [43300239.830000] /dev/vmmon[4141]: host clock rate change request 100 -> 101
Jul 17 02:45:53 evrimweb0 kernel: [43300249.840000] /dev/vmmon[4141]: host clock rate change request 101 -> 100
Jul 17 03:45:43 evrimweb0 kernel: [43303840.050000] /dev/vmmon[4141]: host clock rate change request 100 -> 101
Jul 17 03:45:53 evrimweb0 kernel: [43303850.060000] /dev/vmmon[4141]: host clock rate change request 101 -> 100
Jul 17 04:50:43 evrimweb0 kernel: [43307740.320000] /dev/vmmon[4141]: host clock rate change request 100 -> 101
Jul 17 04:50:53 evrimweb0 kernel: [43307750.320000] /dev/vmmon[4141]: host clock rate change request 101 -> 100
Jul 17 05:50:44 evrimweb0 kernel: [43311340.780000] /dev/vmmon[4141]: host clock rate change request 100 -> 101
Jul 17 05:50:54 evrimweb0 kernel: [43311350.770000] /dev/vmmon[4141]: host clock rate change request 101 -> 100
Jul 17 06:50:44 evrimweb0 kernel: [43314940.760000] /dev/vmmon[4141]: host clock rate change request 100 -> 101
Jul 17 06:50:54 evrimweb0 kernel: [43314950.750000] /dev/vmmon[4141]: host clock rate change request 101 -> 100
Jul 17 07:50:44 evrimweb0 kernel: [43318541.030000] /dev/vmmon[4141]: host clock rate change request 100 -> 101
Jul 17 07:50:54 evrimweb0 kernel: [43318551.030000] /dev/vmmon[4141]: host clock rate change request 101 -> 100
Jul 17 08:50:44 evrimweb0 kernel: [43322141.260000] /dev/vmmon[4141]: host clock rate change request 100 -> 101
Jul 17 08:50:54 evrimweb0 kernel: [43322151.270000] /dev/vmmon[4141]: host clock rate change request 101 -> 100
Jul 17 09:50:44 evrimweb0 kernel: [43325741.560000] /dev/vmmon[4141]: host clock rate change request 100 -> 101
Jul 17 09:50:54 evrimweb0 kernel: [43325751.560000] /dev/vmmon[4141]: host clock rate change request 101 -> 100
Jul 17 10:50:45 evrimweb0 kernel: [43329341.800000] /dev/vmmon[4141]: host clock rate change request 100 -> 101
Jul 17 10:50:55 evrimweb0 kernel: [43329351.800000] /dev/vmmon[4141]: host clock rate change request 101 -> 100
Jul 17 11:50:45 evrimweb0 kernel: [43332942.240000] /dev/vmmon[4141]: host clock rate change request 100 -> 101
Jul 17 11:50:55 evrimweb0 kernel: [43332952.240000] /dev/vmmon[4141]: host clock rate change request 101 -> 100
Jul 17 12:50:45 evrimweb0 kernel: [43336542.220000] /dev/vmmon[4141]: host clock rate change request 100 -> 101
Jul 17 12:50:55 evrimweb0 kernel: [43336552.230000] /dev/vmmon[4141]: host clock rate change request 101 -> 100
Jul 17 13:50:45 evrimweb0 kernel: [43340142.600000] /dev/vmmon[4141]: host clock rate change request 100 -> 101
Jul 17 13:50:55 evrimweb0 kernel: [43340152.600000] /dev/vmmon[4141]: host clock rate change request 101 -> 100

```
------------
```

/var/log/messages :
--------------
Jul 17 07:46:18 evrimweb0 -- MARK --
Jul 17 08:06:19 evrimweb0 -- MARK --
Jul 17 08:26:19 evrimweb0 -- MARK --
Jul 17 08:46:19 evrimweb0 -- MARK --
Jul 17 09:06:20 evrimweb0 -- MARK --
Jul 17 09:26:20 evrimweb0 -- MARK --
Jul 17 09:46:21 evrimweb0 -- MARK --
Jul 17 10:06:21 evrimweb0 -- MARK --
Jul 17 10:26:22 evrimweb0 -- MARK --
Jul 17 10:46:22 evrimweb0 -- MARK --
Jul 17 11:06:23 evrimweb0 -- MARK --
Jul 17 11:26:23 evrimweb0 -- MARK --
Jul 17 11:46:24 evrimweb0 -- MARK --
Jul 17 12:06:24 evrimweb0 -- MARK --
Jul 17 12:26:24 evrimweb0 -- MARK --
Jul 17 12:46:25 evrimweb0 -- MARK --
Jul 17 13:06:25 evrimweb0 -- MARK --
Jul 17 13:26:26 evrimweb0 -- MARK --
Jul 17 13:46:26 evrimweb0 -- MARK --
Jul 17 14:30:36 evrimweb0 syslogd 1.4.1#17ubuntu7.1: restart.
Jul 17 14:30:36 evrimweb0 kernel: Inspecting /boot/System.map-2.6.15-28-server
Jul 17 14:30:36 evrimweb0 kernel: Loaded 23274 symbols from /boot/System.map-2.6.15-28-server.
Jul 17 14:30:36 evrimweb0 kernel: Symbols match kernel version 2.6.15.
Jul 17 14:30:36 evrimweb0 kernel: No module symbols loaded - kernel modules not enabled.
Jul 17 14:30:36 evrimweb0 kernel: [42949372.960000] Linux version 2.6.15-28-server (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 SMP Thu May 10 10:40:27 UTC 2007
Jul 17 14:30:36 evrimweb0 kernel: [42949372.960000] BIOS-provided physical RAM map:
Jul 17 14:30:36 evrimweb0 kernel: [42949372.960000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
Jul 17 14:30:36 evrimweb0 kernel: [42949372.960000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
Jul 17 14:30:36 evrimweb0 kernel: [42949372.960000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Jul 17 14:30:36 evrimweb0 kernel: [42949372.960000]  BIOS-e820: 0000000000100000 - 000000007fee0000 (usable)
Jul 17 14:30:36 evrimweb0 kernel: [42949372.960000]  BIOS-e820: 000000007fee0000 - 000000007fee3000 (ACPI NVS)
Jul 17 14:30:36 evrimweb0 kernel: [42949372.960000]  BIOS-e820: 000000007fee3000 - 000000007fef0000 (ACPI data)
Jul 17 14:30:36 evrimweb0 kernel: [42949372.960000]  BIOS-e820: 000000007fef0000 - 000000007ff00000 (reserved)
Jul 17 14:30:36 evrimweb0 kernel: [42949372.960000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
Jul 17 14:30:36 evrimweb0 kernel: [42949372.960000] 1150MB HIGHMEM available.
Jul 17 14:30:36 evrimweb0 kernel: [42949372.960000] 896MB LOWMEM available.
Jul 17 14:30:36 evrimweb0 kernel: [42949372.960000] found SMP MP-table at 000f5570
Jul 17 14:30:36 evrimweb0 kernel: [42949372.960000] DMI 2.3 present.
Jul 17 14:30:36 evrimweb0 kernel: [42949372.960000] ACPI: PM-Timer IO Port: 0x408
Jul 17 14:30:36 evrimweb0 kernel: [42949372.960000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Jul 17 14:30:36 evrimweb0 kernel: [42949372.960000] Processor #0 15:4 APIC version 20
Jul 17 14:30:36 evrimweb0 kernel: [42949372.960000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Jul 17 14:30:36 evrimweb0 kernel: [42949372.960000] Processor #1 15:4 APIC version 20
Jul 17 14:30:36 evrimweb0 kernel: [42949372.960000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Jul 17 14:30:36 evrimweb0 kernel: [42949372.960000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Jul 17 14:30:36 evrimweb0 kernel: [42949372.960000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Jul 17 14:30:36 evrimweb0 kernel: [42949372.960000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
Jul 17 14:30:36 evrimweb0 kernel: [42949372.960000] ACPI: IOAPIC (id[0x03] address[0xfec10000] gsi_base[24])
Jul 17 14:30:36 evrimweb0 kernel: [42949372.960000] IOAPIC[1]: apic_id 3, version 32, address 0xfec10000, GSI 24-47
Jul 17 14:30:36 evrimweb0 kernel: [42949372.960000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Jul 17 14:30:36 evrimweb0 kernel: [42949372.960000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Jul 17 14:30:36 evrimweb0 kernel: [42949372.960000] Enabling APIC mode:  Flat.  Using 2 I/O APICs
Jul 17 14:30:36 evrimweb0 kernel: [42949372.960000] Using ACPI (MADT) for SMP configuration information
Jul 17 14:30:36 evrimweb0 kernel: [42949372.960000] Allocating PCI resources starting at 80000000 (gap: 7ff00000:7ed00000)
Jul 17 14:30:36 evrimweb0 kernel: [42949372.960000] Built 1 zonelists
Jul 17 14:30:36 evrimweb0 kernel: [42949372.960000] Kernel command line: root=/dev/md0 ro quiet splash
Jul 17 14:30:36 evrimweb0 kernel: [42949372.960000] Initializing CPU#0
Jul 17 14:30:36 evrimweb0 kernel: [42949372.960000] PID hash table entries: 4096 (order: 12, 65536 bytes)
Jul 17 14:30:36 evrimweb0 kernel: [42949372.960000] Detected 2992.706 MHz processor.
Jul 17 14:30:36 evrimweb0 kernel: [42949372.960000] Using pmtmr for high-res timesource
Jul 17 14:30:36 evrimweb0 kernel: [42949372.960000] Console: colour VGA+ 80x25
Jul 17 14:30:36 evrimweb0 kernel: [42949375.030000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Jul 17 14:30:36 evrimweb0 kernel: [42949375.030000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Jul 17 14:30:36 evrimweb0 kernel: [42949375.140000] Memory: 2067064k/2096000k available (2087k kernel code, 27784k reserved, 620k data, 332k init, 1178496k highmem)
Jul 17 14:30:36 evrimweb0 kernel: [42949375.140000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Jul 17 14:30:36 evrimweb0 kernel: [42949375.290000] Calibrating delay using timer specific routine.. 5989.85 BogoMIPS (lpj=29949283)
Jul 17 14:30:36 evrimweb0 kernel: [42949375.290000] Security Framework v1.0.0 initialized
Jul 17 14:30:36 evrimweb0 kernel: [42949375.290000] SELinux:  Disabled at boot.
Jul 17 14:30:36 evrimweb0 kernel: [42949375.290000] Mount-cache hash table entries: 512
Jul 17 14:30:36 evrimweb0 kernel: [42949375.290000] monitor/mwait feature present.
Jul 17 14:30:36 evrimweb0 kernel: [42949375.290000] using mwait in idle threads.
Jul 17 14:30:36 evrimweb0 kernel: [42949375.290000] CPU: Trace cache: 12K uops, L1 D cache: 16K
Jul 17 14:30:36 evrimweb0 kernel: [42949375.290000] CPU: L2 cache: 1024K
Jul 17 14:30:36 evrimweb0 kernel: [42949375.290000] CPU: Hyper-Threading is disabled
Jul 17 14:30:36 evrimweb0 kernel: [42949375.290000] mtrr: v2.0 (20020519)
Jul 17 14:30:36 evrimweb0 kernel: [42949375.290000] Enabling fast FPU save and restore... done.
Jul 17 14:30:36 evrimweb0 kernel: [42949375.290000] Enabling unmasked SIMD FPU exception support... done.
Jul 17 14:30:36 evrimweb0 kernel: [42949375.290000] Checking 'hlt' instruction... OK.
Jul 17 14:30:36 evrimweb0 kernel: [42949375.330000] checking if image is initramfs... it is
Jul 17 14:30:36 evrimweb0 kernel: [42949375.810000] Freeing initrd memory: 6789k freed
Jul 17 14:30:36 evrimweb0 kernel: [42949375.820000] ACPI: Looking for DSDT ... not found!
Jul 17 14:30:36 evrimweb0 kernel: [42949375.820000] CPU0: Intel(R) Pentium(R) 4 CPU 3.00GHz stepping 01
Jul 17 14:30:36 evrimweb0 kernel: [42949375.820000] Booting processor 1/1 eip 3000
Jul 17 14:30:36 evrimweb0 kernel: [42949375.830000] Initializing CPU#1
Jul 17 14:30:36 evrimweb0 kernel: [42949375.980000] Calibrating delay using timer specific routine.. 5985.16 BogoMIPS (lpj=29925837)
Jul 17 14:30:36 evrimweb0 kernel: [42949375.980000] monitor/mwait feature present.
Jul 17 14:30:36 evrimweb0 kernel: [42949375.980000] CPU: Trace cache: 12K uops, L1 D cache: 16K
Jul 17 14:30:36 evrimweb0 kernel: [42949375.980000] CPU: L2 cache: 1024K
Jul 17 14:30:36 evrimweb0 kernel: [42949375.980000] CPU: Hyper-Threading is disabled
Jul 17 14:30:36 evrimweb0 kernel: [42949375.980000] CPU1: Intel(R) Pentium(R) 4 CPU 3.00GHz stepping 01
Jul 17 14:30:36 evrimweb0 kernel: [42949375.980000] Total of 2 processors activated (11975.02 BogoMIPS).
Jul 17 14:30:36 evrimweb0 kernel: [42949375.980000] ENABLING IO-APIC IRQs
Jul 17 14:30:36 evrimweb0 kernel: [42949375.980000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Jul 17 14:30:36 evrimweb0 kernel: [42949376.190000] checking TSC synchronization across 2 CPUs: passed.
Jul 17 14:30:36 evrimweb0 kernel: [42949376.200000] Brought up 2 CPUs
Jul 17 14:30:36 evrimweb0 kernel: [42949376.200000] NET: Registered protocol family 16
Jul 17 14:30:36 evrimweb0 kernel: [42949376.200000] EISA bus registered
Jul 17 14:30:36 evrimweb0 kernel: [42949376.200000] ACPI: bus type pci registered
Jul 17 14:30:36 evrimweb0 kernel: [42949376.200000] PCI: PCI BIOS revision 2.10 entry at 0xfb800, last bus=3
Jul 17 14:30:36 evrimweb0 kernel: [42949376.200000] PCI: Using configuration type 1
Jul 17 14:30:36 evrimweb0 kernel: [42949376.200000] ACPI: Subsystem revision 20051216
Jul 17 14:30:36 evrimweb0 kernel: [42949376.200000] ACPI: Interpreter enabled
Jul 17 14:30:36 evrimweb0 kernel: [42949376.200000] ACPI: Using IOAPIC for interrupt routing
Jul 17 14:30:36 evrimweb0 kernel: [42949376.200000] ACPI: PCI Root Bridge [PCI0] (0000:00)
Jul 17 14:30:36 evrimweb0 kernel: [42949376.200000] PCI quirk: region 0400-047f claimed by ICH4 ACPI/GPIO/TCO
Jul 17 14:30:36 evrimweb0 kernel: [42949376.200000] PCI quirk: region 0480-04bf claimed by ICH4 GPIO
Jul 17 14:30:36 evrimweb0 kernel: [42949376.200000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
Jul 17 14:30:36 evrimweb0 kernel: [42949376.200000] PCI: Transparent bridge - 0000:00:1e.0
Jul 17 14:30:36 evrimweb0 kernel: [42949376.220000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 10 11 *12 14 15)
Jul 17 14:30:36 evrimweb0 kernel: [42949376.220000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 9 *10 11 12 14 15)
Jul 17 14:30:36 evrimweb0 kernel: [42949376.220000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 10 *11 12 14 15)
Jul 17 14:30:36 evrimweb0 kernel: [42949376.220000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 *7 9 10 11 12 14 15)
Jul 17 14:30:36 evrimweb0 kernel: [42949376.220000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
Jul 17 14:30:36 evrimweb0 kernel: [42949376.220000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
Jul 17 14:30:36 evrimweb0 kernel: [42949376.220000] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
Jul 17 14:30:36 evrimweb0 kernel: [42949376.220000] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 *5 7 9 10 11 12 14 15)
Jul 17 14:30:36 evrimweb0 kernel: [42949376.220000] Linux Plug and Play Support v0.97 (c) Adam Belay
Jul 17 14:30:36 evrimweb0 kernel: [42949376.220000] pnp: PnP ACPI init
Jul 17 14:30:36 evrimweb0 kernel: [42949376.220000] pnp: PnP ACPI: found 9 devices
Jul 17 14:30:36 evrimweb0 kernel: [42949376.220000] PnPBIOS: Disabled by ACPI PNP
Jul 17 14:30:36 evrimweb0 kernel: [42949376.220000] PCI: Using ACPI for IRQ routing
Jul 17 14:30:36 evrimweb0 kernel: [42949376.220000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Jul 17 14:30:36 evrimweb0 kernel: [42949376.250000] pnp: 00:05: ioport range 0x400-0x4bf could not be reserved
Jul 17 14:30:36 evrimweb0 kernel: [42949376.250000] PCI: Bridge: 0000:00:03.0
Jul 17 14:30:36 evrimweb0 kernel: [42949376.250000]   IO window: a000-afff
Jul 17 14:30:36 evrimweb0 kernel: [42949376.250000]   MEM window: f0000000-f1ffffff
Jul 17 14:30:36 evrimweb0 kernel: [42949376.250000]   PREFETCH window: 80000000-800fffff
Jul 17 14:30:36 evrimweb0 kernel: [42949376.250000] PCI: Bridge: 0000:00:1c.0
Jul 17 14:30:36 evrimweb0 kernel: [42949376.250000]   IO window: disabled.
Jul 17 14:30:36 evrimweb0 kernel: [42949376.250000]   MEM window: disabled.
Jul 17 14:30:36 evrimweb0 kernel: [42949376.250000]   PREFETCH window: disabled.
Jul 17 14:30:36 evrimweb0 kernel: [42949376.250000] PCI: Bridge: 0000:00:1e.0
Jul 17 14:30:36 evrimweb0 kernel: [42949376.250000]   IO window: b000-bfff
Jul 17 14:30:36 evrimweb0 kernel: [42949376.250000]   MEM window: f2000000-f4ffffff
Jul 17 14:30:36 evrimweb0 kernel: [42949376.250000]   PREFETCH window: 80100000-801fffff
Jul 17 14:30:36 evrimweb0 kernel: [42949376.250000] audit: initializing netlink socket (disabled)
Jul 17 14:30:36 evrimweb0 kernel: [42949376.250000] audit(1184671820.240:1): initialized
Jul 17 14:30:36 evrimweb0 kernel: [42949376.250000] highmem bounce pool size: 64 pages
Jul 17 14:30:36 evrimweb0 kernel: [42949376.250000] VFS: Disk quotas dquot_6.5.1
Jul 17 14:30:36 evrimweb0 kernel: [42949376.250000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Jul 17 14:30:36 evrimweb0 kernel: [42949376.250000] Initializing Cryptographic API
Jul 17 14:30:36 evrimweb0 kernel: [42949376.250000] io scheduler noop registered
Jul 17 14:30:36 evrimweb0 kernel: [42949376.250000] io scheduler anticipatory registered
Jul 17 14:30:36 evrimweb0 kernel: [42949376.250000] io scheduler deadline registered
Jul 17 14:30:36 evrimweb0 kernel: [42949376.250000] io scheduler cfq registered
Jul 17 14:30:36 evrimweb0 kernel: [42949376.250000] isapnp: Scanning for PnP cards...
Jul 17 14:30:36 evrimweb0 kernel: [42949376.610000] isapnp: No Plug & Play device found
Jul 17 14:30:36 evrimweb0 kernel: [42949376.630000] Real Time Clock Driver v1.12
Jul 17 14:30:36 evrimweb0 kernel: [42949376.630000] PNP: No PS/2 controller found. Probing ports directly.
Jul 17 14:30:36 evrimweb0 kernel: [42949376.630000] serio: i8042 AUX port at 0x60,0x64 irq 12
Jul 17 14:30:36 evrimweb0 kernel: [42949376.630000] serio: i8042 KBD port at 0x60,0x64 irq 1
Jul 17 14:30:36 evrimweb0 kernel: [42949376.630000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
Jul 17 14:30:36 evrimweb0 kernel: [42949376.630000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Jul 17 14:30:36 evrimweb0 kernel: [42949376.630000] 00:04: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Jul 17 14:30:36 evrimweb0 kernel: [42949376.630000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Jul 17 14:30:36 evrimweb0 kernel: [42949376.630000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Jul 17 14:30:36 evrimweb0 kernel: [42949376.630000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Jul 17 14:30:36 evrimweb0 kernel: [42949376.630000] mice: PS/2 mouse device common for all mice
Jul 17 14:30:36 evrimweb0 kernel: [42949376.630000] EISA: Probing bus 0 at eisa.0
Jul 17 14:30:36 evrimweb0 kernel: [42949376.630000] EISA: Detected 0 cards.
Jul 17 14:30:36 evrimweb0 kernel: [42949376.630000] NET: Registered protocol family 2
Jul 17 14:30:36 evrimweb0 kernel: [42949376.770000] IP route cache hash table entries: 65536 (order: 6, 262144 bytes)
Jul 17 14:30:36 evrimweb0 kernel: [42949376.770000] TCP established hash table entries: 262144 (order: 9, 2097152 bytes)
Jul 17 14:30:36 evrimweb0 kernel: [42949376.770000] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Jul 17 14:30:36 evrimweb0 kernel: [42949376.770000] TCP: Hash tables configured (established 262144 bind 65536)
Jul 17 14:30:36 evrimweb0 kernel: [42949376.770000] TCP reno registered
Jul 17 14:30:36 evrimweb0 kernel: [42949376.770000] TCP bic registered
Jul 17 14:30:36 evrimweb0 kernel: [42949376.770000] NET: Registered protocol family 1
Jul 17 14:30:36 evrimweb0 kernel: [42949376.770000] NET: Registered protocol family 8
Jul 17 14:30:36 evrimweb0 kernel: [42949376.770000] NET: Registered protocol family 20
Jul 17 14:30:36 evrimweb0 kernel: [42949376.770000] Starting balanced_irq
Jul 17 14:30:36 evrimweb0 kernel: [42949376.770000] Using IPI No-Shortcut mode
Jul 17 14:30:36 evrimweb0 kernel: [42949376.770000] ACPI wakeup devices:
Jul 17 14:30:36 evrimweb0 kernel: [42949376.770000] PCI0 CSAD HUB0  HRB UAR1 USB0 USB1 USBE MODM
Jul 17 14:30:36 evrimweb0 kernel: [42949376.770000] ACPI: (supports S0 S1 S4 S5)
Jul 17 14:30:36 evrimweb0 kernel: [42949376.770000] Freeing unused kernel memory: 332k freed
Jul 17 14:30:36 evrimweb0 kernel: [42949376.810000] vga16fb: mapped to 0xc00a0000
Jul 17 14:30:36 evrimweb0 kernel: [42949376.960000] Console: switching to colour frame buffer device 80x25
Jul 17 14:30:36 evrimweb0 kernel: [42949376.960000] fb0: VGA16 VGA frame buffer device
Jul 17 14:30:36 evrimweb0 kernel: [42949376.970000] Capability LSM initialized
Jul 17 14:30:36 evrimweb0 kernel: [42949377.000000] ACPI: Fan [FAN] (on)
Jul 17 14:30:36 evrimweb0 kernel: [42949377.080000] ACPI: Thermal Zone [THRM] (43 C)
Jul 17 14:30:36 evrimweb0 kernel: [42949377.530000] ICH5: IDE controller at PCI slot 0000:00:1f.1
Jul 17 14:30:36 evrimweb0 kernel: [42949377.530000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 169
Jul 17 14:30:36 evrimweb0 kernel: [42949377.530000] ICH5: chipset revision 2
Jul 17 14:30:36 evrimweb0 kernel: [42949377.530000] ICH5: not 100%% native mode: will probe irqs later
Jul 17 14:30:36 evrimweb0 kernel: [42949377.530000]     ide0: BM-DMA at 0xf000-0xf007, BIOS settings: hda:pio, hdb:pio
Jul 17 14:30:36 evrimweb0 kernel: [42949377.530000]     ide1: BM-DMA at 0xf008-0xf00f, BIOS settings: hdc:DMA, hdd:pio
Jul 17 14:30:36 evrimweb0 kernel: [42949378.940000] hdc: ASUS CD-S520/A5, ATAPI CD/DVD-ROM drive
Jul 17 14:30:36 evrimweb0 kernel: [42949379.310000] ide1 at 0x170-0x177,0x376 on irq 15
Jul 17 14:30:36 evrimweb0 kernel: [42949379.310000] hdc: ATAPI 52X CD-ROM drive, 128kB Cache, UDMA(33)
Jul 17 14:30:36 evrimweb0 kernel: [42949379.310000] Uniform CD-ROM driver Revision: 3.20
Jul 17 14:30:36 evrimweb0 kernel: [42949379.340000] SCSI subsystem initialized
Jul 17 14:30:36 evrimweb0 kernel: [42949379.350000] ACPI: bus type scsi registered
Jul 17 14:30:36 evrimweb0 kernel: [42949379.350000] ACPI: PCI Interrupt 0000:00:1f.2[A] -> GSI 18 (level, low) -> IRQ 169
Jul 17 14:30:36 evrimweb0 kernel: [42949379.350000] ata1: PATA max UDMA/133 cmd 0xC800 ctl 0xCC02 bmdma 0xD800 irq 169
Jul 17 14:30:36 evrimweb0 kernel: [42949379.350000] ata2: PATA max UDMA/133 cmd 0xD000 ctl 0xD402 bmdma 0xD808 irq 169
Jul 17 14:30:36 evrimweb0 kernel: [42949379.550000] ata1: dev 0 ATA-7, max UDMA/133, 156301488 sectors: LBA48
Jul 17 14:30:36 evrimweb0 kernel: [42949379.550000] ata1: dev 0 configured for UDMA/133
Jul 17 14:30:36 evrimweb0 kernel: [42949379.550000] scsi0 : ata_piix
Jul 17 14:30:36 evrimweb0 kernel: [42949379.750000] ata2: dev 0 ATA-7, max UDMA/133, 156301488 sectors: LBA48
Jul 17 14:30:36 evrimweb0 kernel: [42949379.750000] ata2: dev 0 configured for UDMA/133
Jul 17 14:30:36 evrimweb0 kernel: [42949379.750000] scsi1 : ata_piix
Jul 17 14:30:36 evrimweb0 kernel: [42949379.750000]   Vendor: ATA       Model: ST380815AS        Rev: 3.AA
Jul 17 14:30:36 evrimweb0 kernel: [42949379.750000]   Type:   Direct-Access                      ANSI SCSI revision: 05
Jul 17 14:30:36 evrimweb0 kernel: [42949379.750000]   Vendor: ATA       Model: ST380815AS        Rev: 3.AA
Jul 17 14:30:36 evrimweb0 kernel: [42949379.750000]   Type:   Direct-Access                      ANSI SCSI revision: 05
Jul 17 14:30:36 evrimweb0 kernel: [42949379.760000] Driver 'sd' needs updating - please use bus_type methods
Jul 17 14:30:36 evrimweb0 kernel: [42949379.760000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
Jul 17 14:30:36 evrimweb0 kernel: [42949379.760000] SCSI device sda: drive cache: write back
Jul 17 14:30:36 evrimweb0 kernel: [42949379.760000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
Jul 17 14:30:36 evrimweb0 kernel: [42949379.760000] SCSI device sda: drive cache: write back
Jul 17 14:30:36 evrimweb0 kernel: [42949379.760000]  sda: sda1 sda2
Jul 17 14:30:36 evrimweb0 kernel: [42949379.790000] sd 0:0:0:0: Attached scsi disk sda
Jul 17 14:30:36 evrimweb0 kernel: [42949379.790000] SCSI device sdb: 156301488 512-byte hdwr sectors (80026 MB)
Jul 17 14:30:36 evrimweb0 kernel: [42949379.790000] SCSI device sdb: drive cache: write back
Jul 17 14:30:36 evrimweb0 kernel: [42949379.790000] SCSI device sdb: 156301488 512-byte hdwr sectors (80026 MB)
Jul 17 14:30:36 evrimweb0 kernel: [42949379.790000] SCSI device sdb: drive cache: write back
Jul 17 14:30:36 evrimweb0 kernel: [42949379.790000]  sdb: sdb1 sdb2
Jul 17 14:30:36 evrimweb0 kernel: [42949379.790000] sd 1:0:0:0: Attached scsi disk sdb
Jul 17 14:30:36 evrimweb0 kernel: [42949379.960000] usbcore: registered new driver usbfs
Jul 17 14:30:36 evrimweb0 kernel: [42949379.960000] usbcore: registered new driver hub
Jul 17 14:30:36 evrimweb0 kernel: [42949379.960000] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 177
Jul 17 14:30:36 evrimweb0 kernel: [42949379.960000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Jul 17 14:30:36 evrimweb0 kernel: [42949379.960000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
Jul 17 14:30:36 evrimweb0 kernel: [42949379.960000] ehci_hcd 0000:00:1d.7: irq 177, io mem 0xf5000000
Jul 17 14:30:36 evrimweb0 kernel: [42949379.970000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Jul 17 14:30:36 evrimweb0 kernel: [42949379.970000] hub 1-0:1.0: USB hub found
Jul 17 14:30:36 evrimweb0 kernel: [42949379.970000] hub 1-0:1.0: 4 ports detected
Jul 17 14:30:36 evrimweb0 kernel: [42949379.980000] USB Universal Host Controller Interface driver v2.3
Jul 17 14:30:36 evrimweb0 kernel: [42949379.980000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 185
Jul 17 14:30:36 evrimweb0 kernel: [42949379.980000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Jul 17 14:30:36 evrimweb0 kernel: [42949380.090000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
Jul 17 14:30:36 evrimweb0 kernel: [42949380.090000] uhci_hcd 0000:00:1d.0: irq 185, io base 0x0000c400
Jul 17 14:30:36 evrimweb0 kernel: [42949380.090000] hub 2-0:1.0: USB hub found
Jul 17 14:30:36 evrimweb0 kernel: [42949380.090000] hub 2-0:1.0: 2 ports detected
Jul 17 14:30:36 evrimweb0 kernel: [42949380.200000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 193
Jul 17 14:30:36 evrimweb0 kernel: [42949380.200000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Jul 17 14:30:36 evrimweb0 kernel: [42949380.210000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
Jul 17 14:30:36 evrimweb0 kernel: [42949380.210000] uhci_hcd 0000:00:1d.1: irq 193, io base 0x0000c000
Jul 17 14:30:36 evrimweb0 kernel: [42949380.210000] hub 3-0:1.0: USB hub found
Jul 17 14:30:36 evrimweb0 kernel: [42949380.210000] hub 3-0:1.0: 2 ports detected
Jul 17 14:30:36 evrimweb0 kernel: [42949380.600000] usb 3-1: new low speed USB device using uhci_hcd and address 2
Jul 17 14:30:36 evrimweb0 kernel: [42949380.850000] usbcore: registered new driver hiddev
Jul 17 14:30:36 evrimweb0 kernel: [42949380.870000] input: PTC HID PS/2 Keyboard - PS/2 Mouse as /class/input/input0
Jul 17 14:30:36 evrimweb0 kernel: [42949380.870000] input: USB HID v1.00 Keyboard [PTC HID PS/2 Keyboard - PS/2 Mouse] on usb-0000:00:1d.1-1
Jul 17 14:30:36 evrimweb0 kernel: [42949380.880000] input: PTC HID PS/2 Keyboard - PS/2 Mouse as /class/input/input1
Jul 17 14:30:36 evrimweb0 kernel: [42949380.880000] input: USB HID v1.00 Mouse [PTC HID PS/2 Keyboard - PS/2 Mouse] on usb-0000:00:1d.1-1
Jul 17 14:30:36 evrimweb0 kernel: [42949380.880000] usbcore: registered new driver usbhid
Jul 17 14:30:36 evrimweb0 kernel: [42949380.880000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
Jul 17 14:30:36 evrimweb0 kernel: [42949380.990000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
Jul 17 14:30:36 evrimweb0 kernel: [42949380.990000] md: bitmap version 4.39
Jul 17 14:30:36 evrimweb0 kernel: [42949380.990000] md: raid1 personality registered as nr 3
Jul 17 14:30:36 evrimweb0 kernel: [42949381.110000] md: md0 stopped.
Jul 17 14:30:36 evrimweb0 kernel: [42949381.110000] md: bind<sdb1>
Jul 17 14:30:36 evrimweb0 kernel: [42949381.110000] md: bind<sda1>
Jul 17 14:30:36 evrimweb0 kernel: [42949381.110000] raid1: raid set md0 active with 2 out of 2 mirrors
Jul 17 14:30:36 evrimweb0 kernel: [42949381.120000] md: md1 stopped.
Jul 17 14:30:36 evrimweb0 kernel: [42949381.120000] md: bind<sdb2>
Jul 17 14:30:36 evrimweb0 kernel: [42949381.130000] md: bind<sda2>
Jul 17 14:30:36 evrimweb0 kernel: [42949381.130000] raid1: raid set md1 active with 2 out of 2 mirrors
Jul 17 14:30:36 evrimweb0 kernel: [42949381.140000] Attempting manual resume
Jul 17 14:30:36 evrimweb0 kernel: [42949381.260000] EXT3-fs: INFO: recovery required on readonly filesystem.
Jul 17 14:30:36 evrimweb0 kernel: [42949381.260000] EXT3-fs: write access will be enabled during recovery.
Jul 17 14:30:36 evrimweb0 kernel: [42949382.520000] kjournald starting.  Commit interval 5 seconds
Jul 17 14:30:36 evrimweb0 kernel: [42949382.520000] EXT3-fs: md0: orphan cleanup on readonly fs
Jul 17 14:30:36 evrimweb0 kernel: [42949382.650000] EXT3-fs: md0: 4 orphan inodes deleted                  
Jul 17 14:30:36 evrimweb0 kernel: [42949382.650000] EXT3-fs: recovery complete.
Jul 17 14:30:36 evrimweb0 kernel: [42949382.680000] EXT3-fs: mounted filesystem with ordered data mode.
Jul 17 14:30:36 evrimweb0 kernel: [42949386.400000] ts: Compaq touchscreen protocol output
Jul 17 14:30:36 evrimweb0 kernel: [42949386.470000] sd 0:0:0:0: Attached scsi generic sg0 type 0
Jul 17 14:30:36 evrimweb0 kernel: [42949386.470000] sd 1:0:0:0: Attached scsi generic sg1 type 0
Jul 17 14:30:36 evrimweb0 kernel: [42949386.640000] Linux agpgart interface v0.101 (c) Dave Jones
Jul 17 14:30:36 evrimweb0 kernel: [42949386.640000] agpgart: Detected an Intel i875 Chipset.
Jul 17 14:30:36 evrimweb0 kernel: [42949386.650000] agpgart: AGP aperture is 256M @ 0xe0000000
Jul 17 14:30:36 evrimweb0 kernel: [42949386.850000] input: PC Speaker as /class/input/input2
Jul 17 14:30:36 evrimweb0 kernel: [42949387.010000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jul 17 14:30:36 evrimweb0 kernel: [42949387.030000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Jul 17 14:30:36 evrimweb0 kernel: [42949387.360000] Intel(R) PRO/1000 Network Driver - version 7.0.33-k2
Jul 17 14:30:36 evrimweb0 kernel: [42949387.360000] Copyright (c) 1999-2005 Intel Corporation.
Jul 17 14:30:36 evrimweb0 kernel: [42949387.360000] ACPI: PCI Interrupt 0000:01:01.0[A] -> GSI 18 (level, low) -> IRQ 169
Jul 17 14:30:36 evrimweb0 kernel: [42949387.430000] e1000: 0000:01:01.0: e1000_probe: (PCI:33MHz:32-bit) 00:11:d8:ea:63:a4
Jul 17 14:30:36 evrimweb0 kernel: [42949387.640000] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
Jul 17 14:30:36 evrimweb0 kernel: [42949387.640000] ACPI: PCI Interrupt 0000:03:05.0[A] -> GSI 17 (level, low) -> IRQ 201
Jul 17 14:30:36 evrimweb0 kernel: [42949387.920000] e1000: 0000:03:05.0: e1000_probe: (PCI:33MHz:32-bit) 00:11:d8:ea:63:a3
Jul 17 14:30:36 evrimweb0 kernel: [42949388.170000] e1000: eth1: e1000_probe: Intel(R) PRO/1000 Network Connection
Jul 17 14:30:36 evrimweb0 kernel: [42949388.510000] lp: driver loaded but no devices found
Jul 17 14:30:36 evrimweb0 kernel: [42949389.130000] e1000: eth0: e1000_watchdog_task: NIC Link is Up 100 Mbps Full Duplex
Jul 17 14:30:36 evrimweb0 kernel: [42949389.690000] Adding 2955832k swap on /dev/md1.  Priority:-1 extents:1 across:2955832k
Jul 17 14:30:36 evrimweb0 kernel: [42949389.770000] EXT3 FS on md0, internal journal
Jul 17 14:30:36 evrimweb0 kernel: [42949390.150000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
Jul 17 14:30:36 evrimweb0 kernel: [42949390.840000] cdrom: open failed.
Jul 17 14:30:36 evrimweb0 kernel: [42949395.710000] e1000: eth1: e1000_watchdog_task: NIC Link is Up 100 Mbps Full Duplex
Jul 17 14:30:38 evrimweb0 kernel: [42949397.560000] NET: Registered protocol family 10
Jul 17 14:30:38 evrimweb0 kernel: [42949397.560000] lo: Disabled Privacy Extensions
Jul 17 14:30:38 evrimweb0 kernel: [42949397.560000] IPv6 over IPv4 tunneling driver
Jul 17 14:30:39 evrimweb0 kernel: [42949398.120000] eth1: duplicate address detected!
Jul 17 14:30:40 evrimweb0 kernel: [42949399.020000] vmmon: module license 'unspecified' taints kernel.
Jul 17 14:30:40 evrimweb0 kernel: [42949399.450000] bridge-eth0: already up
Jul 17 14:30:40 evrimweb0 kernel: [42949399.470000] bridge-eth1: already up
Jul 17 14:30:44 evrimweb0 kernel: [42949403.190000] device eth0 entered promiscuous mode
Jul 17 14:30:44 evrimweb0 kernel: [42949403.190000] bridge-eth0: enabled promiscuous mode
Jul 17 14:30:44 evrimweb0 kernel: [42949403.190000] device eth1 entered promiscuous mode
Jul 17 14:30:44 evrimweb0 kernel: [42949403.190000] bridge-eth1: enabled promiscuous mode
Jul 17 14:35:04 evrimweb0 kernel: [42949663.090000] usb 3-1: USB disconnect, address 2
Jul 17 14:50:38 evrimweb0 -- MARK --

```
------------

This server only runs BIND9 DNS server and vmware-server. the vmware-server software runs 3 virtual machines. There are no other services loaded. No apache, no nothing. I think the problem is with the vmware-server software but I'm not sure.

---

### Post by Betelgeuse on 2007-07-17
> **kebes said:**
> P.S.: You mentioned VMWare... is the server running inside a VMWare session?

No, My server runs on a bare metal Asus rackmount server machine and runs vmware server service to host 3 virtual windows server machines running inside vmware server.

---

### Post by katsumi on 2007-07-20
I am also experiencing the EXACT same problem -- however in our case the crash seems to cause the machine to reboot, or perhaps the hardware reboots itself in the event of this sort of crash. Either way, we are running 6.06.1 on a HP DL 360 G4. When the crash happens, it doesn't seem to leave any message in the logs what-so-ever. It looks from the logs like the machine was spontaneously powered down. 

My question to the community is, is it possible to turn on some more enhanced kernel logging or crash dump reporting or something? Or, does anyone have any possible explanations for the problem? 

Thank you very much,

katsu :KS

---

