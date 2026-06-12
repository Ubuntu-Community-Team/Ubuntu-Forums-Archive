---
title: "mysqld fails to start on 15.10"
date: 2015-07-12
forum: Ubuntu Development Version
---

### Post by crcarson on 2015-07-12
A late update (last 2 days) to systemd has caused mysqld to fail to start.  The systemd journal indicates trying to mysqld_safe but never completing.  The mysql error log shows failure to bind on TCP/IP port: Cannot assign requested address.  Have been using 15.10 and mysql successfully for several weeks now.  A reboot to 15.04 and mysqld starts and runs OK.

Part of the mysql error log....
2015-07-12 10:43:19 1167 [Note] Server hostname (bind-address): '192.168.1.201'; port: 3306
2015-07-12 10:43:19 1167 [Note]   - '192.168.1.201' resolves to '192.168.1.201';
2015-07-12 10:43:19 1167 [Note] Server socket created on IP: '192.168.1.201'.
2015-07-12 10:43:19 1167 [ERROR] Can't start server: Bind on TCP/IP port: Cannot assign requested address
2015-07-12 10:43:19 1167 [ERROR] Do you already have another mysqld server running on port: 3306 ?
2015-07-12 10:43:19 1167 [ERROR] Aborting


Journal entries for _SYSTEMD_UNIT=mysql.service
Jul 12 10:43:16 Desktopps mysqld_safe[813]: 150712 10:43:16 mysqld_safe Can't log to error log and syslog at the same time.  Remove all --lo
Jul 12 10:43:16 Desktopps mysqld_safe[813]: 150712 10:43:16 mysqld_safe Logging to '/var/log/mysql/error.log'.
Jul 12 10:43:16 Desktopps mysqld_safe[813]: 150712 10:43:16 mysqld_safe Starting mysqld daemon with databases from /var/lib/mysql

---

### Post by QDR06VV9 on 2015-07-12
Have you tried to check bad bind-address in my /etc/mysql/my.cnf
Check that against your 15.04 file.
And also it shows "you already have another mysqld server running on port: 3306"
Maybe kill it and restart?
And just to be sure to start and enable on startup
```
[SIZE=2]sudo systemctl enable sshd[/SIZE]
```
And there is this thread [http://ubuntuforums.org/showthread.php?t=881119](http://ubuntuforums.org/showthread.php?t=881119)

Regards

---

### Post by crcarson on 2015-07-12
Changes have been made in how my.cnf is handled.  When I built the 15.10 system my modified my.cnf was put into /etc/mysql/my.cnf.  Now there is a stripped down my.cnf which has an !include for /etc/mysql/mysql.conf.d.  In that directory is the modified my.cnf with the correct bind address.  There is no other mysqld task running.  Dont' understand your reference to sshd but I did run a systemctl -l status mysql.service and it shows "enabled".

 mysql.service - MySQL Community Server
   Loaded: loaded (/lib/systemd/system/mysql.service; enabled; vendor preset: enabled)
   Active: activating (start-post) since Sun 2015-07-12 19:45:33 EDT; 2min 6s ago
  Process: 834 ExecStart=/usr/bin/mysqld_safe (code=exited, status=0/SUCCESS)
  Process: 829 ExecStartPre=/usr/share/mysql/mysql-systemd-start pre (code=exited, status=0/SUCCESS)
 Main PID: 834 (code=exited, status=0/SUCCESS);         : 835 (mysql-systemd-s)
   CGroup: /system.slice/mysql.service
           &#9492;&#9472;control
             &#9500;&#9472; 835 /bin/bash /usr/share/mysql/mysql-systemd-start post
             &#9492;&#9472;3035 sleep 1

Jul 12 19:45:33 Desktopps systemd[1]: Starting MySQL Community Server...
Jul 12 19:45:34 Desktopps mysqld_safe[834]: 150712 19:45:34 mysqld_safe Can't log to error log and syslog at the same time.  Remove all --log-error configuration options for --syslog to take effect.
Jul 12 19:45:34 Desktopps mysqld_safe[834]: 150712 19:45:34 mysqld_safe Logging to '/var/log/mysql/error.log'.
Jul 12 19:45:34 Desktopps mysqld_safe[834]: 150712 19:45:34 mysqld_safe Starting mysqld daemon with databases from /var/lib/mysql

---

### Post by crcarson on 2015-07-13
Should have check for other types of network operations.  Seem that the 15.10 system can't find eth0 after booting and then builds a new network en01 but uses DHCP to assign IP address.  Need to have the ethernet assign a static address identified in the eth0 part of the /etc/network/interfaces file.  Any ideas on why this system would not be able to find eth0 (this was working for several weeks)

---

### Post by QDR06VV9 on 2015-07-13
Systemd is newish to the works and seems to have mixed opinions which we will not go into here.
But this is a development cycle (15.10) and systemd seems to have a few rough edges(for lack of a better term) and I see a lot of threads to server environments Alot, not just in ubuntu but debian and redhat related.
> Any ideas on why this system would not be able to find eth0 (this was working for several weeks)
I would not even hazard a guess right now.:)
So you did get around to reading the link I added.
> The simple answer is your DHCP server hasn't given you an ip address  when mysqld starts up. The best solution is to give your server a static  ip.

See also [http://ubuntuforums.org/showthread.php?t=821010](http://ubuntuforums.org/showthread.php?t=821010)
Nor am I saying this is your particular fix but helpful suggestions.;)
Keep us updated if you would.
Welcome to Testing!

---

### Post by crcarson on 2015-07-13
runrickus, thanks for the reply.  Didn't spend a lot of time trying to understand the link you added since it was 2008 and the init system was upstart.  I have setup static IPs and the correct bind address.  All was working until three days ago which corresponds with a systemd update.  Tried to change my interfaces file to define eno1 but for some reason didn't work and haven't tried to see what was wrong.

---

### Post by QDR06VV9 on 2015-07-13
Sorry to hear that.:icon_frown: I will see if there is anything else that turns up.
And have you yet to Try "route --help" to see the description of how to add a route.  You'll  likely need root/admin access to set up the routing rule.
and is eno1 a typeO?
This was just suggested by some gentoo friends
>  fix interface eth0 does not exist
 # ln -s /dev/null /etc/udev/rules.d/80-net-name-slot.rules
From here [http://gentoovps.net/interface-eth0-does-not-exist/](http://gentoovps.net/interface-eth0-does-not-exist/)
And even more here [URL="http://forums.fedoraforum.org/showthread.php?t=274152"]http://forums.fedoraforum.org/showthread.php?t=274152
[/URL]It seems some more homework is needed!
And This informative Blog [http://mysqlserverteam.com/mysql-5-7-native-systemd-support/](http://mysqlserverteam.com/mysql-5-7-native-systemd-support/)
Study Hard there will be a pop Quiz Tomorrow.(Joke Here):D
 And I will post back if relevant! 
Regards

---

### Post by crcarson on 2015-07-14
All is well again.  Tried to figure out why the eth0 device was being named eno1 with no success so I gave up and re-configured the /etc/network/interfaces to configure eno1 and got the system up and running again.  Did the normal apt-get update/upgrade to get latest updates and saw another systemd component being updated.  Re-booted and found the ethernet device named back to eth0.  Again reconfigured interfaces and all is well (again).

---

