---
title: "How to overcome checkarray problem"
date: 2009-05-29
forum: Server Platforms
---

### Post by R3d3agl3 on 2009-05-29
Hello everyone,

First of all, sorry for reposting this thread. 

I have a Ubuntu system that uses 3 discs at work. 2 of the discs use raid 1 and the 3rd one uses raid 5.
The mdadm cron task that executes "/usr/share/mdadm/checkarray --cron --all --quiet" at 1:06 AM of the first sunday of every month, crashes my system everytime. On the following monday morning, when I arrive at work I see the status LED on the machine, red.
From what I've seen, this is a common problem and I seriously doubt that there is something wrong with any of my discs, because they are new, and work perfectly the rest of the month :wink:
I've tried to comment out the execution of the checkarray task, but something unexpected happended. What happened was that everyday at 1:06 AM the system became unreponsive, and despite I could see the authentication screen, I was unable to login. Another thing, the status LED on this case was green. This happened on the 20rd of May so why did this happen? When I uncommented the line, to it's original state the system didn't staul, but I know it will happen again next month.
I have VMWare installed and running 2 VM's... Could that have anything to do with the problem?
Any help would be very much appreciated on this problem.

By the way these are the parameters that the check takes into account:


**-cron -> honour AUTOCHECK setting in /etc/default/mdadm.**

_/etc/default/mdadm_

[I]# mdadm Debian configuration
#
# You can run 'dpkg-reconfigure mdadm' to modify the values in this file, if
# you want. You can also change the values here and changes will be preserved.
# Do note that only the values are preserved; the rest of the file is
# rewritten.
#

# AUTOCHECK:
#   should mdadm run periodic redundancy checks over your arrays? See
#   /etc/cron.d/mdadm.
AUTOCHECK=true

# START_DAEMON:
#   should mdadm start the MD monitoring daemon during boot?
START_DAEMON=true

# DAEMON_OPTIONS:
#   additional options to pass to the daemon.
DAEMON_OPTIONS="--syslog"

# VERBOSE:
#   if this variable is set to true, mdadm will be a little more verbose e.g.
#   when creating the initramfs.
VERBOSE=false

# MAIL_TO:
#   this variable is now managed in /etc/mdadm/mdadm.conf (MAILADDR).
#   Please see mdadm.conf(5).[/I]


**-all -> check all assembled arrays (check /proc/mdstat)**

_/proc/mdstat:_

[I]Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md2 : active raid5 sda3[0] sdc3[2] sdb3[1]
      410267776 blocks level 5, 64k chunk, algorithm 2 [3/3] [UUU]

md3 : active raid1 sda2[0] sdc2[2](S) sdb2[1]
      7815552 blocks [2/2] [UU]

md0 : active raid1 sda1[0] sdc1[2](S) sdb1[1]
      31246272 blocks [2/2] [UU]

unused devices: <none>[/I]


**-quiet -> suppress informational messages.**


In light of this information, how do you recomend I solve this problem? I would bet on setting the AUTOCHECK variable to false, but some feedback on this would be very much appreciated :wink:

---

### Post by alastair on 2009-05-29
Seems reasonable. First, I would see : 

/etc/cron.d/mdadm

As instructed i.e. see what it says (comments etc.).

---

### Post by ian dobson on 2009-05-30
Hi,

An array check really stresses the I/O subsystem.

Maybe you could slow down the resync/scan by changing the min/max values in /proc/sys/dev/raid/

Regards
Ian Dobson

---

### Post by R3d3agl3 on 2009-06-02
Thanks for the reply,

> **alastair said:**
> Seems reasonable. First, I would see : 

/etc/cron.d/mdadm

As instructed i.e. see what it says (comments etc.).

I've already checked that file, but nothing on it mentions any eventual problems. Here is it's content:

[I]#
# cron.d/mdadm -- schedules periodic redundancy checks of MD devices
#
# Copyright © martin f. krafft <madduck@madduck.net>
# distributed under the terms of the Artistic Licence 2.0
#
# $Id$
#

