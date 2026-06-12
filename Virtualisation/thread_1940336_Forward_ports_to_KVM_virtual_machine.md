---
title: "Forward ports to KVM virtual machine"
date: 2012-03-13
forum: Virtualisation
---

### Post by iarspider on 2012-03-13
Host machine: Ubuntu 11.04 GNU/Linux 2.6.38-13-server x86_64, KVM 1:84+dfsg-0ubuntu16+0.14.0+noroms+0ubuntu4.5, iptables v1.4.10. It have an external IP address. 

It runs a guest (Ubuntu Lucid), which has internal (host-only) IP address 192.168.122.209. This guest is running a bunch of services (ports) that I need to make visible to the outside world. I can't assign it a public IP - getting one is too damn hard. And I don't want to mess with IPv6 - it is not widespread enough yet, and I don't have time to explain people how to set it up.

So, I have followed [this](https://help.ubuntu.com/community/KVM/Networking#Redirecting_selected_ports_to_virtual_machines) tutorial, but all I get is "connection timed out". 

The guest is configured to accept all connections. Here are the iptables rules for the host:
```

# iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination
fail2ban-ssh  tcp  --  anywhere             anywhere            multiport dports ssh
ACCEPT     udp  --  anywhere             anywhere            udp dpt:domain
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:domain
ACCEPT     udp  --  anywhere             anywhere            udp dpt:bootps
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:bootps

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination
ACCEPT     all  --  anywhere             192.168.122.0/24    state RELATED,ESTABLISHED
ACCEPT     all  --  192.168.122.0/24     anywhere
ACCEPT     all  --  anywhere             anywhere
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

Chain fail2ban-ssh (1 references)
target     prot opt source               destination
RETURN     all  --  anywhere             anywhere

#iptables -t nat -L
Chain PREROUTING (policy ACCEPT)
target     prot opt source               destination
DNAT       tcp  --  anywhere             myserver     tcp dpt:8122 to:192.168.122.209:22
DNAT       tcp  --  anywhere             myserver     tcp dpt:http-alt to:192.168.122.209:80
DNAT       tcp  --  anywhere             myserver     tcp dpt:8443 to:192.168.122.209:443
DNAT       tcp  --  anywhere             myserver     tcp dpt:12320 to:192.168.122.209:12320
DNAT       tcp  --  anywhere             myserver     tcp dpt:12321 to:192.168.122.209:12321
DNAT       tcp  --  anywhere             myserver     tcp dpt:git to:192.168.122.209:9418

Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

Chain POSTROUTING (policy ACCEPT)
target     prot opt source               destination
MASQUERADE  tcp  --  192.168.122.0/24    !192.168.122.0/24    masq ports: 1024-65535
MASQUERADE  udp  --  192.168.122.0/24    !192.168.122.0/24    masq ports: 1024-65535
MASQUERADE  all  --  192.168.122.0/24    !192.168.122.0/24

```

I have enabled ipv4 forwarding.

---

