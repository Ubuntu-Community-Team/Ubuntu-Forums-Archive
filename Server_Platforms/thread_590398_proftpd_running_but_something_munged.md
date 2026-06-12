---
title: "proftpd running but something munged"
date: 2007-10-24
forum: Server Platforms
---

### Post by dbrooke on 2007-10-24
Hello,

It appears proftpd is running (when I do a netstat) but I can't connect to it with ISPConfig and running some debugging reveals some sort of error:

root@ubuntu:/home/donovan# proftpd -t
Checking syntax of configuration file
- setting default address to 127.0.0.1
Syntax check complete.


root@ubuntu:/home/donovan# proftpd -n -c /etc/proftpd.conf
- setting default address to 127.0.0.1
localhost.localdomain - Failed binding to 0.0.0.0, port 21: Address already in use
localhost.localdomain - Check the ServerType directive to ensure you are configured correctly.


root@ubuntu:/home/donovan# proftpd -d 5
- mod_ctrls/0.9.4: binding ctrls socket to '/var/run/proftpd/proftpd.sock'
- parsing '/etc/proftpd/proftpd.conf' configuration
- parsing '/etc/proftpd/modules.conf' configuration
- mod_tls/2.1.1: using OpenSSL 0.9.8e 23 Feb 2007
- disabling runtime support for IPv6 connections
- DenyFilter: compiling deny regex '\*.*/'
- <IfModule>: using 'mod_tls.c' section at line 90
- <IfModule>: skipping 'mod_quota.c' section at line 94
- <IfModule>: skipping 'mod_ratio.c' section at line 98
- <IfModule>: using 'mod_delay.c' section at line 106
- <IfModule>: using 'mod_ctrls.c' section at line 110
- mod_ctrls/0.9.4: closing ctrls socket '/var/run/proftpd/proftpd.sock' (3)
- <IfModule>: using 'mod_ctrls_admin.c' section at line 118
- parsing '/etc/proftpd_ispconfig.conf' configuration
- setting default address to 127.0.0.1
localhost.localdomain -
localhost.localdomain - Config for Debian:
localhost.localdomain - DeferWelcome
localhost.localdomain - DefaultServer
localhost.localdomain - ShowSymlinks
localhost.localdomain - TimeoutNoTransfer
localhost.localdomain - TimeoutStalled
localhost.localdomain - TimeoutIdle
localhost.localdomain - DisplayLogin
localhost.localdomain - DisplayFirstChdir
localhost.localdomain - ListOptions
localhost.localdomain - DenyFilter
localhost.localdomain - UserID
localhost.localdomain - UserName
localhost.localdomain - GroupID
localhost.localdomain - GroupName
localhost.localdomain - Umask
localhost.localdomain - DirUmask
localhost.localdomain - AllowOverwrite
localhost.localdomain - TransferLog
localhost.localdomain - TLSEngine
localhost.localdomain - DelayEngine
localhost.localdomain - DefaultRoot
localhost.localdomain - IdentLookups
localhost.localdomain - ServerIdent
localhost.localdomain -
localhost.localdomain - Config for Debian:
localhost.localdomain - DefaultRoot
localhost.localdomain - AllowOverwrite
localhost.localdomain - Umask
localhost.localdomain - mod_ctrls/0.9.4: binding ctrls socket to '/var/run/proftpd/proftpd.sock'


root@ubuntu:/home/donovan# netstat -tap
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address Foreign Address State PID/Program name
tcp 0 0 *:mysql *:* LISTEN 4156/mysqld
tcp 0 0 *:81 *:* LISTEN 17368/ispconfig_htt
tcp 0 0 *:ftp *:* LISTEN 19043/proftpd: (acc [snip]

Thanks for any help on this!

Donovan

---

### Post by whit on 2007-10-26
> **dbrooke said:**
> 
root@ubuntu:/home/donovan# proftpd -n -c /etc/proftpd.conf
- setting default address to 127.0.0.1
localhost.localdomain - Failed binding to 0.0.0.0, port 21: Address already in use
localhost.localdomain - Check the ServerType directive to ensure you are configured correctly.
Have you tried configuring it to use the address assigned to one of your NICs? I have no idea whether running an ftp daemon on localhost (127.0.0.1) should even work. And since 0.0.0.0 means "every IP," it may be that already being bound to 127.0.0.1 is blocking that move. With some ftp daemons, you should run a separate instance for each IP you want to bind to. But I haven't run proftpd in a few years, so don't recall its requirement on that. (IMHO, pure-ftpd is a bit better.)

---

### Post by dbrooke on 2007-10-28
Just a quick note to say this got solved... now if I could only tell you how! :confused:

The ISPConfig connection was a simple matter of having to set up a user, via the manager, first.

Donovan

---

