---
title: "Mysterious behaviour | interface get shutdown"
date: 2011-04-12
forum: Server Platforms
---

### Post by lazerz on 2011-04-12
[[IMG]http://www.gravatar.com/avatar/d84a5d65e4150a67cfb486edac6a5de2.png?s=48&r=pg&d=http%3A%2F%2Fa.fsdn.com%2Fsf%2Fimages%2Fdevelop%2Fsf-profile-blank.gif[/IMG]]("http://sourceforge.net/users/nobody")                   2011-04-11 11:57:03 UTC



 I don't know what happening with my centralized log-server running  octopussy. Currently it is working in a vmware setup with approx 980 Mb  ram and is set in bridge mode. Currently is it set to receive logs from  logs devices which are 4 in number one of which includes the core  isg-1000 device. This setup is still in its test form....now what  happens after some time (sometimes it taken days and sometimes just  hours) when the connection (https) is suddenly lost to the apache and i  can no longer access the interface.  What happens more strangely my Ethernet interface gets shutdown on  ubuntu. I have to restart the services by issuing /etc/init.d/networking  restart.

Even at times it itself start receiving network packets on its own; without even restarting; i don't what the hell is wrong with the server. I cannot understand its erratic behavior. I need a sound and reliable Ethernet connectivity at all times because coz of loss of connectivity in my case would mean loss of logging functionality. I dnt want any time-gap in logging ...as im currently logging some highly critical devices on this server.

Can someone help me troubleshoot this behavior. ?

Im running ubuntu 10.04 server edition.

---

### Post by rubylaser on 2011-04-12
Some log files might help people with understanding what's going on :)  Otherwise we'd be guessing at your problem.

---

### Post by lazerz on 2011-04-12
> **rubylaser said:**
> Some log files might help people with understanding what's going on :)  Otherwise we'd be guessing at your problem.

Ok im not having access to my server right now tomorrow i will; but in my honest opinion it has nothing to do with the log application which is ocotopussy cause i check its status and it working fine. All its service running the only reason i get the disconnected from apache coz the underlying Ethernet connection is down..

---

### Post by rubylaser on 2011-04-12
I didn't say it was the logging application's fault.  I asked for the logfiles from the host, to understand why the NIC is dropping :)

---

### Post by lazerz on 2011-04-12
> **rubylaser said:**
> I didn't say it was the logging application's fault.  I asked for the logfiles from the host, to understand why the NIC is dropping :)

Ohh sorry in that case which one you want i can get you anything from /var/log folder right or u need any specific logs?

---

### Post by rubylaser on 2011-04-12
syslog, kern.log, and messages would be a good start.

---

### Post by lazerz on 2011-04-12
> **rubylaser said:**
> syslog, kern.log, and messages would be a good start.

ok buddy i would get you that ASAP. thanks

---

### Post by lazerz on 2011-04-13
> **rubylaser said:**
> syslog, kern.log, and messages would be a good start.


I'm attaching logs from the following sources (e.g dmseq,kern.log.1,syslog) 


**dmseq**

