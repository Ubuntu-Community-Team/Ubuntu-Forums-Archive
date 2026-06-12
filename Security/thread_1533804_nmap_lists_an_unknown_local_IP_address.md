---
title: "nmap lists an unknown local IP address"
date: 2010-07-18
forum: Security
---

### Post by bobnutfield on 2010-07-18
Hello Everyone,

I wouldn't call myself paranoid, but I do try to keep reasonably secure on my home network (WPA encryption, router firewall, etc.).  I also occasionally  use nmap to make sure I don't see any unknown computers logged into my network.  The problem is I have five computers that all use DHCP on the network and they are not all up all of the time.  At most, there are two to three online at any one time.  So, my question is:  Do any of the IP addresses remain in the router's database for a computer that has gone offline (shutdown)?

The reason for my question is that today I ran nmap on my home network and noted an IP address that was not currently up on the network.  It is, however, an address that is frequently assigned to one of the computers when it is online, but that address was not up at the time I ran nmap.  

Just trying to make sure my network is not being used by some nearby computer.

Any thoughts appreciated.

---

### Post by wacky_sung on 2010-07-18
Actually you can check through your router firmware which address is using the wire /wireless connected to it but it depend on the type of router which you are using.

---

### Post by bobnutfield on 2010-07-18
Thank you for your reply.  I did check that, and since all the computer (plus two ipod touches that use the network) use DHCP they all show up in the client list, but they are not currently running and online.  The IP address in question has been in the past assigned to an iPod, but it is currently not powered on and the IP address still shows up in nmap.

I am probably being concerned about nothing, but that is just nature.

---

### Post by cariboo on 2010-07-18
if you use:

```
sudo nmap -sP 192.168.1.0/24
```

Change the netblock to the one you use on your internal network, it will also print out the MAC addresses, just check to see if they belong to computers on your network.

---

### Post by bobnutfield on 2010-07-18
> **cariboo907 said:**
> if you use:

```
sudo nmap -sP 192.168.1.0/24
```

Change the netblock to the one you use on your internal network, it will also print out the MAC addresses, just check to see if they belong to computers on your network.

Thanks, looks like I was running nmap as normal user.  With your suggestion, it does indeed show just the computers I currently have running with the correct mac addresses.

Thank you.  I can stop looking for things that go bump in the night now.

---

### Post by The Cog on 2010-07-20
Boo!

Bear in mind that DHCP will allocate addresses more-or-less at random. If machines are left off for a while, the leases expire and the same address can then be allocated to a different machine.

I tend to configure the DHCP server for permanent MAC/IP mappings for most machines in our house, mostly so I know what address to SSH to when I want to go to other machines than the one in front of me.

---

