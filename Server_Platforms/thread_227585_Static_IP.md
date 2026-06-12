---
title: "Static IP?"
date: 2006-08-01
forum: Server Platforms
---

### Post by cpminga on 2006-08-01
Hello. I'm trying to get my server to use a configured IP. Below is my /etc/network/interfaces. I can /etc/init.d/network restart and get the desired address. However, after an amount of time, the machine eventually pulls a DHCP address from my router. How can I stop this and keep the static IP, even after a reboot?

```

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
auto eth0

# The primary network interface
iface eth0 inet static
        address 192.168.1.103
        netmask 255.255.255.0
        gateway 192.168.1.1

```

---

### Post by hasimir44 on 2006-08-02
that's weird.. maybe try killing dhclient. this will give you the PID if it's running:  

ps aux |grep dhclient 

then kill the PID: 

sudo kill -9 <PID>


if that seems to work, then disable dhclient from your startup services..

---

### Post by cpminga on 2006-08-03
Yeah, that seems to have done the trick. Thanks! One more little question, though. How do I remove dhclient from my startup services?

---

