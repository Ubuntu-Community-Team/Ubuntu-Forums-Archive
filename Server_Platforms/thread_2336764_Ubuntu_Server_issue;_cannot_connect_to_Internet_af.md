---
title: "Ubuntu Server issue; cannot connect to Internet after installation/setup"
date: 2016-09-11
forum: Server Platforms
---

### Post by orangesoda-mr on 2016-09-11
I'm new to this so please excuse my ignorance. I installed and finished setting up my Ubuntu server (version 16.04.1), but I cannot connect to the internet via ping google.org. 


This is the info that I have right now: 


**resolv.conf file: **
```
    nameserver 8.8.4.4
    nameserver 8.8.8.8

```

**/etc/network/interfaces file:     **
```
auto eno2 
iface eno2 inet static 
    address 108.241.254.193
    netmask 255.255.255.248
    gateway 192.168.0.1

```


[B]The ifconfig file is attached as a photo. 
[http://i.imgur.com/X8cpULW.jpg](http://i.imgur.com/X8cpULW.jpg)

**This is the information I was given to input as connection data for the server: **
```
    Public IPv4 address
        108.241.254.198
    Public Subnet Mask 
        255.255.255.248
    Start Address
        108.241.254.193
    End Address
        108.241.254.197
    IP From (On Order)
        108.241.254.192

```

All help is greatly appreciated.

---

### Post by darkod on 2016-09-11
The gateway can't be 192.168.0.1. Usually for a public range it would be a public IP too. The 192.168.x.x are private range IPs and usually unroutable on the internet.

Plus, the range that they seem to have assigned you is 108.241.254.193-108.241.254.197. You can't use .198 like on the screenshot above.

I would suggest to contact the provider and ask which IP from that range you should use as gateway. Only that part is missing. And you only use .193 to .197 on your server(s). Of course if the gateway is one of those IPs you can't use it for the server too, you need to avoid it.

PS. Looking again in that info they gave you, it looks to me like .198 is the gateway so try something like this for the settings:
```
address 108.241.254.193
netmask 255.255.255.248
gateway 108.241.254.198
dns-nameservers 8.8.8.8 8.8.4.4
```

Give it a shot and if doesn't work ask the provider to give you exactly what the gateway needs to be.

---

### Post by orangesoda-mr on 2016-09-11
I tried as you suggested, which is also what I was told by my ISP, to no avail. Any other ideas on what's keeping me from connecting to the Internet? 

NOTE: I also found out the LAN port where the Ethernet cable that connects the server with the Uverse box is giving out a solid orange light, which according to the ISP means the Uverse is reading the connection but is not communicating with the device (server).

---

### Post by darkod on 2016-09-11
What's a Uverse box? If that is a kind of a router that does NAT, you would configure private range on your server behind it, not public. But the ISP would have told you that too.

Unfortunately if this doesn't work they are the only ones that can help you because we don't know the setup of how you are supposed to access the internet at all.

The only other thing you can do is try another network cable in case this one is faulty.

---

### Post by orangesoda-mr on 2016-09-11
Yes, Uverse is the router provided to us with AT&T.

---

### Post by darkod on 2016-09-11
So, together with this router you get 5-6 public IPs? Usually the router has a single public IP assigned by the ISP and on it's private port it has dhcp private range for all clients in your home. That way they cover many clients with single public IP.

In such case the gateway can really be 192.168.0.1 or 192.168.1.1 depending which is the private IP assigned to its internal interface. But to servers behind the router you would have to assign 192.168.0.2-192.168.0.254 range, not a public IP. It all depends what kind of service precisely have you bought from them.

---

