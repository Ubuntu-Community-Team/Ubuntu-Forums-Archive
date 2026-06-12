---
title: "How to retrieve mac adress from SSH logs ?"
date: 2012-04-25
forum: Server Platforms
---

### Post by rastaflips on 2012-04-25
Hi,

my laptop has been stolen and I wish to retrieve my the MAC address of my WIFI card.

I used to connect to a Ubuntu server using SSH.

Is it possible to retrieve my MAC address on the server side ? I have root access on that server.

I'm also trying to find it in router's logs I have connected to.

Thanks.

---

### Post by Habitual on 2012-04-25
> **rastaflips said:**
> ...Is it possible to retrieve my MAC address on the server side ? I have root access on that server....

Maybe arp cached it on the server?

```
man arp
```

HTH.

---

### Post by Jonathan L on 2012-04-25
Hi rastaflips

Sorry to hear that.

> retrieve my the MAC address of my WIFI card.
I used to connect to a Ubuntu server using SSH.
There's no reason for an SSH server to know anything at all about the ethernet details of its clients, unless they were on the same LAN, in which case it would be in the ARP cache and possibly elsewhere. However, ARP cache timeouts are quick: last one I timed was 40 minutes, some are 2 minutes.

Wifi MAC addresses are a LAN issue, so ... your DHCP server will definitely know the ether address.  If by chance your Ubuntu server is your DHCP server you'll still, almost certainly, have the details in /var/lib/dhcp3/dhcpd.leases
```
lease 192.168.1.227 {
  starts 2 2011/12/13 10:40:54;
  ends 2 2011/12/13 12:40:54;
  tstp 2 2011/12/13 12:40:54;
  cltt 2 2011/12/13 10:40:54;
  binding state free;
  hardware ethernet 11:22:33:44:55:66;
}
```If you use DHCP on your router, take a look at that.  But hurry before any caches expire.

Also, of course, you might have some TCPDUMP traces somewhere?

I hope that helps.

Kind regards,
Jonathan.

---

