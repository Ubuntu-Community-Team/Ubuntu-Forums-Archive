---
title: "How To track fronze server."
date: 2010-06-23
forum: Server Platforms
---

### Post by citium on 2010-06-23
**My server keep crashing ever so often.**
For the last three days one random server die each days.

**How would I track down the problem to solve this.**

I have around 18 Servers.
Running from ubuntu 9.10 to 10.4.

My servers are traffic and storage intensive,

---

### Post by CharlesA on 2010-06-23
Look at the syslog to see what happened.

---

### Post by citium on 2010-06-24
I just got this from a recently frozen server.
It was down 15 min ago.


What should I be looking for in this file?


I see some shrunk window,

And the following worry me abit, I'll google them

Jun 24 00:05:27 s22 kernel: [    2.489283] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 7864339
Jun 24 00:05:27 s22 kernel: [    2.495573] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 7864399
Jun 24 00:05:27 s22 kernel: [    2.495600] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 7864403
Jun 24 00:05:27 s22 kernel: [    2.495622] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 7864404
Jun 24 00:05:27 s22 kernel: [    2.501734] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 7747018

Jun 24 00:05:27 s22 kernel: [    5.053218] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PMI0._GHL] (Node f740f768), AE_AML_BUFFER_LIMIT
Jun 24 00:05:27 s22 kernel: [    5.053236] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PMI0._PMC] (Node f740f708), AE_AML_BUFFER_LIMIT

Jun 24 00:05:27 s22 kernel: [    8.096975] EXT4-fs (sde1): mounted filesystem with ordered data mode
Jun 24 00:05:27 s22 kernel: [    9.586448] EXT4-fs (sdb1): mounted filesystem with ordered data mode
Jun 24 00:05:27 s22 kernel: [   10.494276] EXT4-fs (sdc1): mounted filesystem with ordered data mode
Jun 24 00:05:27 s22 kernel: [   10.886488] EXT4-fs (sdd1): mounted filesystem with ordered data mode

