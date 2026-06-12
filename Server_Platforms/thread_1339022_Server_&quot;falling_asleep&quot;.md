---
title: "Server &quot;falling asleep&quot;"
date: 2009-11-27
forum: Server Platforms
---

### Post by Znupi on 2009-11-27
I don't know how to better describe this issue I'm having. I have a slightly old PC (AMD K7 @ 1.7Ghz, 1GB RAM) running on Ubuntu Server 9.10 32-bit, although I've had this problem with 9.04, too.

What happens is that the server (seemingly) randomly stops responding to any network requests (ping, ssh, http, ...) from time to time. What I'll do is go upstairs (where it resides) and simply press "Enter". This wakes it up every time and it starts responding, like nothing has happened. Nothing is shown on screen. I've tried debugging this problem myself but I can't seem to be able to. Here are some log excerpts from after such a lock-up (I can't see anything out of place):

```
felix@kitty:~$ tail -n 40 /var/log/syslog
Nov 25 18:39:01 kitty CRON[3809]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Nov 25 19:00:01 kitty CRON[3820]: (andrei) CMD (cd /home/andrei/emmy.5.0.; php ./play.php)
Nov 25 19:09:01 kitty CRON[3827]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Nov 25 19:17:01 kitty CRON[3837]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 25 19:39:01 kitty CRON[3843]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Nov 25 20:09:01 kitty CRON[3856]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Nov 25 20:17:01 kitty CRON[3866]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 25 20:39:01 kitty CRON[3870]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Nov 25 21:00:02 kitty CRON[3881]: (andrei) CMD (cd /home/andrei/emmy.5.0.; php ./play.php)
Nov 25 21:09:01 kitty CRON[3886]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Nov 25 21:17:01 kitty CRON[3897]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 25 21:39:01 kitty CRON[3901]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Nov 25 22:09:02 kitty CRON[3912]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Nov 25 22:17:01 kitty CRON[3923]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 25 22:39:01 kitty CRON[3927]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Nov 25 23:00:01 kitty CRON[3939]: (andrei) CMD (cd /home/andrei/emmy.5.0.; php ./play.php)
Nov 25 23:09:01 kitty CRON[3943]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Nov 25 23:17:01 kitty CRON[3954]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 25 23:39:01 kitty CRON[3958]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Nov 26 00:09:01 kitty CRON[3970]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Nov 26 00:17:01 kitty CRON[3982]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 26 00:39:01 kitty CRON[3986]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Nov 26 01:00:01 kitty CRON[3997]: (andrei) CMD (cd /home/andrei/emmy.5.0.; php ./play.php)
Nov 26 01:09:01 kitty CRON[4002]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Nov 26 01:17:01 kitty CRON[4013]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 26 01:39:01 kitty CRON[4022]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Nov 26 02:09:01 kitty CRON[4167]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Nov 26 02:17:01 kitty CRON[4178]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 26 02:39:01 kitty CRON[4187]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Nov 26 03:00:01 kitty CRON[4198]: (andrei) CMD (cd /home/andrei/emmy.5.0.; php ./play.php)
Nov 26 03:09:01 kitty CRON[4206]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Nov 26 03:17:01 kitty CRON[4217]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 26 03:39:01 kitty CRON[4221]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Nov 26 04:09:01 kitty CRON[4236]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Nov 26 04:17:01 kitty CRON[4247]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 26 04:39:01 kitty CRON[4251]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Nov 26 05:00:01 kitty CRON[4262]: (andrei) CMD (cd /home/andrei/emmy.5.0.; php ./play.php)
Nov 26 05:09:01 kitty CRON[4272]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Nov 26 05:17:01 kitty CRON[4282]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 26 05:39:01 kitty CRON[4292]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
```
```
$ dmesg | tail -n 40
[    4.190917] Adding 1951888k swap on /dev/sda5.  Priority:-1 extents:1 across:1951888k 
[    4.664505] EXT4-fs (sda1): internal journal on sda1:8
[    4.894354] udev: starting version 147
[    5.809156] EXT4-fs (sda6): barriers enabled
[    5.825340] kjournald2 starting: pid 525, dev sda6:8, commit interval 5 seconds
[    5.913892] EXT4-fs (sda6): internal journal on sda6:8
[    5.913904] EXT4-fs (sda6): delayed allocation enabled
[    5.913910] EXT4-fs: file extents enabled
[    5.917559] EXT4-fs: mballoc enabled
[    5.917586] EXT4-fs (sda6): mounted filesystem with ordered data mode
[    5.945432] parport_pc 00:0a: reported by Plug and Play ACPI
[    5.945519] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[    6.060746] lp0: using parport0 (interrupt-driven).
[    6.181349] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    6.186030] ppdev: user-space parallel port driver
[    6.203062] Linux agpgart interface v0.103
[    6.253461] ip_tables: (C) 2000-2006 Netfilter Core Team
[    6.353117] irda_init()
[    6.353146] NET: Registered protocol family 23
[    6.459455] agpgart: Detected VIA KT266/KY266x/KT333 chipset
[    6.480710] agpgart-via 0000:00:00.0: AGP aperture is 256M @ 0xc0000000
[    6.765263] ACPI: PCI Interrupt Link [ALKC] BIOS reported IRQ 0, using IRQ 22
[    6.765271] ACPI: PCI Interrupt Link [ALKC] enabled at IRQ 22
[    6.765281]   alloc irq_desc for 22 on node -1
[    6.765284]   alloc kstat_irqs on node -1
[    6.765298] VIA 82xx Audio 0000:00:11.5: PCI INT C -> Link[ALKC] -> GSI 22 (level, low) -> IRQ 22
[    6.765476] VIA 82xx Audio 0000:00:11.5: setting latency timer to 64
[    7.240301] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[    7.935150] type=1505 audit(1258995213.569:7): operation="profile_replace" pid=652 name=/sbin/dhclient3
[    7.935615] type=1505 audit(1258995213.569:8): operation="profile_replace" pid=652 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    7.935884] type=1505 audit(1258995213.569:9): operation="profile_replace" pid=652 name=/usr/lib/connman/scripts/dhclient-script
[    7.940889] type=1505 audit(1258995213.577:10): operation="profile_replace" pid=653 name=/usr/sbin/mysqld
[    7.945167] type=1505 audit(1258995213.581:11): operation="profile_replace" pid=654 name=/usr/sbin/tcpdump
[    9.726837] type=1503 audit(1258995215.018:12): operation="open" pid=782 parent=781 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[    9.962051] type=1503 audit(1258995215.252:13): operation="open" pid=802 parent=801 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   10.231539] type=1503 audit(1258995215.520:14): operation="open" pid=917 parent=809 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   11.065951] type=1503 audit(1258995216.356:15): operation="open" pid=933 parent=932 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   11.129729] type=1503 audit(1258995216.420:16): operation="open" pid=944 parent=943 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   18.124029] eth0: no IPv6 routers present
[11014.761849] Clocksource tsc unstable (delta = 548359080390 ns)
```

I'm not excluding a hardware failure. This PC is rather old (~5 years) and I also changed its power source recently, the old one's fan had broken. Still, the problem is too peculiar to be sure whether it's soft or hard.

Let me know if I can post more logs. Maybe it could be some sort of driver problem?

---

### Post by lisati on 2009-11-27
I can't help with server-specific issues, but I'm wondering if you've eliminated switching into "hibernate"/"suspend" mode or similar as a possibility for what's happening. A couple of my machines have an option in BIOS related to this - my old Win98 machine's BIOS can be set to suspend the machine after a period of inactivity.

---

### Post by Znupi on 2009-11-27
I thought about that, too. But I haven't changed anything in the BIOS recently (read: 5 years) and this thing just started happening a couple months back. I just looked through all the BIOS settings and nothing popped out.

---

