---
title: "DHCP Server Reservations"
date: 2012-11-06
forum: Server Platforms
---

### Post by MartinChir on 2012-11-06
I'm slowly trying to replace most if not all Windows services with a Linux server and I'm up to DHCP

The way our Windows DHCP server is set up is we have a pool of 254 addresses and within those addresses reservations are added as necessary, currently there are over 100 reservations



The issue I am anticipating is that the dhcpd.conf file states fixed ip addresses should not be in the dynamic pool


Can I create reservations for IP addresses that are in my dynamic pool?

---

### Post by papibe on 2012-11-06
Hi MartinChir.

I wouldn't recommend keeping that design, and I would see this as a opportunity to tight things up.

**However**, if you have to keep that structure, you can cheat a little and have holes in the dynamic range. Actually, what you set is several ranges that leave 'space' for your reservations.

Let's say you have the following reservations:
```
192.168.1.50
192.168.1.100
192.168.1.200
```
You can set something like this:
```
subnet 192.168.1.0 netmask 255.255.255.0
{
    option routers 192.168.1.1;
    option broadcast-address 192.168.1.255;

[B]    range 192.168.1.2   192.168.1.49;
    range 192.168.1.51  192.168.1.99;
    range 192.168.1.101 192.168.1.199;[/B]
}
```
(leaving more reservations available on the range 200+)

I hope that helps. Let us know how it goes.
Regards.

---

### Post by MartinChir on 2012-11-06
> **papibe said:**
> Hi MartinChir.
I wouldn't recommend keeping that design, and I would see this as a opportunity to tight things up.
Regards.
Seems to be the wrong way to create reservations I'm learning however the previous admin for some reason set the network to a /24 mask so I only have 254 addresses to assign and guess what? We only need a single subnet too...makes it hard to create a dynamic upper/lower range

The main issue I have in "fixing" the IP addressing is that we have a lot of static devices such as IP cameras and serial servers that have work load most of the day including weekends

I think I will take your advise and create a few small pools, thanks

---

### Post by bab1 on 2012-11-06
> **MartinChir said:**
> Seems to be the wrong way to create reservations I'm learning however the previous admin for some reason set the network to a /24 mask so I only have 254 addresses to assign and guess what? We only need a single subnet too...makes it hard to create a dynamic upper/lower range

The main issue I have in "fixing" the IP addressing is that we have a lot of static devices such as IP cameras and serial servers that have work load most of the day including weekends

I think I will take your advise and create a few small pools, thanks
Both *reserved *and *dhcp pool* addresses use *dynamic *IP addressing (e.g. DHCP).  Static IP addressing does not use addresses from the DHCP pool.  Don't confuse static IP addressing with reserved IP addresses.  They are different.

---

### Post by SeijiSensei on 2012-11-06
> **MartinChir said:**
> The main issue I have in "fixing" the IP addressing is that we have a lot of static devices such as IP cameras and serial servers that have work load most of the day including weekends

You can assign fixed IPs by MAC addresses like this:

```

host joe {
        hardware ethernet 08:00:2b:4c:29:32;
        fixed-address joe.fugue.com;
        option host-name "joe";
      }

```

(This is the example in the man page for dhcpd.conf.)

If it's not easy to determine a device's MAC address, you can run "tail -f /var/log/syslog" on the server then start the device.  You'll see its MAC address appear in the log when it requests an address.

---

