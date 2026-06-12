---
title: "assign a /24 subnet to one network interface"
date: 2006-05-23
forum: Server Platforms
---

### Post by dimacali on 2006-05-23
I installed ubuntu server and configured apache and all the services I need.  Now I need to assign a whole (well, not xxx.xxx.xxx.1 as I will use that for the gateway) /24 subnet starting from the .2 ip address.  In Redhat, we defined this by using a ifcfg-eth*X*-range*X* file in the network-scripts folder.  Is there an equivalent procedure in ubuntu?

---

### Post by Azrael on 2006-05-23
You can specify a netmask in the /etc/network/interfaces file. Or if you just want to make a temporary change you can use the *ifconfig*, *route* or *ip* command. See the man pages for more information.

---

### Post by dimacali on 2006-05-23
[QUOTE=Azrael]You can specify a netmask in the /etc/network/interfaces file. Or if you just want to make a temporary change you can use the *ifconfig*, *route* or *ip* command. See the man pages for more information.[/QUOTE]
Sorry if I sound clueless, it's maybe because I am.:) 

Lets say for example I have this in my interfaces file right now:

[INDENT][FONT="Courier New"]auto eth0
iface eth0 inet static
        address 192.168.12.2
        netmask 255.255.255.0
        network 192.168.12.0
        broadcast 192.168.12.255
        gateway 192.168.12.1[/FONT][/INDENT]

How or what should I change so that anyone pinging an ip address from 192.168.12.2 to 192.168.12.254 would be able to hit my box?

Thanks in advance.

---

### Post by Azrael on 2006-05-23
You don't need to change anything as far as I can see. Your example looks fine as it is. Can't others ping you?

---

### Post by dimacali on 2006-05-23
[QUOTE=Azrael]You don't need to change anything as far as I can see. Your example looks fine as it is. Can't others ping you?[/QUOTE]
They can ping 192.168.12.2 fine but not the other ip addresses (.3 through .254).  I know the switch forwarding the whole /24 to the correct port and I am sure no other machines are using any of the other ip addresses, what could I be doing wrong?

I hope I wouldn't have to resort to doing

[INDENT][FONT="Courier New"]auto eth0
iface eth0 inet static
address 192.168.12.2
netmask 255.255.255.0
network 192.168.12.0
broadcast 192.168.12.255
gateway 192.168.12.1
auto eth0:0
iface eth0 inet static
address 192.168.12.3
netmask 255.255.255.0
network 192.168.12.0
broadcast 192.168.12.255
gateway 192.168.12.1
auto eth0:1
iface eth0 inet static
address 192.168.12.4
netmask 255.255.255.0
network 192.168.12.0
broadcast 192.168.12.255
gateway 192.168.12.1
etc....[/FONT][/INDENT]

Thanks for the response, I really appreciate it.

---

