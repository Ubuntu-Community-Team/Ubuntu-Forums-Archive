---
title: "dhcp problems"
date: 2010-04-29
forum: Server Platforms
---

### Post by Drenriza on 2010-04-29
i have set up an dhcp service on my server.

Problem, it does not lease any dhcp addresses. And i cannot see any device requesting it either.

```
auto eth1

iface eth1 inet static
address 192.168.1.1
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1

```

```
default-lease-time 600;
    max-lease-time 7200;

    option subnet-mask 255.255.255.0;
    option broadcast-address 192.168.1.255;
    option routers 192.168.1.254;
    option domain-name-servers 192.168.1.1, 192.168.1.2;
    option domain-name "mm.dk";

    subnet 192.168.1.0 netmask 255.255.255.0 {
    range 192.168.1.2 192.168.1.200;
    }

```

```
INTERFACES="eth1
```

What went wrong.
This is for a local network only.

---

### Post by ICEB3AR on 2010-04-29
First question: 
Why is eth1 it's own gateway ?
> iface eth1 inet static
address 192.168.1.1
...
gateway 192.168.1.1

Second: are there any error-messages?
The dhcpd.conf looks okay and i believe, that you made a mistake in copying the INTERFACES and that there really is:
```
INTERFACES="eth1"
```
Which shoudl also be right.

---

### Post by terazen on 2010-04-29
You have your router set to 192.168.1.254 in dhcp and 192.168.1.1 on your server.  Fix that and verify that your dhcp server can ping all of the subnets on your network.

Also, you have 192.168.1.2 as a dns server and it's also in your dhcp range.  I assume your dns server has a static ip address and this is a typo?

---

### Post by Drenriza on 2010-05-03
The "goal" with this. Is that i have 1 device, that needs to get an dhcp address. The device did have an static address, but doesn't anymore and does not have a management port.

I have changed a little settings, and hope these are better.

auto eth1

iface eth1 inet static
address 192.168.1.1
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
#gateway 192.168.1.1

I dont need the gateway since i dont need anything besides my pc and the device (directly connected) to be the only ones talking with eachother. Nothing outside of that "bubble".

default-lease-time 600;
    max-lease-time 7200;

    option subnet-mask 255.255.255.0;
    option broadcast-address 192.168.1.255;
    option routers 192.168.1.201;
    option domain-name-servers 192.168.1.1;
    option domain-name "2M.dk";

    subnet 192.168.1.0 netmask 255.255.255.0 {
    range 192.168.1.10 192.168.1.200;
    }

Changed the range, to avoid conflicts. Hope this is alright. Im not rly used to linux dhcp services.

---

### Post by bab1 on 2010-05-03
> **Drenriza said:**
> i have set up an dhcp service on my server.

Problem, it does not lease any dhcp addresses. And i cannot see any device requesting it either.

...

What went wrong.
This is for a local network only.

I assume the only interface is eh1 and that you have configured it from the /etc/network/interfaces file as below:```
auto eth1
iface eth1 inet static
address 192.168.1.1
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
#gateway 192.168.1.1
```

The first line is there [COLOR="Red"]***to bring up the interface automatically upon boot***[/COLOR].  **It has nothing to do with DHCP**. It should be there as```
auto eth1

``` 

The second line is for DHCP and the correct entry is ```
iface eth1 inet dhcp
```

Everything else can be removed.  The dhcp server can be configured to supply the information for netmask, broadcast and gateway.

See [**_here _**]("http://www.cyberciti.biz/faq/setting-up-an-network-interfaces-file/")for more information.

The entire entry for eth1 should be:```
auto eth1
iface eth1 inet dhcp
```

---

### Post by Drenriza on 2010-05-03
thanks bab1 that worked like a charm

---

