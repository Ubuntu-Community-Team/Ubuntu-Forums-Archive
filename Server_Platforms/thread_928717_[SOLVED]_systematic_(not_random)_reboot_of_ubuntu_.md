---
title: "[SOLVED] systematic (not random) reboot of ubuntu server"
date: 2008-09-24
forum: Server Platforms
---

### Post by leandromartinez98 on 2008-09-24
I have installed the Ubuntu Server in a machine we will be using
for backups. The machine is rebooting systematically every day
at about 6:30AM, at least as we can see from the messages file.
Anyone has any clue about what may be causing this behavior?

Specifications:

Linux 2.6.24-19-server #1 SMP Wed Jun 18 14:44:47 UTC 2008 x86_64 GNU/Linux


Sep 21 06:51:13 gomorra syslogd 1.5.0#1ubuntu1: restart. 
Sep 21 07:18:39 gomorra -- MARK -- 
Sep 21 07:38:39 gomorra -- MARK --
Sep 21 07:58:39 gomorra -- MARK --
...
Sep 22 05:58:39 gomorra -- MARK --
Sep 22 06:18:39 gomorra -- MARK --
Sep 22 06:26:16 gomorra syslogd 1.5.0#1ubuntu1: restart.
Sep 22 06:38:39 gomorra -- MARK --
Sep 22 06:58:39 gomorra -- MARK --
...
Sep 23 06:18:39 gomorra -- MARK --
Sep 23 06:38:39 gomorra -- MARK --
Sep 23 06:47:45 gomorra syslogd 1.5.0#1ubuntu1: restart.
Sep 23 06:58:39 gomorra -- MARK --
Sep 23 07:18:39 gomorra -- MARK --
...
Sep 24 05:58:39 gomorra -- MARK --
Sep 24 06:18:39 gomorra -- MARK --
Sep 24 06:35:29 gomorra syslogd 1.5.0#1ubuntu1: restart.
Sep 24 06:58:39 gomorra -- MARK --
Sep 24 07:18:39 gomorra -- MARK --

By the way, what does this "MARK" message is about? (It is the only
message that appears within two reboots).

Attached I provide the dmesg output.

Since this does not seem to be a random reboot, it maybe related
to some configuration. 

Thank you for the help,
Leandro.

---

### Post by leandromartinez98 on 2008-09-24
By the way, these messages actually mean that the system is rebooting?
I realize that I'm getting the same king of messages in my Ubuntu
desktop, and that they can be reproduced by reestarting the syslogd
daemon. Therefore, the system may not be rebooting, but in that case,
why it is reestarting the syslogd?
Thanks,
Leandro.

---

### Post by cdenley on 2008-09-24
> **leandromartinez98 said:**
> By the way, these messages actually mean that the system is rebooting?
I realize that I'm getting the same king of messages in my Ubuntu
desktop, and that they can be reproduced by reestarting the syslogd
daemon. Therefore, the system may not be rebooting, but in that case,
why it is reestarting the syslogd?
Thanks,
Leandro.

log rotation

It can't log everything forever. It moves the logs around and deletes the old ones every time syslogd is restarted.

---

### Post by leandromartinez98 on 2008-09-24
Is there anyway we can distinguish this from a reboot?
Thanks,
Leandro.

---

### Post by cariboo on 2008-09-24
You get a lot more output than just mark:

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.27-4-generic (buildd@yellow) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu7) ) #1 SMP Wed Sep 24 01:29:06 UTC 2008 (Ubuntu 2.6.27-4.6-generic)
[    0.000000] Command line: root=UUID=99bde364-6452-493f-8401-be4d55eef5e1 ro quiet splash 
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007dfd0000 (usable)
[    0.000000]  BIOS-e820: 000000007dfd0000 - 000000007dfde000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007dfde000 - 000000007e000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fef00000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff780000 - 0000000100000000 (reserved)
[    0.000000] last_pfn = 0x7dfd0 max_arch_pfn = 0x3ffffffff
[    0.000000] init_memory_mapping
```

This is just a small snippet of the boot up message.

Jim

---

### Post by gpredrag on 2008-09-25
You should use
```
uptime
```
or
```
last -x 
```
commands to see how long has your server been up.

---

### Post by leandromartinez98 on 2008-09-30
> **gpredrag said:**
> You should use
```
uptime
```
or
```
last -x 
```
commands to see how long has your server been up.

Excelent! Thank you very much.
Leandro.

---