# By default, run at 01:06 on every Sunday, but do nothing unless the day of
# the month is less than or equal to 7. Thus, only run on the first Sunday of
# each month. crontab(5) sucks, unfortunately, in this regard; therefore this
# hack (see #380425).
6 1 * * 0 root [ -x /usr/share/mdadm/checkarray ] && [ $(date +\%d) -le 7 ] && /usr/share/mdadm/checkarray --cron --all --quiet[/I]

> **ian dobson said:**
> Hi,

An array check really stresses the I/O subsystem.

Maybe you could slow down the resync/scan by changing the min/max values in /proc/sys/dev/raid/

Regards
Ian Dobson

The current values are:

[I]speed_limit_max = 200000
speed_limit_min = 1000[/I]

Wouldn't that change slow down the overall performance of the raid system, making the disks read/write tasks slower? As I've said, I have 2 VM's running and they are already slow by nature.


Anyway, I've set the AUTOCHECK parameter to false and the result was the same as when I commented out the following line:

*6 1 * * 0 root [ -x /usr/share/mdadm/checkarray ] && [ $(date +\%d) -le 7 ] && /usr/share/mdadm/checkarray --cron --all --quiet*

What happened was that the system just freezed. I don't understand why, because the previous line should run, at MOST, only on Sundays, right? :confused:

---

### Post by R3d3agl3 on 2009-06-04
Hy guys!

I think I figured out the problem...
The thing was that my md0 - RAID1 array is mounted on the root (/) and md2 - RAID5 array is mounted on the folder that contains my 2 virtual machines (/vmachine).
You've problably guessed it at this point :) I stopped both the VM's and then ran:

 */usr/share/mdadm/checkarray --cron --all --quiet* 

... and the check ran smoothelly. 

Thanks for the support anyway

---

### Post by R3d3agl3 on 2009-06-15
Sorry, but I guess the crash wasn't caused by the VM's...
On the 7th of June (first sunday of June), I suspended the VM's around 1AM, convinced that this would solve the problem. Unfortunatelly, that didn't work...
This is a stupid problem, because I've already scheduled the mdadm cron task to run at 1.06 AM of the 14th of June (sunday), left the VM's on, and the array check gave no problems.
My only guess, is that there is some other process running on the first sunday of every month that causes this... My daemon logs for the 7th and 14th of June:

[I]Jun  7 00:08:50 GEOSERVER00 dhcpd: DHCPDISCOVER from 00:00:00:00:00:00 via eth0: network eth0: no free leases
Jun  7 00:09:14 GEOSERVER00 last message repeated 3 times
Jun  7 00:17:33 GEOSERVER00 init: ebox.event-daemon main process (1670) killed by TERM signal
Jun  7 00:24:22 GEOSERVER00 dhcpd: DHCPDISCOVER from 00:00:00:00:00:00 via eth0: network eth0: no free leases
Jun  7 00:24:46 GEOSERVER00 last message repeated 3 times
Jun  7 00:29:33 GEOSERVER00 dhcpd: DHCPINFORM from xxx.xxx.xxx.xxx via eth0: not authoritative for subnet xxx.xxx.xxx.xxx
Jun  7 00:36:10 GEOSERVER00 dhcpd: DHCPINFORM from [/I]*xxx.xxx.xxx.xxx** via eth0: not authoritative for subnet **xxx.xxx.xxx.xxx*
[I]Jun  7 00:39:54 GEOSERVER00 dhcpd: DHCPDISCOVER from 00:00:00:00:00:00 via eth0: network eth0: no free leases
Jun  7 00:40:18 GEOSERVER00 last message repeated 3 times
Jun  7 00:55:26 GEOSERVER00 dhcpd: DHCPDISCOVER from 00:00:00:00:00:00 via eth0: network eth0: no free leases
Jun  7 00:55:50 GEOSERVER00 last message repeated 3 times
Jun  7 01:02:01 GEOSERVER00 dhclient: DHCPREQUEST of <null address> on eth1 to [/I]*xxx.xxx.xxx.xxx*[I] port 67
Jun  7 01:02:01 GEOSERVER00 dhclient: DHCPACK of [/I]*xxx.xxx.xxx.xxx** from **xxx.xxx.xxx.xxx*
*Jun  7 01:02:02 GEOSERVER00 dhclient: bound to **xxx.xxx.xxx.xxx*[I] -- renewal in 8715 seconds.
Jun  7 01:06:01 GEOSERVER00 mdadm: RebuildStarted event detected on md device /dev/md0
Jun  7 01:08:01 GEOSERVER00 mdadm: Rebuild20 event detected on md device /dev/md0
Jun  7 01:09:01 GEOSERVER00 mdadm: Rebuild40 event detected on md device /dev/md0
Jun  7 01:10:58 GEOSERVER00 dhcpd: DHCPDISCOVER from 00:00:00:00:00:00 via eth0: network eth0: no free leases
Jun  7 01:11:01 GEOSERVER00 mdadm: Rebuild60 event detected on md device /dev/md0
Jun  7 01:11:06 GEOSERVER00 dhcpd: DHCPDISCOVER from 00:00:00:00:00:00 via eth0: network eth0: no free leases
Jun  7 01:11:22 GEOSERVER00 last message repeated 2 times[/I]
Jun  7 01:12:01 GEOSERVER00 mdadm: Rebuild80 event detected on md device [I]/dev/md0
Jun  7 12:24:09 ...