[    1.293177] Write protecting the kernel read-only data: 1884k
[    1.330478] udev: starting version 151
[    1.676149] Fusion MPT base driver 3.04.12
[    1.676152] Copyright (c) 1999-2008 LSI Corporation
[    1.677999] Fusion MPT SPI Host driver 3.04.12
[    1.678058] mptspi 0000:00:10.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.682207] pcnet32.c:v1.35 21.Apr.2008 [EMAIL="tsbogend@alpha.franken.de"]tsbogend@alpha.franken.de[/EMAIL]
[    1.682514]   alloc irq_desc for 19 on node -1
[    1.682524]   alloc kstat_irqs on node -1
[    1.682558] pcnet32 0000:02:01.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.685192] pcnet32: PCnet/PCI II 79C970A at 0x2000, 00:0c:29:73:63:21 assigned IRQ 19.
[    1.685643] eth0: registered as PCnet/PCI II 79C970A
[    1.685740] pcnet32: 1 cards_found.
[    1.693122] mptbase: ioc0: Initiating bringup
[    1.765324] ioc0: LSI53C1030 B0: Capabilities={Initiator}
[    1.941165] scsi2 : ioc0: LSI53C1030 B0, FwRev=01032920h, Ports=1, MaxQ=128, IRQ=17
[    2.018076] Floppy drive(s): fd0 is 1.44M
[    2.032969] FDC 0 is a post-1991 82077
[    2.053541] scsi 2:0:0:0: Direct-Access     VMware,  VMware Virtual S 1.0  PQ: 0 ANSI: 2
[    2.053582] scsi target2:0:0: Beginning Domain Validation
[    2.054820] scsi target2:0:0: Domain Validation skipping write tests
[    2.054825] scsi target2:0:0: Ending Domain Validation
[    2.054860] scsi target2:0:0: FAST-40 WIDE SCSI 80.0 MB/s ST (25 ns, offset 127)
[    2.056387] sd 2:0:0:0: [sda] 31457280 512-byte logical blocks: (16.1 GB/15.0 GiB)
[    2.056425] sd 2:0:0:0: [sda] Write Protect is off
[    2.056429] sd 2:0:0:0: [sda] Mode Sense: 5d 00 00 00
[    2.056491] sd 2:0:0:0: [sda] Cache data unavailable
[    2.056494] sd 2:0:0:0: [sda] Assuming drive cache: write through
[    2.056719] sd 2:0:0:0: [sda] Cache data unavailable
[    2.056722] sd 2:0:0:0: [sda] Assuming drive cache: write through
[    2.056725]  sda:
[    2.056970] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    2.064171]  sda1 sda2 < sda5 >
[    2.064639] sd 2:0:0:0: [sda] Cache data unavailable
[    2.064643] sd 2:0:0:0: [sda] Assuming drive cache: write through
[    2.064646] sd 2:0:0:0: [sda] Attached SCSI disk
[    2.107148] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
[    2.107154] EXT4-fs (sda1): write access will be enabled during recovery
[    2.528283] EXT4-fs (sda1): recovery complete
[    2.528647] EXT4-fs (sda1): mounted filesystem with ordered data mode
[    3.403012] udev: starting version 151
[    3.480947] vga16fb: initializing
[    3.480955] vga16fb: mapped to 0xc00a0000
[    3.481083] fb0: VGA16 VGA frame buffer device
[    3.482014] Linux agpgart interface v0.103
[    3.484450] agpgart-intel 0000:00:00.0: Intel 440BX Chipset
[    3.511058] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0x0
[    3.511163] ACPI: resource piix4_smbus [0x1040-0x1047] conflicts with ACPI region SMB_ [0x1040-0x104b]
[    3.511166] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    3.511861] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    3.524999] Adding 704504k swap on /dev/sda5.  Priority:-1 extents:1 across:704504k 
[    3.632497] lp: driver loaded but no devices found
[    3.678448] parport_pc 00:08: reported by Plug and Play ACPI
[    3.678790] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[    3.717943] psmouse serio1: ID: 10 00 64
[    3.719996] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input3
[    3.765525]   alloc irq_desc for 16 on node -1
[    3.765529]   alloc kstat_irqs on node -1
[    3.765547] ENS1371 0000:02:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.772185] lp0: using parport0 (interrupt-driven).
[    3.775222] ppdev: user-space parallel port driver
[    3.924999] Console: switching to colour frame buffer device 80x30
[    4.090648] type=1505 audit(1301699346.296:2):  operation="profile_load" pid=557 name="/sbin/dhclient3"
[    4.090683] type=1505 audit(1301699346.296:3):  operation="profile_load" pid=557 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[    4.090720] type=1505 audit(1301699346.296:4):  operation="profile_replace" pid=561 name="/sbin/dhclient3"
[    4.090763] type=1505 audit(1301699346.296:5):  operation="profile_replace" pid=561 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[    4.090831] type=1505 audit(1301699346.296:6):  operation="profile_load" pid=557 name="/usr/lib/connman/scripts/dhclient-script"
[    4.090868] type=1505 audit(1301699346.296:7):  operation="profile_replace" pid=561 name="/usr/lib/connman/scripts/dhclient-script"
[    4.130947] eth0: link up
[    4.471817] type=1505 audit(1301699346.676:8):  operation="profile_replace" pid=637 name="/sbin/dhclient3"
[    4.471965] type=1505 audit(1301699346.676:9):  operation="profile_replace" pid=637 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[    4.472313] type=1505 audit(1301699346.680:10):  operation="profile_replace" pid=637 name="/usr/lib/connman/scripts/dhclient-script"

[B]
kern.log.1[/B]

