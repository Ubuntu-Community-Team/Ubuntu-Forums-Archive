---
title: "Using apparmor to restrict networking to specific ports"
date: 2011-06-12
forum: Security
---

### Post by Lars Noodén on 2011-06-12
Perhaps it is my misinterpretation of AppArmor, how can it be configured to restrict TCP or UDP traffic to/from specific ports?  

The profile "abstractions/nameservice", under the section "# TCP/UDP network access", doesn't seem to lock the application to port 53.  What am I missing?  Restriction to specific ports is something that systrace can do so I'd expect nothing less from AppArmor.

---

### Post by Dave_L on 2011-06-13
From [http://manpages.ubuntu.com/manpages/lucid/en/man5/apparmor.d.5.html](http://manpages.ubuntu.com/manpages/lucid/en/man5/apparmor.d.5.html):

>  Network Rules
       AppArmor supports simple coarse grained network mediation.  The network
       rule restrict all socket(2) based operations.  The mediation done is a
       course grained check on whether a socket of a given type and family can
       be created, read, or written.  There is no mediation based of port
       number or protocol beyond tcp, udp, and raw.

---

### Post by Lars Noodén on 2011-06-13
Right, but looking in "abstractions/nameservice" it looks like networking is an all-or-nothing option rather than limiting to UDP or TCP and to or from specific ports.  Can you provide specific example or instructions on limiting to a particular port.

---

### Post by Dave_L on 2011-06-13
The man page excerpt I quoted above says that limiting to a port is **not possible**.

The same page also provides examples of limiting by protocol:

> network,     #allow access to all networking
network tcp,        #allow access to tcp
network inet tcp,   #allow access to tcp only for inet4 addresses
network inet6 tcp,  #allow access to tcp only for inet6 addresses

---

### Post by Lars Noodén on 2011-06-13
> **Dave_L said:**
> The man page excerpt I quoted above says that limiting to a port is **not possible**.

The same page also provides examples of limiting by protocol:

Thanks.  I see it now.  

What will be easier, getting the functionality to limit port number in AppArmor or moving the distro over to [Systrace](http://www.systrace.org/)?  Neither are anything I could do myself.

---

### Post by Lars Noodén on 2011-06-13
For what it's worth, I've added a feature request as [Bug #796588](https://bugs.launchpad.net/ubuntu/+source/apparmor/+bug/796588) in Launchpad.

---

