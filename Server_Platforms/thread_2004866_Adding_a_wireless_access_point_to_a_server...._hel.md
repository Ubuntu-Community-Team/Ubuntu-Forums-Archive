---
title: "Adding a wireless access point to a server.... help!"
date: 2012-06-16
forum: Server Platforms
---

### Post by RLemm on 2012-06-16
Firstly I am learning as I go here so forgive me if I have made a mistake or two.
Secondly I am not the most up to speed on networking.

Right the story so far (slightly abridged).

Formatted my old dell.
It has a built in lan, a pci lan and now a pci wireless card.

Installed Ubuntu server 12.04 (32bit)

Pretty much a standard install.

Edited /etc/network/interfaces
```

auto lo eth1 eth0 wlan0
iface lo inet loopback

#  WAN  
iface eth0 inet dhcp
post-up iptables-restore < /etc/iptables.up.rules


#  LAN
iface eth1 inet static
address 192.168.0.144
netmask 255.255.255.0
broadcast 192.168.0.244
network 192.168.0.0

iface wlan0 inet static
address 192.168.0.122
netmask 255.255.255.0
broadcast 192.168.0.222
network 192.168.0.0

```installed hostapd
pointed it at the hostpad.conf

then created/edited hostapd.conf
                                  
```

interface=wlan0 bridge=br0
driver=nl80211
ssid=Hereitis
hw_mode=g
channel=9
ignore_broadcast_ssid=0

auth_algs=1
wpa=2
wpa_passphrase=testing123
wpa_key_mgmt=WPA-PSK
wpa_pairwise=TKIP
rsn_pairwise=CCMP

```dnsmasq installed

edit dnsmasq.conf
```

# LAN
interface=eth1
interface=wla0
domain=HOLM
dhcp-range=eth1,192.168.0.40,192.168.0.59
dhcp-range=wlan0,192.168.0.60,192.168.0.84
dhcp-authoritative




```Packet forwarding set by editing /etc/sysctl.conf

```
net.ipv4.ip_forward=1
```IPtables is running, but there are no DROP clauses against this interface or anything. I have also tried with only ACCEPTS in all instances with no results.

From my wired connection I can quite happily use the server, but I cannot connect using wireless.... The network broadcasts, I think I even get past the authentication without a problem, it all falls down when the an ip is not assigned.

What am I missing in my ignorance?

I have searched quite a bit and not found much of use to me, basically I am waving a little white flag and hoping someone who knows this better than I do can lay out what needs to be done.

---

### Post by N0oki3 on 2012-06-16
hello. Here you have a nice [guide ](http://modelr.wordpress.com/2009/06/01/how-to-get-wireless-network-on-ubuntu-server/)

I hope  it will help you

---

### Post by Cheesehead on 2012-06-16
> **RLemm said:**
> 
edit dnsmasq.conf

# LAN
interface=eth1
[COLOR="Red"]interface=wla0[/COLOR]
domain=HOLM
dhcp-range=eth1,192.168.0.40,192.168.0.59
dhcp-range=wlan0,192.168.0.60,192.168.0.84
dhcp-authoritative


Typo in your dnsmasq.conf?

---

### Post by RLemm on 2012-06-22
Groan <shuffles away and puts dunces hat on> #-o

The typo it is....

But I do have access to the server now :-)

Failing to access the internet though. Could I impose on the collective wisdom here to point me in the right direction to look?

Thanks for the help so far.

---

### Post by volkswagner on 2012-06-23
I'm no expert so I can't say what the exact issue is.

I can say it has to do with lack of gateway directive.  It may be due to the fact you have specified your bridge... interface=wlan0 bridge=br0 in hostapd.conf but you have no entry in /etc/network/interfaces for br0.

You may want to look a some guides for ubuntu as router or ubuntu as router and access point.

---

