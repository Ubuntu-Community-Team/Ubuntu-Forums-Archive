---
title: "Server not responding"
date: 2018-11-19
forum: Server Platforms
---

### Post by fernandoch on 2018-11-19
Hello,

I have an Ubuntu LAMP server and from time to time, the server does not respond, and all sites are down.

I can't even connect via ssh.

I reboot the server via control panel and I connect but I can't find much in the logs.

Where do you suggest that I dig deaper to check the cause?

Thanks

---

### Post by darkod on 2018-11-19
Looks like network connectivity stops working. Did you try checking /var/log/syslog to start with?

Any possibility that you have IP conflict? That would result in server networking getting messed up.

---

### Post by fernandoch on 2018-11-19
No IP conflict, this is a dedicated server.

---

### Post by lisati on 2018-11-19
Sometimes an IP conflict can sneak up on us unawares, particularly when we configure it only on the server. When I was running a server at home, I managed to avoid it by having a reserved address set directly on my router's control panel, and letting the server use whichever address the router handed out.

---

### Post by fernandoch on 2018-11-20
I don't think an IP is the problem as it was working well and never had IP problems with OVH.

Any other ideas?

---

### Post by darkod on 2018-11-20
Did you check syslog for messages?

---

### Post by fernandoch on 2018-11-20
Nop, I will next time.

---

### Post by fernandoch on 2018-11-23
Server freezed again, here are some logs from syslog, I think this might be the problem

