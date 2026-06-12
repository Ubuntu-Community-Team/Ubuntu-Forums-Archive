---
title: "can't set static ip (ubuntu server 12.10)"
date: 2012-12-17
forum: Server Platforms
---

### Post by noobcakes on 2012-12-17
Hi, this is my first post here. I've been scouring the net looking for a solution, so i signed up. I did a forum search for static ip issues after joining, and none of the recent entries seemed to match my problem, which is this:

I am running ubuntu server (12.10) on a gateway laptop. I'm wired into my home router and want to set my IP to a static value. Any time i edit /etc/network/interfaces to static instead of DHCP, i can't connect to anything. Can't ssh in from my desktop or even ping my router.

I'm not sure whether this is a problem with my platform, my network adapter, my router, or ??? but i'm pretty sure i've narrowed down the problem to my interfaces file and the dhcp/static swap.

The meat of my interfaces file is pasted below. I have my wireless card switched off to prevent its tomfoolery. I've been editing the file so much, i'm not even bothering at this point to delete lines. I just comment out the dhcp line when i'm trying a static configuration. I've done every "can't set static ip" help tip i could find online.

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
#iface eth0 inet static
#       address 192.168.1.37
#       netmask 225.225.225.0
#       gateway 192.168.1.1

```Any time i edit, i run a "service networking restart" and then "ifconfig"

Here's my ifconfig output with DHCP enabled (with static i only get the loopback block):```

eth0      Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx:xx  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:b8ff:fee7:f71c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:281 errors:0 dropped:0 overruns:0 frame:0
          TX packets:352 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:31874 (31.8 KB)  TX bytes:45369 (45.3 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:430 errors:0 dropped:0 overruns:0 frame:0
          TX packets:430 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:41740 (41.7 KB)  TX bytes:41740 (41.7 KB)
```
Here's my network card. I could give other system info if anybody thinks it's relevant.
```
07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)
```My router (linksys WRT54G) does not support IP reservations for MAC addresses, so that's not a possible fix.

I have also tried static/DHCP after an "apt-get update" and an "apt-get upgrade" with the same results.

---

### Post by chadk5utc on 2012-12-17
Not sure what your using to edit the file but I would try within a terminal
> sudo vi /etc/network/interfaces I prefer vi but you can change that for what ever your used to using, nano, pico.....then do networking restart and ifconfig, also be sure network manager is not trying to set the NIC to DHCP
Oh and swap these like so
> #iface eth0 inet dhcp
iface eth0 inet static

---

### Post by noobcakes on 2012-12-17
> **chadk5utc said:**
> Not sure what your using to edit the file but I would try within a terminalI'm on ubuntu server and don't have a graphical interface installed.

 > Oh and swap these like soYeah, i've been swapping the commented out sections when i want to swap between DHCP and (an attempt at) static. When i comment out the DHCP line and uncomment the static block, i lose connection upon networking reset.

So if i'm using DHCP, the interfaces file and ifconfig output look like this:

```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
#iface eth0 inet static
#       address 192.168.1.37
#       netmask 225.225.225.0
#       gateway 192.168.1.1

----------------------------------------

eth0      Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx:xx  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:b8ff:fee7:f71c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:281 errors:0 dropped:0 overruns:0 frame:0
          TX packets:352 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:31874 (31.8 KB)  TX bytes:45369 (45.3 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:430 errors:0 dropped:0 overruns:0 frame:0
          TX packets:430 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:41740 (41.7 KB)  TX bytes:41740 (41.7 KB)

```

And if i'm trying to use a static IP, my file/output look like this:

```

auto lo
iface lo inet loopback

auto eth0
#iface eth0 inet dhcp
iface eth0 inet static
       address 192.168.1.37
       netmask 225.225.225.0
       gateway 192.168.1.1

----------------------------------------

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:430 errors:0 dropped:0 overruns:0 frame:0
          TX packets:430 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:41740 (41.7 KB)  TX bytes:41740 (41.7 KB)

```

---

### Post by volkswagner on 2012-12-18
Have you tried rebooting the machine after setting to static.  I know this is not "usually" required, but I have seen this in Debian Wheezy.

So instead of restarting networking, restart the machine.

---

### Post by noobcakes on 2012-12-18
> **volkswagner said:**
> So instead of restarting networking, restart the machine.
No dice.

Also have tried "/etc/init.d/networking restart" and "ifconfig eth0 {down,up}" instead of the service restart, to no avail.

The only thing that will get me a set IP is ```
ifconfig eth0 192.168.1.37 netmask 255.255.255.0
``` but that must be done after booting and automatic network configuration.

Will that suffice to get me a static IP? Like for instance if the router has a power hiccup and resets, will it reassign a new IP?

---

### Post by steeldriver on 2012-12-18
do you have network-manager service running as well?

```
service network-manager status
```

---

### Post by noobcakes on 2012-12-18
No network-manager installed.

---

### Post by steeldriver on 2012-12-18
OK so is there anything in dmesg to suggest why eth0 just plain isn't coming up when you restart networking with the static IP stanza in your interfaces file?

---

### Post by noobcakes on 2012-12-18
Somebody at askubuntu spotted the problem. It was a typo in the /etc/network/interfaces file:

> **noobcakes said:**
> 
       netmask 225.225.225.0


Should have been `netmask 255.255.255.0`

Problem solved, static IP set.

---

### Post by steeldriver on 2012-12-18
omg! can't believe we all missed that... :lolflag:

---

### Post by chadk5utc on 2012-12-18
> **steeldriver said:**
> omg! can't believe we all missed that... :lolflag:

Wow I agree funny how the numbers looked right at a glance. Glad you were able to figure it out.

---

