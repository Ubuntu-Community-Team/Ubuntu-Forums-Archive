---
title: "Fresh ubuntu server installation doesn't connect to internet"
date: 2013-10-17
forum: Server Platforms
---

### Post by Alessandro_sepich on 2013-10-17
Hello It's 3 days me an my colleague are trying to install a small server in the office (for development purpose).

I downloaded the latest version of ubuntu server (12.04.3 64-bit) from the ubuntu site, and installed in a brand new PC. the PC is a Lenovo thinkcentre edge (72 i think but not sure).
Before going to the real installation I used the same ISO file to install a version in a Virtual machine using VirtualBox and everything went OK. So we proceed to the real installation.

during the installation the system was unable to auto configure the network so we did it manually:
ip 10.18.62.122 gateway 10.18.62.254 subnet 255.255.254.0
during the boot it says that the network is not up.

now, here is my /etc/network/interfaces file:

```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet looback

# The primary network interface
auto eth0
iface eth0 inet static
    address 10.18.62.122
    netmask 255.255.254.0
    gateway 10.18.62.254

```

if I try to ping:
```

ping google.com

```

I get nothing, but nothing at all, until I do Ctrl-C

if I ping the gateway, I get from 10.18.62.122 (me) Destination Host Unreachable

so no internet but no Ethernet either.

I tried setting up the DNS also by modifying the file /etc/resolv.conf and also by adding 
```
dns-nameservers 192.168.33.1 192.162.33.2
```
or
```
dns-nameservers 8.8.8.8 8.8.4.4
```
to /etc/network/interfaces file.

Nothing helps.

any suggestion???

---

### Post by oldfred on 2013-10-17
I do not know servers, but you cannot overlap the DHCP range on your router. Often routers reserve a group of 100 or 150 numbers starting at 100 for DHCP, so you cannot use those.

Often then servers and other hardware are .1, .2 etc or .250, .251 etc. I set my desktop to .20 so it is fixed but I use gui network connections and you do not mix gui configurations with interfaces file configurations or it will not work.

So try changing your device from 10.18.62.122 to something like 10.18.62.20.
Your router should have configuration settings that you can see on exactly what numbers are reserved for DHCP.

---

### Post by houstonbofh on 2013-10-17
So, it did not auto-config an IP and when you config it, you get nothing...  Are you sure your nic is good?  What is the output of "ifcong" from the cli?

---

### Post by SeijiSensei on 2013-10-18
First things first.  When you plug in the ethernet cable, does the link light on the back of the adapter card light up?

Next, run "ifconfig" and see if it has an entry for eth0.

Are you sure you are in a /23 subnet, equivalent to your netmask of 255.255.254.0?  Maybe it should be 255.255.255.0?

What do you see when you run "route -n"?

---

