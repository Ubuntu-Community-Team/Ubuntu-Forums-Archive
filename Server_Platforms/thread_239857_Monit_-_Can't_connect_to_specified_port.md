---
title: "Monit - Can't connect to specified port"
date: 2006-08-19
forum: Server Platforms
---

### Post by Gouki on 2006-08-19
My question is about Monit. I'm trying to install it on my 'test' server but I can't seem to get it to work. For some strange reason, even after I start the daemon, I can't establish a connection to the specified (/etc/monit/monitrc) port.

I have followed [this guide](http://howtoforge.com/server_monitoring_monit_munin_p2), skiping and deleting what I don't need (apache monitoring, postfix, sql and HTTPS support).

This is my monitrc content. As you can see, I just want to start by monitoring SSHd and ProFTPd
```
set daemon  60
set logfile syslog facility log_daemon
set mailserver localhost
set mail-format { from: monit@server1.example.com }
set alert root@localhost
set httpd port 2812 and


check process proftpd with pidfile /var/run/proftpd.pid
   start program = "/etc/init.d/proftpd start"
   stop program  = "/etc/init.d/proftpd stop"
   if failed port 21 protocol ftp then restart
   if 5 restarts within 5 cycles then timeout

check process sshd with pidfile /var/run/sshd.pid
   start program  "/etc/init.d/ssh start"
   stop program  "/etc/init.d/ssh stop"
   if failed port 22 protocol ssh then restart
   if 5 restarts within 5 cycles then timeout
```

My /etc/default/monit:

```
# Defaults for monit initscript
# sourced by /etc/init.d/monit
# installed at /etc/default/monit by maintainer scripts
# Fredrik Steen <stone@debian.org>

# You must set this variable to for monit to start
startup=1

# To change the intervals which monit should run uncomment
# and change this variable.
CHECK_INTERVALS=60
```

Any ideas?

---

### Post by Gouki on 2006-08-20
I was able to find what I had wrong.

```
set daemon  60
set logfile syslog facility log_daemon
set mailserver localhost
set mail-format { from: monit@server1.example.com }
set alert root@localhost
set httpd port 2812 and
```

We need to specify who is allowed to see the Monit page. In my case, I added:

```
set daemon  60
set logfile syslog facility log_daemon
set mailserver localhost
set mail-format { from: monit@server1.example.com }
set alert root@localhost
set httpd port 2812 and
allow ROOT:PASSWORD
```

There are numerous other arguments you can add, for example, limiting by IP:

```
allow 10.0.0.1
```

---

