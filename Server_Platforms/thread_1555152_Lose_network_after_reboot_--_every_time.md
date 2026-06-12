---
title: "Lose network after reboot -- every time"
date: 2010-08-17
forum: Server Platforms
---

### Post by garfonzo on 2010-08-17
Hey Folks,

I have this weird thing happening. Whenever I reboot my server, it looses all network connectivity. It can't see the LAN nor the internet. I have to issue the following:

```

ifconfig eth0 down
ifconfig eth1 down
ifconfig eth1 up

```

This will get the server talking to the LAN, but still not to the internet. To get that I have to do:

```

route add default gw 192.168.0.1

```

Then I'm up and running. 

But why? 

Granted I only have to reboot now and then (after a power failure, or, like last night where the server was actually heating the house too much on a hot August day) but why is this happening? It is like these settings are temporary and are lost on shutdown.

Any thoughts?

---

### Post by dcollier on 2010-08-17
Just a thought, but have you tried reinstalling or updating the drivers for your network adapter?

---

### Post by Iowan on 2010-08-17
What's in */etc/network/interfaces*?

---

### Post by garfonzo on 2010-08-17
@ dcollier: No I haven't. I will try that to see if there is any gain. 

@ Iowan: Here:

```


# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address         192.168.0.147
network         192.168.0.1
netmask         255.255.255.0
gateway         192.168.0.1

# The secondary (Gigabit) card
auto eth1
iface eth1 inet static
address         192.168.0.148
network         192.168.0.1
netmask         255.255.255.0
gateway         192.168.0.1

```

eth0 is the built in NIC. I add the second (eth1) because it is Gb speed. My whole house is wired with Gb so I needed the server to be able to push data fast too.

---

### Post by Iowan on 2010-08-18
Having multiple interfaces in the same subnet usually causes problems (and violates Spanning Tree Protocol). Is there a reason both need to be in the same subnet?

---

