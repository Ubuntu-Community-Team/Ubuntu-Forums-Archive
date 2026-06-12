---
title: "Mysql do not start at boot"
date: 2010-07-26
forum: Server Platforms
---

### Post by bovcan on 2010-07-26
HI!
Recently, few days or maybe a week ago I updated mysql and now mysql service do not start at boot. I must start it manualy, before this update it start automaticly.

How to fix this?

---

### Post by cdenley on 2010-07-26
How is mysql configured?
```

sudo grep '^[^#]' /etc/mysql/my.cnf

```

What interfaces does it listen on?
```

sudo netstat -tlnp|grep '/mysqld *$'
ifconfig

```

---

### Post by ruffEdgz on 2010-07-26
This information I posted is wrong, see below!

##EDIT##
cdenley is correct as I haven't played around with the new 10.04 ubuntu and mysql recently so I was going off my knowledge of how process started in the past, my apologize.

---

### Post by cdenley on 2010-07-26
In 10.04, sysv is no longer used for mysql. There are no links in /etc/rc*.d for mysql. It is configured in /etc/init/mysql.conf.

There is a common problem with upstart and network services:
> **cdenley said:**
> The services which don't start, what network interfaces do they bind to? If they require all network interfaces to be up, then that is probably your problem. With upstart, most services are configured to start when any network interface is brought up, which is usually 127.0.0.1. If the service is configured to listen on all interfaces, then this shouldn't be an issue.

---

### Post by bovcan on 2010-07-27
I get this:

> root@server1:~# grep '^[^#]' /etc/mysql/my.cnf
[client]
port		= 3306
socket		= /var/run/mysqld/mysqld.sock
[mysqld_safe]
socket		= /var/run/mysqld/mysqld.sock
nice		= 0
[mysqld]
user		= mysql
socket		= /var/run/mysqld/mysqld.sock
port		= 3306
basedir		= /usr
datadir		= /var/lib/mysql
tmpdir		= /tmp
skip-external-locking
bind-address		= 127.0.0.1
key_buffer		= 16M
max_allowed_packet	= 16M
thread_stack		= 192K
thread_cache_size       = 8
myisam-recover         = BACKUP
query_cache_limit	= 1M
query_cache_size        = 16M
log_error                = /var/log/mysql/error.log
expire_logs_days	= 10
max_binlog_size         = 100M
[mysqldump]
quick
quote-names
max_allowed_packet	= 16M
[mysql]
[isamchk]
key_buffer		= 16M
!includedir /etc/mysql/conf.d/
root@server1:~# 


> root@server1:~# sudo netstat -tlnp|grep '/mysqld *$'
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN      4078/mysqld     
root@server1:

---

### Post by cdenley on 2010-07-27
That doesn't look like the problem I was talking about, because 127.0.0.1 is usually the first interface to be brought up. Just to make sure, make this change to /etc/init/mysql.conf:
```

# MySQL Service

description     "MySQL Server"
author          "Mario Limonciello <superm1@ubuntu.com>"

start on (net-device-up **[COLOR="Red"]IFACE=lo[/COLOR]**
          and local-filesystems)
stop on runlevel [016]

```

---

### Post by bovcan on 2010-07-27
Nope, didn't start at boot.
> root@server1:~# grep '^[^#]' /etc/init/mysql.conf
description     "MySQL Server"
author          "Mario Limonciello <superm1@ubuntu.com>"
start on (net-device-up IFACE=lo
          and local-filesystems
	  and runlevel[2345])
stop on runlevel [016]
respawn
env HOME=/etc/mysql
umask 007
pre-start script
    #Sanity checks
    [ -r $HOME/my.cnf ]
    [ -d /var/run/mysqld ] || install -m 755 -o mysql -g root -d /var/run/mysqld
    # Load AppArmor profile
    if aa-status --enabled 2>/dev/null; then
        apparmor_parser -r /etc/apparmor.d/usr.sbin.mysqld || true
    fi
    LC_ALL=C BLOCKSIZE= df --portability /var/lib/mysql/. | tail -n 1 | awk '{ exit ($4<4096) }'
end script
exec /usr/sbin/mysqld
post-start script
    for i in `seq 1 30` ; do
		/usr/bin/mysqladmin --defaults-file=$HOME/debian.cnf ping
		ret = $?
		if [ $ret -eq 0 ] ; then
			break
		fi
		sleep 1
    done
	if [ $ret -eq 0 ] ; then
    	exec $HOME/debian-start
	else
		echo "timeout."
	fi
end script
root@server1:~# 


---

### Post by evey on 2010-07-28
@Bovcan

