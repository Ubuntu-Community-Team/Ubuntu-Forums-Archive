---
title: "Removing virtual ip interfaces"
date: 2016-09-12
forum: Server Platforms
---

### Post by David_Moore on 2016-09-12
I have created some virtual interfaces somehow and I'd like to remove them just for aesthetic sake.

docker0   Link encap:Ethernet  HWaddr 02:42:9f:79:93:97
          inet addr:172.17.0.1  Bcast:0.0.0.0  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

virbr0    Link encap:Ethernet  HWaddr 52:54:00:6d:0a:f5
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

I installed docker at one point, but I'm pretty sure I've removed it. Then docker0 still remains and I'm unsure what I need to do to completely get rid of it.

I have no idea why virbr0 was created.

Thanks for your time.

---

### Post by newbie-user on 2016-09-13
You need a bridge to connect your container to the outside, hence virbr0. docker0 is the virtual nic of the container. Anyway, check /etc/network/interfaces to see if it's specified there.

---

### Post by David_Moore on 2016-09-15
> **newbie-user said:**
> You need a bridge to connect your container to the outside, hence virbr0. docker0 is the virtual nic of the container. Anyway, check /etc/network/interfaces to see if it's specified there.

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

This is all I have in the interfaces file.

---

### Post by SeijiSensei on 2016-09-15
You can try tearing down the interfaces manually with ifconfig:
```
sudo ifconfig docker0 down
```
but you should still see if you can determine what is creating the interface in the first place.  I have no experience with containers so I can't help much more I'm afraid.

---

### Post by David_Moore on 2016-09-15
> **SeijiSensei said:**
> You can try tearing down the interfaces manually with ifconfig:
```
sudo ifconfig docker0 down
```
but you should still see if you can determine what is creating the interface in the first place.  I have no experience with containers so I can't help much more I'm afraid.

Yeah, they can go down, but they just come back after a reboot.

---

### Post by SeijiSensei on 2016-09-15
Do you see anything in /etc/rc.local?  Is there a launcher for docker still hanging around in /etc/init.d?  These are the likely places where the interface would be created.

---

### Post by newbie-user on 2016-09-16
Here is Docker's documentation on Docker networking: [https://docs.docker.com/engine/userguide/networking/]("https://docs.docker.com/engine/userguide/networking/")

Seems virbr0 and docker0 are automatically created when you install Docker

---

