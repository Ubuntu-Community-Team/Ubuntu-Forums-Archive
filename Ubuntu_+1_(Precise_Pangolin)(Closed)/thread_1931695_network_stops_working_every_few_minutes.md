---
title: "network stops working every few minutes"
date: 2012-02-26
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by TDK800 on 2012-02-26
Network works great, then either after a few minutes or a dozen page visits, it stops working. 

Network information shows everything is working correctly.

When I do a network restart it starts working again, so currently I have to restart the network every few minutes.

I have static network configuration in /etc/network/interfaces and network manager has resolv.conf using nameserver 127.0.0.1

Any ideas how to troubleshoot this?

Edit: doesn't seem to be web browser related, just stops working after a few minutes.

---

### Post by sanderj on 2012-02-26
"nameserver 127.0.0.1" in resolv.conf? That is strange; nameserver should be some remote system: your router/modem, or your ISP's DNS. 
Unless ... you have done non-standard, complicated things like installing a nameserver on your local system.

To monitor the network, open a terminal, and type "ping -n 8.8.8.8". Keep it running all the the time. What does it show normally? And what when your network is down?

```

sander@R540:~$ ping -n 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_req=1 ttl=56 time=24.2 ms
64 bytes from 8.8.8.8: icmp_req=2 ttl=56 time=24.5 ms
64 bytes from 8.8.8.8: icmp_req=3 ttl=56 time=24.5 ms
64 bytes from 8.8.8.8: icmp_req=4 ttl=56 time=25.1 ms
64 bytes from 8.8.8.8: icmp_req=5 ttl=56 time=24.8 ms
64 bytes from 8.8.8.8: icmp_req=6 ttl=56 time=24.5 ms



```


EDIT:

I opened my plain 12.04 alpha in VirtualBox, and indeed it has 127.0.0.1 as nameserver in resolv.conf. So please ignore my comment about that.

---

### Post by lucazade on 2012-02-26
> **sanderj said:**
> "nameserver 127.0.0.1" in resolv.conf? That is strange; nameserver should be some remote system: your router/modem, or your ISP's DNS. 
Unless ... you have done non-standard, complicated things like installing a nameserver on your local system.

To monitor the network, open a terminal, and type "ping -n 8.8.8.8". Keep it running all the the time. What does it show normally? And what when your network is down?

```

sander@R540:~$ ping -n 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_req=1 ttl=56 time=24.2 ms
64 bytes from 8.8.8.8: icmp_req=2 ttl=56 time=24.5 ms
64 bytes from 8.8.8.8: icmp_req=3 ttl=56 time=24.5 ms
64 bytes from 8.8.8.8: icmp_req=4 ttl=56 time=25.1 ms
64 bytes from 8.8.8.8: icmp_req=5 ttl=56 time=24.8 ms
64 bytes from 8.8.8.8: icmp_req=6 ttl=56 time=24.5 ms



```

DNS support in Precise is different from old releases because it now allows to use  specific nameserver for each connection. This is useful especially if connected to more than a network at the same time, i.e. wired or wireless and to a VPN.
So I believe that 127.0.0.1 is correct in resolv.conf

[http://www.ubuntugeek.com/ubuntu-12-04-precise-pangolin-alpha-2-released.html](http://www.ubuntugeek.com/ubuntu-12-04-precise-pangolin-alpha-2-released.html)
"DNS resolution is now done through dnsmasq, which should help split-DNS VPNs and faster DNS resolution."

---

### Post by effenberg0x0 on 2012-02-26
If you have a static connection set manually at /etc/network/interfaces/ and /etc/resolv.conf, eth0 should not be managed by network-manager. In this case, I would advice you to simply remove it. 
```
sudo apt-get remove network-manager network-manager-gnome

```
And then you shouldn't need resolfconf too. And if dnsmasq is installed, you probably don't need it or you would have mentioned it.
```
sudo apt-get remove resolvconf dnsmasq

```
But if you setup the static connection **via network-manager**, than eth0 **is** managed by network-manager, and no matter what you set as your nameservers, it will randomly overwrites it. (Which is pointless IMO for those that use a static connection).

About DNSs, you want something like this, for example:
```

sudo nano /etc/resolv.conf
nameserver 208.67.222.222
nameserver 208.67.220.220
nameserver 8.8.8.8
```
Press Ctrl+X, Y and Enter

However, if none of this fixes the problem, you should check your logs to see if your NIC is going Up/Down and Ready/Not Ready too often, which is characteristic of some poorly supported NICs.

```
grep -i "eth" /var/log/dmesg
```

Regards,
Effenberg

---

### Post by lucazade on 2012-02-26
I'd just add to Effenberg notes also to check for corrupted/malformed network packets with 'ifconfig'

---

### Post by dino99 on 2012-02-26
more details:  [http://www.stgraber.org/2012/02/24/dns-in-ubuntu-12-04/](http://www.stgraber.org/2012/02/24/dns-in-ubuntu-12-04/)

---

### Post by TDK800 on 2012-02-26
> **dino99 said:**
> more details:  [http://www.stgraber.org/2012/02/24/dns-in-ubuntu-12-04/](http://www.stgraber.org/2012/02/24/dns-in-ubuntu-12-04/)

nm-tool helped solve the issue:

Initial Problem: interfaces file was set to use eth2 which wasn't detecting the wired network (though net was working) and was overwriting the resolv.conf on every reboot, cleaning out the ISPs nameserver, so had to manually change it on startup and restart network.


New Problem: I switched interfaces file to use eth1, which detected the wired connection and didn't overwrite the resolv.conf, but that started causing the connection stop working after every few minutes.


Solution: nm-tool showed wired conenction was on eth2, so switched interfaces file back to eth2. This time also added "dns-nameservers" line with the ISPs nameserver to the interfaces file. The correct nameserver is now in resolv.conf and everything works. Though "Connection Information" says no active connections found.

---

