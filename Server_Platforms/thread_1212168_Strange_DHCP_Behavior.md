---
title: "Strange DHCP Behavior"
date: 2009-07-13
forum: Server Platforms
---

### Post by joan.domenech on 2009-07-13
Hello all

I installed a clean Ubuntu Server 9.04 (64 bits) on a machine with 2 NICs. I tried a lot of configurations I found on this forum and google, but still no luck. I tried with only one NIC, etc 

The problem I have is that when I start the dhcpd it seems to start ok but on the /var/log/daemon.log I can't see the listening message and it doesn't lease new addresses.

I attach the configurations files just in case someone can help me.


/etc/dhcp3/dhcpd.conf
```

ddns-update-style none;
authoritative;

subnet 84.88.159.0 netmask 255.255.255.0 {
   
        range 84.88.159.2 84.88.159.254;
        option subnet-mask 255.255.255.0;
        option domain-name "udg.edu";
        option domain-name-servers 84.88.128.2, 84.88.128.3;
        option routers 84.88.159.1;
        option broadcast-address 84.88.159.255;
 
#       2592000 seconds = 30 days
        default-lease-time 2592000;

        get-lease-hostnames          on;
        use-host-decl-names          on;


        host FME00001 { hardware ethernet 00:22:41:25:6a:06; fixed-address 84.88.159.14; }
        host FME00005 { hardware ethernet 00:1e:8c:eb:e2:3b; fixed-address 84.88.159.18; }
}

subnet 192.168.0.0 netmask 255.255.255.0 {
        range 192.168.0.2 192.168.0.254;
        option subnet-mask 255.255.255.0;
        option routers 192.168.0.1;

        default-lease-time 600;
}
```


/etc/default/dhcp3-server
```
INTERFACES="eth0 eth1"
```

/var/log/daemon.log (result after starting service)
```
Jul 13 18:35:15 fm dhcpd: Internet Systems Consortium DHCP Server V3.1.1
Jul 13 18:35:15 fm dhcpd: Copyright 2004-2008 Internet Systems Consortium.
Jul 13 18:35:15 fm dhcpd: All rights reserved.
Jul 13 18:35:15 fm dhcpd: For info, please visit http://www.isc.org/sw/dhcp/
Jul 13 18:35:17 fm dhcpd: Internet Systems Consortium DHCP Server V3.1.1
Jul 13 18:35:17 fm dhcpd: Copyright 2004-2008 Internet Systems Consortium.
Jul 13 18:35:17 fm dhcpd: All rights reserved.
Jul 13 18:35:17 fm dhcpd: For info, please visit http://www.isc.org/sw/dhcp/
Jul 13 18:35:17 fm dhcpd: Wrote 0 leases to leases file.
```


I think after the last line I should get something like that if I'm not wrong

```
Listening on LPF/eth0/00:1e:8c:a5:ce:53/84.88.159/24
Sending on   LPF/eth0/00:1e:8c:a5:ce:53/84.88.159/24
Listening on LPF/eth1/00:04:75:d6:c5:06/192.168.0/24
Sending on   LPF/eth1/00:04:75:d6:c5:06/192.168.0/24
```

Does anyone have any idea of what I'm doing wrong? I searched a lot and I can't find a solution. Some help will be some light on this darkness ;)

Thanks in advance

---

### Post by koenn on 2009-07-13
The Listening/sending thing is awhat you see on the clients, not on the server. Your server log should show something like

```

Jul 13 20:06:37 xinix dnsmasq[2000]: DHCPDISCOVER(eth0) 192.168.1.251 00:50:04:35:38:32 
Jul 13 20:06:37 xinix dnsmasq[2000]: DHCPOFFER(eth0) 192.168.1.251 00:50:04:35:38:32 
Jul 13 20:06:37 xinix dnsmasq[2000]: DHCPREQUEST(eth0) 192.168.1.251 00:50:04:35:38:32  
Jul 13 20:06:37 xinix dnsmasq[2000]: DHCPACK(eth0) 192.168.1.251 00:50:04:35:38:32 

```
but only if you actually have clients requesting a dhcp lease

---

### Post by joan.domenech on 2009-07-14
Ok thanks for information I was little confused about it.

But the problem still remains. When the clients connect I don't see any request on the DHCP server log and the IP I get is from subnetwork 169.254.241.0 and netmask 255.255.0.0

I'm completely lost I don't know where or what else to try.

Any help will be helpful

Thanks in advance

---

### Post by koenn on 2009-07-14
> 169.254.241.0 and netmask 255.255.0.0
that's an autoconfig ip address, your computer assigns itself this address, by lack of anything else.

You may have a link problem (network cable not plugged in or broken, faulty network card, broken switch in between ...)

What happens if you manually configure a client and try to get something going between this client and the server (anything : ping, traceroute,  ... )

---

### Post by joan.domenech on 2009-07-16
Hi koenn

Thanks for the answers and help. I think I solved it. on my organitzation there's a corporate Firewall that blocks the DHCP traffic. Because with a crossed ethernet cable it worked.

I'll ask them to solve that situation.

Thanks for ur help.

Joan

---

### Post by koenn on 2009-07-16
I'm not quite sure I understand how you have things layed out, but if you got it working with a crosslink cable, at least we can be reasnoably sure it was a connectivity problem, and your dhcp setup was sound. 

> **joan.domenech said:**
> 
Thanks for ur help.

no problem.

---

