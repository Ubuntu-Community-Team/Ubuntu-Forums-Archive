---
title: "Server Crashing"
date: 2010-08-30
forum: Server Platforms
---

### Post by triunenature on 2010-08-30
Ok, so every few days my server completely stops responding.  And it can remain in this state between 5 minutes and a few hours. (note, it doesn't reflect this on uptime, so i know the server doesn't completely go down, it just freezes)

Ubuntu 10.04 Server Edition.

Im not exactly sure whats going on with the logs either...

my daemon.log is showing some weird activity...
daemon.log:
```

Aug 29 18:37:55 server ntpd[15611]: synchronized to 209.114.111.1, stratum 2
Aug 29 18:37:55 server ntpd[15611]: kernel time sync status change 2001
Aug 29 19:28:58 server ntpd[15611]: kernel time sync status change 6001
Aug 29 20:03:07 server ntpd[15611]: synchronized to 149.20.68.17, stratum 2
Aug 29 21:07:39 server ntpd[15611]: kernel time sync status change 2001
Aug 29 21:58:53 server ntpd[15611]: kernel time sync status change 6001
Aug 29 22:19:38 server ntpd[15611]: Listening on interface #7 eth0, 2002:c0a8:640b:1234:222:68ff:fe09:e83a#123 Enabled
Aug 29 22:19:38 server ntpd[15611]: new interface(s) found: waking up resolver
Aug 29 22:24:38 server ntpd[15611]: Deleting interface #3 eth0, 2002:4402:7084:1234:222:68ff:fe09:e83a#123, interface stats: received=0, sent=0, dropped=0, active_time=68101 secs
Aug 29 23:29:38 server ntpd[15611]: Listening on interface #8 eth0, 2002:4402:7084:1234:222:68ff:fe09:e83a#123 Enabled
Aug 29 23:29:38 server ntpd[15611]: new interface(s) found: waking up resolver
Aug 29 23:34:38 server ntpd[15611]: Deleting interface #7 eth0, 2002:c0a8:640b:1234:222:68ff:fe09:e83a#123, interface stats: received=0, sent=0, dropped=0, active_time=4500 secs
Aug 29 23:41:23 server ntpd[15611]: synchronized to 209.114.111.1, stratum 2
Aug 29 23:45:05 server ntpd[15611]: synchronized to 91.189.94.4, stratum 2
Aug 29 23:45:05 server ntpd[15611]: kernel time sync status change 2001
Aug 29 23:45:09 server ntpd[15611]: no servers reachable
Aug 29 23:58:26 server ntpd[15611]: synchronized to 149.20.68.17, stratum 2

```
daemon.log.1:
```

Aug 24 19:53:15 server /etc/mysql/debian-start[1009]: Upgrading MySQL tables if necessary.
Aug 24 19:53:16 server /etc/mysql/debian-start[1012]: /usr/bin/mysql_upgrade: the '--basedir' option is always ignored
Aug 24 19:53:16 server /etc/mysql/debian-start[1012]: Looking for 'mysql' as: /usr/bin/mysql
Aug 24 19:53:16 server /etc/mysql/debian-start[1012]: Looking for 'mysqlcheck' as: /usr/bin/mysqlcheck
Aug 24 19:53:16 server /etc/mysql/debian-start[1012]: This installation of MySQL is already upgraded to 5.1.41, use --force if you still need to run mysql_upgrade
Aug 24 19:53:16 server /etc/mysql/debian-start[1019]: Checking for insecure root accounts.
Aug 24 19:53:16 server /etc/mysql/debian-start[1023]: Triggering myisam-recover for all MyISAM tables
Aug 29 03:13:44 server ntpd[15477]: ntpd 4.2.4p8@1.1612-o Fri Apr  9 03:13:54 UTC 2010 (1)
Aug 29 03:13:44 server ntpd[15478]: precision = 1.000 usec
Aug 29 03:13:44 server ntpd[15478]: ntp_io: estimated max descriptors: 1024, initial socket boundary: 16
Aug 29 03:13:44 server ntpd[15478]: Listening on interface #0 wildcard, 0.0.0.0#123 Disabled
Aug 29 03:13:44 server ntpd[15478]: Listening on interface #1 wildcard, ::#123 Disabled
Aug 29 03:13:44 server ntpd[15478]: Listening on interface #2 lo, ::1#123 Enabled
Aug 29 03:13:44 server ntpd[15478]: Listening on interface #3 eth0, 2002:4402:7084:1234:222:68ff:fe09:e83a#123 Enabled
Aug 29 03:13:44 server ntpd[15478]: Listening on interface #4 eth0, fe80::222:68ff:fe09:e83a#123 Enabled
Aug 29 03:13:44 server ntpd[15478]: Listening on interface #5 lo, 127.0.0.1#123 Enabled
Aug 29 03:13:44 server ntpd[15478]: Listening on interface #6 eth0, 192.168.1.14#123 Enabled
Aug 29 03:13:44 server ntpd[15478]: kernel time sync status 2040
Aug 29 03:18:01 server ntpd[15478]: synchronized to 91.189.94.4, stratum 2
Aug 29 03:18:01 server ntpd[15478]: kernel time sync status change 2001
Aug 29 03:23:46 server ntpd[15478]: ntpd exiting on signal 15
Aug 29 03:23:48 server ntpd[15529]: ntpd 4.2.4p8@1.1612-o Fri Apr  9 03:13:54 UTC 2010 (1)
Aug 29 03:23:48 server ntpd[15530]: precision = 1.000 usec
Aug 29 03:23:48 server ntpd[15530]: ntp_io: estimated max descriptors: 1024, initial socket boundary: 16
Aug 29 03:23:48 server ntpd[15530]: Listening on interface #0 wildcard, 0.0.0.0#123 Disabled
Aug 29 03:23:48 server ntpd[15530]: Listening on interface #1 wildcard, ::#123 Disabled
Aug 29 03:23:48 server ntpd[15530]: Listening on interface #2 lo, ::1#123 Enabled
Aug 29 03:23:48 server ntpd[15530]: Listening on interface #3 eth0, 2002:4402:7084:1234:222:68ff:fe09:e83a#123 Enabled
Aug 29 03:23:48 server ntpd[15530]: Listening on interface #4 eth0, fe80::222:68ff:fe09:e83a#123 Enabled
Aug 29 03:23:48 server ntpd[15530]: Listening on interface #5 lo, 127.0.0.1#123 Enabled
Aug 29 03:23:48 server ntpd[15530]: Listening on interface #6 eth0, 192.168.1.14#123 Enabled
Aug 29 03:23:48 server ntpd[15530]: kernel time sync status 2040
Aug 29 03:23:48 server ntpd[15530]: frequency initialized 0.000 PPM from /var/lib/ntp/ntp.drift
Aug 29 03:24:02 server ntpd[15530]: ntpd exiting on signal 15
Aug 29 03:24:13 server ntpd[15550]: ntpd 4.2.4p8@1.1612-o Fri Apr  9 03:13:54 UTC 2010 (1)
Aug 29 03:24:13 server ntpd[15551]: precision = 1.000 usec
Aug 29 03:24:13 server ntpd[15551]: ntp_io: estimated max descriptors: 1024, initial socket boundary: 16
Aug 29 03:24:13 server ntpd[15551]: Listening on interface #0 wildcard, 0.0.0.0#123 Disabled
Aug 29 03:24:13 server ntpd[15551]: Listening on interface #1 wildcard, ::#123 Disabled
Aug 29 03:24:13 server ntpd[15551]: Listening on interface #2 lo, ::1#123 Enabled
Aug 29 03:24:13 server ntpd[15551]: Listening on interface #3 eth0, 2002:4402:7084:1234:222:68ff:fe09:e83a#123 Enabled
Aug 29 03:24:13 server ntpd[15551]: Listening on interface #4 eth0, fe80::222:68ff:fe09:e83a#123 Enabled
Aug 29 03:24:13 server ntpd[15551]: Listening on interface #5 lo, 127.0.0.1#123 Enabled
Aug 29 03:24:13 server ntpd[15551]: Listening on interface #6 eth0, 192.168.1.14#123 Enabled
Aug 29 03:24:13 server ntpd[15551]: kernel time sync status 2040
Aug 29 03:24:13 server ntpd[15551]: frequency initialized 0.000 PPM from /var/lib/ntp/ntp.drift
Aug 29 03:27:28 server ntpd[15551]: synchronized to 149.20.68.17, stratum 2
Aug 29 03:27:28 server ntpd[15551]: kernel time sync status change 2001
Aug 29 03:29:34 server ntpd[15551]: ntpd exiting on signal 15
Aug 29 03:29:37 server ntpdate[15583]: adjust time server 64.183.56.58 offset -0.017963 sec
Aug 29 03:29:37 server ntpd[15610]: ntpd 4.2.4p8@1.1612-o Fri Apr  9 03:13:54 UTC 2010 (1)
Aug 29 03:29:37 server ntpd[15611]: precision = 1.000 usec
Aug 29 03:29:37 server ntpd[15611]: ntp_io: estimated max descriptors: 1024, initial socket boundary: 16
Aug 29 03:29:37 server ntpd[15611]: Listening on interface #0 wildcard, 0.0.0.0#123 Disabled
Aug 29 03:29:37 server ntpd[15611]: Listening on interface #1 wildcard, ::#123 Disabled
Aug 29 03:29:37 server ntpd[15611]: Listening on interface #2 lo, ::1#123 Enabled
Aug 29 03:29:37 server ntpd[15611]: Listening on interface #3 eth0, 2002:4402:7084:1234:222:68ff:fe09:e83a#123 Enabled
Aug 29 03:29:37 server ntpd[15611]: Listening on interface #4 eth0, fe80::222:68ff:fe09:e83a#123 Enabled
Aug 29 03:29:37 server ntpd[15611]: Listening on interface #5 lo, 127.0.0.1#123 Enabled
Aug 29 03:29:37 server ntpd[15611]: Listening on interface #6 eth0, 192.168.1.14#123 Enabled
Aug 29 03:29:37 server ntpd[15611]: kernel time sync status 2040
Aug 29 03:29:37 server ntpd[15611]: frequency initialized 0.000 PPM from /var/lib/ntp/ntp.drift
Aug 29 03:32:55 server ntpd[15611]: synchronized to 149.20.68.17, stratum 2
Aug 29 03:32:55 server ntpd[15611]: kernel time sync status change 2001
Aug 29 03:39:24 server ntpd[15611]: synchronized to 169.229.70.201, stratum 2
Aug 29 03:47:00 server ntpd[15611]: synchronized to 149.20.68.17, stratum 2
Aug 29 03:51:06 server ntpd[15611]: synchronized to 169.229.70.201, stratum 2
Aug 29 03:57:35 server ntpd[15611]: synchronized to 149.20.68.17, stratum 2
Aug 29 04:05:11 server ntpd[15611]: synchronized to 91.189.94.4, stratum 2
Aug 29 04:11:41 server ntpd[15611]: synchronized to 149.20.68.17, stratum 2

```

