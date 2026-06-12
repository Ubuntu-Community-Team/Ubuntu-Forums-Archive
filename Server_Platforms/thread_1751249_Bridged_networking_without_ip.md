---
title: "Bridged networking without ip"
date: 2011-05-06
forum: Server Platforms
---

### Post by Marvin on 2011-05-06
Hello,

Everything works as I want it to but I have a potential security question.
I setup a bunch of virtual machines with a following network setup

internet ---- br0{virtual machines}br1---- intranet

br0 is set up like this:

```
auto br0
iface br0 inet manual
 bridge_ports	eth0
 bridge_stp	off
 bridge_maxwait 5
```

as you can see there is no ip addresses given to br0 which is connected
to the internet. br1 does have an ip address.

The br0 interface does not have any kind of firewall or filtering.
Can anyone see br0 being totally open as a potential security issue even tough it has no ip address and if so why?

---

### Post by YesWeCan on 2011-05-06
What does 'ifconfig' say about IP addresses?

---

### Post by Marvin on 2011-05-06
No ip addresses are shown in ifconfig for either eth0 or br0. ipv6 is disabled.
I think everything should be ok, but I have this nagging feeling that I might have forgotten to consider some security aspect.

Probably just paranoia.

---

