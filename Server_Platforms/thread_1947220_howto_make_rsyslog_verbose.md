---
title: "howto make rsyslog verbose ?"
date: 2012-03-26
forum: Server Platforms
---

### Post by LeFelis on 2012-03-26
Hi,
My remote server crash from time to time. It needs a hard reboot to restart. The log files (/etc/log/ufw.log, daemon.log, dmesg, udev...) don't log any problem. 

I would like to log much more details to find the bug.I don't know how to edit the rsyslog.conf. What are the daemons that should be logged ? Which level of log should be set in rsyslog.conf ?

My production server is a 10.04 ubuntu LTS with apache, mysql, ufw, vsftp, apparmor and a few user's daemons.

Thanks,
LeFélis

---

### Post by LeFelis on 2012-03-27
My serveur crash again this morning. There is something strange in the log. I don't undestand what this mean. (XXXXXXX is the server name).

Mar 27 07:23:30 XXXXXXX kernel: [UFW BLOCK] IN=eth0 OUT= [...]
Mar 27 07:59:48 XXXXXXX kernel: imklog 4.2.0, log source = /proc/kmsg started.
Mar 27 07:59:48 XXXXXXX kernel: Initializing cgroup subsys cpuset
Mar 27 07:59:48 XXXXXXX kernel: Linux version 2.6.38.2-grsec-xxxx-grs-ipv6-6Mar 27 08:05:12 XXXXXXX kernel: imklog 4.2.0, log source = /proc/kmsg started.
Mar 27 08:05:12 XXXXXXX kernel: Initializing cgroup subsys cpuset
Mar 27 08:05:12 XXXXXXX kernel: Linux version 2.6.38.2-grsec-xxxx-grs-ipv6-64 (root@kernel-64.ovh.net) (gcc version 4.3.2 (Debian 4.3.2-1.1) ) #1 SMP Fri Apr 15 17:44:15 UTC 2011
Mar 27 08:05:12 XXXXXXX kernel: Command line: BOOT_IMAGE=/boot/bzImage-2.6.38.2-xxxx-grs-ipv6-64 root=/dev/md1 ro nomodeset
Mar 27 08:05:12 XXXXXXX kernel: BIOS-provided physical RAM map:
Mar 27 08:05:12 XXXXXXX kernel: BIOS-e820: 0000000000000000 - 000000000009d800 (usable)
Mar 27 08:05:12 XXXXXXX kernel: BIOS-e820: 000000000009d800 - 00000000000a0000 (reserved)

---

### Post by SeijiSensei on 2012-03-27
I don't see anything especially alarming in that log output.

One common reason for random system failures is a bad memory chip.  Often you won't see anything in the log that identifies this situation.  You'll need to have physical access to the machine and run the memtest86 program at boot to diagnose memory errors.  I realize that's not an easy solution to implement on a remote server, but there's no other way to run a memory check.

---

### Post by LeFelis on 2012-03-28
The strange ligne is this one:
Mar 27 07:59:48 XXXXXXX kernel: Linux version  2.6.38.2-grsec-xxxx-grs-ipv6-6Mar 27 08:05:12 XXXXXXX kernel: imklog  4.2.0, log source = /proc/kmsg started.

The server crash during the boot and restant a few minutes later.


I make a memory test, a disk test and a cpu test. All tests are ok.
A rsyslog with more log may be usefull ?

---