```
Nov 23 15:14:11 ns30XX870 kernel: [UFW BLOCK] IN=eth0 OUT= MAC=00:22:4d:a4:06:52:10:bd:18:e5:ff:80:08:00 SRC=178.169.212.198 DST=XX.188.23.70 LEN=40 TOS=0x00 PREC=0x00 TTL=56 ID=17407 PROTO=TCP SPT=16273 DPT=37215 WINDOW=50033 RES=0x00 SYN URGP=0
Nov 23 15:14:24 ns30XX870 kernel: [UFW BLOCK] IN=eth0 OUT= MAC=00:22:4d:a4:06:52:10:bd:18:e5:ff:80:08:00 SRC=176.119.7.6 DST=XX.188.23.70 LEN=40 TOS=0x00 PREC=0x00 TTL=248 ID=21868 PROTO=TCP SPT=58548 DPT=20969 WINDOW=1024 RES=0x00 SYN URGP=0
^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@
Nov 23 15:16:06 ns3011870 rsyslogd: [origin software="rsyslogd" swVersion="8.16.0" x-pid="639" x-info="http://www.rsyslog.com"] start
Nov 23 15:16:06 ns3011870 rsyslogd-2222: command 'KLogPermitNonKernelFacility' is currently not permitted - did you already set it via a RainerScript command (v6+ config)? [v8.16.0 try http://www.rsyslog.com/e/2222 ]
Nov 23 15:16:06 ns3011870 systemd-sysctl[254]: Couldn't write '1' to 'kernel/yama/ptrace_scope', ignoring: No such file or directory
Nov 23 15:16:06 ns3011870 rsyslogd: rsyslogd's groupid changed to 108
Nov 23 15:16:06 ns3011870 rsyslogd: rsyslogd's userid changed to 104
Nov 23 15:16:06 ns3011870 ureadahead[242]: ureadahead: Error while tracing: No such file or directory
Nov 23 15:16:06 ns3011870 systemd[1]: ureadahead.service: Main process exited, code=exited, status=5/NOTINSTALLED
Nov 23 15:16:06 ns3011870 systemd[1]: ureadahead.service: Unit entered failed state.
Nov 23 15:16:06 ns3011870 systemd[1]: ureadahead.service: Failed with result 'exit-code'.
Nov 23 15:16:06 ns3011870 systemd-fsck[246]: /: clean, 184170/29818880 files, 3241270/119273472 blocks
Nov 23 15:16:06 ns3011870 systemd[1]: Started File System Check on Root Device.
Nov 23 15:16:06 ns3011870 systemd[1]: Starting Remount Root and Kernel File Systems...
Nov 23 15:16:06 ns3011870 systemd[1]: Started LVM2 metadata daemon.
Nov 23 15:16:06 ns3011870 systemd[1]: Started Remount Root and Kernel File Systems.
Nov 23 15:16:06 ns3011870 systemd[1]: Starting udev Coldplug all Devices...
Nov 23 15:16:06 ns3011870 systemd[1]: Starting Flush Journal to Persistent Storage...
Nov 23 15:16:06 ns3011870 rsyslogd-2039: Could not open output pipe '/dev/xconsole':: No such file or directory [v8.16.0 try http://www.rsyslog.com/e/2039 ]
Nov 23 15:16:06 ns3011870 systemd[1]: Starting Load/Save Random Seed...
Nov 23 15:16:06 ns3011870 kernel: Linux version 4.9.87-xxxx-std-ipv6-64 (kernel@kernel.ovh.net) (gcc version 7.3.0 (GCC) ) #1 SMP Tue Mar 13 18:41:47 CET 2018
Nov 23 15:16:06 ns3011870 kernel: Command line: BOOT_IMAGE=/bzImage-4.9.87-xxxx-std-ipv6-64 root=/dev/sda2 ro noquiet nosplash net.ifnames=0 biosdevname=0
Nov 23 15:16:06 ns3011870 kernel: Disabled fast string operations
Nov 23 15:16:06 ns3011870 systemd[1]: Started Create Static Device Nodes in /dev.
Nov 23 15:16:06 ns3011870 kernel: x86/fpu: Legacy x87 FPU detected.
Nov 23 15:16:06 ns3011870 kernel: x86/fpu: Using 'eager' FPU context switches.
Nov 23 15:16:06 ns3011870 systemd[1]: Starting udev Kernel Device Manager...
Nov 23 15:16:06 ns3011870 kernel: e820: BIOS-provided physical RAM map:
Nov 23 15:16:06 ns3011870 kernel: BIOS-e820: [mem 0x0000000000000000-0x000000000008efff] usable
Nov 23 15:16:06 ns3011870 kernel: BIOS-e820: [mem 0x000000000008f000-0x000000000008ffff] reserved
Nov 23 15:16:06 ns3011870 kernel: BIOS-e820: [mem 0x0000000000090000-0x000000000009e7ff] usable
Nov 23 15:16:06 ns3011870 kernel: BIOS-e820: [mem 0x000000000009e800-0x000000000009ffff] reserved
Nov 23 15:16:06 ns3011870 kernel: BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved
Nov 23 15:16:06 ns3011870 systemd[1]: Started Load/Save Random Seed.
Nov 23 15:16:06 ns3011870 kernel: BIOS-e820: [mem 0x0000000000100000-0x000000007ee94fff] usable
Nov 23 15:16:06 ns3011870 kernel: BIOS-e820: [mem 0x000000007ee95000-0x000000007eebefff] reserved
Nov 23 15:16:06 ns3011870 kernel: BIOS-e820: [mem 0x000000007eebf000-0x000000007eee3fff] usable
Nov 23 15:16:06 ns3011870 kernel: BIOS-e820: [mem 0x000000007eee4000-0x000000007efbefff] ACPI NVS
Nov 23 15:16:06 ns3011870 kernel: BIOS-e820: [mem 0x000000007efbf000-0x000000007efeefff] usable
Nov 23 15:16:06 ns3011870 systemd[1]: Started Flush Journal to Persistent Storage.
Nov 23 15:16:06 ns3011870 rsyslogd-2007: action 'action 10' suspended, next retry is Fri Nov 23 15:16:36 2018 [v8.16.0 try http://www.rsyslog.com/e/2007 ]
Nov 23 15:16:06 ns3011870 kernel: BIOS-e820: [mem 0x000000007efef000-0x000000007effefff] ACPI data
Nov 23 15:16:06 ns3011870 kernel: BIOS-e820: [mem 0x000000007efff000-0x000000007effffff] usable
Nov 23 15:16:06 ns3011870 kernel: BIOS-e820: [mem 0x000000007f000000-0x000000007fffffff] reserved
Nov 23 15:16:06 ns3011870 kernel: BIOS-e820: [mem 0x00000000e0000000-0x00000000e3ffffff] reserved
Nov 23 15:16:06 ns3011870 kernel: BIOS-e820: [mem 0x00000000ffe00000-0x00000000ffffffff] reserved
Nov 23 15:16:06 ns3011870 kernel: NX (Execute Disable) protection: active
Nov 23 15:16:06 ns3011870 systemd-udevd[281]: Network interface NamePolicy= disabled on kernel command line, ignoring.
Nov 23 15:16:06 ns3011870 kernel: SMBIOS 2.7 present.
Nov 23 15:16:06 ns3011870 kernel: DMI:                  /DN2800MT, BIOS MTCDT10N.86A.0165.2013.0114.1540 01/14/2013
Nov 23 15:16:06 ns3011870 kernel: e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
Nov 23 15:16:06 ns3011870 kernel: e820: remove [mem 0x000a0000-0x000fffff] usable
Nov 23 15:16:06 ns3011870 kernel: e820: last_pfn = 0x7f000 max_arch_pfn = 0x400000000
Nov 23 15:16:06 ns3011870 kernel: MTRR default type: uncachable
Nov 23 15:16:06 ns3011870 loadkeys[248]: Loading /etc/console-setup/cached.kmap.gz
Nov 23 15:16:06 ns3011870 kernel: MTRR fixed ranges enabled:
Nov 23 15:16:06 ns3011870 kernel:  00000-9FFFF write-back
```

---

