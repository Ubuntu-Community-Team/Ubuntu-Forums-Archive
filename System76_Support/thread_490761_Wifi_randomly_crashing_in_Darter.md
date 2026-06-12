---
title: "Wifi randomly crashing in Darter"
date: 2007-07-02
forum: System76 Support
---

### Post by beuno on 2007-07-02
I just got a hold on my new Darter today, and I have been running into some problems.

The main one has been having the wifi card randomly crash on me, and spitting out the following into the console:

```
Message from syslogd@ubuntu at Tue Jul  3 02:02:59 2007 ...
ubuntu kernel: [ 4644.464000]  [worker_thread+327/368] worker_thread+0x147/0x170

Message from syslogd@ubuntu at Tue Jul  3 02:02:59 2007 ...
ubuntu kernel: [ 4644.464000]  [default_wake_function+0/16] default_wake_function+0x0/0x10

Message from syslogd@ubuntu at Tue Jul  3 02:02:59 2007 ...
ubuntu kernel: [ 4644.464000]  [worker_thread+0/368] worker_thread+0x0/0x170

Message from syslogd@ubuntu at Tue Jul  3 02:02:59 2007 ...
ubuntu kernel: [ 4644.464000]  [kthread+186/240] kthread+0xba/0xf0

Message from syslogd@ubuntu at Tue Jul  3 02:02:59 2007 ...
ubuntu kernel: [ 4644.464000]  [kthread+0/240] kthread+0x0/0xf0

Message from syslogd@ubuntu at Tue Jul  3 02:02:59 2007 ...
ubuntu kernel: [ 4644.464000]  [kernel_thread_helper+7/16] kernel_thread_helper+0x7/0x10

Message from syslogd@ubuntu at Tue Jul  3 02:02:59 2007 ...
ubuntu kernel: [ 4644.464000]  =======================

Message from syslogd@ubuntu at Tue Jul  3 02:02:59 2007 ...
ubuntu kernel: [ 4644.464000]  [<f8bd5d17>] ipw_bg_abort_scan+0x57/0x60 [ipw3945]

Message from syslogd@ubuntu at Tue Jul  3 02:02:59 2007 ...
ubuntu kernel: [ 4644.464000] Code: ff ff f7 ff 89 83 30 05 00 00 83 c4 10 5b c3 90 8d 74 26 00 89 e2 89 d8 e8 e7 f8 ff ff 85 c0 75 26 8b 54 24 04 8b 82 a4 00 00 00 <83> 78 08 01 74 0a 81 a3 30 05 00 00 ff ff d7 ff 89 d0 e8 52 cb 

Message from syslogd@ubuntu at Tue Jul  3 02:02:59 2007 ...
ubuntu kernel: [ 4644.464000] EIP: [<f8bd5c87>] ipw_abort_scan+0x77/0xb0 [ipw3945] SS:ESP 0068:f7815f34
```

And my messages file has the following:

```
Jul  3 02:10:25 ubuntu kernel: [   40.724000] lo: Disabled Privacy Extensions
Jul  3 02:10:25 ubuntu kernel: [   40.724000] ADDRCONF(NETDEV_UP): eth1: link is not ready
Jul  3 02:10:25 ubuntu kernel: [   40.724000] ADDRCONF(NETDEV_UP): eth2: link is not ready
Jul  3 02:10:29 ubuntu gconfd (beuno-5491): Resolved address "xml:readwrite:/home/beuno/.gconf" to a writable configuration source at position 0
Jul  3 02:10:32 ubuntu dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth2 for sub-path eth2.dbus.get.reason
Jul  3 02:10:34 ubuntu bonobo-activation-server (beuno-5538): Passing command-line arguments in .server files is deprecated: "/usr/bin/tomboy --panel-applet"
Jul  3 02:10:37 ubuntu kernel: [   52.328000] ADDRCONF(NETDEV_CHANGE): eth2: link becomes ready
Jul  3 02:10:43 ubuntu dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth2 for sub-path eth2.dbus.get.domain_name
Jul  3 02:10:43 ubuntu dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth2 for sub-path eth2.dbus.get.nis_domain
Jul  3 02:10:43 ubuntu dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth2 for sub-path eth2.dbus.get.nis_servers
Jul  3 02:16:02 ubuntu kernel: [  378.060000] ACPI Error (psargs-0355): [\_SB_.PCI0.P0P2.VGA_.LCDD] Namespace lookup failure, AE_NOT_FOUND
Jul  3 02:16:02 ubuntu kernel: [  378.060000] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.SBRG.EC0_._Q0F] (Node df8bf75c), AE_NOT_FOUND
Jul  3 02:16:02 ubuntu kernel: [  378.244000] ACPI Error (psargs-0355): [\_SB_.PCI0.P0P2.VGA_.LCDD] Namespace lookup failure, AE_NOT_FOUND
Jul  3 02:16:02 ubuntu kernel: [  378.244000] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.SBRG.EC0_._Q0F] (Node df8bf75c), AE_NOT_FOUND
Jul  3 02:16:03 ubuntu kernel: [  378.416000] ACPI Error (psargs-0355): [\_SB_.PCI0.P0P2.VGA_.LCDD] Namespace lookup failure, AE_NOT_FOUND
Jul  3 02:16:03 ubuntu kernel: [  378.416000] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.SBRG.EC0_._Q0F] (Node df8bf75c), AE_NOT_FOUND
Jul  3 02:16:03 ubuntu kernel: [  378.556000] ACPI Error (psargs-0355): [\_SB_.PCI0.P0P2.VGA_.LCDD] Namespace lookup failure, AE_NOT_FOUND
Jul  3 02:16:03 ubuntu kernel: [  378.556000] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.SBRG.EC0_._Q0E] (Node df8bdc20), AE_NOT_FOUND
Jul  3 02:16:03 ubuntu kernel: [  378.712000] ACPI Error (psargs-0355): [\_SB_.PCI0.P0P2.VGA_.LCDD] Namespace lookup failure, AE_NOT_FOUND
Jul  3 02:16:03 ubuntu kernel: [  378.712000] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.SBRG.EC0_._Q0E] (Node df8bdc20), AE_NOT_FOUND
Jul  3 02:16:03 ubuntu kernel: [  378.872000] ACPI Error (psargs-0355): [\_SB_.PCI0.P0P2.VGA_.LCDD] Namespace lookup failure, AE_NOT_FOUND
Jul  3 02:16:03 ubuntu kernel: [  378.872000] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.SBRG.EC0_._Q0E] (Node df8bdc20), AE_NOT_FOUND
Jul  3 02:16:03 ubuntu kernel: [  379.032000] ACPI Error (psargs-0355): [\_SB_.PCI0.P0P2.VGA_.LCDD] Namespace lookup failure, AE_NOT_FOUND
Jul  3 02:16:03 ubuntu kernel: [  379.032000] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.SBRG.EC0_._Q0E] (Node df8bdc20), AE_NOT_FOUND
Jul  3 02:16:03 ubuntu kernel: [  379.204000] ACPI Error (psargs-0355): [\_SB_.PCI0.P0P2.VGA_.LCDD] Namespace lookup failure, AE_NOT_FOUND
Jul  3 02:16:03 ubuntu kernel: [  379.204000] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.SBRG.EC0_._Q0E] (Node df8bdc20), AE_NOT_FOUND
Jul  3 02:16:04 ubuntu kernel: [  379.364000] ACPI Error (psargs-0355): [\_SB_.PCI0.P0P2.VGA_.LCDD] Namespace lookup failure, AE_NOT_FOUND
Jul  3 02:16:04 ubuntu kernel: [  379.364000] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.SBRG.EC0_._Q0E] (Node df8bdc20), AE_NOT_FOUND
Jul  3 02:16:04 ubuntu kernel: [  379.528000] ACPI Error (psargs-0355): [\_SB_.PCI0.P0P2.VGA_.LCDD] Namespace lookup failure, AE_NOT_FOUND
Jul  3 02:16:04 ubuntu kernel: [  379.528000] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.SBRG.EC0_._Q0E] (Node df8bdc20), AE_NOT_FOUND
Jul  3 02:16:05 ubuntu kernel: [  380.492000] ACPI Error (psargs-0355): [\_SB_.PCI0.P0P2.VGA_.LCDD] Namespace lookup failure, AE_NOT_FOUND
Jul  3 02:16:05 ubuntu kernel: [  380.492000] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.SBRG.EC0_._Q0E] (Node df8bdc20), AE_NOT_FOUND
Jul  3 02:16:05 ubuntu kernel: [  380.652000] ACPI Error (psargs-0355): [\_SB_.PCI0.P0P2.VGA_.LCDD] Namespace lookup failure, AE_NOT_FOUND
Jul  3 02:16:05 ubuntu kernel: [  380.652000] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.SBRG.EC0_._Q0E] (Node df8bdc20), AE_NOT_FOUND
Jul  3 02:16:05 ubuntu kernel: [  380.820000] ACPI Error (psargs-0355): [\_SB_.PCI0.P0P2.VGA_.LCDD] Namespace lookup failure, AE_NOT_FOUND
Jul  3 02:16:05 ubuntu kernel: [  380.820000] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.SBRG.EC0_._Q0E] (Node df8bdc20), AE_NOT_FOUND
Jul  3 02:16:05 ubuntu kernel: [  381.000000] ACPI Error (psargs-0355): [\_SB_.PCI0.P0P2.VGA_.LCDD] Namespace lookup failure, AE_NOT_FOUND
Jul  3 02:16:05 ubuntu kernel: [  381.000000] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.SBRG.EC0_._Q0F] (Node df8bf75c), AE_NOT_FOUND
Jul  3 02:16:05 ubuntu kernel: [  381.108000] ACPI Error (psargs-0355): [\_SB_.PCI0.P0P2.VGA_.LCDD] Namespace lookup failure, AE_NOT_FOUND
Jul  3 02:16:05 ubuntu kernel: [  381.108000] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.SBRG.EC0_._Q0E] (Node df8bdc20), AE_NOT_FOUND
Jul  3 02:16:05 ubuntu kernel: [  381.232000] ACPI Error (psargs-0355): [\_SB_.PCI0.P0P2.VGA_.LCDD] Namespace lookup failure, AE_NOT_FOUND
Jul  3 02:16:05 ubuntu kernel: [  381.232000] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.SBRG.EC0_._Q0F] (Node df8bf75c), AE_NOT_FOUND
Jul  3 02:16:06 ubuntu kernel: [  381.368000] ACPI Error (psargs-0355): [\_SB_.PCI0.P0P2.VGA_.LCDD] Namespace lookup failure, AE_NOT_FOUND
Jul  3 02:16:06 ubuntu kernel: [  381.368000] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.SBRG.EC0_._Q0E] (Node df8bdc20), AE_NOT_FOUND
Jul  3 02:16:06 ubuntu kernel: [  381.404000] ACPI Error (psargs-0355): [\_SB_.PCI0.P0P2.VGA_.LCDD] Namespace lookup failure, AE_NOT_FOUND
Jul  3 02:16:06 ubuntu kernel: [  381.404000] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.SBRG.EC0_._Q0F] (Node df8bf75c), AE_NOT_FOUND
Jul  3 02:16:06 ubuntu kernel: [  381.576000] ACPI Error (psargs-0355): [\_SB_.PCI0.P0P2.VGA_.LCDD] Namespace lookup failure, AE_NOT_FOUND
Jul  3 02:16:06 ubuntu kernel: [  381.576000] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.SBRG.EC0_._Q0E] (Node df8bdc20), AE_NOT_FOUND
Jul  3 02:16:06 ubuntu kernel: [  381.696000] ACPI Error (psargs-0355): [\_SB_.PCI0.P0P2.VGA_.LCDD] Namespace lookup failure, AE_NOT_FOUND
Jul  3 02:16:06 ubuntu kernel: [  381.696000] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.SBRG.EC0_._Q0F] (Node df8bf75c), AE_NOT_FOUND
Jul  3 02:16:06 ubuntu kernel: [  381.792000] ACPI Error (psargs-0355): [\_SB_.PCI0.P0P2.VGA_.LCDD] Namespace lookup failure, AE_NOT_FOUND
Jul  3 02:16:06 ubuntu kernel: [  381.792000] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.SBRG.EC0_._Q0E] (Node df8bdc20), AE_NOT_FOUND
Jul  3 02:22:48 ubuntu kernel: [  784.032000] ACPI Error (psargs-0355): [\_SB_.PCI0.P0P2.VGA_.LCDD] Namespace lookup failure, AE_NOT_FOUND
Jul  3 02:22:48 ubuntu kernel: [  784.032000] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.SBRG.EC0_._Q0E] (Node df8bdc20), AE_NOT_FOUND
Jul  3 02:22:48 ubuntu kernel: [  784.192000] ACPI Error (psargs-0355): [\_SB_.PCI0.P0P2.VGA_.LCDD] Namespace lookup failure, AE_NOT_FOUND
Jul  3 02:22:48 ubuntu kernel: [  784.192000] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.SBRG.EC0_._Q0E] (Node df8bdc20), AE_NOT_FOUND
Jul  3 02:22:48 ubuntu kernel: [  784.340000] ACPI Error (psargs-0355): [\_SB_.PCI0.P0P2.VGA_.LCDD] Namespace lookup failure, AE_NOT_FOUND
Jul  3 02:22:48 ubuntu kernel: [  784.340000] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.SBRG.EC0_._Q0E] (Node df8bdc20), AE_NOT_FOUND
Jul  3 02:22:49 ubuntu kernel: [  784.492000] ACPI Error (psargs-0355): [\_SB_.PCI0.P0P2.VGA_.LCDD] Namespace lookup failure, AE_NOT_FOUND
Jul  3 02:22:49 ubuntu kernel: [  784.492000] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.SBRG.EC0_._Q0E] (Node df8bdc20), AE_NOT_FOUND
Jul  3 02:22:49 ubuntu kernel: [  784.652000] ACPI Error (psargs-0355): [\_SB_.PCI0.P0P2.VGA_.LCDD] Namespace lookup failure, AE_NOT_FOUND
Jul  3 02:22:49 ubuntu kernel: [  784.652000] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.SBRG.EC0_._Q0E] (Node df8bdc20), AE_NOT_FOUND
Jul  3 02:22:49 ubuntu kernel: [  784.824000] ACPI Error (psargs-0355): [\_SB_.PCI0.P0P2.VGA_.LCDD] Namespace lookup failure, AE_NOT_FOUND
Jul  3 02:22:49 ubuntu kernel: [  784.824000] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.SBRG.EC0_._Q0E] (Node df8bdc20), AE_NOT_FOUND
Jul  3 02:22:50 ubuntu kernel: [  785.656000] ACPI Error (psargs-0355): [\_SB_.PCI0.P0P2.VGA_.LCDD] Namespace lookup failure, AE_NOT_FOUND
Jul  3 02:22:50 ubuntu kernel: [  785.656000] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.SBRG.EC0_._Q0F] (Node df8bf75c), AE_NOT_FOUND
Jul  3 02:22:50 ubuntu kernel: [  785.816000] ACPI Error (psargs-0355): [\_SB_.PCI0.P0P2.VGA_.LCDD] Namespace lookup failure, AE_NOT_FOUND
Jul  3 02:22:50 ubuntu kernel: [  785.816000] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.SBRG.EC0_._Q0F] (Node df8bf75c), AE_NOT_FOUND
Jul  3 02:22:50 ubuntu kernel: [  785.972000] ACPI Error (psargs-0355): [\_SB_.PCI0.P0P2.VGA_.LCDD] Namespace lookup failure, AE_NOT_FOUND
Jul  3 02:22:50 ubuntu kernel: [  785.972000] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.SBRG.EC0_._Q0F] (Node df8bf75c), AE_NOT_FOUND
Jul  3 02:22:50 ubuntu kernel: [  786.136000] ACPI Error (psargs-0355): [\_SB_.PCI0.P0P2.VGA_.LCDD] Namespace lookup failure, AE_NOT_FOUND
Jul  3 02:22:50 ubuntu kernel: [  786.136000] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.SBRG.EC0_._Q0F] (Node df8bf75c), AE_NOT_FOUND
Jul  3 02:22:50 ubuntu kernel: [  786.292000] ACPI Error (psargs-0355): [\_SB_.PCI0.P0P2.VGA_.LCDD] Namespace lookup failure, AE_NOT_FOUND
Jul  3 02:22:50 ubuntu kernel: [  786.292000] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.SBRG.EC0_._Q0F] (Node df8bf75c), AE_NOT_FOUND
Jul  3 02:22:51 ubuntu kernel: [  786.448000] ACPI Error (psargs-0355): [\_SB_.PCI0.P0P2.VGA_.LCDD] Namespace lookup failure, AE_NOT_FOUND
Jul  3 02:22:51 ubuntu kernel: [  786.448000] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.SBRG.EC0_._Q0F] (Node df8bf75c), AE_NOT_FOUND
Jul  3 02:22:51 ubuntu kernel: [  786.604000] ACPI Error (psargs-0355): [\_SB_.PCI0.P0P2.VGA_.LCDD] Namespace lookup failure, AE_NOT_FOUND
Jul  3 02:22:51 ubuntu kernel: [  786.604000] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.SBRG.EC0_._Q0F] (Node df8bf75c), AE_NOT_FOUND
Jul  3 02:22:51 ubuntu kernel: [  786.708000] ACPI Error (psargs-0355): [\_SB_.PCI0.P0P2.VGA_.LCDD] Namespace lookup failure, AE_NOT_FOUND
Jul  3 02:22:51 ubuntu kernel: [  786.708000] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.SBRG.EC0_._Q0E] (Node df8bdc20), AE_NOT_FOUND
Jul  3 02:22:51 ubuntu kernel: [  786.828000] ACPI Error (psargs-0355): [\_SB_.PCI0.P0P2.VGA_.LCDD] Namespace lookup failure, AE_NOT_FOUND
Jul  3 02:22:51 ubuntu kernel: [  786.828000] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.SBRG.EC0_._Q0F] (Node df8bf75c), AE_NOT_FOUND
Jul  3 02:22:51 ubuntu kernel: [  786.908000] ACPI Error (psargs-0355): [\_SB_.PCI0.P0P2.VGA_.LCDD] Namespace lookup failure, AE_NOT_FOUND
Jul  3 02:22:51 ubuntu kernel: [  786.908000] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.SBRG.EC0_._Q0E] (Node df8bdc20), AE_NOT_FOUND
Jul  3 02:22:51 ubuntu kernel: [  787.020000] ACPI Error (psargs-0355): [\_SB_.PCI0.P0P2.VGA_.LCDD] Namespace lookup failure, AE_NOT_FOUND
Jul  3 02:22:51 ubuntu kernel: [  787.020000] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.SBRG.EC0_._Q0F] (Node df8bf75c), AE_NOT_FOUND
Jul  3 02:22:51 ubuntu kernel: [  787.096000] ACPI Error (psargs-0355): [\_SB_.PCI0.P0P2.VGA_.LCDD] Namespace lookup failure, AE_NOT_FOUND
Jul  3 02:22:51 ubuntu kernel: [  787.096000] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.SBRG.EC0_._Q0E] (Node df8bdc20), AE_NOT_FOUND
Jul  3 02:22:51 ubuntu kernel: [  787.196000] ACPI Error (psargs-0355): [\_SB_.PCI0.P0P2.VGA_.LCDD] Namespace lookup failure, AE_NOT_FOUND
Jul  3 02:22:51 ubuntu kernel: [  787.196000] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.SBRG.EC0_._Q0F] (Node df8bf75c), AE_NOT_FOUND
Jul  3 02:22:51 ubuntu kernel: [  787.256000] ACPI Error (psargs-0355): [\_SB_.PCI0.P0P2.VGA_.LCDD] Namespace lookup failure, AE_NOT_FOUND
Jul  3 02:22:51 ubuntu kernel: [  787.256000] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.SBRG.EC0_._Q0E] (Node df8bdc20), AE_NOT_FOUND
Jul  3 02:22:52 ubuntu kernel: [  787.400000] ACPI Error (psargs-0355): [\_SB_.PCI0.P0P2.VGA_.LCDD] Namespace lookup failure, AE_NOT_FOUND
Jul  3 02:22:52 ubuntu kernel: [  787.400000] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.SBRG.EC0_._Q0E] (Node df8bdc20), AE_NOT_FOUND
Jul  3 02:22:52 ubuntu kernel: [  787.552000] ACPI Error (psargs-0355): [\_SB_.PCI0.P0P2.VGA_.LCDD] Namespace lookup failure, AE_NOT_FOUND
Jul  3 02:22:52 ubuntu kernel: [  787.552000] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.SBRG.EC0_._Q0E] (Node df8bdc20), AE_NOT_FOUND
Jul  3 02:22:52 ubuntu kernel: [  787.708000] ACPI Error (psargs-0355): [\_SB_.PCI0.P0P2.VGA_.LCDD] Namespace lookup failure, AE_NOT_FOUND
Jul  3 02:22:52 ubuntu kernel: [  787.708000] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.SBRG.EC0_._Q0E] (Node df8bdc20), AE_NOT_FOUND
Jul  3 02:22:52 ubuntu kernel: [  787.984000] ACPI Error (psargs-0355): [\_SB_.PCI0.P0P2.VGA_.LCDD] Namespace lookup failure, AE_NOT_FOUND
Jul  3 02:22:52 ubuntu kernel: [  787.984000] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.SBRG.EC0_._Q0E] (Node df8bdc20), AE_NOT_FOUND
Jul  3 02:22:52 ubuntu kernel: [  788.128000] ACPI Error (psargs-0355): [\_SB_.PCI0.P0P2.VGA_.LCDD] Namespace lookup failure, AE_NOT_FOUND
Jul  3 02:22:52 ubuntu kernel: [  788.128000] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.SBRG.EC0_._Q0E] (Node df8bdc20), AE_NOT_FOUND
Jul  3 02:22:52 ubuntu kernel: [  788.268000] ACPI Error (psargs-0355): [\_SB_.PCI0.P0P2.VGA_.LCDD] Namespace lookup failure, AE_NOT_FOUND
Jul  3 02:22:52 ubuntu kernel: [  788.268000] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.SBRG.EC0_._Q0E] (Node df8bdc20), AE_NOT_FOUND
Jul  3 02:22:52 ubuntu kernel: [  788.336000] ACPI Error (psargs-0355): [\_SB_.PCI0.P0P2.VGA_.LCDD] Namespace lookup failure, AE_NOT_FOUND
Jul  3 02:22:52 ubuntu kernel: [  788.336000] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.SBRG.EC0_._Q0F] (Node df8bf75c), AE_NOT_FOUND
Jul  3 02:29:20 ubuntu kernel: [ 1175.996000] hdb: status timeout: status=0xd0 { Busy }
Jul  3 02:29:20 ubuntu kernel: [ 1175.996000] ide: failed opcode was: unknown
Jul  3 02:29:21 ubuntu kernel: [ 1177.000000] Modules linked in: arc4 ecb blkcipher ieee80211_crypt_wep ipv6 binfmt_misc rfcomm l2cap ppdev i915 drm acpi_cpufreq cpufreq_userspace cpufreq_stats cpufreq_powersave cpufreq_ondemand freq_table cpufreq_conservative sony_acpi pcc_acpi dev_acpi tc1100_wmi video sbs i2c_ec i2c_core dock container button battery ac asus_acpi backlight af_packet sbp2 parport_pc lp parport joydev snd_hda_intel snd_hda_codec snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device ipw3945 ieee80211 snd hci_usb bluetooth ieee80211_crypt soundcore pcspkr sdhci mmc_core psmouse snd_page_alloc iTCO_wdt iTCO_vendor_support shpchp pci_hotplug serio_raw intel_agp agpgart evdev tsdev usbhid hid ext3 jbd mbcache ide_cd cdrom ide_disk 8139too ata_generic libata scsi_mod generic 8139cp mii ohci1394 ieee1394 ehci_hcd uhci_hcd usbcore thermal processor fan dm_mod fbcon tileblit font bitblit softcursor vesafb capability comm
Jul  3 02:29:21 ubuntu kernel: ncap piix
```

I have all the latest updates, including the latest Drivers (2.0.5).

Any ideas?

---

### Post by thomasaaron on 2007-07-03
Hi,

I'm not exactly sure what's going on (yet), but I Googled some of those error messages, and they don't really seem to be related to your wireless.

Most references from the on  the net deal with ACPI issues, VGA issues, Compiz and Beryl.
It's possible that loosing your wireless is either a separate problem or a side-effect of something else.

Can you give a little more info on your configuration / software, etc...  (Kubuntu, Compiz, Dual Monitors, networking, router, etc...)
Did the problem begin after creating/downloading a particular configuration/package?
Does the problem occur after a fresh restart, or after suspend/hibernate?


Best,
Tom

---