```

Jun 23 06:50:40 s22 rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="802" x-info="http://www.rsyslog.com"] rsyslogd was HUPed, type 'lightweight'.
Jun 23 06:55:01 s22 CRON[7367]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Jun 23 07:05:01 s22 CRON[13798]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Jun 23 07:09:01 s22 CRON[16554]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Jun 23 07:15:01 s22 CRON[20786]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Jun 23 07:17:01 s22 CRON[22318]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jun 23 07:25:01 s22 CRON[28999]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Jun 23 07:35:01 s22 CRON[4179]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Jun 23 07:39:01 s22 CRON[6880]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Jun 23 07:45:01 s22 CRON[10944]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Jun 23 07:53:41 s22 kernel: [2462882.005893] TCP: Peer 218.248.64.148:54277/80 unexpectedly shrunk window 467493985:467513865 (repaired)
Jun 23 07:53:42 s22 kernel: [2462883.547188] TCP: Peer 218.248.64.148:54277/80 unexpectedly shrunk window 467493985:467513865 (repaired)
Jun 23 07:55:01 s22 CRON[19239]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Jun 23 07:58:00 s22 postfix/sendmail[21202]: fatal: open /etc/postfix/main.cf: No such file or directory
Jun 23 08:05:01 s22 CRON[26206]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Jun 23 08:09:01 s22 CRON[28945]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Jun 23 08:15:01 s22 CRON[1038]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Jun 23 08:17:01 s22 CRON[2773]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jun 23 08:25:01 s22 CRON[7894]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Jun 23 08:32:03 s22 ntpd[17957]: kernel time sync status change 6001
Jun 23 08:35:01 s22 CRON[15784]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Jun 23 08:39:01 s22 CRON[18631]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Jun 23 08:44:57 s22 kernel: [2465952.848117] TCP: Peer 187.136.23.108:49826/80 unexpectedly shrunk window 2112874015:2112876623 (repaired)
Jun 23 08:45:01 s22 CRON[22690]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Jun 23 08:49:07 s22 ntpd[17957]: kernel time sync status change 2001
Jun 23 08:55:01 s22 CRON[29724]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Jun 23 09:05:01 s22 CRON[4011]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Jun 23 09:09:01 s22 CRON[6696]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Jun 23 09:14:47 s22 kernel: [2467739.337626] TCP: Peer 86.134.167.13:20464/80 unexpectedly shrunk window 1112420652:1112423368 (repaired)
Jun 23 09:14:48 s22 kernel: [2467740.839006] TCP: Peer 86.134.167.13:20464/80 unexpectedly shrunk window 1112420652:1112423368 (repaired)
Jun 23 09:15:01 s22 CRON[10475]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Jun 23 09:15:25 s22 kernel: [2467777.215523] TCP: Peer 86.134.167.13:20464/80 unexpectedly shrunk window 1112639448:1112642368 (repaired)
Jun 23 09:15:26 s22 kernel: [2467778.549196] TCP: Peer 86.134.167.13:20464/80 unexpectedly shrunk window 1112639448:1112642368 (repaired)
Jun 23 09:15:40 s22 kernel: [2467792.564743] TCP: Peer 86.134.167.13:20464/80 unexpectedly shrunk window 1112732888:1112735808 (repaired)
Jun 23 09:15:51 s22 kernel: [2467803.198926] TCP: Peer 86.134.167.13:20464/80 unexpectedly shrunk window 1112785448:1112788368 (repaired)
Jun 23 09:16:12 s22 kernel: [2467824.792570] TCP: Peer 86.134.167.13:20464/80 unexpectedly shrunk window 1112929360:1112931448 (repaired)
Jun 23 09:16:14 s22 kernel: [2467826.158179] TCP: Peer 86.134.167.13:20464/80 unexpectedly shrunk window 1112929360:1112931448 (repaired)
Jun 23 09:17:01 s22 CRON[11817]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jun 23 09:20:12 s22 kernel: [2468063.731544] TCP: Peer 187.136.23.108:49826/80 unexpectedly shrunk window 2172430403:2172431855 (repaired)
Jun 23 09:25:02 s22 CRON[17933]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Jun 23 09:25:58 s22 kernel: [2468409.105425] TCP: Peer 187.136.23.108:51973/80 unexpectedly shrunk window 3858705198:3858706650 (repaired)
Jun 23 09:26:00 s22 kernel: [2468411.971960] TCP: Peer 187.136.23.108:51973/80 unexpectedly shrunk window 3858705198:3858706650 (repaired)
Jun 23 09:26:06 s22 kernel: [2468417.705965] TCP: Peer 187.136.23.108:51973/80 unexpectedly shrunk window 3858705198:3858706650 (repaired)
Jun 23 09:35:01 s22 CRON[25553]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Jun 23 09:39:01 s22 CRON[28288]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Jun 23 09:45:01 s22 CRON[32354]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Jun 23 09:49:41 s22 kernel: [2469830.045455] TCP: Peer 86.134.167.13:20464/80 unexpectedly shrunk window 1125903548:1125906468 (repaired)
Jun 23 09:49:45 s22 kernel: [2469834.198206] TCP: Peer 86.134.167.13:20464/80 unexpectedly shrunk window 1125903548:1125906468 (repaired)
Jun 23 09:55:01 s22 CRON[6624]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Jun 23 10:04:01 s22 kernel: [2470688.859247] TCP: Peer 86.134.167.13:20464/80 unexpectedly shrunk window 1131461768:1131463228 (repaired)
Jun 23 10:04:03 s22 kernel: [2470690.192673] TCP: Peer 86.134.167.13:20464/80 unexpectedly shrunk window 1131461768:1131463228 (repaired)
Jun 23 10:04:05 s22 kernel: [2470692.860082] TCP: Peer 86.134.167.13:20464/80 unexpectedly shrunk window 1131461768:1131463228 (repaired)
Jun 23 10:05:01 s22 CRON[13544]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Jun 23 10:09:01 s22 CRON[16328]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Jun 23 10:14:28 s22 ntpd[17957]: kernel time sync status change 6001
Jun 23 10:15:01 s22 CRON[20626]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Jun 23 10:17:01 s22 CRON[21968]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jun 23 10:25:01 s22 CRON[27343]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Jun 23 10:35:01 s22 CRON[2065]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Jun 23 10:39:01 s22 CRON[4838]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Jun 23 10:41:17 s22 kernel: [2472920.704826] TCP: Peer 86.134.167.13:20464/80 unexpectedly shrunk window 1146099728:1146102648 (repaired)
Jun 23 10:41:18 s22 kernel: [2472921.679128] TCP: Peer 86.134.167.13:20464/80 unexpectedly shrunk window 1146099728:1146102648 (repaired)
Jun 23 10:41:20 s22 kernel: [2472923.628289] TCP: Peer 86.134.167.13:20464/80 unexpectedly shrunk window 1146099728:1146102648 (repaired)
Jun 23 10:41:24 s22 kernel: [2472927.524926] TCP: Peer 86.134.167.13:20464/80 unexpectedly shrunk window 1146099728:1146102648 (repaired)
Jun 24 00:05:27 s22 kernel: imklog 4.2.0, log source = /proc/kmsg started.
Jun 24 00:05:27 s22 rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="884" x-info="http://www.rsyslog.com"] (re)start
Jun 24 00:05:27 s22 rsyslogd: rsyslogd's groupid changed to 103
Jun 24 00:05:27 s22 rsyslogd: rsyslogd's userid changed to 101
Jun 24 00:05:27 s22 rsyslogd-2039: Could no open output file '/dev/xconsole' [try http://www.rsyslog.com/e/2039 ]
Jun 24 00:05:27 s22 kernel: [    0.000000] Initializing cgroup subsys cpuset
Jun 24 00:05:27 s22 kernel: [    0.000000] Initializing cgroup subsys cpu
Jun 24 00:05:27 s22 kernel: [    0.000000] Linux version 2.6.32-22-generic-pae (buildd@rothera) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #33-Ubuntu SMP Wed Apr 28 14:57:29 UTC 2010 (Ubuntu 2.6.32-22.33-generic-pae 2.6.32.11+drm33.2)
Jun 24 00:05:27 s22 kernel: [    0.000000] KERNEL supported cpus:
Jun 24 00:05:27 s22 kernel: [    0.000000]   Intel GenuineIntel
Jun 24 00:05:27 s22 kernel: [    0.000000]   AMD AuthenticAMD
Jun 24 00:05:27 s22 kernel: [    0.000000]   NSC Geode by NSC
Jun 24 00:05:27 s22 kernel: [    0.000000]   Cyrix CyrixInstead
Jun 24 00:05:27 s22 kernel: [    0.000000]   Centaur CentaurHauls
Jun 24 00:05:27 s22 kernel: [    0.000000]   Transmeta GenuineTMx86
Jun 24 00:05:27 s22 kernel: [    0.000000]   Transmeta TransmetaCPU
Jun 24 00:05:27 s22 kernel: [    0.000000]   UMC UMC UMC UMC
Jun 24 00:05:27 s22 kernel: [    0.000000] BIOS-provided physical RAM map:
Jun 24 00:05:27 s22 kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009d000 (usable)
Jun 24 00:05:27 s22 kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 00000000bf699000 (usable)
Jun 24 00:05:27 s22 kernel: [    0.000000]  BIOS-e820: 00000000bf699000 - 00000000bf6af000 (reserved)
Jun 24 00:05:27 s22 kernel: [    0.000000]  BIOS-e820: 00000000bf6af000 - 00000000bf6ce000 (ACPI data)
Jun 24 00:05:27 s22 kernel: [    0.000000]  BIOS-e820: 00000000bf6ce000 - 00000000c0000000 (reserved)
Jun 24 00:05:27 s22 kernel: [    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
Jun 24 00:05:27 s22 kernel: [    0.000000]  BIOS-e820: 00000000fe000000 - 0000000100000000 (reserved)
Jun 24 00:05:27 s22 kernel: [    0.000000]  BIOS-e820: 0000000100000000 - 0000000140000000 (usable)
Jun 24 00:05:27 s22 kernel: [    0.000000] DMI 2.6 present.
Jun 24 00:05:27 s22 kernel: [    0.000000] last_pfn = 0x140000 max_arch_pfn = 0x1000000
Jun 24 00:05:27 s22 kernel: [    0.000000] MTRR default type: uncachable
Jun 24 00:05:27 s22 kernel: [    0.000000] MTRR fixed ranges enabled:
Jun 24 00:05:27 s22 kernel: [    0.000000]   00000-9FFFF write-back
Jun 24 00:05:27 s22 kernel: [    0.000000]   A0000-BFFFF uncachable
Jun 24 00:05:27 s22 kernel: [    0.000000]   C0000-CFFFF write-protect
Jun 24 00:05:27 s22 kernel: [    0.000000]   D0000-EBFFF uncachable
Jun 24 00:05:27 s22 kernel: [    0.000000]   EC000-FFFFF write-protect
Jun 24 00:05:27 s22 kernel: [    0.000000] MTRR variable ranges enabled:
Jun 24 00:05:27 s22 kernel: [    0.000000]   0 base 000000000 mask F80000000 write-back
Jun 24 00:05:27 s22 kernel: [    0.000000]   1 base 080000000 mask FC0000000 write-back
Jun 24 00:05:27 s22 kernel: [    0.000000]   2 base 100000000 mask FC0000000 write-back
Jun 24 00:05:27 s22 kernel: [    0.000000]   3 disabled
Jun 24 00:05:27 s22 kernel: [    0.000000]   4 disabled
Jun 24 00:05:27 s22 kernel: [    0.000000]   5 disabled
Jun 24 00:05:27 s22 kernel: [    0.000000]   6 disabled
Jun 24 00:05:27 s22 kernel: [    0.000000]   7 disabled
Jun 24 00:05:27 s22 kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Jun 24 00:05:27 s22 kernel: [    0.000000] e820 update range: 00000000c0000000 - 0000000100000000 (usable) ==> (reserved)
Jun 24 00:05:27 s22 kernel: [    0.000000] e820 update range: 0000000000002000 - 0000000000006000 (usable) ==> (reserved)
Jun 24 00:05:27 s22 kernel: [    0.000000] Scanning 1 areas for low memory corruption
Jun 24 00:05:27 s22 kernel: [    0.000000] modified physical RAM map:
Jun 24 00:05:27 s22 kernel: [    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
Jun 24 00:05:27 s22 kernel: [    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
Jun 24 00:05:27 s22 kernel: [    0.000000]  modified: 0000000000006000 - 000000000009d000 (usable)
Jun 24 00:05:27 s22 kernel: [    0.000000]  modified: 0000000000100000 - 00000000bf699000 (usable)
Jun 24 00:05:27 s22 kernel: [    0.000000]  modified: 00000000bf699000 - 00000000bf6af000 (reserved)
Jun 24 00:05:27 s22 kernel: [    0.000000]  modified: 00000000bf6af000 - 00000000bf6ce000 (ACPI data)
Jun 24 00:05:27 s22 kernel: [    0.000000]  modified: 00000000bf6ce000 - 00000000c0000000 (reserved)
Jun 24 00:05:27 s22 kernel: [    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
Jun 24 00:05:27 s22 kernel: [    0.000000]  modified: 00000000fe000000 - 0000000100000000 (reserved)
Jun 24 00:05:27 s22 kernel: [    0.000000]  modified: 0000000100000000 - 0000000140000000 (usable)
Jun 24 00:05:27 s22 kernel: [    0.000000] initial memory mapped : 0 - 00e00000
Jun 24 00:05:27 s22 kernel: [    0.000000] init_memory_mapping: 0000000000000000-00000000379fe000
Jun 24 00:05:27 s22 kernel: [    0.000000] NX (Execute Disable) protection: active
Jun 24 00:05:27 s22 kernel: [    0.000000]  0000000000 - 0000200000 page 4k
Jun 24 00:05:27 s22 kernel: [    0.000000]  0000200000 - 0037800000 page 2M
Jun 24 00:05:27 s22 kernel: [    0.000000]  0037800000 - 00379fe000 page 4k
Jun 24 00:05:27 s22 kernel: [    0.000000] kernel direct mapping tables up to 379fe000 @ 7000-d000
Jun 24 00:05:27 s22 kernel: [    0.000000] RAMDISK: 37864000 - 37fef9c2
Jun 24 00:05:27 s22 kernel: [    0.000000] Allocated new RAMDISK: 00938000 - 010c39c2
Jun 24 00:05:27 s22 kernel: [    0.000000] Move RAMDISK from 0000000037864000 - 0000000037fef9c1 to 00938000 - 010c39c1
Jun 24 00:05:27 s22 kernel: [    0.000000] ACPI: RSDP 000f0b40 00024 (v02 DELL  )
Jun 24 00:05:27 s22 kernel: [    0.000000] ACPI: XSDT 000f0c40 00094 (v01 DELL   PE_SC3   00000001 DELL 00000001)
Jun 24 00:05:27 s22 kernel: [    0.000000] ACPI: FACP bf6c3bb4 000F4 (v03 DELL   PE_SC3   00000001 DELL 00000001)
Jun 24 00:05:27 s22 kernel: [    0.000000] ACPI: DSDT bf6af000 0398C (v01 DELL   PE_SC3   00000001 INTL 20050624)
Jun 24 00:05:27 s22 kernel: [    0.000000] ACPI: FACS bf6c6000 00040
Jun 24 00:05:27 s22 kernel: [    0.000000] ACPI: APIC bf6c3478 00152 (v01 DELL   PE_SC3   00000001 DELL 00000001)
Jun 24 00:05:27 s22 kernel: [    0.000000] ACPI: SPCR bf6c35cc 00050 (v01 DELL   PE_SC3   00000001 DELL 00000001)
Jun 24 00:05:27 s22 kernel: [    0.000000] ACPI: HPET bf6c3620 00038 (v01 DELL   PE_SC3   00000001 DELL 00000001)
Jun 24 00:05:27 s22 kernel: [    0.000000] ACPI: DM__ bf6c365c 000A8 (v01 DELL   PE_SC3   00000001 DELL 00000001)
Jun 24 00:05:27 s22 kernel: [    0.000000] ACPI: MCFG bf6c3850 0003C (v01 DELL   PE_SC3   00000001 DELL 00000001)
Jun 24 00:05:27 s22 kernel: [    0.000000] ACPI: WD__ bf6c3890 00134 (v01 DELL   PE_SC3   00000001 DELL 00000001)
Jun 24 00:05:27 s22 kernel: [    0.000000] ACPI: SLIC bf6c39c8 00024 (v01 DELL   PE_SC3   00000001 DELL 00000001)
Jun 24 00:05:27 s22 kernel: [    0.000000] ACPI: ERST bf6b2b0c 00270 (v01 DELL   PE_SC3   00000001 DELL 00000001)
Jun 24 00:05:27 s22 kernel: [    0.000000] ACPI: HEST bf6b2d7c 003A8 (v01 DELL   PE_SC3   00000001 DELL 00000001)
Jun 24 00:05:27 s22 kernel: [    0.000000] ACPI: BERT bf6b298c 00030 (v01 DELL   PE_SC3   00000001 DELL 00000001)
Jun 24 00:05:27 s22 kernel: [    0.000000] ACPI: EINJ bf6b29bc 00150 (v01 DELL   PE_SC3   00000001 DELL 00000001)
Jun 24 00:05:27 s22 kernel: [    0.000000] ACPI: TCPA bf6c3b4c 00064 (v02 DELL   PE_SC3   00000001 DELL 00000001)
Jun 24 00:05:27 s22 kernel: [    0.000000] ACPI: SSDT bf6c7000 012D4 (v01  INTEL PPM RCM  80000001 INTL 20061109)
Jun 24 00:05:27 s22 kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Jun 24 00:05:27 s22 kernel: [    0.000000] 4230MB HIGHMEM available.
Jun 24 00:05:27 s22 kernel: [    0.000000] 889MB LOWMEM available.
Jun 24 00:05:27 s22 kernel: [    0.000000]   mapped low ram: 0 - 379fe000
Jun 24 00:05:27 s22 kernel: [    0.000000]   low ram: 0 - 379fe000
Jun 24 00:05:27 s22 kernel: [    0.000000]   node 0 low ram: 00000000 - 379fe000
Jun 24 00:05:27 s22 kernel: [    0.000000]   node 0 bootmap 00009000 - 0000ff40
Jun 24 00:05:27 s22 kernel: [    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00379fe000]
Jun 24 00:05:27 s22 kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
Jun 24 00:05:27 s22 kernel: [    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
Jun 24 00:05:27 s22 kernel: [    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
Jun 24 00:05:27 s22 kernel: [    0.000000]   #3 [0000100000 - 000092f7d8]    TEXT DATA BSS ==> [0000100000 - 000092f7d8]
Jun 24 00:05:27 s22 kernel: [    0.000000]   #4 [000009dc00 - 0000100000]    BIOS reserved ==> [000009dc00 - 0000100000]
Jun 24 00:05:27 s22 kernel: [    0.000000]   #5 [0000930000 - 0000937201]              BRK ==> [0000930000 - 0000937201]
Jun 24 00:05:27 s22 kernel: [    0.000000]   #6 [0000007000 - 0000009000]          PGTABLE ==> [0000007000 - 0000009000]
Jun 24 00:05:27 s22 kernel: [    0.000000]   #7 [0000938000 - 00010c39c2]      NEW RAMDISK ==> [0000938000 - 00010c39c2]
Jun 24 00:05:27 s22 kernel: [    0.000000]   #8 [0000009000 - 0000010000]          BOOTMAP ==> [0000009000 - 0000010000]
Jun 24 00:05:27 s22 kernel: [    0.000000] found SMP MP-table at [c00fe710] fe710
Jun 24 00:05:27 s22 kernel: [    0.000000] Zone PFN ranges:
Jun 24 00:05:27 s22 kernel: [    0.000000]   DMA      0x00000000 -> 0x00001000
Jun 24 00:05:27 s22 kernel: [    0.000000]   Normal   0x00001000 -> 0x000379fe
Jun 24 00:05:27 s22 kernel: [    0.000000]   HighMem  0x000379fe -> 0x00140000
Jun 24 00:05:27 s22 kernel: [    0.000000] Movable zone start PFN for each node
Jun 24 00:05:27 s22 kernel: [    0.000000] early_node_map[4] active PFN ranges
Jun 24 00:05:27 s22 kernel: [    0.000000]     0: 0x00000000 -> 0x00000002
Jun 24 00:05:27 s22 kernel: [    0.000000]     0: 0x00000006 -> 0x0000009d
Jun 24 00:05:27 s22 kernel: [    0.000000]     0: 0x00000100 -> 0x000bf699
Jun 24 00:05:27 s22 kernel: [    0.000000]     0: 0x00100000 -> 0x00140000
Jun 24 00:05:27 s22 kernel: [    0.000000] On node 0 totalpages: 1046066
Jun 24 00:05:27 s22 kernel: [    0.000000] free_area_init_node: node 0, pgdat c07d4d20, node_mem_map c10c5000
Jun 24 00:05:27 s22 kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Jun 24 00:05:27 s22 kernel: [    0.000000]   DMA zone: 0 pages reserved
Jun 24 00:05:27 s22 kernel: [    0.000000]   DMA zone: 3961 pages, LIFO batch:0
Jun 24 00:05:27 s22 kernel: [    0.000000]   Normal zone: 1748 pages used for memmap
Jun 24 00:05:27 s22 kernel: [    0.000000]   Normal zone: 221994 pages, LIFO batch:31
Jun 24 00:05:27 s22 kernel: [    0.000000]   HighMem zone: 8461 pages used for memmap
Jun 24 00:05:27 s22 kernel: [    0.000000]   HighMem zone: 809870 pages, LIFO batch:31
Jun 24 00:05:27 s22 kernel: [    0.000000] Using APIC driver default
Jun 24 00:05:27 s22 kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x808
Jun 24 00:05:27 s22 kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Jun 24 00:05:27 s22 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Jun 24 00:05:27 s22 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
Jun 24 00:05:27 s22 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x04] enabled)
Jun 24 00:05:27 s22 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x06] enabled)
Jun 24 00:05:27 s22 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x24] disabled)
Jun 24 00:05:27 s22 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x25] disabled)
Jun 24 00:05:27 s22 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x26] disabled)
Jun 24 00:05:27 s22 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x27] disabled)
Jun 24 00:05:27 s22 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x09] lapic_id[0x28] disabled)
Jun 24 00:05:27 s22 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x0a] lapic_id[0x29] disabled)
Jun 24 00:05:27 s22 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x0b] lapic_id[0x2a] disabled)
Jun 24 00:05:27 s22 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x0c] lapic_id[0x2b] disabled)
Jun 24 00:05:27 s22 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x0d] lapic_id[0x2c] disabled)
Jun 24 00:05:27 s22 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x0e] lapic_id[0x2d] disabled)
Jun 24 00:05:27 s22 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x0f] lapic_id[0x2e] disabled)
Jun 24 00:05:27 s22 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x10] lapic_id[0x2f] disabled)
Jun 24 00:05:27 s22 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x11] lapic_id[0x30] disabled)
Jun 24 00:05:27 s22 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x12] lapic_id[0x31] disabled)
Jun 24 00:05:27 s22 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x13] lapic_id[0x32] disabled)
Jun 24 00:05:27 s22 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x14] lapic_id[0x33] disabled)
Jun 24 00:05:27 s22 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x15] lapic_id[0x34] disabled)
Jun 24 00:05:27 s22 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x16] lapic_id[0x35] disabled)
Jun 24 00:05:27 s22 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x17] lapic_id[0x36] disabled)
Jun 24 00:05:27 s22 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x18] lapic_id[0x37] disabled)
Jun 24 00:05:27 s22 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x19] lapic_id[0x38] disabled)
Jun 24 00:05:27 s22 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x1a] lapic_id[0x39] disabled)
Jun 24 00:05:27 s22 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x1b] lapic_id[0x3a] disabled)
Jun 24 00:05:27 s22 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x1c] lapic_id[0x3b] disabled)
Jun 24 00:05:27 s22 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x1d] lapic_id[0x3c] disabled)
Jun 24 00:05:27 s22 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x1e] lapic_id[0x3d] disabled)
Jun 24 00:05:27 s22 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x1f] lapic_id[0x3e] disabled)
Jun 24 00:05:27 s22 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x20] lapic_id[0x3f] disabled)
Jun 24 00:05:27 s22 kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0xff] high edge lint[0x1])
Jun 24 00:05:27 s22 kernel: [    0.000000] ACPI: IOAPIC (id[0x00] address[0xfec00000] gsi_base[0])
Jun 24 00:05:27 s22 kernel: [    0.000000] IOAPIC[0]: apic_id 0, version 32, address 0xfec00000, GSI 0-23
Jun 24 00:05:27 s22 kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Jun 24 00:05:27 s22 kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Jun 24 00:05:27 s22 kernel: [    0.000000] ACPI: IRQ0 used by override.
Jun 24 00:05:27 s22 kernel: [    0.000000] ACPI: IRQ2 used by override.
Jun 24 00:05:27 s22 kernel: [    0.000000] ACPI: IRQ9 used by override.
Jun 24 00:05:27 s22 kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Jun 24 00:05:27 s22 kernel: [    0.000000] ACPI: HPET id: 0x8086a701 base: 0xfed00000
Jun 24 00:05:27 s22 kernel: [    0.000000] 32 Processors exceeds NR_CPUS limit of 8
Jun 24 00:05:27 s22 kernel: [    0.000000] SMP: Allowing 8 CPUs, 4 hotplug CPUs
Jun 24 00:05:27 s22 kernel: [    0.000000] nr_irqs_gsi: 24
Jun 24 00:05:27 s22 kernel: [    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
Jun 24 00:05:27 s22 kernel: [    0.000000] PM: Registered nosave memory: 000000000009d000 - 0000000000100000
Jun 24 00:05:27 s22 kernel: [    0.000000] Allocating PCI resources starting at c0000000 (gap: c0000000:20000000)
Jun 24 00:05:27 s22 kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Jun 24 00:05:27 s22 kernel: [    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:8 nr_node_ids:1
Jun 24 00:05:27 s22 kernel: [    0.000000] PERCPU: Embedded 15 pages/cpu @c3a00000 s39448 r0 d21992 u262144
Jun 24 00:05:27 s22 kernel: [    0.000000] pcpu-alloc: s39448 r0 d21992 u262144 alloc=1*2097152
Jun 24 00:05:27 s22 kernel: [    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
Jun 24 00:05:27 s22 kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 1035825
Jun 24 00:05:27 s22 kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-22-generic-pae root=UUID=2bbd6ae2-4908-48c5-b086-a94ce6331d30 ro splash quiet
Jun 24 00:05:27 s22 kernel: [    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
Jun 24 00:05:27 s22 kernel: [    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Jun 24 00:05:27 s22 kernel: [    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Jun 24 00:05:27 s22 kernel: [    0.000000] Enabling fast FPU save and restore... done.
Jun 24 00:05:27 s22 kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Jun 24 00:05:27 s22 kernel: [    0.000000] Initializing CPU#0
Jun 24 00:05:27 s22 kernel: [    0.000000] allocated 26214400 bytes of page_cgroup
Jun 24 00:05:27 s22 kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Jun 24 00:05:27 s22 kernel: [    0.000000] Initializing HighMem for node 0 (000379fe:00140000)
Jun 24 00:05:27 s22 kernel: [    0.000000] Memory: 4098784k/5242880k available (4826k kernel code, 84080k reserved, 2211k data, 672k init, 3273324k highmem)
Jun 24 00:05:27 s22 kernel: [    0.000000] virtual kernel memory layout:
Jun 24 00:05:27 s22 kernel: [    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
Jun 24 00:05:27 s22 kernel: [    0.000000]     pkmap   : 0xffa00000 - 0xffc00000   (2048 kB)
Jun 24 00:05:27 s22 kernel: [    0.000000]     vmalloc : 0xf81fe000 - 0xff9fe000   ( 120 MB)
Jun 24 00:05:27 s22 kernel: [    0.000000]     lowmem  : 0xc0000000 - 0xf79fe000   ( 889 MB)
Jun 24 00:05:27 s22 kernel: [    0.000000]       .init : 0xc07e0000 - 0xc0888000   ( 672 kB)
Jun 24 00:05:27 s22 kernel: [    0.000000]       .data : 0xc05b6a4b - 0xc07df7a8   (2211 kB)
Jun 24 00:05:27 s22 kernel: [    0.000000]       .text : 0xc0100000 - 0xc05b6a4b   (4826 kB)
Jun 24 00:05:27 s22 kernel: [    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Jun 24 00:05:27 s22 kernel: [    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
Jun 24 00:05:27 s22 kernel: [    0.000000] Hierarchical RCU implementation.
Jun 24 00:05:27 s22 kernel: [    0.000000] NR_IRQS:2304 nr_irqs:472
Jun 24 00:05:27 s22 kernel: [    0.000000] Extended CMOS year: 2000
Jun 24 00:05:27 s22 kernel: [    0.000000] Console: colour VGA+ 80x25
Jun 24 00:05:27 s22 kernel: [    0.000000] console [tty0] enabled
Jun 24 00:05:27 s22 kernel: [    0.000000] hpet clockevent registered
Jun 24 00:05:27 s22 kernel: [    0.000000]   alloc irq_desc for 24 on node 0
Jun 24 00:05:27 s22 kernel: [    0.000000]   alloc kstat_irqs on node 0
Jun 24 00:05:27 s22 kernel: [    0.000000]   alloc irq_desc for 25 on node 0
Jun 24 00:05:27 s22 kernel: [    0.000000]   alloc kstat_irqs on node 0
Jun 24 00:05:27 s22 kernel: [    0.000000]   alloc irq_desc for 26 on node 0
Jun 24 00:05:27 s22 kernel: [    0.000000]   alloc kstat_irqs on node 0
Jun 24 00:05:27 s22 kernel: [    0.000000]   alloc irq_desc for 27 on node 0
Jun 24 00:05:27 s22 kernel: [    0.000000]   alloc kstat_irqs on node 0
Jun 24 00:05:27 s22 kernel: [    0.000000]   alloc irq_desc for 28 on node 0
Jun 24 00:05:27 s22 kernel: [    0.000000]   alloc kstat_irqs on node 0
Jun 24 00:05:27 s22 kernel: [    0.000000] HPET: 8 timers in total, 5 timers will be used for per-cpu timer
Jun 24 00:05:27 s22 kernel: [    0.000000] Fast TSC calibration using PIT
Jun 24 00:05:27 s22 kernel: [    0.004000] Detected 2393.774 MHz processor.
Jun 24 00:05:27 s22 kernel: [    0.000003] Calibrating delay loop (skipped), value calculated using timer frequency.. 4787.54 BogoMIPS (lpj=9575096)
Jun 24 00:05:27 s22 kernel: [    0.000013] Security Framework initialized
Jun 24 00:05:27 s22 kernel: [    0.000024] AppArmor: AppArmor initialized
Jun 24 00:05:27 s22 kernel: [    0.000029] Mount-cache hash table entries: 512
Jun 24 00:05:27 s22 kernel: [    0.000108] Initializing cgroup subsys ns
Jun 24 00:05:27 s22 kernel: [    0.000111] Initializing cgroup subsys cpuacct
Jun 24 00:05:27 s22 kernel: [    0.000114] Initializing cgroup subsys memory
Jun 24 00:05:27 s22 kernel: [    0.000118] Initializing cgroup subsys devices
Jun 24 00:05:27 s22 kernel: [    0.000120] Initializing cgroup subsys freezer
Jun 24 00:05:27 s22 kernel: [    0.000121] Initializing cgroup subsys net_cls
Jun 24 00:05:27 s22 kernel: [    0.000134] CPU: Physical Processor ID: 0
Jun 24 00:05:27 s22 kernel: [    0.000135] CPU: Processor Core ID: 0
Jun 24 00:05:27 s22 kernel: [    0.000138] CPU: L1 I cache: 32K, L1 D cache: 32K
Jun 24 00:05:27 s22 kernel: [    0.000140] CPU: L2 cache: 256K
Jun 24 00:05:27 s22 kernel: [    0.000141] CPU: L3 cache: 8192K
Jun 24 00:05:27 s22 kernel: [    0.000143] mce: CPU supports 9 MCE banks
Jun 24 00:05:27 s22 kernel: [    0.000152] CPU0: Thermal monitoring enabled (TM1)
Jun 24 00:05:27 s22 kernel: [    0.000156] CPU 0 MCA banks CMCI:2 CMCI:3 CMCI:5 CMCI:6 CMCI:8
Jun 24 00:05:27 s22 kernel: [    0.000163] using mwait in idle threads.
Jun 24 00:05:27 s22 kernel: [    0.000166] Performance Events: Nehalem/Corei7 events, Intel PMU driver.
Jun 24 00:05:27 s22 kernel: [    0.000170] ... version:                3
Jun 24 00:05:27 s22 kernel: [    0.000171] ... bit width:              48
Jun 24 00:05:27 s22 kernel: [    0.000172] ... generic registers:      4
Jun 24 00:05:27 s22 kernel: [    0.000174] ... value mask:             0000ffffffffffff
Jun 24 00:05:27 s22 kernel: [    0.000175] ... max period:             000000007fffffff
Jun 24 00:05:27 s22 kernel: [    0.000176] ... fixed-purpose events:   3
Jun 24 00:05:27 s22 kernel: [    0.000178] ... event mask:             000000070000000f
Jun 24 00:05:27 s22 kernel: [    0.000181] Checking 'hlt' instruction... OK.
Jun 24 00:05:27 s22 kernel: [    0.014474] ACPI: Core revision 20090903
Jun 24 00:05:27 s22 kernel: [    0.018255] ftrace: converting mcount calls to 0f 1f 44 00 00
Jun 24 00:05:27 s22 kernel: [    0.018258] ftrace: allocating 22402 entries in 44 pages
Jun 24 00:05:27 s22 kernel: [    0.024623] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Jun 24 00:05:27 s22 kernel: [    0.024950] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Jun 24 00:05:27 s22 kernel: [    0.064562] CPU0: Intel(R) Xeon(R) CPU           X3430  @ 2.40GHz stepping 05
Jun 24 00:05:27 s22 kernel: [    0.172140] Booting processor 1 APIC 0x2 ip 0x6000
Jun 24 00:05:27 s22 kernel: [    0.182512] Initializing CPU#1
Jun 24 00:05:27 s22 kernel: [    0.259905] CPU: Physical Processor ID: 0
Jun 24 00:05:27 s22 kernel: [    0.259906] CPU: Processor Core ID: 1
Jun 24 00:05:27 s22 kernel: [    0.259908] CPU: L1 I cache: 32K, L1 D cache: 32K
Jun 24 00:05:27 s22 kernel: [    0.259910] CPU: L2 cache: 256K
Jun 24 00:05:27 s22 kernel: [    0.259911] CPU: L3 cache: 8192K
Jun 24 00:05:27 s22 kernel: [    0.259921] CPU1: Thermal monitoring enabled (TM1)
Jun 24 00:05:27 s22 kernel: [    0.259924] CPU 1 MCA banks CMCI:2 CMCI:3 CMCI:5 SHD:6 SHD:8
Jun 24 00:05:27 s22 kernel: [    0.260015] CPU1: Intel(R) Xeon(R) CPU           X3430  @ 2.40GHz stepping 05
debug2: channel 0: window 995673 sent adjust 41034
Jun 24 00:05:27 s22 kernel: [    0.260024] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
Jun 24 00:05:27 s22 kernel: [    0.280063] Booting processor 2 APIC 0x4 ip 0x6000
Jun 24 00:05:27 s22 kernel: [    0.290325] Initializing CPU#2
Jun 24 00:05:27 s22 kernel: [    0.367713] CPU: Physical Processor ID: 0
Jun 24 00:05:27 s22 kernel: [    0.367714] CPU: Processor Core ID: 2
Jun 24 00:05:27 s22 kernel: [    0.367716] CPU: L1 I cache: 32K, L1 D cache: 32K
Jun 24 00:05:27 s22 kernel: [    0.367717] CPU: L2 cache: 256K
Jun 24 00:05:27 s22 kernel: [    0.367718] CPU: L3 cache: 8192K
Jun 24 00:05:27 s22 kernel: [    0.367728] CPU2: Thermal monitoring enabled (TM1)
Jun 24 00:05:27 s22 kernel: [    0.367731] CPU 2 MCA banks CMCI:2 CMCI:3 CMCI:5 SHD:6 SHD:8
Jun 24 00:05:27 s22 kernel: [    0.367838] CPU2: Intel(R) Xeon(R) CPU           X3430  @ 2.40GHz stepping 05
Jun 24 00:05:27 s22 kernel: [    0.367848] checking TSC synchronization [CPU#0 -> CPU#2]: passed.
Jun 24 00:05:27 s22 kernel: [    0.387883] Booting processor 3 APIC 0x6 ip 0x6000
Jun 24 00:05:27 s22 kernel: [    0.398145] Initializing CPU#3
Jun 24 00:05:27 s22 kernel: [    0.475520] CPU: Physical Processor ID: 0
Jun 24 00:05:27 s22 kernel: [    0.475522] CPU: Processor Core ID: 3
Jun 24 00:05:27 s22 kernel: [    0.475524] CPU: L1 I cache: 32K, L1 D cache: 32K
Jun 24 00:05:27 s22 kernel: [    0.475525] CPU: L2 cache: 256K
Jun 24 00:05:27 s22 kernel: [    0.475526] CPU: L3 cache: 8192K
Jun 24 00:05:27 s22 kernel: [    0.475536] CPU3: Thermal monitoring enabled (TM1)
Jun 24 00:05:27 s22 kernel: [    0.475539] CPU 3 MCA banks CMCI:2 CMCI:3 CMCI:5 SHD:6 SHD:8
Jun 24 00:05:27 s22 kernel: [    0.475558] CPU3: Intel(R) Xeon(R) CPU           X3430  @ 2.40GHz stepping 05
Jun 24 00:05:27 s22 kernel: [    0.475569] checking TSC synchronization [CPU#0 -> CPU#3]: passed.
Jun 24 00:05:27 s22 kernel: [    0.495551] Brought up 4 CPUs
Jun 24 00:05:27 s22 kernel: [    0.495553] Total of 4 processors activated (19150.81 BogoMIPS).
Jun 24 00:05:27 s22 kernel: [    0.496925] CPU0 attaching sched-domain:
Jun 24 00:05:27 s22 kernel: [    0.496928]  domain 0: span 0-3 level MC
Jun 24 00:05:27 s22 kernel: [    0.496930]   groups: 0 1 2 3
Jun 24 00:05:27 s22 kernel: [    0.496936] CPU1 attaching sched-domain:
Jun 24 00:05:27 s22 kernel: [    0.496937]  domain 0: span 0-3 level MC
Jun 24 00:05:27 s22 kernel: [    0.496939]   groups: 1 2 3 0
Jun 24 00:05:27 s22 kernel: [    0.496943] CPU2 attaching sched-domain:
Jun 24 00:05:27 s22 kernel: [    0.496944]  domain 0: span 0-3 level MC
Jun 24 00:05:27 s22 kernel: [    0.496946]   groups: 2 3 0 1
Jun 24 00:05:27 s22 kernel: [    0.496949] CPU3 attaching sched-domain:
Jun 24 00:05:27 s22 kernel: [    0.496951]  domain 0: span 0-3 level MC
Jun 24 00:05:27 s22 kernel: [    0.496952]   groups: 3 0 1 2
Jun 24 00:05:27 s22 kernel: [    0.497127] devtmpfs: initialized
Jun 24 00:05:27 s22 kernel: [    0.497408] regulator: core version 0.5
Jun 24 00:05:27 s22 kernel: [    0.497433] Time:  0:05:16  Date: 06/24/10
Jun 24 00:05:27 s22 kernel: [    0.497471] NET: Registered protocol family 16
Jun 24 00:05:27 s22 kernel: [    0.497542] Trying to unpack rootfs image as initramfs...
Jun 24 00:05:27 s22 kernel: [    0.497554] EISA bus registered
Jun 24 00:05:27 s22 kernel: [    0.497560] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
Jun 24 00:05:27 s22 kernel: [    0.497562] ACPI: bus type pci registered
Jun 24 00:05:27 s22 kernel: [    0.497609] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
Jun 24 00:05:27 s22 kernel: [    0.497611] PCI: MCFG area at e0000000 reserved in E820
Jun 24 00:05:27 s22 kernel: [    0.497612] PCI: Using MMCONFIG for extended config space
Jun 24 00:05:27 s22 kernel: [    0.497614] PCI: Using configuration type 1 for base access
Jun 24 00:05:27 s22 kernel: [    0.498284] bio: create slab <bio-0> at 0
Jun 24 00:05:27 s22 kernel: [    0.498707] ACPI: EC: Look up EC in DSDT
Jun 24 00:05:27 s22 kernel: [    0.500456] ACPI: BIOS _OSI(Linux) query ignored
Jun 24 00:05:27 s22 kernel: [    0.500559] ACPI: Interpreter enabled
Jun 24 00:05:27 s22 kernel: [    0.500564] ACPI: (supports S0 S4 S5)
Jun 24 00:05:27 s22 kernel: [    0.500575] ACPI: Using IOAPIC for interrupt routing
Jun 24 00:05:27 s22 kernel: [    0.503831] ACPI: No dock devices found.
Jun 24 00:05:27 s22 kernel: [    0.504141] ACPI: PCI Root Bridge [PCI0] (0000:00)
Jun 24 00:05:27 s22 kernel: [    0.504204] pci 0000:00:00.0: PME# supported from D0 D3hot D3cold
Jun 24 00:05:27 s22 kernel: [    0.504207] pci 0000:00:00.0: PME# disabled
Jun 24 00:05:27 s22 kernel: [    0.504264] pci 0000:00:03.0: PME# supported from D0 D3hot D3cold
Jun 24 00:05:27 s22 kernel: [    0.504267] pci 0000:00:03.0: PME# disabled
Jun 24 00:05:27 s22 kernel: [    0.504321] pci 0000:00:05.0: PME# supported from D0 D3hot D3cold
Jun 24 00:05:27 s22 kernel: [    0.504324] pci 0000:00:05.0: PME# disabled
Jun 24 00:05:27 s22 kernel: [    0.504586] pci 0000:00:1a.0: reg 10 32bit mmio: [0xdf8fa000-0xdf8fa3ff]
Jun 24 00:05:27 s22 kernel: [    0.504637] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
Jun 24 00:05:27 s22 kernel: [    0.504641] pci 0000:00:1a.0: PME# disabled
Jun 24 00:05:27 s22 kernel: [    0.504699] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
Jun 24 00:05:27 s22 kernel: [    0.504702] pci 0000:00:1c.0: PME# disabled
Jun 24 00:05:27 s22 kernel: [    0.504762] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
Jun 24 00:05:27 s22 kernel: [    0.504765] pci 0000:00:1c.4: PME# disabled
Jun 24 00:05:27 s22 kernel: [    0.504824] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
Jun 24 00:05:27 s22 kernel: [    0.504828] pci 0000:00:1c.5: PME# disabled
Jun 24 00:05:27 s22 kernel: [    0.504877] pci 0000:00:1d.0: reg 10 32bit mmio: [0xdf8fc000-0xdf8fc3ff]
Jun 24 00:05:27 s22 kernel: [    0.504929] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
Jun 24 00:05:27 s22 kernel: [    0.504933] pci 0000:00:1d.0: PME# disabled
Jun 24 00:05:27 s22 kernel: [    0.505104] pci 0000:00:1f.2: reg 10 io port: [0xfcd0-0xfcd7]
Jun 24 00:05:27 s22 kernel: [    0.505110] pci 0000:00:1f.2: reg 14 io port: [0xfcc8-0xfccb]
Jun 24 00:05:27 s22 kernel: [    0.505115] pci 0000:00:1f.2: reg 18 io port: [0xfcd8-0xfcdf]
Jun 24 00:05:27 s22 kernel: [    0.505120] pci 0000:00:1f.2: reg 1c io port: [0xfccc-0xfccf]
Jun 24 00:05:27 s22 kernel: [    0.505125] pci 0000:00:1f.2: reg 20 io port: [0xfce0-0xfcff]
Jun 24 00:05:27 s22 kernel: [    0.505130] pci 0000:00:1f.2: reg 24 32bit mmio: [0xdf8fe000-0xdf8fe7ff]
Jun 24 00:05:27 s22 kernel: [    0.505160] pci 0000:00:1f.2: PME# supported from D3hot
Jun 24 00:05:27 s22 kernel: [    0.505163] pci 0000:00:1f.2: PME# disabled
Jun 24 00:05:27 s22 kernel: [    0.505324] pci 0000:04:00.0: reg 10 64bit mmio: [0xdf9f0000-0xdf9fffff]
Jun 24 00:05:27 s22 kernel: [    0.505399] pci 0000:04:00.0: PME# supported from D3hot D3cold
Jun 24 00:05:27 s22 kernel: [    0.505403] pci 0000:04:00.0: PME# disabled
Jun 24 00:05:27 s22 kernel: [    0.505453] pci 0000:00:1c.4: bridge 32bit mmio: [0xdf900000-0xdf9fffff]
Jun 24 00:05:27 s22 kernel: [    0.505530] pci 0000:06:03.0: reg 10 32bit mmio pref: [0xde000000-0xde7fffff]
Jun 24 00:05:27 s22 kernel: [    0.505536] pci 0000:06:03.0: reg 14 32bit mmio: [0xdeffc000-0xdeffffff]
Jun 24 00:05:27 s22 kernel: [    0.505542] pci 0000:06:03.0: reg 18 32bit mmio: [0xdf000000-0xdf7fffff]
Jun 24 00:05:27 s22 kernel: [    0.505562] pci 0000:06:03.0: reg 30 32bit mmio pref: [0x000000-0x00ffff]
Jun 24 00:05:27 s22 kernel: [    0.505616] pci 0000:00:1e.0: transparent bridge
Jun 24 00:05:27 s22 kernel: [    0.505622] pci 0000:00:1e.0: bridge 32bit mmio: [0xde800000-0xdf7fffff]
Jun 24 00:05:27 s22 kernel: [    0.505627] pci 0000:00:1e.0: bridge 64bit mmio pref: [0xde000000-0xde7fffff]
Jun 24 00:05:27 s22 kernel: [    0.505649] pci_bus 0000:00: on NUMA node 0
Jun 24 00:05:27 s22 kernel: [    0.505652] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Jun 24 00:05:27 s22 kernel: [    0.505926] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.LYD0._PRT]
Jun 24 00:05:27 s22 kernel: [    0.505996] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.LYD2._PRT]
Jun 24 00:05:27 s22 kernel: [    0.506069] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]
Jun 24 00:05:27 s22 kernel: [    0.506137] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX4._PRT]
Jun 24 00:05:27 s22 kernel: [    0.506205] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX5._PRT]
Jun 24 00:05:27 s22 kernel: [    0.506279] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.COMP._PRT]
Jun 24 00:05:27 s22 kernel: [    0.508548] ACPI: PCI Interrupt Link [LK00] (IRQs 3 4 5 6 7 10 11 14 *15)
Jun 24 00:05:27 s22 kernel: [    0.508639] ACPI: PCI Interrupt Link [LK01] (IRQs 3 4 5 6 7 10 11 14 15) *0, disabled.
Jun 24 00:05:27 s22 kernel: [    0.508728] ACPI: PCI Interrupt Link [LK02] (IRQs 3 4 5 6 7 10 11 14 15) *0, disabled.
Jun 24 00:05:27 s22 kernel: [    0.508818] ACPI: PCI Interrupt Link [LK03] (IRQs 3 4 5 *6 7 10 11 14 15)
Jun 24 00:05:27 s22 kernel: [    0.508906] ACPI: PCI Interrupt Link [LK04] (IRQs 3 4 5 6 7 10 *11 14 15)
Jun 24 00:05:27 s22 kernel: [    0.508995] ACPI: PCI Interrupt Link [LK05] (IRQs 3 4 5 6 7 10 11 14 15) *0, disabled.
Jun 24 00:05:27 s22 kernel: [    0.509085] ACPI: PCI Interrupt Link [LK06] (IRQs 3 4 5 6 7 10 11 *14 15)
Jun 24 00:05:27 s22 kernel: [    0.509173] ACPI: PCI Interrupt Link [LK07] (IRQs 3 4 5 6 7 10 11 14 15) *0, disabled.
Jun 24 00:05:27 s22 kernel: [    0.509259] vgaarb: device added: PCI:0000:06:03.0,decodes=io+mem,owns=io+mem,locks=none
Jun 24 00:05:27 s22 kernel: [    0.509261] vgaarb: loaded
Jun 24 00:05:27 s22 kernel: [    0.509335] SCSI subsystem initialized
Jun 24 00:05:27 s22 kernel: [    0.509395] libata version 3.00 loaded.
Jun 24 00:05:27 s22 kernel: [    0.509442] usbcore: registered new interface driver usbfs
Jun 24 00:05:27 s22 kernel: [    0.509450] usbcore: registered new interface driver hub
Jun 24 00:05:27 s22 kernel: [    0.509467] usbcore: registered new device driver usb
Jun 24 00:05:27 s22 kernel: [    0.509549] ACPI: WMI: Mapper loaded
Jun 24 00:05:27 s22 kernel: [    0.509550] PCI: Using ACPI for IRQ routing
Jun 24 00:05:27 s22 kernel: [    0.509655] NetLabel: Initializing
Jun 24 00:05:27 s22 kernel: [    0.509656] NetLabel:  domain hash size = 128
Jun 24 00:05:27 s22 kernel: [    0.509657] NetLabel:  protocols = UNLABELED CIPSOv4
Jun 24 00:05:27 s22 kernel: [    0.509666] NetLabel:  unlabeled traffic allowed by default
Jun 24 00:05:27 s22 kernel: [    0.509694] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 24, 25, 26, 27, 28, 0
Jun 24 00:05:27 s22 kernel: [    0.509700] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
Jun 24 00:05:27 s22 kernel: [    0.515458] hpet: hpet2 irq 24 for MSI
Jun 24 00:05:27 s22 kernel: [    0.515691] hpet: hpet3 irq 25 for MSI
Jun 24 00:05:27 s22 kernel: [    0.519608] hpet: hpet4 irq 26 for MSI
Jun 24 00:05:27 s22 kernel: [    0.523515] hpet: hpet5 irq 27 for MSI
Jun 24 00:05:27 s22 kernel: [    0.523525] Switching to clocksource tsc
Jun 24 00:05:27 s22 kernel: [    0.525031] AppArmor: AppArmor Filesystem Enabled
Jun 24 00:05:27 s22 kernel: [    0.525038] pnp: PnP ACPI init
Jun 24 00:05:27 s22 kernel: [    0.525044] ACPI: bus type pnp registered
Jun 24 00:05:27 s22 kernel: [    0.527563] pnp: PnP ACPI: found 13 devices
Jun 24 00:05:27 s22 kernel: [    0.527564] ACPI: ACPI bus type pnp unregistered
Jun 24 00:05:27 s22 kernel: [    0.527567] PnPBIOS: Disabled by ACPI PNP
Jun 24 00:05:27 s22 kernel: [    0.527578] system 00:07: ioport range 0x800-0x87f has been reserved
Jun 24 00:05:27 s22 kernel: [    0.527580] system 00:07: ioport range 0x880-0x8ff has been reserved
Jun 24 00:05:27 s22 kernel: [    0.527582] system 00:07: ioport range 0x900-0x91f has been reserved
Jun 24 00:05:27 s22 kernel: [    0.527584] system 00:07: ioport range 0x920-0x923 has been reserved
Jun 24 00:05:27 s22 kernel: [    0.527586] system 00:07: ioport range 0x924-0x924 has been reserved
Jun 24 00:05:27 s22 kernel: [    0.527588] system 00:07: ioport range 0xca0-0xca7 has been reserved
Jun 24 00:05:27 s22 kernel: [    0.527591] system 00:07: ioport range 0xca9-0xcab has been reserved
Jun 24 00:05:27 s22 kernel: [    0.527593] system 00:07: ioport range 0xcad-0xcaf has been reserved
Jun 24 00:05:27 s22 kernel: [    0.527597] system 00:08: ioport range 0xca8-0xca8 has been reserved
Jun 24 00:05:27 s22 kernel: [    0.527599] system 00:08: ioport range 0xcac-0xcac has been reserved
Jun 24 00:05:27 s22 kernel: [    0.527608] system 00:0a: iomem range 0xe0000000-0xefffffff has been reserved
Jun 24 00:05:27 s22 kernel: [    0.527612] system 00:0c: iomem range 0xfed50000-0xfed53fff has been reserved
Jun 24 00:05:27 s22 kernel: [    0.562192] pci 0000:00:03.0: PCI bridge, secondary bus 0000:01
Jun 24 00:05:27 s22 kernel: [    0.562194] pci 0000:00:03.0:   IO window: disabled
Jun 24 00:05:27 s22 kernel: [    0.562197] pci 0000:00:03.0:   MEM window: disabled
Jun 24 00:05:27 s22 kernel: [    0.562200] pci 0000:00:03.0:   PREFETCH window: disabled
Jun 24 00:05:27 s22 kernel: [    0.562204] pci 0000:00:05.0: PCI bridge, secondary bus 0000:02
Jun 24 00:05:27 s22 kernel: [    0.562206] pci 0000:00:05.0:   IO window: disabled
Jun 24 00:05:27 s22 kernel: [    0.562209] pci 0000:00:05.0:   MEM window: disabled
Jun 24 00:05:27 s22 kernel: [    0.562211] pci 0000:00:05.0:   PREFETCH window: disabled
Jun 24 00:05:27 s22 kernel: [    0.562215] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:03
Jun 24 00:05:27 s22 kernel: [    0.562217] pci 0000:00:1c.0:   IO window: disabled
Jun 24 00:05:27 s22 kernel: [    0.562221] pci 0000:00:1c.0:   MEM window: disabled
Jun 24 00:05:27 s22 kernel: [    0.562224] pci 0000:00:1c.0:   PREFETCH window: disabled
Jun 24 00:05:27 s22 kernel: [    0.562229] pci 0000:00:1c.4: PCI bridge, secondary bus 0000:04
Jun 24 00:05:27 s22 kernel: [    0.562230] pci 0000:00:1c.4:   IO window: disabled
Jun 24 00:05:27 s22 kernel: [    0.562235] pci 0000:00:1c.4:   MEM window: 0xdf900000-0xdf9fffff
Jun 24 00:05:27 s22 kernel: [    0.562238] pci 0000:00:1c.4:   PREFETCH window: disabled
Jun 24 00:05:27 s22 kernel: [    0.562243] pci 0000:00:1c.5: PCI bridge, secondary bus 0000:05
Jun 24 00:05:27 s22 kernel: [    0.562245] pci 0000:00:1c.5:   IO window: disabled
Jun 24 00:05:27 s22 kernel: [    0.562248] pci 0000:00:1c.5:   MEM window: disabled
Jun 24 00:05:27 s22 kernel: [    0.562251] pci 0000:00:1c.5:   PREFETCH window: disabled
Jun 24 00:05:27 s22 kernel: [    0.562259] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:06
Jun 24 00:05:27 s22 kernel: [    0.562260] pci 0000:00:1e.0:   IO window: disabled
Jun 24 00:05:27 s22 kernel: [    0.562264] pci 0000:00:1e.0:   MEM window: 0xde800000-0xdf7fffff
Jun 24 00:05:27 s22 kernel: [    0.562268] pci 0000:00:1e.0:   PREFETCH window: 0x000000de000000-0x000000de7fffff
Jun 24 00:05:27 s22 kernel: [    0.562280]   alloc irq_desc for 16 on node -1
Jun 24 00:05:27 s22 kernel: [    0.562282]   alloc kstat_irqs on node -1
Jun 24 00:05:27 s22 kernel: [    0.562286] pci 0000:00:03.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jun 24 00:05:27 s22 kernel: [    0.562290] pci 0000:00:03.0: setting latency timer to 64
Jun 24 00:05:27 s22 kernel: [    0.562296] pci 0000:00:05.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jun 24 00:05:27 s22 kernel: [    0.562299] pci 0000:00:05.0: setting latency timer to 64
Jun 24 00:05:27 s22 kernel: [    0.562306] pci 0000:00:1c.0: setting latency timer to 64
Jun 24 00:05:27 s22 kernel: [    0.562314] pci 0000:00:1c.4: setting latency timer to 64
Jun 24 00:05:27 s22 kernel: [    0.562322] pci 0000:00:1c.5: setting latency timer to 64
Jun 24 00:05:27 s22 kernel: [    0.562328] pci 0000:00:1e.0: setting latency timer to 64
Jun 24 00:05:27 s22 kernel: [    0.562331] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
Jun 24 00:05:27 s22 kernel: [    0.562334] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]
Jun 24 00:05:27 s22 kernel: [    0.562336] pci_bus 0000:04: resource 1 mem: [0xdf900000-0xdf9fffff]
Jun 24 00:05:27 s22 kernel: [    0.562338] pci_bus 0000:06: resource 1 mem: [0xde800000-0xdf7fffff]
Jun 24 00:05:27 s22 kernel: [    0.562340] pci_bus 0000:06: resource 2 pref mem [0xde000000-0xde7fffff]
Jun 24 00:05:27 s22 kernel: [    0.562342] pci_bus 0000:06: resource 3 io:  [0x00-0xffff]
Jun 24 00:05:27 s22 kernel: [    0.562344] pci_bus 0000:06: resource 4 mem: [0x000000-0xffffffffffffffff]
Jun 24 00:05:27 s22 kernel: [    0.562371] NET: Registered protocol family 2
Jun 24 00:05:27 s22 kernel: [    0.562440] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Jun 24 00:05:27 s22 kernel: [    0.562645] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Jun 24 00:05:27 s22 kernel: [    0.563258] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Jun 24 00:05:27 s22 kernel: [    0.563563] TCP: Hash tables configured (established 131072 bind 65536)
Jun 24 00:05:27 s22 kernel: [    0.563565] TCP reno registered
Jun 24 00:05:27 s22 kernel: [    0.563631] NET: Registered protocol family 1
Jun 24 00:05:27 s22 kernel: [    0.579602] pci 0000:06:03.0: Boot video device
Jun 24 00:05:27 s22 kernel: [    0.579826] cpufreq-nforce2: No nForce2 chipset.
Jun 24 00:05:27 s22 kernel: [    0.579843] Scanning for low memory corruption every 60 seconds
Jun 24 00:05:27 s22 kernel: [    0.579916] audit: initializing netlink socket (disabled)
Jun 24 00:05:27 s22 kernel: [    0.579922] type=2000 audit(1277337916.428:1): initialized
Jun 24 00:05:27 s22 kernel: [    0.589175] highmem bounce pool size: 64 pages
Jun 24 00:05:27 s22 kernel: [    0.589179] HugeTLB registered 2 MB page size, pre-allocated 0 pages
Jun 24 00:05:27 s22 kernel: [    0.590215] VFS: Disk quotas dquot_6.5.2
Jun 24 00:05:27 s22 kernel: [    0.590258] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Jun 24 00:05:27 s22 kernel: [    0.590658] fuse init (API version 7.13)
Jun 24 00:05:27 s22 kernel: [    0.590719] msgmni has been set to 1614
Jun 24 00:05:27 s22 kernel: [    0.590886] alg: No test for stdrng (krng)
Jun 24 00:05:27 s22 kernel: [    0.590925] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
Jun 24 00:05:27 s22 kernel: [    0.590927] io scheduler noop registered
Jun 24 00:05:27 s22 kernel: [    0.590929] io scheduler anticipatory registered
Jun 24 00:05:27 s22 kernel: [    0.590930] io scheduler deadline registered
Jun 24 00:05:27 s22 kernel: [    0.590958] io scheduler cfq registered (default)
Jun 24 00:05:27 s22 kernel: [    0.591053]   alloc irq_desc for 29 on node -1
Jun 24 00:05:27 s22 kernel: [    0.591054]   alloc kstat_irqs on node -1
Jun 24 00:05:27 s22 kernel: [    0.591061] pcieport 0000:00:03.0: irq 29 for MSI/MSI-X
Jun 24 00:05:27 s22 kernel: [    0.591067] pcieport 0000:00:03.0: setting latency timer to 64
Jun 24 00:05:27 s22 kernel: [    0.591149]   alloc irq_desc for 30 on node -1
Jun 24 00:05:27 s22 kernel: [    0.591150]   alloc kstat_irqs on node -1
Jun 24 00:05:27 s22 kernel: [    0.591155] pcieport 0000:00:05.0: irq 30 for MSI/MSI-X
Jun 24 00:05:27 s22 kernel: [    0.591161] pcieport 0000:00:05.0: setting latency timer to 64
Jun 24 00:05:27 s22 kernel: [    0.591245]   alloc irq_desc for 31 on node -1
Jun 24 00:05:27 s22 kernel: [    0.591246]   alloc kstat_irqs on node -1
Jun 24 00:05:27 s22 kernel: [    0.591252] pcieport 0000:00:1c.0: irq 31 for MSI/MSI-X
Jun 24 00:05:27 s22 kernel: [    0.591258] pcieport 0000:00:1c.0: setting latency timer to 64
Jun 24 00:05:27 s22 kernel: [    0.591339]   alloc irq_desc for 32 on node -1
Jun 24 00:05:27 s22 kernel: [    0.591341]   alloc kstat_irqs on node -1
Jun 24 00:05:27 s22 kernel: [    0.591346] pcieport 0000:00:1c.4: irq 32 for MSI/MSI-X
Jun 24 00:05:27 s22 kernel: [    0.591353] pcieport 0000:00:1c.4: setting latency timer to 64
Jun 24 00:05:27 s22 kernel: [    0.591435]   alloc irq_desc for 33 on node -1
Jun 24 00:05:27 s22 kernel: [    0.591436]   alloc kstat_irqs on node -1
Jun 24 00:05:27 s22 kernel: [    0.591442] pcieport 0000:00:1c.5: irq 33 for MSI/MSI-X
Jun 24 00:05:27 s22 kernel: [    0.591448] pcieport 0000:00:1c.5: setting latency timer to 64
Jun 24 00:05:27 s22 kernel: [    0.591715] aer 0000:00:03.0:pcie02: service driver aer loaded
Jun 24 00:05:27 s22 kernel: [    0.591745] aer 0000:00:05.0:pcie02: service driver aer loaded
Jun 24 00:05:27 s22 kernel: [    0.591751] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jun 24 00:05:27 s22 kernel: [    0.591768] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Jun 24 00:05:27 s22 kernel: [    0.591834] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
Jun 24 00:05:27 s22 kernel: [    0.591836] ACPI: Power Button [PWRF]
Jun 24 00:05:27 s22 kernel: [    0.592255] Monitor-Mwait will be used to enter C-1 state
Jun 24 00:05:27 s22 kernel: [    0.592275] Monitor-Mwait will be used to enter C-2 state
Jun 24 00:05:27 s22 kernel: [    0.592291] Monitor-Mwait will be used to enter C-3 state
Jun 24 00:05:27 s22 kernel: [    0.592322] processor LNXCPU:00: registered as cooling_device0
Jun 24 00:05:27 s22 kernel: [    0.603647] processor LNXCPU:01: registered as cooling_device1
Jun 24 00:05:27 s22 kernel: [    0.603997] processor LNXCPU:02: registered as cooling_device2
Jun 24 00:05:27 s22 kernel: [    0.604362] processor LNXCPU:03: registered as cooling_device3
Jun 24 00:05:27 s22 kernel: [    0.606368] isapnp: Scanning for PnP cards...
Jun 24 00:05:27 s22 kernel: [    0.607035] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
Jun 24 00:05:27 s22 kernel: [    0.607128] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Jun 24 00:05:27 s22 kernel: [    0.607222] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
Jun 24 00:05:27 s22 kernel: [    0.607454] 00:05: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Jun 24 00:05:27 s22 kernel: [    0.607587] 00:06: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
Jun 24 00:05:27 s22 kernel: [    0.608340] brd: module loaded
Jun 24 00:05:27 s22 kernel: [    0.608656] loop: module loaded
Jun 24 00:05:27 s22 kernel: [    0.608715] input: Macintosh mouse button emulation as /devices/virtual/input/input1
Jun 24 00:05:27 s22 kernel: [    0.608993] Fixed MDIO Bus: probed
Jun 24 00:05:27 s22 kernel: [    0.609016] PPP generic driver version 2.4.2
Jun 24 00:05:27 s22 kernel: [    0.609039] tun: Universal TUN/TAP device driver, 1.6
Jun 24 00:05:27 s22 kernel: [    0.609041] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Jun 24 00:05:27 s22 kernel: [    0.609105] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Jun 24 00:05:27 s22 kernel: [    0.609121]   alloc irq_desc for 22 on node -1
Jun 24 00:05:27 s22 kernel: [    0.609122]   alloc kstat_irqs on node -1
Jun 24 00:05:27 s22 kernel: [    0.609127] ehci_hcd 0000:00:1a.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Jun 24 00:05:27 s22 kernel: [    0.609135] ehci_hcd 0000:00:1a.0: setting latency timer to 64
Jun 24 00:05:27 s22 kernel: [    0.609138] ehci_hcd 0000:00:1a.0: EHCI Host Controller
Jun 24 00:05:27 s22 kernel: [    0.609163] ehci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
Jun 24 00:05:27 s22 kernel: [    0.609184] ehci_hcd 0000:00:1a.0: debug port 2
Jun 24 00:05:27 s22 kernel: [    0.613065] ehci_hcd 0000:00:1a.0: cache line size of 32 is not supported
Jun 24 00:05:27 s22 kernel: [    0.613076] ehci_hcd 0000:00:1a.0: irq 22, io mem 0xdf8fa000
Jun 24 00:05:27 s22 kernel: [    0.623498] ehci_hcd 0000:00:1a.0: USB 2.0 started, EHCI 1.00
Jun 24 00:05:27 s22 kernel: [    0.623561] usb usb1: configuration #1 chosen from 1 choice
Jun 24 00:05:27 s22 kernel: [    0.623580] hub 1-0:1.0: USB hub found
Jun 24 00:05:27 s22 kernel: [    0.623585] hub 1-0:1.0: 2 ports detected
Jun 24 00:05:27 s22 kernel: [    0.623620] ehci_hcd 0000:00:1d.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Jun 24 00:05:27 s22 kernel: [    0.623629] ehci_hcd 0000:00:1d.0: setting latency timer to 64
Jun 24 00:05:27 s22 kernel: [    0.623631] ehci_hcd 0000:00:1d.0: EHCI Host Controller
Jun 24 00:05:27 s22 kernel: [    0.623657] ehci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
Jun 24 00:05:27 s22 kernel: [    0.623676] ehci_hcd 0000:00:1d.0: debug port 2
Jun 24 00:05:27 s22 kernel: [    0.627567] ehci_hcd 0000:00:1d.0: cache line size of 32 is not supported
Jun 24 00:05:27 s22 kernel: [    0.627571] ehci_hcd 0000:00:1d.0: irq 22, io mem 0xdf8fc000
Jun 24 00:05:27 s22 kernel: [    0.639468] ehci_hcd 0000:00:1d.0: USB 2.0 started, EHCI 1.00
Jun 24 00:05:27 s22 kernel: [    0.639520] usb usb2: configuration #1 chosen from 1 choice
Jun 24 00:05:27 s22 kernel: [    0.639538] hub 2-0:1.0: USB hub found
Jun 24 00:05:27 s22 kernel: [    0.639542] hub 2-0:1.0: 2 ports detected
Jun 24 00:05:27 s22 kernel: [    0.639573] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Jun 24 00:05:27 s22 kernel: [    0.639583] uhci_hcd: USB Universal Host Controller Interface driver
Jun 24 00:05:27 s22 kernel: [    0.639636] PNP: No PS/2 controller found. Probing ports directly.
Jun 24 00:05:27 s22 kernel: [    0.640500] i8042.c: No controller found.
Jun 24 00:05:27 s22 kernel: [    0.640544] mice: PS/2 mouse device common for all mice
Jun 24 00:05:27 s22 kernel: [    0.640603] rtc_cmos 00:04: RTC can wake from S4
Jun 24 00:05:27 s22 kernel: [    0.640627] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
Jun 24 00:05:27 s22 kernel: [    0.640652] rtc0: alarms up to one day, y3k, 242 bytes nvram, hpet irqs
Jun 24 00:05:27 s22 kernel: [    0.640721] device-mapper: uevent: version 1.0.3
Jun 24 00:05:27 s22 kernel: [    0.640792] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
Jun 24 00:05:27 s22 kernel: [    0.640859] device-mapper: multipath: version 1.1.0 loaded
Jun 24 00:05:27 s22 kernel: [    0.640861] device-mapper: multipath round-robin: version 1.0.0 loaded
Jun 24 00:05:27 s22 kernel: [    0.640940] EISA: Probing bus 0 at eisa.0
Jun 24 00:05:27 s22 kernel: [    0.640966] EISA: Detected 0 cards.
Jun 24 00:05:27 s22 kernel: [    0.641143] cpuidle: using governor ladder
Jun 24 00:05:27 s22 kernel: [    0.641285] cpuidle: using governor menu
Jun 24 00:05:27 s22 kernel: [    0.641604] TCP cubic registered
Jun 24 00:05:27 s22 kernel: [    0.641710] NET: Registered protocol family 10
Jun 24 00:05:27 s22 kernel: [    0.642031] lo: Disabled Privacy Extensions
Jun 24 00:05:27 s22 kernel: [    0.642249] NET: Registered protocol family 17
Jun 24 00:05:27 s22 kernel: [    0.642935] Using IPI No-Shortcut mode
Jun 24 00:05:27 s22 kernel: [    0.642988] PM: Resume from disk failed.
Jun 24 00:05:27 s22 kernel: [    0.642996] registered taskstats version 1
Jun 24 00:05:27 s22 kernel: [    0.643286]   Magic number: 14:312:52
Jun 24 00:05:27 s22 kernel: [    0.643336] rtc_cmos 00:04: setting system clock to 2010-06-24 00:05:16 UTC (1277337916)
Jun 24 00:05:27 s22 kernel: [    0.643338] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Jun 24 00:05:27 s22 kernel: [    0.643339] EDD information not available.
Jun 24 00:05:27 s22 kernel: [    0.670585] Freeing initrd memory: 7726k freed
Jun 24 00:05:27 s22 kernel: [    0.934933] usb 1-1: new high speed USB device using ehci_hcd and address 2
Jun 24 00:05:27 s22 kernel: [    0.972152] isapnp: No Plug & Play device found
Jun 24 00:05:27 s22 kernel: [    0.972163] Freeing unused kernel memory: 672k freed
Jun 24 00:05:27 s22 kernel: [    0.972333] Write protecting the kernel text: 4828k
Jun 24 00:05:27 s22 kernel: [    0.972377] Write protecting the kernel read-only data: 1876k
Jun 24 00:05:27 s22 kernel: [    0.982912] udev: starting version 151
Jun 24 00:05:27 s22 kernel: [    0.997991] tg3.c:v3.102 (September 1, 2009)
Jun 24 00:05:27 s22 kernel: [    0.998005] tg3 0000:04:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jun 24 00:05:27 s22 kernel: [    0.998012] tg3 0000:04:00.0: setting latency timer to 64
Jun 24 00:05:27 s22 kernel: [    1.009182] ahci 0000:00:1f.2: version 3.0
Jun 24 00:05:27 s22 kernel: [    1.009194]   alloc irq_desc for 20 on node -1
Jun 24 00:05:27 s22 kernel: [    1.009195]   alloc kstat_irqs on node -1
Jun 24 00:05:27 s22 kernel: [    1.009201] ahci 0000:00:1f.2: PCI INT A -> GSI 20 (level, low) -> IRQ 20
Jun 24 00:05:27 s22 kernel: [    1.009228]   alloc irq_desc for 34 on node -1
Jun 24 00:05:27 s22 kernel: [    1.009229]   alloc kstat_irqs on node -1
Jun 24 00:05:27 s22 kernel: [    1.009236] ahci 0000:00:1f.2: irq 34 for MSI/MSI-X
Jun 24 00:05:27 s22 kernel: [    1.016273] eth0: Tigon3 [partno(BCM95722) rev a200] (PCI Express) MAC address 00:26:b9:85:fd:bc
Jun 24 00:05:27 s22 kernel: [    1.016276] eth0: attached PHY is 5722/5756 (10/100/1000Base-T Ethernet) (WireSpeed[1])
Jun 24 00:05:27 s22 kernel: [    1.016278] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[1] TSOcap[1]
Jun 24 00:05:27 s22 kernel: [    1.016280] eth0: dma_rwctrl[76180000] dma_mask[64-bit]
Jun 24 00:05:27 s22 kernel: [    1.022797] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 3 Gbps 0x3f impl SATA mode
Jun 24 00:05:27 s22 kernel: [    1.022800] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pmp pio slum part ems sxs apst 
Jun 24 00:05:27 s22 kernel: [    1.022804] ahci 0000:00:1f.2: setting latency timer to 64
Jun 24 00:05:27 s22 kernel: [    1.062727] scsi0 : ahci
Jun 24 00:05:27 s22 kernel: [    1.062791] scsi1 : ahci
Jun 24 00:05:27 s22 kernel: [    1.062831] scsi2 : ahci
Jun 24 00:05:27 s22 kernel: [    1.062868] scsi3 : ahci
Jun 24 00:05:27 s22 kernel: [    1.062904] scsi4 : ahci
Jun 24 00:05:27 s22 kernel: [    1.062940] scsi5 : ahci
Jun 24 00:05:27 s22 kernel: [    1.062967] ata1: SATA max UDMA/133 abar m2048@0xdf8fe000 port 0xdf8fe100 irq 34
Jun 24 00:05:27 s22 kernel: [    1.062970] ata2: SATA max UDMA/133 abar m2048@0xdf8fe000 port 0xdf8fe180 irq 34
Jun 24 00:05:27 s22 kernel: [    1.062972] ata3: SATA max UDMA/133 abar m2048@0xdf8fe000 port 0xdf8fe200 irq 34
Jun 24 00:05:27 s22 kernel: [    1.062975] ata4: SATA max UDMA/133 abar m2048@0xdf8fe000 port 0xdf8fe280 irq 34
Jun 24 00:05:27 s22 kernel: [    1.062977] ata5: SATA max UDMA/133 abar m2048@0xdf8fe000 port 0xdf8fe300 irq 34
Jun 24 00:05:27 s22 kernel: [    1.062979] ata6: SATA max UDMA/133 abar m2048@0xdf8fe000 port 0xdf8fe380 irq 34
Jun 24 00:05:27 s22 kernel: [    1.071128] usb 1-1: configuration #1 chosen from 1 choice
Jun 24 00:05:27 s22 kernel: [    1.071230] hub 1-1:1.0: USB hub found
Jun 24 00:05:27 s22 kernel: [    1.071331] hub 1-1:1.0: 6 ports detected
Jun 24 00:05:27 s22 kernel: [    1.182549] usb 2-1: new high speed USB device using ehci_hcd and address 2
Jun 24 00:05:27 s22 kernel: [    1.315070] usb 2-1: configuration #1 chosen from 1 choice
Jun 24 00:05:27 s22 kernel: [    1.315349] hub 2-1:1.0: USB hub found
Jun 24 00:05:27 s22 kernel: [    1.315479] hub 2-1:1.0: 6 ports detected
Jun 24 00:05:27 s22 kernel: [    1.545947] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Jun 24 00:05:27 s22 kernel: [    1.545968] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Jun 24 00:05:27 s22 kernel: [    1.545983] ata5: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Jun 24 00:05:27 s22 kernel: [    1.545997] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Jun 24 00:05:27 s22 kernel: [    1.546011] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Jun 24 00:05:27 s22 kernel: [    1.546025] ata6: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Jun 24 00:05:27 s22 kernel: [    1.547331] ata1.00: ATA-8: WDC WD2502ABYS-18B7A0, 02.03B04, max UDMA/133
Jun 24 00:05:27 s22 kernel: [    1.547337] ata3.00: ATA-8: ST32000542AS, CC34, max UDMA/133
Jun 24 00:05:27 s22 kernel: [    1.547342] ata4.00: ATA-8: ST32000542AS, CC34, max UDMA/133
Jun 24 00:05:27 s22 kernel: [    1.547347] ata2.00: ATA-8: ST32000542AS, CC34, max UDMA/133
Jun 24 00:05:27 s22 kernel: [    1.547352] ata3.00: 3907029168 sectors, multi 0: LBA48 NCQ (depth 31/32)
Jun 24 00:05:27 s22 kernel: [    1.547357] ata4.00: 3907029168 sectors, multi 0: LBA48 NCQ (depth 31/32)
Jun 24 00:05:27 s22 kernel: [    1.547362] ata2.00: 3907029168 sectors, multi 0: LBA48 NCQ (depth 31/32)
Jun 24 00:05:27 s22 kernel: [    1.547368] ata1.00: 488281250 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
Jun 24 00:05:27 s22 kernel: [    1.547396] ata5.00: ATA-8: ST32000542AS, CC34, max UDMA/133
Jun 24 00:05:27 s22 kernel: [    1.547401] ata5.00: 3907029168 sectors, multi 0: LBA48 NCQ (depth 31/32)
Jun 24 00:05:27 s22 kernel: [    1.547405] ata6.00: ATA-8: ST32000542AS, CC34, max UDMA/133
Jun 24 00:05:27 s22 kernel: [    1.547409] ata6.00: 3907029168 sectors, multi 0: LBA48 NCQ (depth 31/32)
Jun 24 00:05:27 s22 kernel: [    1.548836] ata1.00: configured for UDMA/133
Jun 24 00:05:27 s22 kernel: [    1.548977] ata5.00: configured for UDMA/133
Jun 24 00:05:27 s22 kernel: [    1.549018] ata6.00: configured for UDMA/133
Jun 24 00:05:27 s22 kernel: [    1.549035] ata3.00: configured for UDMA/133
Jun 24 00:05:27 s22 kernel: [    1.549037] ata2.00: configured for UDMA/133
Jun 24 00:05:27 s22 kernel: [    1.549039] ata4.00: configured for UDMA/133
Jun 24 00:05:27 s22 kernel: [    1.562201] scsi 0:0:0:0: Direct-Access     ATA      WDC WD2502ABYS-1 02.0 PQ: 0 ANSI: 5
Jun 24 00:05:27 s22 kernel: [    1.562290] sd 0:0:0:0: Attached scsi generic sg0 type 0
Jun 24 00:05:27 s22 kernel: [    1.562347] sd 0:0:0:0: [sda] 488281250 512-byte logical blocks: (250 GB/232 GiB)
Jun 24 00:05:27 s22 kernel: [    1.562378] sd 0:0:0:0: [sda] Write Protect is off
Jun 24 00:05:27 s22 kernel: [    1.562380] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Jun 24 00:05:27 s22 kernel: [    1.562385] scsi 1:0:0:0: Direct-Access     ATA      ST32000542AS     CC34 PQ: 0 ANSI: 5
Jun 24 00:05:27 s22 kernel: [    1.562394] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jun 24 00:05:27 s22 kernel: [    1.562474] sd 1:0:0:0: Attached scsi generic sg1 type 0
Jun 24 00:05:27 s22 kernel: [    1.562485]  sda:
Jun 24 00:05:27 s22 kernel: [    1.562516] sd 1:0:0:0: [sdb] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
Jun 24 00:05:27 s22 kernel: [    1.562544] sd 1:0:0:0: [sdb] Write Protect is off
Jun 24 00:05:27 s22 kernel: [    1.562546] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
Jun 24 00:05:27 s22 kernel: [    1.562561] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jun 24 00:05:27 s22 kernel: [    1.562564] scsi 2:0:0:0: Direct-Access     ATA      ST32000542AS     CC34 PQ: 0 ANSI: 5
Jun 24 00:05:27 s22 kernel: [    1.562645]  sdb:
Jun 24 00:05:27 s22 kernel: [    1.562648] sd 2:0:0:0: Attached scsi generic sg2 type 0
Jun 24 00:05:27 s22 kernel: [    1.562672] sd 2:0:0:0: [sdc] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
Jun 24 00:05:27 s22 kernel: [    1.562699] sd 2:0:0:0: [sdc] Write Protect is off
Jun 24 00:05:27 s22 kernel: [    1.562701] sd 2:0:0:0: [sdc] Mode Sense: 00 3a 00 00
Jun 24 00:05:27 s22 kernel: [    1.562715] sd 2:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jun 24 00:05:27 s22 kernel: [    1.562718] scsi 3:0:0:0: Direct-Access     ATA      ST32000542AS     CC34 PQ: 0 ANSI: 5
Jun 24 00:05:27 s22 kernel: [    1.562797]  sdc:
Jun 24 00:05:27 s22 kernel: [    1.562799] sd 3:0:0:0: Attached scsi generic sg3 type 0
Jun 24 00:05:27 s22 kernel: [    1.562843] sd 3:0:0:0: [sdd] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
Jun 24 00:05:27 s22 kernel: [    1.562873] sd 3:0:0:0: [sdd] Write Protect is off
Jun 24 00:05:27 s22 kernel: [    1.562875] sd 3:0:0:0: [sdd] Mode Sense: 00 3a 00 00
Jun 24 00:05:27 s22 kernel: [    1.562883] scsi 4:0:0:0: Direct-Access     ATA      ST32000542AS     CC34 PQ: 0 ANSI: 5
Jun 24 00:05:27 s22 kernel: [    1.562890] sd 3:0:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jun 24 00:05:27 s22 kernel: [    1.562967] sd 4:0:0:0: [sde] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
Jun 24 00:05:27 s22 kernel: [    1.562979] sd 4:0:0:0: Attached scsi generic sg4 type 0
Jun 24 00:05:27 s22 kernel: [    1.562994] sd 4:0:0:0: [sde] Write Protect is off
Jun 24 00:05:27 s22 kernel: [    1.562996] sd 4:0:0:0: [sde] Mode Sense: 00 3a 00 00
Jun 24 00:05:27 s22 kernel: [    1.563010] sd 4:0:0:0: [sde] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jun 24 00:05:27 s22 kernel: [    1.563050] scsi 5:0:0:0: Direct-Access     ATA      ST32000542AS     CC34 PQ: 0 ANSI: 5
Jun 24 00:05:27 s22 kernel: [    1.563102]  sde:
Jun 24 00:05:27 s22 kernel: [    1.563114] sd 5:0:0:0: [sdf] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
Jun 24 00:05:27 s22 kernel: [    1.563122]  sdd:
Jun 24 00:05:27 s22 kernel: [    1.563142] sd 5:0:0:0: [sdf] Write Protect is off
Jun 24 00:05:27 s22 kernel: [    1.563144] sd 5:0:0:0: [sdf] Mode Sense: 00 3a 00 00
Jun 24 00:05:27 s22 kernel: [    1.563159] sd 5:0:0:0: [sdf] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jun 24 00:05:27 s22 kernel: [    1.563235]  sdf:
Jun 24 00:05:27 s22 kernel: [    1.563283] sd 5:0:0:0: Attached scsi generic sg5 type 0
Jun 24 00:05:27 s22 kernel: [    1.573558]  sda1 sda2 < sda5 >
Jun 24 00:05:27 s22 kernel: [    1.593943] sd 0:0:0:0: [sda] Attached SCSI disk
Jun 24 00:05:27 s22 kernel: [    1.611853]  sdb1
Jun 24 00:05:27 s22 kernel: [    1.612232] sd 1:0:0:0: [sdb] Attached SCSI disk
Jun 24 00:05:27 s22 kernel: [    1.612586]  sdc1
Jun 24 00:05:27 s22 kernel: [    1.612983] sd 2:0:0:0: [sdc] Attached SCSI disk
Jun 24 00:05:27 s22 kernel: [    1.656336]  sdd1
Jun 24 00:05:27 s22 kernel: [    1.656719] sd 3:0:0:0: [sdd] Attached SCSI disk
Jun 24 00:05:27 s22 kernel: [    1.658702]  sde1
Jun 24 00:05:27 s22 kernel: [    1.659081] sd 4:0:0:0: [sde] Attached SCSI disk
Jun 24 00:05:27 s22 kernel: [    1.661909]  sdf1
Jun 24 00:05:27 s22 kernel: [    1.662212] sd 5:0:0:0: [sdf] Attached SCSI disk
Jun 24 00:05:27 s22 kernel: [    1.810189] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
Jun 24 00:05:27 s22 kernel: [    1.810192] EXT4-fs (sda1): write access will be enabled during recovery
Jun 24 00:05:27 s22 kernel: [    2.467679] EXT4-fs (sda1): orphan cleanup on readonly fs
Jun 24 00:05:27 s22 kernel: [    2.489283] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 7864339
Jun 24 00:05:27 s22 kernel: [    2.495573] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 7864399
Jun 24 00:05:27 s22 kernel: [    2.495600] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 7864403
Jun 24 00:05:27 s22 kernel: [    2.495622] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 7864404
Jun 24 00:05:27 s22 kernel: [    2.501734] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 7747018
Jun 24 00:05:27 s22 kernel: [    2.502047] EXT4-fs (sda1): 5 orphan inodes deleted
Jun 24 00:05:27 s22 kernel: [    2.502054] EXT4-fs (sda1): recovery complete
Jun 24 00:05:27 s22 kernel: [    2.748412] EXT4-fs (sda1): mounted filesystem with ordered data mode
Jun 24 00:05:27 s22 kernel: [    4.227206] Adding 93176k swap on /dev/sda5.  Priority:-1 extents:1 across:93176k 
Jun 24 00:05:27 s22 kernel: [    4.383965] udev: starting version 151
Jun 24 00:05:27 s22 kernel: [    5.027064] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
Jun 24 00:05:27 s22 kernel: [    5.043695] dell-wmi: No known WMI GUID found
Jun 24 00:05:27 s22 kernel: [    5.050035] vga16fb: initializing
Jun 24 00:05:27 s22 kernel: [    5.050037] vga16fb: mapped to 0xc00a0000
Jun 24 00:05:27 s22 kernel: [    5.050071] fb0: VGA16 VGA frame buffer device
Jun 24 00:05:27 s22 kernel: [    5.053212] ACPI Error: SMBus or IPMI write requires Buffer of length 42, found length 20 (20090903/exfield-286)
Jun 24 00:05:27 s22 kernel: [    5.053218] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PMI0._GHL] (Node f740f768), AE_AML_BUFFER_LIMIT
Jun 24 00:05:27 s22 kernel: [    5.053236] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PMI0._PMC] (Node f740f708), AE_AML_BUFFER_LIMIT
Jun 24 00:05:27 s22 kernel: [    5.053252] ACPI Exception: AE_AML_BUFFER_LIMIT, Evaluating _PMC (20090903/power_meter-772)
Jun 24 00:05:27 s22 kernel: [    5.061423] lp: driver loaded but no devices found
Jun 24 00:05:27 s22 kernel: [    5.098412] type=1505 audit(1277352320.960:2):  operation="profile_load" pid=542 name="/sbin/dhclient3"
Jun 24 00:05:27 s22 kernel: [    5.098824] type=1505 audit(1277352320.960:3):  operation="profile_load" pid=542 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Jun 24 00:05:27 s22 kernel: [    5.099044] type=1505 audit(1277352320.960:4):  operation="profile_load" pid=542 name="/usr/lib/connman/scripts/dhclient-script"
Jun 24 00:05:27 s22 kernel: [    5.280256] type=1505 audit(1277352321.144:5):  operation="profile_load" pid=653 name="/usr/sbin/ntpd"
Jun 24 00:05:27 s22 kernel: [    5.312571] Console: switching to colour frame buffer device 80x30
Jun 24 00:05:27 s22 kernel: [    5.363887]   alloc irq_desc for 35 on node -1
Jun 24 00:05:27 s22 kernel: [    5.363889]   alloc kstat_irqs on node -1
Jun 24 00:05:27 s22 kernel: [    5.363902] tg3 0000:04:00.0: irq 35 for MSI/MSI-X
Jun 24 00:05:27 s22 kernel: [    5.398023] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jun 24 00:05:27 s22 kernel: [    5.616474] Adding 8388600k swap on /mnt/8192Mb.swap.  Priority:-2 extents:38 across:9314296k 
Jun 24 00:05:27 s22 kernel: [    7.796002] tg3: eth0: Link is up at 1000 Mbps, full duplex.
Jun 24 00:05:27 s22 kernel: [    7.796004] tg3: eth0: Flow control is on for TX and on for RX.
Jun 24 00:05:27 s22 kernel: [    7.796143] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Jun 24 00:05:27 s22 kernel: [    8.096975] EXT4-fs (sde1): mounted filesystem with ordered data mode
Jun 24 00:05:27 s22 kernel: [    9.586448] EXT4-fs (sdb1): mounted filesystem with ordered data mode
Jun 24 00:05:27 s22 kernel: [   10.494276] EXT4-fs (sdc1): mounted filesystem with ordered data mode
Jun 24 00:05:27 s22 kernel: [   10.886488] EXT4-fs (sdd1): mounted filesystem with ordered data mode
Jun 24 00:05:27 s22 kernel: [   11.562551] type=1505 audit(1277352327.436:6):  operation="profile_replace" pid=903 name="/sbin/dhclient3"
Jun 24 00:05:27 s22 kernel: [   11.562927] type=1505 audit(1277352327.436:7):  operation="profile_replace" pid=903 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Jun 24 00:05:27 s22 kernel: [   11.563130] type=1505 audit(1277352327.436:8):  operation="profile_replace" pid=903 name="/usr/lib/connman/scripts/dhclient-script"
Jun 24 00:05:27 s22 kernel: [   11.564390] type=1505 audit(1277352327.440:9):  operation="profile_replace" pid=904 name="/usr/sbin/ntpd"
Jun 24 00:05:27 s22 kernel: [   11.579060] type=1505 audit(1277352327.452:10):  operation="profile_load" pid=905 name="/usr/sbin/tcpdump"
Jun 24 00:05:27 s22 cron[932]: (CRON) INFO (pidfile fd = 3)
Jun 24 00:05:27 s22 cron[939]: (CRON) STARTUP (fork ok)
Jun 24 00:05:27 s22 cron[939]: (CRON) INFO (Running @reboot jobs)
Jun 24 00:05:29 s22 ntpdate[801]: step time server 91.189.94.4 offset -0.057976 sec
Jun 24 00:05:29 s22 ntpd[1029]: ntpd 4.2.4p8@1.1612-o Fri Apr  9 00:28:40 UTC 2010 (1)
Jun 24 00:05:29 s22 ntpd[1044]: precision = 1.000 usec
Jun 24 00:05:29 s22 ntpd[1044]: ntp_io: estimated max descriptors: 1024, initial socket boundary: 16
Jun 24 00:05:29 s22 ntpd[1044]: Listening on interface #0 wildcard, 0.0.0.0#123 Disabled
Jun 24 00:05:29 s22 ntpd[1044]: Listening on interface #1 wildcard, ::#123 Disabled
Jun 24 00:05:29 s22 ntpd[1044]: Listening on interface #2 lo, ::1#123 Enabled
Jun 24 00:05:29 s22 ntpd[1044]: Listening on interface #3 eth0, fe80::226:b9ff:fe85:fdbc#123 Enabled
Jun 24 00:05:29 s22 ntpd[1044]: Listening on interface #4 lo, 127.0.0.1#123 Enabled
Jun 24 00:05:29 s22 ntpd[1044]: Listening on interface #5 eth0, 127.0.0.1#123 Enabled
Jun 24 00:05:29 s22 ntpd[1044]: Listening on interface #6 eth0:1, 127.0.0.1#123 Enabled
Jun 24 00:05:29 s22 ntpd[1044]: kernel time sync status 2040
Jun 24 00:05:29 s22 ntpd[1044]: frequency initialized -59.423 PPM from /var/lib/ntp/ntp.drift
Jun 24 00:05:31 s22 ntpd[1044]: ntpd exiting on signal 15
Jun 24 00:05:32 s22 ntpdate[1077]: step time server 91.189.94.4 offset 0.000067 sec
Jun 24 00:05:32 s22 ntpd[1104]: ntpd 4.2.4p8@1.1612-o Fri Apr  9 00:28:40 UTC 2010 (1)
Jun 24 00:05:32 s22 ntpd[1105]: precision = 1.000 usec
Jun 24 00:05:32 s22 ntpd[1105]: ntp_io: estimated max descriptors: 1024, initial socket boundary: 16
Jun 24 00:05:32 s22 ntpd[1105]: Listening on interface #0 wildcard, 0.0.0.0#123 Disabled
Jun 24 00:05:32 s22 ntpd[1105]: Listening on interface #1 wildcard, ::#123 Disabled
Jun 24 00:05:32 s22 ntpd[1105]: Listening on interface #2 lo, ::1#123 Enabled
Jun 24 00:05:32 s22 ntpd[1105]: Listening on interface #3 eth0, fe80::226:b9ff:fe85:fdbc#123 Enabled
Jun 24 00:05:32 s22 ntpd[1105]: Listening on interface #4 lo, 127.0.0.1#123 Enabled
Jun 24 00:05:32 s22 ntpd[1105]: Listening on interface #5 eth0, 127.0.0.1#123 Enabled
Jun 24 00:05:32 s22 ntpd[1105]: Listening on interface #6 eth0:1, 127.0.0.1#123 Enabled
Jun 24 00:05:32 s22 ntpd[1105]: kernel time sync status 2040
Jun 24 00:05:32 s22 ntpd[1105]: frequency initialized -59.423 PPM from /var/lib/ntp/ntp.drift
Jun 24 00:05:34 s22 kernel: [   18.687777] eth0: no IPv6 routers present
Jun 24 00:06:01 s22 postfix/sendmail[1461]: fatal: open /etc/postfix/main.cf: No such file or directory
Jun 24 00:09:01 s22 CRON[2956]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Jun 24 00:09:51 s22 ntpd[1105]: synchronized to 91.189.94.4, stratum 2
Jun 24 00:09:51 s22 ntpd[1105]: kernel time sync status change 2001
Jun 24 00:15:01 s22 CRON[6976]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Jun 24 00:17:01 s22 CRON[8203]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jun 24 00:25:01 s22 CRON[13076]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)

```

---

