---
title: "HangUp Ubuntu server 12.04.01"
date: 2013-04-02
forum: Server Platforms
---

### Post by SergioMaroni on 2013-04-02
Hi all! 
[U][I]
first of all. sorry for my bad english[/I][/U]

I`m have some problem with Ubuntu server (12.04.01 LTS) . Periodicaly its hangup and dont responding (i`m cant connect by ssh, http, but can ping server). On server install this program:

1) MySQL 14,14
2) Zabbix 2.0.1
3) Apache 2,2,22

Server we use for Zabbix (monitoring system) 
Server configuration:

On Log last message:
```
Apr  3 04:39:01 kam-zabbix CRON[32152]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -t$
Apr  3 04:39:01 kam-zabbix CRON[32151]: pam_unix(cron:session): session closed for user root
Apr  3 05:09:01 kam-zabbix CRON[3729]: pam_unix(cron:session): session opened for user root by (uid=0)
Apr  3 05:09:01 kam-zabbix CRON[3730]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -ty$
Apr  3 05:09:01 kam-zabbix CRON[3729]: pam_unix(cron:session): session closed for user root
Apr  3 05:17:01 kam-zabbix CRON[4848]: pam_unix(cron:session): session opened for user root by (uid=0)
Apr  3 05:17:01 kam-zabbix CRON[4849]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr  3 05:17:01 kam-zabbix CRON[4848]: pam_unix(cron:session): session closed for user root
Apr  3 05:39:01 kam-zabbix CRON[7947]: pam_unix(cron:session): session opened for user root by (uid=0)
Apr  3 05:39:01 kam-zabbix CRON[7948]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -ty$
Apr  3 05:39:01 kam-zabbix CRON[7947]: pam_unix(cron:session): session closed for user root
Apr  3 06:09:01 kam-zabbix CRON[12190]: pam_unix(cron:session): session opened for user root by (uid=0)
Apr  3 06:09:01 kam-zabbix CRON[12191]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -t$
Apr  3 06:09:01 kam-zabbix CRON[12190]: pam_unix(cron:session): session closed for user root
Apr  3 06:17:01 kam-zabbix CRON[13333]: pam_unix(cron:session): session opened for user root by (uid=0)
Apr  3 06:17:01 kam-zabbix CRON[13334]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr  3 06:17:01 kam-zabbix CRON[13333]: pam_unix(cron:session): session closed for user root



```
When it happens again i`m look at tty1 and see many message like this:

```
[50400.335434] INFO: task zabbix_server:1106 blocked for more than 120 seconds.
[50400.335434] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs"  disabe this message.

```
_**Please help me solve this problem.**_

---

