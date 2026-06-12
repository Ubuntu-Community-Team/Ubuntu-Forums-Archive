---
title: "Issue or Reinstall"
date: 2019-02-14
forum: Server Platforms
---

### Post by ejkeebler2 on 2019-02-14
I ran an apt-get dist-upgrade on a machine I use as nas storage.  It mounts a zfs raid of 5 drives.  Since that upgrade my nas seemed to be shutting down every few hours. I've been just cycling the power because it was a headless system. Today I actually took time to see what's going on.  It's getting an acpi surge message and sitting at the post screen.  Its an older build but the coincidence to the update has me wondering.  It seems to be fine as long as its in use but when I leave for a few hours it will shutdown.

So I'm wondering if I should try and figure out if maybe a power package is conflicting, or just reinstall.

If I reinstall I have no idea how to ensure my zfs raid stays in tact it has been years since I set it up.  Is there any risk? It's 16.04 thought maybe just wiping and starting with 18 might resolve.  And if not I'll get a new psu.?

---

### Post by TheFu on 2019-02-14
I would check the log files for issues.  /var/log/*log
Then let the data guide an appropriate response.

---

### Post by ejkeebler2 on 2019-02-15
Yeah, its just difficult to get any kind of timing of when it went down.  I just know its down because I try to access it and cannot.  I restart and its all good.  When I look at syslog, theres not much info before the boot messages.  The closest I've come is seeing this in the kernel log:


Feb 14 12:48:27 nas kernel: [    5.372304] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver, but when looking t the syslog, it's basically good, good, good, and its booting up.


Feb 14 01:39:01 nas CRON[27283]: (root) CMD (  [ -x /usr/lib/php/sessionclean ] && if [ ! -d /run/systemd/system ]; then /usr/lib/php/sessionclean; fi)
Feb 14 01:39:01 nas CRON[27284]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -x /usr/lib/php5/sessionclean ] && [ -d /var/lib/php5 ] && /usr/lib/php5/sessionclean /
var/lib/php5 $(/usr/lib/php5/maxlifetime))
Feb 14 01:40:01 nas CRON[27334]: (smmsp) CMD (test -x /etc/init.d/sendmail && /usr/share/sendmail/sendmail cron-msp)
Feb 14 02:00:01 nas CRON[28409]: (smmsp) CMD (test -x /etc/init.d/sendmail && /usr/share/sendmail/sendmail cron-msp)
Feb 14 12:48:27 nas rsyslogd: [origin software="rsyslogd" swVersion="7.4.4" x-pid="1888" x-info="http://www.rsyslog.com"] start
Feb 14 12:48:27 nas rsyslogd: rsyslogd's groupid changed to 103
Feb 14 12:48:27 nas rsyslogd: rsyslogd's userid changed to 101
Feb 14 12:48:27 nas kernel: [    0.000000] CPU0 microcode updated early to revision 0x20, date = 2018-04-10
Feb 14 12:48:27 nas kernel: [    0.000000] Initializing cgroup subsys cpuset
Feb 14 12:48:27 nas kernel: [    0.000000] Initializing cgroup subsys cpu
Feb 14 12:48:27 nas kernel: [    0.000000] Initializing cgroup subsys cpuacct

and another time:


Feb 14 14:39:01 nas CRON[13975]: (root) CMD (  [ -x /usr/lib/php/sessionclean ] && if [ ! -d /run/systemd/system ]; then /usr/lib/php/sessionclean; fi)
Feb 14 14:39:01 nas CRON[13976]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -x /usr/lib/php5/sessionclean ] && [ -d /var/lib/php5 ] && /usr/lib/php5/sessionclean /
var/lib/php5 $(/usr/lib/php5/maxlifetime))
Feb 14 15:09:01 nas CRON[15512]: (root) CMD (  [ -x /usr/lib/php/sessionclean ] && if [ ! -d /run/systemd/system ]; then /usr/lib/php/sessionclean; fi)
Feb 14 15:09:01 nas CRON[15513]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -x /usr/lib/php5/sessionclean ] && [ -d /var/lib/php5 ] && /usr/lib/php5/sessionclean /
var/lib/php5 $(/usr/lib/php5/maxlifetime))
Feb 14 18:31:27 nas rsyslogd: [origin software="rsyslogd" swVersion="7.4.4" x-pid="1872" x-info="http://www.rsyslog.com"] start
Feb 14 18:31:27 nas rsyslogd: rsyslogd's groupid changed to 103
Feb 14 18:31:27 nas rsyslogd: rsyslogd's userid changed to 101
Feb 14 18:31:27 nas kernel: [    0.000000] CPU0 microcode updated early to revision 0x20, date = 2018-04-10

---

### Post by howefield on 2019-02-15
Thread moved to the "*Server Platforms*" forum.

---

### Post by ejkeebler2 on 2019-02-15
Since I cannot really track down if this is an issue or not, i'm leaning towards reinstalling my os. I have a ZFS Pool that is 4 seperate disks raided for storage.  I should be safe to just export that pool, delete my other partitions and reload my os and then simply import my zfs pool?  There's nothing else I'll have to worry about?

NAME   FSTYPE       SIZE MOUNTPOINT LABEL
sda                59.6G
&#9500;&#9472;sda1 ext4          52G /
&#9500;&#9472;sda2                1K
&#9492;&#9472;sda5 swap         7.7G [SWAP]
sdb                 1.8T
&#9500;&#9472;sdb1 zfs_member   1.8T            storage
&#9492;&#9472;sdb9                8M
sdc                 1.8T
&#9500;&#9472;sdc1 zfs_member   1.8T            storage
&#9492;&#9472;sdc9                8M
sdd                 1.8T
&#9500;&#9472;sdd1 zfs_member   1.8T            storage
&#9492;&#9472;sdd9                8M
sde                 1.8T
&#9500;&#9472;sde1 zfs_member   1.8T            storage
&#9492;&#9472;sde9                8M

---

### Post by TheFu on 2019-02-19
Does the SMART data show any issues for any of the devices? Check that first.  **smartctl**

Also, sometimes there are issues with specific packages and/or specific kernels which cause problems.  
[https://www.phoronix.com/scan.php?page=news_item&px=ZFS-On-Linux-5.0-Workaround](https://www.phoronix.com/scan.php?page=news_item&px=ZFS-On-Linux-5.0-Workaround)

---

