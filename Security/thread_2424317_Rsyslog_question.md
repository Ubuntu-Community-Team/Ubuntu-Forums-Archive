---
title: "Rsyslog question"
date: 2019-08-06
forum: Security
---

### Post by ch0sen1 on 2019-08-06
Hello all,

I have an rsyslog configuration question. I ran cat /var/log/syslog to view system message logs. I got the following results:


Aug  6 21:23:36 raspberrypi rsyslogd-2207: error during parsing file /etc/rsyslog.d/10-my_iptables.conf, on or before line 1: errors occured in file '/etc/rsyslog.d/10-my_iptables.conf' around line 1 [try [http://www.rsyslog.com/e/2207](http://www.rsyslog.com/e/2207) ]
Aug  6 21:23:36 raspberrypi rsyslogd-3000: invalid character in selector line - ';template' expected
Aug  6 21:23:36 raspberrypi rsyslogd-2207: error during parsing file /etc/rsyslog.d/ip6tables.conf, on or before line 1: errors occured in file '/etc/rsyslog.d/ip6tables.conf' around line 1 [try [http://www.rsyslog.com/e/2207](http://www.rsyslog.com/e/2207) ]
Aug  6 21:23:36 raspberrypi rsyslogd-3000: invalid character in selector line - ';template' expected
Aug  6 21:23:36 raspberrypi rsyslogd-2207: error during parsing file /etc/rsyslog.d/iptables.conf, on or before line 1: errors occured in file '/etc/rsyslog.d/iptables.conf' around line 1 [try [http://www.rsyslog.com/e/2207](http://www.rsyslog.com/e/2207) ]
Aug  6 21:23:36 raspberrypi systemd[1]: Started System Logging Service.


When I comment out the lines in 10-my_iptables.conf, ip6tables.conf and iptables.conf I get the following:

Aug  6 21:23:36 raspberrypi rsyslogd-2207: error during parsing file /etc/rsyslog.d/ip6tables.conf, on or before line 1: errors occured in file '/etc/rsyslog.d/ip6tables.conf' around line 1 [try [http://www.rsyslog.com/e/2207](http://www.rsyslog.com/e/2207) ]
Aug  6 21:23:36 raspberrypi rsyslogd-3000: invalid character in selector line - ';template' expected
Aug  6 21:23:36 raspberrypi rsyslogd-2207: error during parsing file /etc/rsyslog.d/iptables.conf, on or before line 1: errors occured in file '/etc/rsyslog.d/iptables.conf' around line 1 [try [http://www.rsyslog.com/e/2207](http://www.rsyslog.com/e/2207) ]
Aug  6 21:23:36 raspberrypi systemd[1]: Started System Logging Service.
Aug  6 21:28:00 raspberrypi named[663]: zone 1.168.192.in-addr.arpa/IN: refresh: retry limit for master 192.168.1.121#53 exceeded (source 0.0.0.0#0)
Aug  6 21:28:00 raspberrypi named[663]: zone 1.168.192.in-addr.arpa/IN: Transfer started.
Aug  6 21:28:03 raspberrypi named[663]: transfer of '1.168.192.in-addr.arpa/IN' from 192.168.1.121#53: failed to connect: host unreachable
Aug  6 21:28:03 raspberrypi named[663]: transfer of '1.168.192.in-addr.arpa/IN' from 192.168.1.121#53: Transfer completed: 0 messages, 0 records, 0 bytes, 3.137 secs (0 bytes/sec)
Aug  6 21:28:46 raspberrypi named[663]: zone yer1.lan/IN: refresh: retry limit for master 192.168.1.121#53 exceeded (source 0.0.0.0#0)
Aug  6 21:39:01 raspberrypi CRON[3418]: (root) CMD (  [ -x /usr/lib/php5/sessionclean ] && /usr/lib/php5/sessionclean)]


So at this point I want to also ensure that zone yer.1.lan/IN... does not have the retry limit for master 192.168.1.121#53 exceeded.

How can this issue be solved? Your help is much appreciated.

---

### Post by Doug S on 2019-08-09
I think you need to fix your primary problem (your iptables config files), then your secondary problem (zone transfer/refresh) should go away. So, we need more information about /etc/rsyslog.d/10-my_iptables.conf.

---

