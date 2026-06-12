---
title: "Keep losing Internet after setting up static ip."
date: 2014-09-17
forum: Server Platforms
---

### Post by irv on 2014-09-17
After reinstalling my server I went to the network interface file and changed this 
[ATTACH=CONFIG]256500[/ATTACH] 
to this: I need to keep this static ip for my server because of all the ports I have opened on my router. tcp, html, etc.
[ATTACH=CONFIG]256501[/ATTACH]
and when I restart my server I can't get on the Internet.
I can ssh to the server so I am on the network it is just the Internet that will not connect.

What ever the problem is I just can't see it.

---

### Post by Habitual on 2014-09-17
can you ping 192.168.1.1?

---

### Post by irv on 2014-09-17
> **Habitual said:**
> can you ping 192.168.1.1?

When I have the inet set to dhcp I can ping it but when I set the static ip I can't ping it.

---

### Post by irv on 2014-09-17
It appears that my DHCP Active IP Table has my wabasha-server set to 192.168.1.105 but I need to make sure it stays at that ip address.
[ATTACH=CONFIG]256502[/ATTACH]

---

### Post by nerdtron on 2014-09-17
I don't see any DNS entries on your /etc/network/interfaces file. What is your /etc/resolv.conf?

---

### Post by Iowan on 2014-09-17
One option I've used is to set up a static lease in my DHCP server so a machine gets the same IP address based on MAC address.

---

### Post by nerdtron on 2014-09-17
Also post the output of "route -n" when you can't ping your gateway.

---

### Post by irv on 2014-09-18
> **nerdtron said:**
> I don't see any DNS entries on your /etc/network/interfaces file. What is your /etc/resolv.conf?

[ATTACH=CONFIG]256516[/ATTACH]

---

### Post by irv on 2014-09-18
> **nerdtron said:**
> Also post the output of "route -n" when you can't ping your gateway.
> @wabasha-server:~$ ping 192.168.1.1

PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=64 time=2.41 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=64 time=1.18 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=64 time=0.975 ms
64 bytes from 192.168.1.1: icmp_seq=4 ttl=64 time=0.973 ms
64 bytes from 192.168.1.1: icmp_seq=5 ttl=64 time=0.980 ms
64 bytes from 192.168.1.1: icmp_seq=6 ttl=64 time=0.988 ms
64 bytes from 192.168.1.1: icmp_seq=7 ttl=64 time=0.987 ms
64 bytes from 192.168.1.1: icmp_seq=8 ttl=64 time=0.981 ms
64 bytes from 192.168.1.1: icmp_seq=9 ttl=64 time=0.980 ms
^C
--- 192.168.1.1 ping statistics ---
9 packets transmitted, 9 received, 0% packet loss, time 8009ms
rtt min/avg/max/mdev = 0.973/1.162/2.414/0.449 ms

Is this what you wanted to see.

---

### Post by irv on 2014-09-18
> **Iowan said:**
> One option I've used is to set up a static lease in my DHCP server so a machine gets the same IP address based on MAC address.

This is done in my router from my isp.
[ATTACH=CONFIG]256517[/ATTACH] 

I also have a ip address assigned to my router for my domain name "wabasha-server.net" Here is the assignment
[ATTACH=CONFIG]256532[/ATTACH]

---

### Post by tgalati4 on 2014-09-18
Do you have a graphical desktop environment installed on this server?  If so, there may be a conflict between NetworkManager and the older *ifup* framework.  This issue has nabbed me in the past.

There are a couple of ways to fix it:

Clean up /etc/network/interfaces:

> tgalati4@Mint14-Extensa ~ $ cat /etc/network/interfaces
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

# Lines below are causing issues with NetworkManager
#
# iface wlan0 inet static
# address 192.168.1.156
# netmask 255.255.255.0
# gateway 192.168.1.1
# wireless-essid "Galati Slow Lane"
# auto wlan0
# iface wlan0 inet dhcp

# iface eth0 inet static
# address 192.168.1.156
# netmask 255.255.255.0
# Don't need a second gateway statement--it can cause issues.
# 

# auto eth0
# iface eth0 inet dhcp


Then set up your static assignments using the graphical NetworkManager icon:  (nm-applet).  

There is also a setting in the nm configuration file to allow nm to obey the /etc/network/interfaces file:

> 
tgalati4@Mint14-Extensa ~ $ cat /etc/NetworkManager/NetworkManager.conf 
[main]
plugins=ifupdown,keyfile
dns=dnsmasq

no-auto-default=00:XX:D3:XX:EF:1E,00:00:XX:3C:76:XX,

[ifupdown]
**managed=false**


So between these two scenarios, there is a room for error and being locked out of your network.

---

### Post by irv on 2014-09-18
I don't  have a graphical desktop environment installed on this server so I don't think that is the problem.

---

### Post by nerdtron on 2014-09-19
You may want to remove your /etc/udev/rules.d/70-persistent-net.rules. Copy it first on another location and then remove/delete the file. I have encountered before that it keeps messing up my network interface when the server changed from dhcp to static IP address. Be sure to activate your static IP in the /etc/network/interfaces and the reboot and see the changes.

