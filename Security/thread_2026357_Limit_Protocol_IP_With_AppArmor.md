---
title: "Limit Protocol/ IP With AppArmor?"
date: 2012-07-15
forum: Security
---

### Post by Hungry Man on 2012-07-15
What's the format (if there is one) for creating protocol and IP rules? 

Like if I only want to allow Firefox to connect to a specific site and deny it icmp and ftp.

---

### Post by CharlesA on 2012-07-15
I dunno if AppArmor can do that. That sounds like more of a firewall thing.

---

### Post by Hungry Man on 2012-07-15
Very sure that it can.

edit: Or at least I'm sure that there are network rules. I'm just wondering the extent of them.

---

### Post by bodhi.zazen on 2012-07-15
> **Hungry Man said:**
> Very sure that it can.

edit: Or at least I'm sure that there are network rules. I'm just wondering the extent of them.

Apparmor has rules for networking, but not as you are wanting.

> Network Rules
       AppArmor supports simple coarse grained network mediation.  The network
       rule restrict all socket(2) based operations.  The mediation done is a
       course grained check on whether a socket of a given type and family can
       be created, read, or written.  There is no mediation based of port
       number or protocol beyond tcp, udp, and raw.

       AppArmor network rules are accumulated so that the granted network
       permissions are the union of all the listed network rule permissions.

       AppArmor network rules are broad and general and become more
       restrictive as further information is specified.

       eg.

        network,               #allow access to all networking
        network tcp,           #allow access to tcp
        network inet tcp,      #allow access to tcp only for inet4 addresses
        network inet6 tcp,     #allow access to tcp only for inet6 addresses

See :

[http://manpages.ubuntu.com/manpages/precise/en/man5/apparmor.d.5.html](http://manpages.ubuntu.com/manpages/precise/en/man5/apparmor.d.5.html)

[http://doc.opensuse.org/documentation/html/openSUSE/opensuse-security/cha.apparmor.profiles.html#sec.apparmor.profiles.nac](http://doc.opensuse.org/documentation/html/openSUSE/opensuse-security/cha.apparmor.profiles.html#sec.apparmor.profiles.nac)

Most of what you want will be configured by iptables.

Linux does not really have an application firewall. Closest is Leopardflower

[http://leopardflower.sourceforge.net/](http://leopardflower.sourceforge.net/)

Note: Leopardflower has not been maintained recently. Last I looked it was not working, but a newer version was released in 2/2012

[http://sourceforge.net/projects/leopardflower/files/](http://sourceforge.net/projects/leopardflower/files/)

---