Mar 29 19:29:03 octopussy kernel: [    3.397156] vga16fb: mapped to 0xc00a0000
Mar 29 19:29:03 octopussy kernel: [    3.397298] fb0: VGA16 VGA frame buffer device
Mar 29 19:29:03 octopussy kernel: [    3.426283] lp: driver loaded but no devices found
Mar 29 19:29:03 octopussy kernel: [    3.574804] parport_pc 00:08: reported by Plug and Play ACPI
Mar 29 19:29:03 octopussy kernel: [    3.575033] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
Mar 29 19:29:03 octopussy kernel: [    3.603516] psmouse serio1: ID: 10 00 64
Mar 29 19:29:03 octopussy kernel: [    3.605809] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input3
Mar 29 19:29:03 octopussy kernel: [    3.660147] type=1505 audit(1301408942.867:2):  operation="profile_load" pid=509 name="/sbin/dhclient3"
Mar 29 19:29:03 octopussy kernel: [    3.660265] type=1505 audit(1301408942.867:3):  operation="profile_load" pid=509 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Mar 29 19:29:03 octopussy kernel: [    3.660384] type=1505 audit(1301408942.867:4):  operation="profile_load" pid=509 name="/usr/lib/connman/scripts/dhclient-script"
Mar 29 19:29:03 octopussy kernel: [    3.677603] lp0: using parport0 (interrupt-driven).
Mar 29 19:29:03 octopussy kernel: [    3.682702] ppdev: user-space parallel port driver
Mar 29 19:29:03 octopussy kernel: [    3.683997]   alloc irq_desc for 16 on node -1
Mar 29 19:29:03 octopussy kernel: [    3.683997]   alloc kstat_irqs on node -1
Mar 29 19:29:03 octopussy kernel: [    3.683997] ENS1371 0000:02:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Mar 29 19:29:03 octopussy kernel: [    3.741862] eth0: link down
Mar 29 19:29:03 octopussy kernel: [    3.824577] Console: switching to colour frame buffer device 80x30
Mar 29 19:29:03 octopussy kernel: [    4.154003] ADDRCONF(NETDEV_UP): eth0: link is not ready
Mar 29 19:29:03 octopussy kernel: [    4.448100] type=1505 audit(1301408943.655:5):  operation="profile_replace" pid=630 name="/sbin/dhclient3"
Mar 29 19:29:03 octopussy kernel: [    4.448609] type=1505 audit(1301408943.655:6):  operation="profile_replace" pid=630 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Mar 29 19:29:03 octopussy kernel: [    4.448889] type=1505 audit(1301408943.655:7):  operation="profile_replace" pid=630 name="/usr/lib/connman/scripts/dhclient-script"
Mar 29 19:29:03 octopussy kernel: [    4.449797] type=1505 audit(1301408943.659:8):  operation="profile_load" pid=631 name="/usr/sbin/tcpdump"
Mar 29 19:29:07 octopussy kernel: [    7.804127] eth0: link up
Mar 29 19:29:07 octopussy kernel: [    7.804370] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Mar 29 19:29:17 octopussy kernel: [   18.704126] eth0: no IPv6 routers present
Mar 29 19:30:12 octopussy kernel: [   72.999097] eth0: link down
Mar 29 19:30:12 octopussy kernel: [   73.405409] ADDRCONF(NETDEV_UP): eth0: link is not ready
Mar 29 19:30:18 octopussy kernel: [   78.816239] eth0: link up
Mar 29 19:30:18 octopussy kernel: [   78.816422] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Mar 29 19:30:29 octopussy kernel: [   90.120097] eth0: no IPv6 routers present
Mar 29 19:45:41 octopussy kernel: [ 1002.295009] SGI XFS with ACLs, security attributes, realtime, large block/inode numbers, no debug enabled
Mar 29 19:45:41 octopussy kernel: [ 1002.296239] SGI XFS Quota Management subsystem
Mar 29 19:45:41 octopussy kernel: [ 1002.304957] JFS: nTxBlock = 7194, nTxLock = 57554
Mar 29 19:45:41 octopussy kernel: [ 1002.361284] NTFS driver 2.1.29 [Flags: R/O MODULE].
Mar 29 19:45:41 octopussy kernel: [ 1002.390849] QNX4 filesystem 0.2.3 registered.
Mar 29 19:45:41 octopussy kernel: [ 1002.474111] Btrfs loaded
Mar 29 19:48:42 octopussy kernel: [ 1183.409657] type=1505 audit(1301410122.619:9):  operation="profile_load" pid=19251 name="/usr/sbin/mysqld"
Mar 29 19:48:42 octopussy kernel: [ 1183.515616] type=1505 audit(1301410122.724:10):  operation="profile_replace" pid=19256 name="/usr/sbin/mysqld"
Mar 29 19:48:50 octopussy kernel: [ 1190.855882] type=1505 audit(1301410130.063:11):  operation="profile_replace" pid=19590 name="/usr/sbin/mysqld"

**syslog**

