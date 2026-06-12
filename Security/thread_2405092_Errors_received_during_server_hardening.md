---
title: "Errors received during server hardening"
date: 2018-11-01
forum: Security
---

### Post by vegas5882 on 2018-11-01
I am relatively new to Ubuntu and was going through some server hardening tasks. I ran these commands below:
```
# IP Spoofing protection
?net.ipv4.conf.all.rp_filter = 1
?net.ipv4.conf.default.rp_filter = 1
?
?# Ignore ICMP broadcast requests
?net.ipv4.icmp_echo_ignore_broadcasts = 1
?
?# Disable source packet routing
?net.ipv4.conf.all.accept_source_route = 0
?net.ipv6.conf.all.accept_source_route = 0 
?net.ipv4.conf.default.accept_source_route = 0
?net.ipv6.conf.default.accept_source_route = 0
?
?# Ignore send redirects
?net.ipv4.conf.all.send_redirects = 0
?net.ipv4.conf.default.send_redirects = 0
?
?# Block SYN attacks
?net.ipv4.tcp_syncookies = 1
?net.ipv4.tcp_max_syn_backlog = 2048
?net.ipv4.tcp_synack_retries = 2
?net.ipv4.tcp_syn_retries = 5
?
?# Log Martians
?net.ipv4.conf.all.log_martians = 1
?net.ipv4.icmp_ignore_bogus_error_responses = 1
?
?# Ignore ICMP redirects
?net.ipv4.conf.all.accept_redirects = 0
?net.ipv6.conf.all.accept_redirects = 0
?net.ipv4.conf.default.accept_redirects = 0 
?net.ipv6.conf.default.accept_redirects = 0
?
?# Ignore Directed pings
?net.ipv4.icmp_echo_ignore_all = 1

Errors I received upon restarting SYSCTL -p:

root@Ubuntu1:~# sysctl -p
net.ipv4.conf.default.rp_filter = 1
net.ipv4.conf.all.rp_filter = 1
net.ipv4.icmp_echo_ignore_broadcasts = 1
net.ipv4.tcp_syncookies = 1
sysctl: cannot stat /proc/sys/?net/ipv4/tcp_max_syn_backlog: No such file or directory
sysctl: cannot stat /proc/sys/?net/ipv4/tcp_synack_retries: No such file or directory
sysctl: cannot stat /proc/sys/?net/ipv4/tcp_syn_retries: No such file or directory
net.ipv4.conf.all.accept_redirects = 0
net.ipv6.conf.all.accept_redirects = 0
sysctl: cannot stat /proc/sys/?net/ipv4/conf/default/accept_redirects: No such file or directory
sysctl: cannot stat /proc/sys/?net/ipv6/conf/default/accept_redirects: No such file or directory
net.ipv4.conf.all.send_redirects = 0
net.ipv4.conf.default.send_redirects = 0
net.ipv4.conf.all.accept_source_route = 0
net.ipv6.conf.all.accept_source_route = 0
net.ipv4.conf.default.accept_source_route = 0
net.ipv6.conf.default.accept_source_route = 0
net.ipv4.conf.all.log_martians = 1
sysctl: cannot stat /proc/sys/net/ipv4/icmp_ignore_bogus_error_messages: No such file or directory
net.ipv4.icmp_echo_ignore_all = 1
root@Ubuntu1:~#
```

Thank you for your help.

---

### Post by TheFu on 2018-11-02
Are you new to Linux too or just Ubuntu?

None of those are commands. They are system config parameters.  And having a '?" at the beginning of every line breaks whatever it is.

---

### Post by vegas5882 on 2018-11-02
my bad. The ? at the beginnings of the lines seen above were not included in the config file. I only put in the actual parameters. Still got those errors or warnings though.

---