messages:
```
Aug 29 06:47:31 server rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="839" x-info="http://www.rsyslog.com"] rsyslogd was HUPed, type 'lightweight'.

```

not to mention, after about 5 minutes of ssh'ing into my server, the connection dies out.  Its made me have to rework all my longer commands into ways that if i lose connection, they will keep working (ie -> screen)

Any help would be loved!!!

---

### Post by maikel.b on 2010-08-30
[FONT=Calibri][SIZE=3]Oke i don&#8217;t know this will help you, bud I see some strange things in the log file..[/SIZE][/FONT]
[FONT=Calibri][SIZE=3] [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]The log file  has many ntpd logs, and the log is from 29 aug and ntpd from April the 9e [/SIZE][/FONT]
[FONT=Calibri][SIZE=3] [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Try to set you ntpd client to default time zone of you country..[/SIZE][/FONT]
[FONT=Calibri][SIZE=3] [/SIZE][/FONT]
[SIZE=3][FONT=Calibri]With the command  [COLOR=black]sudo tzconfig and select the time zone again..[/COLOR][/FONT][/SIZE]
[COLOR=black][FONT=Calibri][SIZE=3] [/SIZE][/FONT][/COLOR]
[COLOR=black][SIZE=3][FONT=Calibri]If this won&#8217;t work  stop the ntpd and look if the server still has problems.. and set the server on time with the date command&#8230; see man date for the best solution..[/FONT][/SIZE][/COLOR]
[COLOR=black][FONT=Calibri][SIZE=3] [/SIZE][/FONT][/COLOR]
[COLOR=black][SIZE=3][FONT=Calibri]Do you use a DHCP server in your network?? Is this a server that automatic receives an IP address?[/FONT][/SIZE][/COLOR]
[COLOR=black][FONT=Calibri][SIZE=3] [/SIZE][/FONT][/COLOR]
[COLOR=black][SIZE=3][FONT=Calibri] [/FONT][/SIZE][/COLOR]
[COLOR=black][FONT=Calibri][SIZE=3] [/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Calibri][SIZE=3] [/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Calibri][SIZE=3]Greetz Maikel.b[/SIZE][/FONT][/COLOR]

---