Mar 29 19:48:44 octopussy /etc/mysql/debian-start[19282]: status   : OK
Mar 29 19:48:44 octopussy /etc/mysql/debian-start[19282]: mysql.help_category                                OK
Mar 29 19:48:44 octopussy /etc/mysql/debian-start[19282]: mysql.help_keyword                                 OK
Mar 29 19:48:44 octopussy /etc/mysql/debian-start[19282]: mysql.help_relation                                OK
Mar 29 19:48:44 octopussy /etc/mysql/debian-start[19282]: mysql.help_topic                                   OK
Mar 29 19:48:44 octopussy /etc/mysql/debian-start[19282]: mysql.host                                         OK
Mar 29 19:48:44 octopussy /etc/mysql/debian-start[19282]: mysql.ndb_binlog_index                             OK
Mar 29 19:48:44 octopussy /etc/mysql/debian-start[19282]: mysql.plugin                                       OK
Mar 29 19:48:44 octopussy /etc/mysql/debian-start[19282]: mysql.proc                                         OK
Mar 29 19:48:44 octopussy /etc/mysql/debian-start[19282]: mysql.procs_priv                                   OK
Mar 29 19:48:44 octopussy /etc/mysql/debian-start[19282]: mysql.servers                                      OK
Mar 29 19:48:44 octopussy /etc/mysql/debian-start[19282]: mysql.slow_log
Mar 29 19:48:44 octopussy /etc/mysql/debian-start[19282]: Error    : You can't use locks with log tables.
Mar 29 19:48:44 octopussy /etc/mysql/debian-start[19282]: status   : OK
Mar 29 19:48:44 octopussy /etc/mysql/debian-start[19282]: mysql.tables_priv                                  OK
Mar 29 19:48:44 octopussy /etc/mysql/debian-start[19282]: mysql.time_zone                                    OK
Mar 29 19:48:44 octopussy /etc/mysql/debian-start[19282]: mysql.time_zone_leap_second                        OK
Mar 29 19:48:44 octopussy /etc/mysql/debian-start[19282]: mysql.time_zone_name                               OK
Mar 29 19:48:44 octopussy /etc/mysql/debian-start[19282]: mysql.time_zone_transition                         OK
Mar 29 19:48:44 octopussy /etc/mysql/debian-start[19282]: mysql.time_zone_transition_type                    OK
Mar 29 19:48:44 octopussy /etc/mysql/debian-start[19282]: mysql.user                                         OK
Mar 29 19:48:44 octopussy /etc/mysql/debian-start[19282]: Running 'mysql_fix_privilege_tables'...
Mar 29 19:48:44 octopussy /etc/mysql/debian-start[19282]: OK
Mar 29 19:48:44 octopussy /etc/mysql/debian-start[19321]: Checking for insecure root accounts.
Mar 29 19:48:44 octopussy /etc/mysql/debian-start[19330]: WARNING: mysql.user contains 3 root accounts without password!
Mar 29 19:48:44 octopussy /etc/mysql/debian-start[19331]: Triggering myisam-recover for all MyISAM tables
Mar 29 19:48:50 octopussy octo_dispatcher: Started !
Mar 29 19:48:50 octopussy octo_dispatcher: Load Devices Configuration
Mar 29 19:48:50 octopussy kernel: [ 1190.855882] type=1505 audit(1301410130.063:11):  operation="profile_replace" pid=19590 name="/usr/sbin/mysqld"
Mar 29 19:48:51 octopussy /etc/mysql/debian-start[19616]: Upgrading MySQL tables if necessary.
Mar 29 19:48:51 octopussy /etc/mysql/debian-start[19619]: /usr/bin/mysql_upgrade: the '--basedir' option is always ignored
Mar 29 19:48:51 octopussy /etc/mysql/debian-start[19619]: Looking for 'mysql' as: /usr/bin/mysql
Mar 29 19:48:51 octopussy /etc/mysql/debian-start[19619]: Looking for 'mysqlcheck' as: /usr/bin/mysqlcheck
Mar 29 19:48:51 octopussy /etc/mysql/debian-start[19619]: This installation of MySQL is already upgraded to 5.1.41, use --force if you still need to run mysql_upgrade
Mar 29 19:48:51 octopussy /etc/mysql/debian-start[19636]: Checking for insecure root accounts.
Mar 29 19:48:51 octopussy /etc/mysql/debian-start[19640]: WARNING: mysql.user contains 3 root accounts without password!
Mar 29 19:48:51 octopussy /etc/mysql/debian-start[19641]: Triggering myisam-recover for all MyISAM tables

---

### Post by disabledaccount on 2011-04-13
use: > cat /var/log/<logfile> | grep 'eth0:'
It would show only those lines that are related to the problem.

But from what You've already presented it seems to be hardware fault:
> Mar 29 **19:29:03** octopussy kernel: [    3.741862] **eth0: link down**
Mar 29 19:29:03 octopussy kernel: [    4.154003] ADDRCONF(NETDEV_UP): eth0: link is not ready
Mar 29 **19:29:07** octopussy kernel: [    7.804127] **eth0: link up**
Mar 29 19:29:07 octopussy kernel: [    7.804370] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready

Mar 29 **19:30:12** octopussy kernel: [   72.999097] **eth0: link down**
Mar 29 19:30:12 octopussy kernel: [   73.405409] ADDRCONF(NETDEV_UP): eth0: link is not ready
Mar 29 **19:30:18** octopussy kernel: [   78.816239] **eth0: link up**First thing to do is to check/replace the cable, then Your router/modem whatever You have

---

