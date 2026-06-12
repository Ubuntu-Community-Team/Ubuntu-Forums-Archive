---
title: "Need to use Static IP"
date: 2009-10-29
forum: Server Platforms
---

### Post by Vegan on 2009-10-29
I need to have my machine use a static IP, upgrading distribution so it will be a moment till its done.

This way I do not have to change port forwarding all the time, unless there some uPNP available.

---

### Post by kevin11951 on 2009-10-29
> **Vegan said:**
> I need to have my machine use a static IP, upgrading distribution so it will be a moment till its done.

This way I do not have to change port forwarding all the time, unless there some uPNP available.

I am not sure what you want, but to setup a static ip,

```
nano /etc/network/interfaces
```

and find the line "auto eth0" and remove everything under it.  add this under it:
```
iface eth0 inet static
address <ip address>
netmask <netmask>
gateway <gateway>
```

---

### Post by Vegan on 2009-10-29
Thanks, now I have it safe from power outages. If the Linksys box goes off, all ip addresses are reassigned as they reboot.

Static avoids the problem.

---

### Post by lisati on 2009-10-29
I generally set my Netgear router to assign specific IP addresses to specific machines (i.e. MAC addresses) - that's its job, not the computer's. It also has the advantage of helping track down the offending machine if a spam report comes in.

---

### Post by Vegan on 2009-10-30
I am ok with assigned IP addresses, its just another way to go. There are a lot of ways to go. I use NAT so I need IP addresses to redirect to the machine doing the job.

My old Linksys is not that advanced, but I am looking at new gear weekly and so far I have not seen any real advantages.

I would love to have 10Gb Ethernet but right now gear is rather pricey for my budget.

---

### Post by kevin11951 on 2009-10-30
> **Vegan said:**
> I am ok with assigned IP addresses, its just another way to go. There are a lot of ways to go. I use NAT so I need IP addresses to redirect to the machine doing the job.

My old Linksys is not that advanced, but I am looking at new gear weekly and so far I have not seen any real advantages.

I would love to have 10Gb Ethernet but right now gear is rather pricey for my budget.

If you ever decide to get a new router, this is the best possible one in the world!  [Linksys WRT54GL]("http://www.newegg.com/Product/Product.aspx?Item=N82E16833124190&Tpk=wrt54gl") + [DDWRT]("http://www.dd-wrt.com/site/index")

You will never be happier (as long as you know how to use it ;))

---

### Post by Iowan on 2009-10-30
I'm also fond of letting the DHCP server issue static leases - but I'm not familiar with the different routers to know which ones can, and which cannot. (I took that job away from my DSL modem and let one of my servers handle DNS/DHCP via **dnsmasq**).

---

### Post by cariboo on 2009-10-30
If the router works the way you like it to, just leave it, and instead have a look at a ups, they are wonderful devices, they don't care about power bumps or even short power outages.

I have my main system and router connected to a Belkin ups and my server is connected to an APC ups.

I have a Linksys wrt54gs router, and after every power bump it had to be reset. Now that it's connected to the ups I don't care about bumps and don't need to reset it.

---

### Post by Vegan on 2009-11-02
I have a small UPS, but the last power outage was longer than the battery to keep the cable modem and gateway both running. I guess I need a much larger one.

---

### Post by abdusamed on 2009-11-07
im tryin to achive static ip...

by runnin this command
```
nano /etc/network/interfaces
``` .i typed this up
```

iface lo inet statoc
address 192.168.1.10
netmask 203.99.163.240
broadcast 203.99.163.240
gateway 202.125.132.12

```i got those values from my dsl model interface .. i pretty much guess where the number go
:lolflag:
```

LAN IP Address                192.168.1.1
Default Gateway               203.99.176.1
Primary DNS Server         203.99.163.240
Secondary DNS Server     202.125.132.12
```
i try to save the file..but permission denied..but more importantly.. is this what im dion is right to get an static ip???

---

### Post by Vegan on 2009-11-08
Be sure you use

```
sudo nano ....
```.

or you will not be able to save.

---

### Post by abdusamed on 2009-11-08
really.thanks..it workin

---

