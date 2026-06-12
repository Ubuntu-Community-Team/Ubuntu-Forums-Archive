---
title: "running perl script with privilege"
date: 2012-03-23
forum: Security
---

### Post by user008 on 2012-03-23
hi,
i have a problem with privilege on ubuntu.
i am trying to create cgi script using perl which need root privilege access.

i use [noparse]Net::Ping[/noparse] module, and here is the script which i tried to run.

socket($self->{"fh"}, PF_INET, SOCK_RAW, $self->{"proto_num"}) || confess("icmp socket error - $!");

I've already edit the sudoers file, and add these lines :

# User privilege specification
root    ALL=(ALL) ALL

# added by me
User_Alias APACHE = www-data
Cmnd_Alias FIREWALL = /sbin/iptables, /sbin/ifconfig, /sbin/route
APACHE ALL = (ALL) NOPASSWD:FIREWALL


i still cannot execute my cgi script command with browser, but it is fine when i execute it with terminal using
root privilege. i think i still have misconfiguration on that sudoers file.

Need your advice.

---

