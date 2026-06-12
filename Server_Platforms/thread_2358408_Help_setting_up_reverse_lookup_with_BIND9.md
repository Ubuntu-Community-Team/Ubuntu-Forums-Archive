---
title: "Help setting up reverse lookup with BIND9"
date: 2017-04-13
forum: Server Platforms
---

### Post by jdsixtos on 2017-04-13
Hello everyone, first off, I'm still a newbie when it comes to Ubuntu. I would appreciate if someone could show me what I'm doing wrong. I have a Windows 10 machine as my main machine, and I run two VMs with VMWare, one of them is Ubuntu server, and the other is Ubuntu client. I've managed to successfully set up the DHCP server so far. I'm stuck with setting up the DNS server, I managed to get the hostname nslookup (i.e. ns1) to work correctly, however, I have NOT been able to get the nslookup 192.168.1.3 (i.e IP address) to work correctly. Here is what is currently in my settings:
named.conf.local:
```

    //The following code defines the forward lookup zone.
    zone &#8220;group2.lab&#8221; {
    type master;
    file &#8220;/etc/bind/zones/group2.lab.db&#8221;;
    };
    //The following code defines the reverse lookup zone.  
    zone &#8220;1.168.192.in-addr.arpa&#8221; {
    type master;
    file &#8220;/etc/bind/zones/rev.1.168.192.in-addr.arpa&#8221;;
    };

```
group2.lab.db:
```

    $TTL 86400
    @      IN   SOA   group2.lab. root (
        2 ; serial
        28800 ; refresh
        14400 ; retry
        3600000 ; expire
        86400 ; ttl
        )
           IN   NS    192.168.1.3.
           IN   MX    10  group2.lab.
    ns1    IN   A     192.168.1.3
    www    IN   CNAME ns1

```
rev.1.168.192.in-addr.arpa:
```

    $TTL 86400
    @           IN    SOA    group2.lab.  root (
            2009031001 ; serial
        28800 ; refresh
        14400 ; retry
        3600000 ; expire
        86400 ; ttl
        )
         IN    NS    192.168.1.3.
    1         IN    PTR   ns1.group2.lab.

```
resolv.conf:
```

    nameserver 192.168.1.3
    nameserver 8.8.8.8
    search group2.lab

```
named.conf.options:
```

forwarders {
     8.8.8.8
     8.8.4.4
}

```
hostname:
```

ubuntu

```
hosts:
```

    127.0.0.1      localhost
    127.0.1.1      ubuntu
    192.168.1.3    ns1.group2.lab ns1
    # The following lines are desirable for IPv6 capable hosts
    ::1     ip6-localhost ip6-loopback
    fe00::0 ip6-localnet
    ff00::0 ip6-mcastprefix
    ff02::1 ip6-allnodes
    ff02::2 ip6-allrouters

```
This is what I see when I attempt an nslookup:
```

    root@ubuntu:~# nslookup ns1
    Server: 192.168.1.3
    Address: 192.168.1.3#53
    Name: ns1.group2.lab
    Address:    192.168.1.3
    root@ubuntu:~# nslookup 192.168.1.3
    Server: 192.168.1.3
    Address:  192.168.1.3#53
    ** server can't find 3.1.168.192.in-addr.arpa.: NXDOMAIN

```
Does anyone have any ideas? Any help is greatly appreciated. Thank you!

---

### Post by jdsixtos on 2017-04-13
rev.1.168.192.in-addr.arpa:
```

$TTL 86400
@           IN    SOA    group2.lab.  root (
              2009031001 ; serial
          28800 ; refresh
          14400 ; retry
          3600000 ; expire
          86400 ; ttl
          )
        IN    NS    192.168.1.3.
1           IN    PTR   ns1.group2.lab.


```should be:

```

$TTL 86400
@           IN    SOA    group2.lab.  root (
              2009031001 ; serial
          28800 ; refresh
          14400 ; retry
          3600000 ; expire
          86400 ; ttl
          )
        IN    NS    192.168.1.3.
3           IN    PTR   ns1.group2.lab.


```Thanks for at least taking a look guys, after spending countless hours/days on this, I figured it out...the 1 should've been a 3 :).

---

### Post by jdsixtos on 2017-04-14
Hello again everyone,

My apologies for asking this. But it seems that with the above settings in place, I have lost Internet connection on both the Server and Client VMs. Internet was working up until just after I configured the DCHP server, I could run sudo apt-get install packageName and download successfully, as well as ping/nslookup external sites and they would resolve. However, after moving forward with the attempt to configure the DNS server, is when the Internet stopped working. I have double checked my router, DHCP is turned off, the DHCP settings are still being managed by the DHCP Server that I configured, the NICs are still set to bridged in VMWare as well. The router IP is 192.168.1.1 and my Windows 10 machine hosting the VMs is 192.168.1.2, the Server has both eth0, and eth1, eth0 has an IP of 192.168.1.4, and eth1 has an IP of 192.168.1.3.

Here is the configuration for /etc/network/interfaces:
```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.4
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1
dns-nameservers 192.168.1.3 8.8.8.8
dns-search group2.lab

auto eth1
iface eth1 inet static
address 192.168.1.3
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1
dns-nameservers 192.168.1.3 8.8.8.8
dns-search group2.lab

```

I really cannot seem to figure out what I'm doing wrong. Any help is greatly appreciated. Thanks again.

---

### Post by jdsixtos on 2017-04-19
Hello,

Is there anyone out there that could assist me with this? I still cannot seem to figure out why my server machine no longer has Internet access. I appreciate any input. Thanks!

---

### Post by wildmanne39 on 2017-04-19
*Thread moved to **Server Platforms**.*

---

### Post by SeijiSensei on 2017-04-19
You have two interfaces on the same IP subnet.  That can lead to routing problems.  Choose one interface, presumably eth0, for the 192.168.1.0/24 network and disable the other one.  Any better?

---