I think my problem is the same as yours with upstart: Mythbuntu 10.4 clean install - not an upgrade.  
Same thing, a week or so ago mysql stopped starting automatically on boot up (ps aux | grep mysql > just not running). 
Can -as root- service mysql start and mysql runs fine.

From looking at this and other posts have tried (Reboot in between each change) :
/etc/init/mysql.conf > adding IFACE=lo, IFACE=eth0, IFACE=eth1 (My net adapter is on eth1) after net-device-up.
Also tried replacing line in same file "exec /usr/sbin/mysqld" with "exec sudo -u mysql /usr/sbin/mysqld"
Also tried in /etc/mysql/my.cnf setting the bind-address to the actual network IP, then commenting out the bind-address line altogether.

None of the above worked and can't seem to see any output in the logs to point at.  Have now left the IFACE=lo in, set the startup line as original "exec /usr/sbin/mysqld" and returned the bind-address to normal 127.0.0.1

Anyone else with some ideas?

---

### Post by bovcan on 2010-07-28
yea, kinda strange becouse before worked. I just know, I updated mysql, there was some updates.
well, I can start MySql in Webmin manualy but it is better, if it starts at boot like apache and other stuff.

---

### Post by cdenley on 2010-07-28
Works fine for me.
```

apt-cache policy mysql-server-5.1
mount
tail /var/log/mysql/error.log

```

---

### Post by evey on 2010-07-28
/var/log/mysql/error.log is empty, but /var/log/error.log-old contains some output from yesterday but nothing I can see indicating why it's not starting.  Only really shows where I've been doing a restart and having to manually start mysql :

----------------------------

100727 20:19:22 [Note] /usr/sbin/mysqld: Normal shutdown

100727 20:19:23 [Note] Event Scheduler: Purging the queue. 0 events
100727 20:19:25  InnoDB: Starting shutdown...
100727 20:46:19 [Note] Plugin 'FEDERATED' is disabled.
InnoDB: The log sequence number in ibdata files does not match
InnoDB: the log sequence number in the ib_logfiles!
100727 20:46:19  InnoDB: Database was not shut down normally!
InnoDB: Starting crash recovery.
InnoDB: Reading tablespace information from the .ibd files...
InnoDB: Restoring possible half-written data pages from the doublewrite
InnoDB: buffer...
100727 20:46:19  InnoDB: Started; log sequence number 0 636458
100727 20:46:19 [Note] Event Scheduler: Loaded 0 events
100727 20:46:19 [Note] /usr/sbin/mysqld: ready for connections.
Version: '5.1.41-3ubuntu12.4'  socket: '/var/run/mysqld/mysqld.sock'  port: 3306  (Ubuntu)
100727 20:49:29 [Note] /usr/sbin/mysqld: Normal shutdown

100727 20:49:29 [Note] Event Scheduler: Purging the queue. 0 events
100727 20:49:29  InnoDB: Starting shutdown...
100727 20:49:30  InnoDB: Shutdown completed; log sequence number 0 636458
100727 20:49:30 [Note] /usr/sbin/mysqld: Shutdown complete

100727 20:53:07 [Note] Plugin 'FEDERATED' is disabled.
100727 20:53:07  InnoDB: Started; log sequence number 0 636458
100727 20:53:07 [Note] Event Scheduler: Loaded 0 events
100727 20:53:07 [Note] /usr/sbin/mysqld: ready for connections.
Version: '5.1.41-3ubuntu12.4'  socket: '/var/run/mysqld/mysqld.sock'  port: 3306  (Ubuntu)
----------------------

The only part I can suspect in /var/log/messages is "eth0: link is not ready" followed by a bit further down "/usr/sbin/mysqld" , network is actually on eth1 (Not dhcp, ip set):

--------------------

Jul 25 19:49:38 media kernel: [   24.698664] sky2 eth0: enabling interface
Jul 25 19:49:38 media kernel: [   24.698988] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jul 25 19:49:40 media kernel: [   26.790839] type=1505 audit(1280083780.721:6):  operation="profile_replace" pid=1044 name="/sbin/dhclient3"
Jul 25 19:49:40 media kernel: [   26.791130] type=1505 audit(1280083780.721:7):  operation="profile_replace" pid=1044 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Jul 25 19:49:40 media kernel: [   26.791296] type=1505 audit(1280083780.721:8):  operation="profile_replace" pid=1044 name="/usr/lib/connman/scripts/dhclient-script"
Jul 25 19:49:40 media kernel: [   26.987845] type=1505 audit(1280083780.914:9):  operation="profile_load" pid=1045 name="/usr/bin/evince"
Jul 25 19:49:40 media kernel: [   26.991668] type=1505 audit(1280083780.914:10):  operation="profile_load" pid=1045 name="/usr/bin/evince-previewer"
Jul 25 19:49:40 media kernel: [   26.994003] type=1505 audit(1280083780.924:11):  operation="profile_load" pid=1045 name="/usr/bin/evince-thumbnailer"
Jul 25 19:49:41 media kernel: [   27.309246] type=1505 audit(1280083781.231:12):  operation="profile_load" pid=1061 name="/usr/sbin/mysqld"
Jul 25 19:49:41 media kernel: [   27.311315] type=1505 audit(1280083781.241:13):  operation="profile_replace" pid=1064 name="/usr/sbin/ntpd"
Jul 25 19:49:41 media kernel: [   27.596398] type=1505 audit(1280083781.521:14):  operation="profile_load" pid=1065 name="/usr/sbin/tcpdump"

