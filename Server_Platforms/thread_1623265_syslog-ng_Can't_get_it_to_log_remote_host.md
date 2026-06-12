---
title: "syslog-ng: Can't get it to log remote host"
date: 2010-11-16
forum: Server Platforms
---

### Post by morrty11 on 2010-11-16
I'm trying to get my Ubuntu 10.04 LTS 64-bit Server to store logs via syslog. Specifically, I have a Linksys router with Tomato firmware that will log to a remote syslog server.

Here are the steps I performed to set this up:

Installation
```
sudo apt-get install syslog-ng
```

Configure **/etc/syslog-ng/syslog-ng.conf**
```

source s_tomato { udp(ip(10.42.23.11) port(514)); };
destination d_tomato { file("/var/log/tomato.log"); };
log { source(s_tomato); destination(d_tomato); };

```

Restart service
```
sudo /etc/init.d/syslog-ng restart
```

Setup Tomato Firmware to log to **10.42.23.11:514**

I made a file in **/var/log** called **tomato.log**

Nothing is being logged when I check the contents of the file.

If I run **netstat -a | grep sys**
```
udp        0      0 [server hostname.domain here has been removed for privacy]:syslog  *:*
```

I'm at a loss here, I do not know where my problem is or why it isn't logging.

I think my problem may be network/firewall related because I can't ```
telnet 10.42.23.11 514
```

Anyone have any ideas?

---

### Post by morrty11 on 2010-11-16
Here is some more diagnostics:

```
user@server:~$ sudo netstat -nap | grep 514
udp        0      0 10.42.23.11:514         0.0.0.0:*    
```

```
user@server:~$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

```

```
user@server:~$ ps aux | grep syslog
root      1340  0.0  0.0  12732   628 ?        Ss   Oct28   0:01 /sbin/mdadm --monitor --pid-file /var/run/mdadm/monitor.pid --daemonise --scan --syslog
root     19041  0.0  0.0  43344   788 ?        S    12:31   0:00 supervising syslog-ng
root     19042  0.0  0.0  49752  2512 ?        Ss   12:31   0:00 /usr/sbin/syslog-ng -p /var/run/syslog-ng.pid
ryan     19144  0.0  0.0   7628  1008 pts/0    S+   13:18   0:00 grep --color=auto syslog

```

Still not working.

---

### Post by ajoliveira on 2010-11-29
Hello

Please check [this]("http://ajoliveira.com/ajoliveira/uk/software/rsyslog.php").

Hope it helps...

---

### Post by morrty11 on 2010-12-28
> **ajoliveira said:**
> Hello

Please check [this]("http://ajoliveira.com/ajoliveira/uk/software/rsyslog.php").

Hope it helps...

sorry, still does not seem to work.

---

### Post by john_mc on 2011-01-03
> **ajoliveira said:**
> Hello

Please check [this]("http://ajoliveira.com/ajoliveira/uk/software/rsyslog.php").

Hope it helps...

Your read this nailed it for me mate. Thanks, really appreciate it mate.. Off to learn how to make us of this and monitor some Internet connections.


morrty11 - you get sorted mate? I am a novice on Linux and just picked this up a project because I need a tool to monitor Internet connections. I have a thread up but don't know if it would be any use to you but if I can help drop me message.

[http://ubuntuforums.org/showthread.php?p=10311219#post10311219](http://ubuntuforums.org/showthread.php?p=10311219#post10311219)

---

