---
title: "server hardening - network /etc/sysctl options"
date: 2016-11-21
forum: Security
---

### Post by Drenriza on 2016-11-21
I am currently looking to how i can harden my Ubuntu server 16.04 installation and have come across several sites that
suggest the following

> 
# IP Spoofing protection
net.ipv4.conf.all.rp_filter = 1 (default)
net.ipv4.conf.default.rp_filter = 1 (default)

# Ignore ICMP broadcast requests
net.ipv4.icmp_echo_ignore_broadcasts = 1 (default)

# Disable source packet routing
net.ipv4.conf.all.accept_source_route = 0 (default)
net.ipv6.conf.all.accept_source_route = 0  (default)
net.ipv4.conf.default.accept_source_route = 0
net.ipv6.conf.default.accept_source_route = 0 (default)

# Ignore send redirects
net.ipv4.conf.all.send_redirects = 0 (default)
net.ipv4.conf.default.send_redirects = 0

# Block SYN attacks
net.ipv4.tcp_syncookies = 1 (default)
net.ipv4.tcp_max_syn_backlog = 2048
net.ipv4.tcp_synack_retries = 2
net.ipv4.tcp_syn_retries = 5

# Log Martians
net.ipv4.conf.all.log_martians = 1 (default)
net.ipv4.icmp_ignore_bogus_error_responses = 1 (default)

# Ignore ICMP redirects
net.ipv4.conf.all.accept_redirects = 0 (default)
net.ipv6.conf.all.accept_redirects = 0
net.ipv4.conf.default.accept_redirects = 0 
net.ipv6.conf.default.accept_redirects = 0

# Ignore Directed pings
net.ipv4.icmp_echo_ignore_all = 1


Some of the options can be read from /etc/sysctl.conf but options like net.ipv4.tcp_max_syn_backlog arent noted in the file.

_**My question**_: Where can i read about the different options available for /etc/sysctl.conf?

Thanks on advance
Kind regards

---

### Post by Drenriza on 2016-11-22
Anyone who can point me in the right direction?

I have checked
man sysctl
man sysctl.conf

And cant find neither the options or that the refer other man pages that could have the information.

---

### Post by Drenriza on 2016-11-27
Anyone who can point me in a semi right direction?

---

### Post by alexjpowell on 2016-11-30
Hi,
What is the server used for? What environment is it in? Is it public facing? Does it send and receive data from other servers in the same network?

---

### Post by SeijiSensei on 2016-11-30
Those are kernel parameters.  Here's some older documentation I found for the ipv4 parameters including tcp_max_syn_backlog: [http://tldp.org/HOWTO/Adv-Routing-HOWTO/lartc.kernel.obscure.html#AEN1252](http://tldp.org/HOWTO/Adv-Routing-HOWTO/lartc.kernel.obscure.html#AEN1252)

Searching for "linux net kernel parameters" brings up a lot of pages.

---

