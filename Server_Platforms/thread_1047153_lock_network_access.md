---
title: "lock network access"
date: 2009-01-22
forum: Server Platforms
---

### Post by fouadk on 2009-01-22
hi everyone...

i have an ubuntu server that is serving dns and dhcp...

my question is the following, is there is a way to make only computer with specific mac address get DNS and DHCp from that server ?

please help.
thanks in advance

---

### Post by cdenley on 2009-01-22
> **fouadk said:**
> hi everyone...

i have an ubuntu server that is serving dns and dhcp...

my question is the following, is there is a way to make only computer with specific mac address get DNS and DHCp from that server ?

please help.
thanks in advance

For dhcp, you can remove the IP range from your configuration, then configure a fixed IP for each host you want to allow.
```

subnet 192.168.0.0 netmask 255.255.255.0 {
   option domain-name-servers 208.67.222.222,208.67.220.220;
   option routers 192.168.0.1;
   option broadcast-address 192.168.0.255;
}
host myhost {
   hardware ethernet xx:xx:xx:xx:xx:xx;
   fixed-address 192.168.0.2;
}

```
For either one, you can simply use iptables to filter the incoming traffic by mac address. Keep in mind that your users can always assign themselves a static IP and specify an external DNS server.

---

### Post by fouadk on 2009-01-22
isn't there any other way to go over users assigning a static ip and getting dns from an external server,....

the thing is that i dont wat users with laptops to disconnect destops to plug their laptop, they should use wireless instead.

---

### Post by cdenley on 2009-01-22
I installed a linux computer as a bridge between the router and switched network to filter based on MAC address. Unless it has a whitelisted MAC address, any computer on the LAN cannot reach the router. You would have to filter all network traffic to control your network effectively, and even then users can spoof the mac on their laptop for any given desktop computer which has been whitelisted.

---

### Post by fouadk on 2009-01-22
do u have any idea where i can find a good tutorial for what u did ?

---

### Post by cdenley on 2009-01-22
> **fouadk said:**
> do u have any idea where i can find a good tutorial for what u did ?

Not really, what I did was kind of complicated. This might point you in the right direction, though.
[https://help.ubuntu.com/community/NetworkMonitoringBridge](https://help.ubuntu.com/community/NetworkMonitoringBridge)
Just combine that with iptables rules. I think you can use the FORWARD chain in iptables, or PREROUTING in the "nat" table if you want to DNAT or redirect traffic instead of dropping it.

---

### Post by cdtech on 2009-01-22
Yes, this is a dhcpd.conf issue. You'll need to look at how to create classes, pools and how to evaluate the hardware string to extract part of the mac address.
```
class "my-hosts" {
        match if substring (option hardware,0,10) = "00:1a:73:b5";
}

pool {
        range 192.168.1.100 192.168.1.150;
        allow members of "my-hosts";
}
```
Hope this puts you in the right direction......

---

