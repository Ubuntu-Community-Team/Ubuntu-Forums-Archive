---
title: "QUERY: 4 quick queries"
date: 2009-02-07
forum: Server Platforms
---

### Post by andwan0 on 2009-02-07
1. I just installed ubuntu server and was surprised there's no GUI. Is it possible to install a GUI and is it advisable?

2. During installing I never got asked for root password. Is this normal? So we never use root login, just sudo?

3. I have two NICs, one with static external WAN IP, and the other with static internal IP. During installation it help me setup the external WAN IP. How do I setup the static internal IP NIC?

4. I wish to do IP masqerade on my ubuntu server. What is the quickest and easiest way to do this?

---

### Post by cariboo on 2009-02-07
> 1. I just installed ubuntu server and was surprised there's no GUI. Is it possible to install a GUI and is it advisable?

I would suggest instead of installing a gui, use [webmin]("http://www.webmin.com/"), to administer your server.

> 2. During installing I never got asked for root password. Is this normal? So we never use root login, just sudo?

The root account isn't enabled, use sudo. If you need to be  root for longer use:

```
sudo -i
```

> 3. I have two NICs, one with static external WAN IP, and the other with static internal IP. During installation it help me setup the external WAN IP. How do I setup the static internal IP NIC?


You can setup your second nic with a static ip address in /etc/network/interfaces,  it should look something like this:

```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
    address 192.168.1.200
    netmask 255.255.255.0
    broadcast 192.168.1.255
    gateway	192.168.1.1
```

> 4. I wish to do IP masqerade on my ubuntu server. What is the quickest and easiest way to do this? 

Check out this [thread=713874]thread[/thread] for a NAT howto.

Jim

---

### Post by jimv on 2009-02-08
As far as the no gui thing...that's to keep the install as minimal as possible.  For example, I have 5 servers running with no gui, and I manage them all with SSH.

If you would like a gui, you can install kde/gnome/xfce with these commands:

Gnome:
sudo apt-get install ubuntu-desktop

KDE:
sudo apt-get install kubuntu-desktop

XFCE
sudo apt-get install xubuntu-desktop

---

### Post by andwan0 on 2009-02-09
Thanks guys.

One more quick question.

I reinstalled ubuntu-server but this time I chose the eth1 (2nd NIC on LAN) as the primary. It detected the DHCP server and got assigned IP address, settings, etc. The DHCP server is our Windows 2000 Server. The Windows 2000 Server also has 2 NICs (one static LAN IP, one static WAN IP) and does IP masquerading.

Is is possible to have ubuntu-server & Windows 2000 Server DHCP servers co-operate? So that if Windows 2000 Server dies, then the ubuntu-server DHCP kicks in... and obviously takes over the IP masquerading....

---

### Post by NetworkGuy on 2009-02-11
2 DHCP servers on the same subnet can be done as long as both servers have different address ranges.  

For example the first server hands out addresses from .10 to .100 and the second server does .150 to .250

Since DHCP requests are a multicast, you shouldn't have to worry about IP masquerading to the first server IP address unless you specify the exact address in a router somewhere (Cisco IP Helper command for example)

---

### Post by andwan0 on 2009-02-11
> **NetworkGuy said:**
> 2 DHCP servers on the same subnet can be done as long as both servers have different address ranges.  

For example the first server hands out addresses from .10 to .100 and the second server does .150 to .250

Since DHCP requests are a multicast, you shouldn't have to worry about IP masquerading to the first server IP address unless you specify the exact address in a router somewhere (Cisco IP Helper command for example)

Yep, I did the different subnets.. problem is, the linux server somehow takes prority...

thing is, I want the win2k server take prority 100%... until it goes down ofcourse....

coz the win2k server had domain data, auth, etc... until I figure out how to interop AD stuff on linux....

---