---

### Post by bovcan on 2010-07-28
have the same here (/var/log/mysql/error.log is empty, but /var/log/error.log-old )
Well, I have connection on wlan0. I tried to disabe onboard eth0(lan), but still the same.

---

### Post by cdenley on 2010-07-28
I did post 3 commands which may give relevant details.

---

### Post by bovcan on 2010-07-28
What to do with this commands?

> mysql-server-5.1:
  Installed: 5.1.41-3ubuntu12.4
  Candidate: 5.1.41-3ubuntu12.5
  Version table:
     5.1.41-3ubuntu12.5 0
        500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-proposed/main Packages
 *** 5.1.41-3ubuntu12.4 0
        100 /var/lib/dpkg/status
     5.1.41-3ubuntu12.3 0
        500 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Packages
        500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/main Packages
     5.1.41-3ubuntu12 0
        500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/main Packages
root@server1:~# 



> root@server1:~# mount
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /root/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev)
root@server1:~# 


> root@server1:~# tail /var/log/mysql/error.log
100728 17:46:54 [Note] Event Scheduler: Purging the queue. 0 events
100728 17:46:54  InnoDB: Starting shutdown...
100728 17:46:56  InnoDB: Shutdown completed; log sequence number 0 118659
100728 17:46:56 [Note] /usr/sbin/mysqld: Shutdown complete

100728 17:52:25 [Note] Plugin 'FEDERATED' is disabled.
100728 17:52:26  InnoDB: Started; log sequence number 0 118659
100728 17:52:26 [Note] Event Scheduler: Loaded 0 events
100728 17:52:26 [Note] /usr/sbin/mysqld: ready for connections.
Version: '5.1.41-3ubuntu12.4'  socket: '/var/run/mysqld/mysqld.sock'  port: 3306  (Ubuntu)
root@server1:~# 




EDIT: Aha,new update. 12.5, but no effect.

---

### Post by cdenley on 2010-07-28
Version 5.1.41-3ubuntu12.5 is still in the lucid-proposed branch for a reason! I upgraded from 5.1.41-3ubuntu12.3 in the lucid branch to 5.1.41-3ubuntu12.5 in lucid-proposed branch, and I could see your problem. You should be using 5.1.41-3ubuntu12.3.

---

### Post by cdenley on 2010-07-28
I think I figured out the problem with the proposed update.

/etc/init/mysql.conf
```

# MySQL Service

description     "MySQL Server"
author          "Mario Limonciello <superm1@ubuntu.com>"

start on (net-device-up
          and local-filesystems
	  and **[COLOR="Red"]runlevel [2345][/COLOR]**)
stop on runlevel [016]

respawn

```
There needs to be a space after "runlevel".

---

### Post by evey on 2010-07-29
Brilliant cdenley - I added the space after runlevel, rebooted and mysql came up fine.

Thanks a bunch - wonder how many other people are thinking it's something to do with upstart and a net interface not being ready when mysql launches instead of just a missing space :shock:

---

### Post by bovcan on 2010-07-29
Ha, good one and thanks a lot. Probably noone thought the space will cause this problem.
thanks again

---

### Post by Ni-el on 2010-07-30
> **cdenley said:**
> I think I figured out the problem with the proposed update.

/etc/init/mysql.conf
```

# MySQL Service

description     "MySQL Server"
author          "Mario Limonciello <superm1@ubuntu.com>"

start on (net-device-up
          and local-filesystems
      and **[COLOR=Red]runlevel [2345][/COLOR]**)
stop on runlevel [016]

respawn

```There needs to be a space after "runlevel".

--------------------------------------------------------------------------------------------------


YEP, THAT'S THE ONE.
Mucho Gusto!

---

### Post by thetankgirl on 2010-08-11
Oh wow, I never thought the solution would be as simple as adding a space hahaha!
Thank you so much! I've tried everything to make mysql run at boot and this solution works!

---