Jun 14 00:10:24 GEOSERVER00 last message repeated 3 times
Jun 14 00:17:03 GEOSERVER00 init: ebox.event-daemon main process (2303) killed by TERM signal
Jun 14 00:25:32 GEOSERVER00 dhcpd: DHCPDISCOVER from 00:00:00:00:00:00 via eth0: network eth0: no free leases
Jun 14 00:25:56 GEOSERVER00 last message repeated 3 times
Jun 14 00:41:04 GEOSERVER00 dhcpd: DHCPDISCOVER from 00:00:00:00:00:00 via eth0: network eth0: no free leases
Jun 14 00:41:27 GEOSERVER00 last message repeated 3 times
Jun 14 00:56:36 GEOSERVER00 dhcpd: DHCPDISCOVER from 00:00:00:00:00:00 via eth0: network eth0: no free leases
Jun 14 00:56:59 GEOSERVER00 last message repeated 3 times
Jun 14 00:59:40 GEOSERVER00 dhcpd: DHCPINFORM from xxx.xxx.xxx.xxx via eth0: not authoritative for subnet [/I]*xxx.xxx.xxx.xxx*
*Jun 14 01:02:15 GEOSERVER00 dhcpd: DHCPINFORM from **xxx.xxx.xxx.xxx** via eth0: not authoritative for subnet **xxx.xxx.xxx.xxx*
[I]Jun 14 01:06:01 GEOSERVER00 mdadm: RebuildStarted event detected on md device /dev/md0
Jun 14 01:08:01 GEOSERVER00 mdadm: Rebuild20 event detected on md device /dev/md0
Jun 14 01:08:33 GEOSERVER00 dhclient: DHCPREQUEST of <null address> on eth1 to [/I]*xxx.xxx.xxx.xxx*[I] port 67
Jun 14 01:08:33 GEOSERVER00 dhclient: DHCPACK of [/I]*xxx.xxx.xxx.xxx** from **xxx.xxx.xxx.xxx*
*Jun 14 01:08:33 GEOSERVER00 dhclient: bound to **xxx.xxx.xxx.xxx*[I] -- renewal in 7047 seconds.
Jun 14 01:10:01 GEOSERVER00 mdadm: Rebuild40 event detected on md device /dev/md0
Jun 14 01:11:01 GEOSERVER00 mdadm: Rebuild60 event detected on md device /dev/md0
Jun 14 01:12:07 GEOSERVER00 dhcpd: DHCPDISCOVER from 00:00:00:00:00:00 via eth0: network eth0: no free leases
Jun 14 01:12:31 GEOSERVER00 last message repeated 3 times
Jun 14 01:13:01 GEOSERVER00 mdadm: Rebuild80 event detected on md device /dev/md0
Jun 14 01:13:55 GEOSERVER00 mdadm: RebuildStarted event detected on md device /dev/md3
Jun 14 01:13:55 GEOSERVER00 mdadm: RebuildFinished event detected on md device /dev/md0, component device  mismatches found: 5760
Jun 14 01:14:55 GEOSERVER00 mdadm: Rebuild40 event detected on md device /dev/md3
Jun 14 01:15:38 GEOSERVER00 mdadm: RebuildStarted event detected on md device /dev/md2
Jun 14 01:15:38 GEOSERVER00 mdadm: RebuildFinished event detected on md device /dev/md3, component device  mismatches found: 19328
Jun 14 01:17:04 GEOSERVER00 init: ebox.event-daemon main process (2990) killed by TERM signal
Jun 14 01:25:38 GEOSERVER00 mdadm: Rebuild20 event detected on md device /dev/md2
Jun 14 01:26:49 GEOSERVER00 dhcpd: DHCPINFORM from [/I]*xxx.xxx.xxx.xxx** via eth0: not authoritative for subnet **xxx.xxx.xxx.xxx*
[I]Jun 14 01:27:39 GEOSERVER00 dhcpd: DHCPDISCOVER from 00:00:00:00:00:00 via eth0: network eth0: no free leases
Jun 14 01:28:03 GEOSERVER00 last message repeated 3 times
Jun 14 01:35:38 GEOSERVER00 mdadm: Rebuild40 event detected on md device /dev/md2
Jun 14 01:43:11 GEOSERVER00 dhcpd: DHCPDISCOVER from 00:00:00:00:00:00 via eth0: network eth0: no free leases
Jun 14 01:43:35 GEOSERVER00 last message repeated 3 times
Jun 14 01:45:38 GEOSERVER00 mdadm: Rebuild60 event detected on md device /dev/md2
Jun 14 01:57:38 GEOSERVER00 mdadm: Rebuild80 event detected on md device /dev/md2
Jun 14 01:58:43 GEOSERVER00 dhcpd: DHCPDISCOVER from 00:00:00:00:00:00 via eth0: network eth0: no free leases
Jun 14 01:59:07 GEOSERVER00 last message repeated 3 times
Jun 14 02:06:18 GEOSERVER00 dhcpd: DHCPINFORM from [/I]*xxx.xxx.xxx.xxx** via eth0: not authoritative for subnet **xxx.xxx.xxx.xxx*
[I]Jun 14 02:12:13 GEOSERVER00 mdadm: RebuildFinished event detected on md device /dev/md2
[/I]

