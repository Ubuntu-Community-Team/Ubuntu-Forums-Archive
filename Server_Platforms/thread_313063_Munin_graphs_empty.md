---
title: "Munin graphs empty"
date: 2006-12-05
forum: Server Platforms
---

### Post by briguy on 2006-12-05
I have installed munin on a server and it is not updating the graphs.  That is to say - it IS updating them, just no new information is being put on the graphs!  Here are some of the configuration files:

munin.conf:
```
dbdir   /var/lib/munin
htmldir /var/www/munin
logdir  /var/log/munin
rundir  /var/run/munin

[localhost.localdomain]
    address 127.0.0.1
    use_node_name yes

```

munin-node.conf:
```
log_level 4
log_file /var/log/munin/munin-node.log
port 4949
pid_file /var/run/munin/munin-node.pid
background 1
setseid 1

# Which port to bind to;
host *
user root
group root
setsid yes

ignore_file ~$
ignore_file \.bak$
ignore_file %$
ignore_file \.dpkg-(tmp|new|old|dist)$
ignore_file \.rpm(save|new)$

host_name localhost.localdomain

allow ^127\.0\.0\.1$

```

In /var/log/munin, the files munin-html.log, and -graph.log show updates every five minutes, but munin-update.log is empty.

Ideas?  Thanks in advance! :p

---

### Post by briguy on 2006-12-05
Problem solved - some of the directories listed in munin.conf belonged to root, I chowned them to munin and everything seems to be working fine now.

---

