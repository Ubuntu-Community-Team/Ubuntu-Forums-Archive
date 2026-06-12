---
title: "Precise (12.04LTS) on Citrix Xen not booting all the way to login at console"
date: 2015-01-15
forum: Server Platforms
---

### Post by mdlueck on 2015-01-15
Greetings,

I host a couple of servers running Ubuntu Precise (12.04LTS) on a Citrix Xen host.

Suddenly these servers are no longer booting all of the way to the login prompt on the remote console.

I happen to have some tasks defined in /etc/rc.local, which I believe runs fairly close to the end of the IPL process, and those are being run. So I know the IPL process is getting to that point.

All of the console terminal processes are running, I see them in ps. In fact, hhhmmm....

```
$ ps aux | grep getty
root       812  0.0  0.0  15788   968 tty4     Ss+  Jan12   0:00 /sbin/getty -8 38400 tty4
root       825  0.0  0.0  15788   968 tty5     Ss+  Jan12   0:00 /sbin/getty -8 38400 tty5
root       836  0.0  0.0  15788   964 tty2     Ss+  Jan12   0:00 /sbin/getty -8 38400 tty2
root       837  0.0  0.0  15788   964 tty3     Ss+  Jan12   0:00 /sbin/getty -8 38400 tty3
root       846  0.0  0.0  15788   968 tty6     Ss+  Jan12   0:00 /sbin/getty -8 38400 tty6
root      1403  0.0  0.0  15788   972 tty1     Ss+  Jan12   0:00 /sbin/getty -8 38400 tty1
```

The PID for the getty tty1 is a lot higher than the rest of the PID's for the other getty tasks. Could that be a clue?

First one of the servers started the nonsense, and then a while later... a few Ubuntu updates later... the bad behavior showed up on the other 12.04 server.

Has anyone seen this behavior before and resolved it? If so, how?

I am thankful,

---

### Post by MAFoElffen on 2015-01-16
For diagnostics of startup, I do a couple things.

First is to to turn on verbose debugging with kernel boot options appending this to the end of the kernel boot line:
```

--verbose debug text plymouth:debug

```
That will throw out a lot of messages to help see what is going on.

Next is to temporarily install bootchart.
```

sudo apt-get install bootchart

```
That will create a .png graphical chart representation of the boot process and timings of each, each time it boots. You can find those graphics files after that at /var/log/bootchart. I started using this doing U+1 testing on Dev Cycles and found it useful. I don't leave it installed though... because if keeps creating those files. They rotate and archive, by I don't justify keeping using it after I find what is wrong.

Lately, on the newer kernels, a lot of users have been reporting a slight pause during udev, where they found it was looking for a floppy. They turned off in BIOS and commented out in fstab... and faster for them. That probably doesn't affect a virtual BIOS of a VM, but something to check in the fstab.

A note some 12.04 users are getting recently, is a message saying that the new plan for 12.04 is upgrading to a 14.04LTS kernel. A test slice has started getting these messages. Supposedly it also says that, that should be by July. I'm still trying to find out more on that. Cause users that went that way... with the package that was picked for them = not all worked out yet. But I can confirm that the upgrade path (full instead of older framework running a newer kernel) to 14.04LTS went very smoothly for me. 

Hope that was somewhat helpful.

---

### Post by mdlueck on 2015-02-12
An update on this, and thank you to MAFoElffen for posting those various suggestions.

The second of these LTS 12.04 servers to develop the problem... after this latest Ubuntu kernel revision regained ability to boot all the way to the logon screen on the console terminal screen. Woo hoo! One healed, one to go.

I noticed a difference in the two server's boot process logging.

First is the server which again is booting all of the way to the login screen:

```
Feb 12 20:25:01 wwwweb01 kernel: [    7.491839] type=1400 audit(1423790697.655:9): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=743 comm="apparmor_parser"
Feb 12 20:25:01 wwwweb01 kernel: [    7.491846] type=1400 audit(1423790697.655:10): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=743 comm="apparmor_parser"
Feb 12 20:25:01 wwwweb01 kernel: [    7.493333] type=1400 audit(1423790697.659:11): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=743 comm="apparmor_parser"
Feb 12 20:25:01 wwwweb01 kernel: [    8.218751] input: ImExPS/2 Generic Explorer Mouse as /devices/platform/i8042/serio1/input/input4
Feb 12 20:25:01 wwwweb01 kernel: [    8.382416] XFS (xvda7): Mounting Filesystem
Feb 12 20:25:01 wwwweb01 kernel: [    8.607900] XFS (xvda7): Ending clean mount
Feb 12 20:25:01 wwwweb01 kernel: [    8.690421] XFS (xvda8): Mounting Filesystem
Feb 12 20:25:01 wwwweb01 kernel: [    9.213188] XFS (xvda8): Ending clean mount
Feb 12 20:25:01 wwwweb01 kernel: [    9.302817] XFS (xvda6): Mounting Filesystem
Feb 12 20:25:01 wwwweb01 kernel: [   10.203340] XFS (xvda6): Ending clean mount
Feb 12 20:25:01 wwwweb01 kernel: [   10.276276] XFS (xvda9): Mounting Filesystem
Feb 12 20:25:01 wwwweb01 kernel: [   10.482004] XFS (xvda9): Ending clean mount
Feb 12 20:25:01 wwwweb01 kernel: [   10.539294] EXT4-fs (xvda1): mounted filesystem with ordered data mode. Opts: (null)
Feb 12 20:25:01 wwwweb01 kernel: [   10.716661] init: failsafe main process (908) killed by TERM signal
Feb 12 20:25:02 wwwweb01 acpid: starting up with netlink and the input layer
Feb 12 20:25:02 wwwweb01 cron[1045]: (CRON) INFO (pidfile fd = 3)
Feb 12 20:25:02 wwwweb01 cron[1067]: (CRON) STARTUP (fork ok)
Feb 12 20:25:02 wwwweb01 acpid: 1 rule loaded
Feb 12 20:25:02 wwwweb01 acpid: waiting for events: event logging is off
Feb 12 20:25:02 wwwweb01 kernel: [   12.495012] audit_printk_skb: 30 callbacks suppressed
Feb 12 20:25:02 wwwweb01 kernel: [   12.495019] type=1400 audit(1423790702.659:22): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/mysqld" pid=1098 comm="apparmor_parser"
Feb 12 20:25:02 wwwweb01 cron[1067]: (CRON) INFO (Running @reboot jobs)
Feb 12 20:25:09 wwwweb01 /etc/mysql/debian-start[1625]: Upgrading MySQL tables if necessary.
Feb 12 20:25:10 wwwweb01 /etc/mysql/debian-start[1628]: /usr/bin/mysql_upgrade: the '--basedir' option is always ignored
Feb 12 20:25:10 wwwweb01 /etc/mysql/debian-start[1628]: Looking for 'mysql' as: /usr/bin/mysql
Feb 12 20:25:10 wwwweb01 /etc/mysql/debian-start[1628]: Looking for 'mysqlcheck' as: /usr/bin/mysqlcheck
Feb 12 20:25:10 wwwweb01 /etc/mysql/debian-start[1628]: This installation of MySQL is already upgraded to 5.5.41, use --force if you still need to run mysql_upgrade
Feb 12 20:25:10 wwwweb01 /etc/mysql/debian-start[1639]: Checking for insecure root accounts.
Feb 12 20:25:10 wwwweb01 /etc/mysql/debian-start[1644]: Triggering myisam-recover for all MyISAM tables

```


Next is the one that has the server console get stuck / does not get to the login screen:

```
Feb 12 20:21:42 wwwweb02 kernel: [    4.171275] type=1400 audit(1423790501.604:5): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=556 comm="apparmor_parser"
Feb 12 20:21:42 wwwweb02 kernel: [    4.171283] type=1400 audit(1423790501.604:6): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=556 comm="apparmor_parser"
Feb 12 20:21:42 wwwweb02 kernel: [    4.171516] type=1400 audit(1423790501.604:7): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=556 comm="apparmor_parser"
Feb 12 20:21:42 wwwweb02 kernel: [    4.717824] ppdev: user-space parallel port driver
Feb 12 20:21:42 wwwweb02 kernel: [    4.791718] XFS (xvda7): Ending clean mount
Feb 12 20:21:42 wwwweb02 kernel: [    4.929034] init: failsafe main process (702) killed by TERM signal
Feb 12 20:21:42 wwwweb02 kernel: [    5.020093] input: ImExPS/2 Generic Explorer Mouse as /devices/platform/i8042/serio1/input/input4
Feb 12 20:21:42 wwwweb02 kernel: [    5.320881] type=1400 audit(1423790502.756:8): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=783 comm="apparmor_parser"
Feb 12 20:21:42 wwwweb02 kernel: [    5.320898] type=1400 audit(1423790502.756:9): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=783 comm="apparmor_parser"
Feb 12 20:21:42 wwwweb02 kernel: [    5.320906] type=1400 audit(1423790502.756:10): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=783 comm="apparmor_parser"
Feb 12 20:21:43 wwwweb02 acpid: starting up with netlink and the input layer
Feb 12 20:21:43 wwwweb02 acpid: 1 rule loaded
Feb 12 20:21:43 wwwweb02 acpid: waiting for events: event logging is off
Feb 12 20:21:43 wwwweb02 cron[819]: (CRON) INFO (pidfile fd = 3)
Feb 12 20:21:43 wwwweb02 cron[846]: (CRON) STARTUP (fork ok)
Feb 12 20:21:43 wwwweb02 cron[846]: (CRON) INFO (Running @reboot jobs)
Feb 12 20:21:44 wwwweb02 ooRexx: Magic is now registered
Feb 12 20:21:46 wwwweb02 /etc/mysql/debian-start[1377]: Upgrading MySQL tables if necessary.
Feb 12 20:21:46 wwwweb02 /etc/mysql/debian-start[1380]: /usr/bin/mysql_upgrade: the '--basedir' option is always ignored
Feb 12 20:21:46 wwwweb02 /etc/mysql/debian-start[1380]: Looking for 'mysql' as: /usr/bin/mysql
Feb 12 20:21:46 wwwweb02 /etc/mysql/debian-start[1380]: Looking for 'mysqlcheck' as: /usr/bin/mysqlcheck
Feb 12 20:21:46 wwwweb02 /etc/mysql/debian-start[1380]: This installation of MySQL is already upgraded to 5.5.41, use --force if you still need to run mysql_upgrade
Feb 12 20:21:46 wwwweb02 /etc/mysql/debian-start[1391]: Checking for insecure root accounts.
Feb 12 20:21:46 wwwweb02 /etc/mysql/debian-start[1396]: Triggering myisam-recover for all MyISAM tables

```

That second server, it's console gets stuck after having mounted all of the XFS filesystem partitions. Normally next I see some mention that the hardware clock was ahead last time the server booted, so Linux is fixing the clock. These servers run on Citrix Xen, so I attribute the "clock incorrect" message to the fact that it is not a real actually computer running the OS, but a virtual machine. Anyway, I never see  that message about fixing the clock, so it is as if the console boot process gets stuck right at that spot in the boot process.

Now, other than the fact that things happen a little out of order between the two virtual servers... I believe the wwwweb02 (which is the one that fails to get to the login screen) is running on the faster Citrix Xen host... does anyone see signs of what might be preventing it from displaying that "hardware clock fix" message and continuing to the login prompt?

Could it be a timing issue that even though the partition scheme between the two servers is identical, the partitions get mounted at a different time between the two servers? And the partitions get mounted in a different order, though like I said the partition schemes between the two servers are identical?

I am thankful,

---

### Post by mdlueck on 2015-05-16
I resolved this problem which plagued Xen powered Ubuntu Server 12.04 servers by switching from the linux-image-generic-lts-trusty kernel back to the original for this LTS release linux-image-generic.

From time to time, the other "near identical" server would also not boot all the way to the login screen on the remote server console.

As this is a Xen powered environment, we did not have a desperate hardware need for running the "lts-trusty" updated kernel, so the default LTS kernel which boots all the way to the server console login screen looks like a winning work-around.

I am thankful,

---