By the way, my /proc/mdstat file is like this after the array check:

[I]Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md2 : active raid5 sda3[0] sdc3[2] sdb3[1]
      410267776 blocks level 5, 64k chunk, algorithm 2 [3/3] [UUU]

md3 : active raid1 sda2[0] sdc2[2](S) sdb2[1]
      7815552 blocks [2/2] [UU]

md0 : active raid1 sda1[0] sdc1[2](S) sdb1[1]
      31246272 blocks [2/2] [UU]

unused devices: <none>[/I]

As you can see there are no fails on any of the partitions.

Please help... I'm running out of ideas...

---

### Post by ian dobson on 2009-06-15
Hi,

I've a strange feeling that your hardware/disk subsystem just can't cope with a fullscale checkarray. On my array a checkarray hits the disk subsystem alot harder than any other process that I can run (50k I/O's a second for a checkarray against 5K I/O's a second recording several HD channels at the same time). See [http://mail.planet-ian.com/munin/planet-ian.com/alpha2.planet-ian.com-md_iostat_md1-month.png](http://mail.planet-ian.com/munin/planet-ian.com/alpha2.planet-ian.com-md_iostat_md1-month.png) see what I mean (The peak in KW23 is the check array)

Maybe you should try reducing the max value in /proc/sys/dev/raid/ just while the array is being scanned. Once the check it finished just set it back to full speed

What do you see in /proc/mdstat when the array is being checked?

Regards
Ian Dobson

---

### Post by enrico.simonetti on 2010-05-01
Hi there,

Any luck on this yet?

I run OpenVZ on hardy (2.6.24-27-openvz and 2.6.24-26-openvz) on 2  different servers.
They both keep crashing.

Is this related to bug [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/212684](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/212684)  ?

Thanks

---

### Post by wickedmonkey on 2013-02-04
Did you ever get to the bottom of this?

---

