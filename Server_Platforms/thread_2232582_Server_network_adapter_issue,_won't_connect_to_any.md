---
title: "Server network adapter issue, won't connect to *anything*"
date: 2014-07-02
forum: Server Platforms
---

### Post by daniel_roop2 on 2014-07-02
I run an ubuntu 14.04 server for mostly games but have an apache server running on it aswell. With a clean install the machine works perfectly and is usable untill it is shut off and turned on again because the IP is not static, i tried to set it static and it deleted the network adapter in the ifconfig list, then i tried to set it back to how it was, and it does nothing... Without this working adapter(or assumed adapter issue) i cannot connect to the internet or even my own network to ssh from my windows machine.

In my /etc/network/interfaces i have written the text i found in it originally before i altered it after the static settings didnt work, it says:
```
#This file describes the network interfaces available on your system
and how to activate them. For more information, see interfaces(5)

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto p5p1
iface p5p1 inet dhcp
```
I wrote this down before i even altered anything then put it right back in, and now nothing will work and the only i found out to fix it is to do a clean install and reconfigure everything... something that i do not want to do again after my first time.

The only thing that shows up in ifconfig is the 'lo'

---

### Post by nerdtron on 2014-07-03
What is the output of "ifconfig -a"?
Also have you tried "sudo ifup p5p1"? Is there an error? Post it here.


EDIT: You said you post it back??

```
#This file describes the network interfaces available on your system and how to activate them. For more information, see interfaces(5)
```

Be sure the this is a single line or that you have commented the second line like this:

```
#This file describes the network interfaces available on your system
#and how to activate them. For more information, see interfaces(5)
```

---

