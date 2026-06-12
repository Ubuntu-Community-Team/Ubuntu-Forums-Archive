---
title: "Mysql does not start at boot"
date: 2011-04-13
forum: Server Platforms
---

### Post by gary4gar on 2011-04-13
Hi,
On my Ubuntu 10.04 LTS Server, mysql does not start at boot. 

I tried this but does not work

 ```
root@dev:~# chkconfig mysql ON

The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'K02mysql' missing LSB tags and overrides
insserv: warning: script 'S10vzquota' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script is corrupt or invalid: /etc/init.d/../rc6.d/S00vzreboot
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'mysql' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'module-init-tools' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'plymouth' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'udev-finish' missing LSB tags and overrides
insserv: warning: script 'vzquota' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'vsftpd' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'hwclock' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'hwclock-save' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'udevtrigger' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'plymouth-splash' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'console-setup' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'network-interface-security' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'cron' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'plymouth-stop' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'network-interface' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'hostname' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'udev' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'plymouth-log' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'udevmonitor' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'failsafe-x' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'procps' missing LSB tags and overrides
insserv: Starting vzquota depends on rc.local and therefore on system facility `$all' which can not be true!
insserv: Starting vzquota depends on rc.local and therefore on system facility `$all' which can not be true!
insserv: Starting vzquota depends on rc.local and therefore on system facility `$all' which can not be true!
insserv: can not symlink(../init.d/vzquota, ../rc2.d/S04vzquota): File exists
insserv: can not symlink(../init.d/vzquota, ../rc3.d/S04vzquota): File exists
insserv: can not symlink(../init.d/vzquota, ../rc4.d/S04vzquota): File exists
insserv: can not symlink(../init.d/vzquota, ../rc5.d/S04vzquota): File exists
```


Can anyone tell me how to make sure mysql process comes up automatically after every reboot

---

### Post by BkkBonanza on 2011-04-13
The default install of mysql should be set to start at boot.

chkconfig is the command used on Red Hat/Fedora distributions. On Debian based ones like Ubuntu you would use,

sudo update-rc.d mysql defaults

I don't think mysql is setup for Upstart yet. At least my last install a week ago seemed to be same old sysvinit so this should still work.

---

### Post by gary4gar on 2011-04-13
I think it is using upstart, notice Event Scheduler. Its a part of upstart.
```
110413 14:21:12 [Note] /usr/sbin/mysqld: Normal shutdown

110413 14:21:13 [Note] Event Scheduler: Purging the queue. 0 events
110413 14:21:13  InnoDB: Starting shutdown...
110413 14:21:15  InnoDB: Shutdown completed; log sequence number 0 124448092
110413 14:21:15 [Note] /usr/sbin/mysqld: Shutdown complete

110413 14:21:15 [Note] Plugin 'FEDERATED' is disabled.
110413 14:21:15  InnoDB: Started; log sequence number 0 124448092
110413 14:21:15 [Note] Event Scheduler: Loaded 0 events
110413 14:21:15 [Note] /usr/sbin/mysqld: ready for connections.
Version: '5.1.41-3ubuntu12.7'  socket: '/var/run/mysqld/mysqld.sock'  port: 3306  (Ubuntu)
110413 14:34:03 [Note] /usr/sbin/mysqld: Normal shutdown

110413 14:34:03 [Note] Event Scheduler: Purging the queue. 0 events
110413 14:34:03  InnoDB: Starting shutdown...
110413 14:34:06  InnoDB: Shutdown completed; log sequence number 0 124448854
110413 14:34:06 [Note] /usr/sbin/mysqld: Shutdown complete

110413 14:35:27 [Note] Plugin 'FEDERATED' is disabled.
110413 14:35:27  InnoDB: Started; log sequence number 0 124448854
110413 14:35:27 [Note] Event Scheduler: Loaded 0 events
110413 14:35:27 [Note] /usr/sbin/mysqld: ready for connections.
Version: '5.1.41-3ubuntu12.7'  socket: '/var/run/mysqld/mysqld.sock'  port: 3306  (Ubuntu)

```


On your advice I did this:

```
root@dev:~# update-rc.d mysql defaults
update-rc.d: warning: /etc/init.d/mysql missing LSB information
update-rc.d: see <http://wiki.debian.org/LSBInitScripts>
 System start/stop links for /etc/init.d/mysql already exist
```

But still mysql does not start:|

---

### Post by BkkBonanza on 2011-04-13
Event Scheduler has nothing to do with Upstart as far as I know.

That message from update-rc.d indicates the sysvinit links are already present so it should be starting at boot. That also indicates that it's not using Upstart. If it were using Upstart you would see a file named /etc/init/mysql.conf - you can check that just in case.

You should check the mysql error.log for messages that indicate why it isn't starting.

Your log dump above seems to finish with a message that mysqld is ready for connections. Which means it has started. Unless what you posted is some old log.

You can use **ps ax |grep mysqld** to check if it's running.

If what you want is to manually start it then,

sudo /etc/init.d/mysql start 

should work.

---

### Post by gary4gar on 2011-04-14
Adding **start mysql** into */etc/rc.local* file did the trick. Thanks for reply:)

---