---

### Post by irv on 2014-09-19
That file does not exist so I can't move it.
> cannot access /etc/udev/rules.d/70-persistent-net.rules: No such file or directory

---

### Post by Tadaen_Sylvermane on 2014-09-20
Add this line to your p3p1 static ip section.

```
dns-nameservers 8.8.8.8 8.8.4.4
```

These are googles dns servers. change them for whatever you prefer to use.

---

### Post by lisati on 2014-09-20
> **irv said:**
> This is done in my router from my isp.
[ATTACH=CONFIG]256517[/ATTACH] 

I also have a ip address assigned to my router for my domain name "wabasha-server.net" Here is the assignment

What I'm seeing in the screenshot is what your router needs to access the internet. I'm not familiar with configuring a Linksys device, but setting a static IP on my personal router (a different brand) for one of my devices (phone, laptop, etc) is via its equivalent of what I'm assuming the applications and gaming menu does on yours.

---

### Post by irv on 2014-09-20
This morning I tried changing my interfaces file again and here is what the file looks like:

> # This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto p3p1

iface p2p1 inet static
      address 192.168.1.105
      netmask 255.255.255.0
      network 192.168.1.0
      broadcast 192.168.1.255
      gateway 192.168.1.1
      dns-nameservers 8.8.8.8 8.8.4.4


When my interaces file is setup like this it will not not get to the internet or even my network now. I can't remote to my server using the static ip address 192.168.1.105 or my domain name wabasha-server.net but if I change back to:

> # This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto p3p1
 iface p3p1 inet dhcp


Everything works fine.

Now my router's local setting are:

> MAC Address:	 00:18:39:DC:1B:99	 	 
 	 	 	IP Address:	 192.168.1.1	 	 
 	 	 	Subnet Mask:	 255.255.255.0	 	 
 	 	 	DHCP Server:	 Enable	 	 
 	 	 	Start IP Address:	 192.168.1.100 	 	 
 	 	 	End IP Address:	 192.168.1.149 
Which means it is sending out ip address' beween 192.168.1.100 and .149.
My DHCP Active IP table is showing that wabasha-server which is my server has a ip address of 192.168.1.105 and will expire 23:42:56 so it will change.
By adding the line dns-nameservers really does nothing because it is dealing with dns names not internal ip address across a dhcp.
Now my big question is: when I setup my server did it setup a dhcp server and is it running in conflict with my dhcp on my router? I wouldn't think so. My old server 12.04 worked just fine with static setting.

Just for the record my Linksys router gaming menu is no more then port setting. It is opening ports for ftp,, httml etc. It has nothing to do with dhcp. I use it to open port for my server so I can get to the Internet.

In closing here is what my output from ifconfig command looks like:

```
irv@wabasha-server:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:40 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3617 (3.6 KB)  TX bytes:3617 (3.6 KB)

p3p1      Link encap:Ethernet  HWaddr 00:30:18:ad:bc:1e  
          [COLOR="#FF0000"]inet addr:192.168.1.105 [/COLOR] Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::230:18ff:fead:bc1e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1725 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1752 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:147818 (147.8 KB)  TX bytes:2198538 (2.1 MB)

```

---

### Post by Iowan on 2014-09-20
> # This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto [COLOR="#FF0000"]p3p1[/COLOR]

iface [COLOR="#FF0000"]p2p1[/COLOR] inet static
      address 192.168.1.105
      netmask 255.255.255.0
      network 192.168.1.0
      broadcast 192.168.1.255
      gateway 192.168.1.1
      dns-nameservers 8.8.8.8 8.8.4.4
I presume that was a typo...
By the way, are you trying to set up a static address inside the DHCP server's range?

---

### Post by irv on 2014-09-20
lowan, you have a good eye. that was the problem al it was was a typo. At least I was in the static address range. Thank you for catching this because it fix the problem. The problem was it couldn't find the network card p3p1. I don't have a p2p1. I will mark solved. Wow, my server setup is now complete and this is the first time I did it completely from the command prompt. No GUI on my server. I may have to setup a few more server, I am starting to like this.

---

### Post by Iowan on 2014-09-20
A static address in the DHCP server's range may lead to conflicts - the DHCP server is free to assign 192.168.1.105 to another machine.

---

### Post by irv on 2014-09-20
I am not using my own DHCP server so I should be safe. I did check to make sure it was not installed. The only DHCP I am using is the one on my Router.

---

### Post by vollenweider on 2014-09-21
maybe u have no dns, i guess. AFIK ubuntu's networkmanager will not let you add it to /etc/resolv.conf just as elsewhere.
But in your interfaces add 2 DNS-Servers to your interface with the "dns-nameservers x.x.x.x x.x.x.x" statement

HTH


PS: just noticed that this hint has allready been placed on the second page …

---

### Post by irv on 2014-09-21
vollenweider see post 18 and 19 the problem was solved. It was a typo on my part.

---

