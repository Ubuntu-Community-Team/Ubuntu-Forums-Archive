---
title: "overwriting resolv.conf"
date: 2010-05-03
forum: Server Platforms
---

### Post by leg on 2010-05-03
I have recently upgraded to 10.4 and now my resolv.conf file is getting overwritten on start up. I have had this before and I think it is because I am getting my ip address dynamically from my router. The dhcp client is the process that is overwriting if I remember correctly. What I can't remember is how to correct the problem. I need to be able to set the nameserver to an address other than the routers and I can't remember how.

---

### Post by windependence on 2010-05-03
If this is a server, why would you have it set for DHCP? Are you saying you want to know how to set a static IP? Here is an example:

Change your /etc/network/interfaces to look similar to this but with your own IP information:

```
auto eth0
iface eth0 inet static
        address 192.168.1.100
         netmask 255.255.255.0
        network 192.168.1.0
         broadcast 192.168.1.255
        gateway 192.168.1.1
```

-Tim

---

### Post by leg on 2010-05-03
No it is my laptop which is receiving a dynamic ip address and to be honest that bit is fine but using dhcpclient overwrites my resolv.conf file which I need to set to the nameservers of my router otherwise Firefox doesn't work. 

Basically at the moment resolv.conf has a line ```
nameserver 192.168.1.1
``` and I have to set it to ```
nameserver 212.74.112.66
``` each session as it gets overwritten. I need to know which config files of dhcpclient to alter so that resolv.conf gets overwritten with the correct address. Sorry if I wasn't clear in my last post.

---

### Post by HermanAB on 2010-05-03
Howdy, 

The correct solution is to configure your DHCP server properly.  The bad information in resolv.conf is a symptom, not the problem.

---

### Post by Tommetje on 2010-05-03
Well, it could be fine that your DHCP server hands out the IP address for a DNS server. If it's only on that laptop that you need a different DNS server, configure your DHCP client program (dhclient) on the laptop not to use the IP address of the DNS server given to you by the DHCP server.

---

### Post by leg on 2010-05-04
> **Tommetje said:**
> Well, it could be fine that your DHCP server hands out the IP address for a DNS server. If it's only on that laptop that you need a different DNS server, configure your DHCP client program (dhclient) on the laptop not to use the IP address of the DNS server given to you by the DHCP server.That's what I have done before and can't remember how to do. My router hands out my ip addresses but the dns server is from my provider. my router is the 192. address and it has its dns server set as the other one. Networking is fine at the os level i.e I can ping and all that but apps seem to be confused. If I have the 212 ip in resolv it all works and I know that some config of dhclient is how I can do this. I will investigate I think.

---

### Post by ICEB3AR on 2010-05-04
[http://ubuntuforums.org/showthread.php?t=1396703](http://ubuntuforums.org/showthread.php?t=1396703)

---

### Post by leg on 2010-05-04
> **ICEB3AR said:**
> [http://ubuntuforums.org/showthread.php?t=1396703](http://ubuntuforums.org/showthread.php?t=1396703)That looks like it I think.

---

