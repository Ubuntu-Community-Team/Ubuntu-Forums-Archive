---
title: "Help with initial network setup for linux server in windows group"
date: 2010-06-22
forum: Server Platforms
---

### Post by Shinhan on 2010-06-22
I have 3 windows computers and just bought linux server. All of them are currently connected to switch. There is also Wireless AP connected to switch and ADSL router connected to switch (yeah, I know its possible to buy a 3in1 but this was bought piecemeal). ADSL is doing the DHCP and I'm not using any other advanced services.

Now, I want to route everything over the linux server. I got the 3 LAN cards for him (one for wireless, one for LAN and one for ADSL) but when I connect everything this way its not working (surprise surprise). I'm following [Linux Advanced Routing & Traffic Control HOWTO]("http://lartc.org/howto/") but its surprisingly sparse on the topic of network setup and i dont know how to proceed now.

Since the server will be a choke point I presume I need to setup DHCP server on him? First question is: can I use same netmask on all of these subnets? [Ubuntu DHCP server guide]("https://help.ubuntu.com/community/dhcp3-server") uses both static and DHCP and am not sure if I should also use static on some routes or is it ok to use DHCP on all.

Also, when I was installing ubuntu server only one LAN card was used (eth2) so ifconfig shows only lo and eth2, but when I do ifconfig eth0 up and ifconfig eth1 up it doesnt look like its working.

Anyway, hope somebody has some tips to point me in the right direction, primarily DHCP server setup and if I missed any steps...

---

### Post by brettg on 2010-06-22
Here is a basic list of what you need to do;

1) Connect your linux box to the adsl router with static IP addresses on both. (This is your WAN port)

2) Set your default route on the linux box to go via the adsl router. 

3) Configure ip forwarding and masquerading to the WAN port. 

4) Setup an IP subnet, a DHCP server and a DNS proxy (I recommend dnsmasq) on the linux box on the LAN port

5) Connect everything together using the ethernet switch. 

6) Connect the WAP to the 3rd LAN port and repeat steps 3 -6 using a different IP subnet 

Good luck

---

### Post by Shinhan on 2010-06-22
Well, I did start setting up DHCP server on the linux box, but thats where I got bogged down. So, static IPs for WAN. 
And how would I go about setting up masquerading?

---

### Post by brettg on 2010-06-22
What you need is iptables. 

The basic gist of it is this

```
sudo /sbin/iptables --table nat -A PREROUTING -i ETH0 -j MASQUERADE
sudo /sbin/iptables -A INPUT -m state --state ESTABLISHED -j ACCEPT

```
 
There are plenty of articles on setting up masquerading on the net.

[Take your pick]("http://www.google.com/search?hl=en&lr=lang_en&tbs=lr%3Alang_1en&q=ip+masquerading+ubuntu&aq=f&aqi=g1&aql=&oq=&gs_rfai=")

---

### Post by Shinhan on 2010-06-23
So, something like this?

```

# /etc/dhcpd.conf 
default-lease-time 600;
max-lease-time 86400;
ddns-update-style none;
log-facility local7;

# WAP
subnet 192.168.1.0 netmask 255.255.255.0 {
    range 192.168.1.10 192.168.1.100;
    option subnet-mask 255.255.255.0;
    option broadcast-address 192.168.1.255;
}

# LAN
    subnet 192.168.2.0 netmask 255.255.255.0 {
    range 192.168.2.10 192.168.2.100;
    option subnet-mask 255.255.255.0;
    option broadcast-address 192.168.2.255;
}

```

```

# /etc/network/interfaces
auto lo
iface lo inet loopback

mapping hotplug
        script grep
        map eth1

iface eth2 inet dhcp
iface eth1 inet dhcp

auto eth0
iface eth0 inet static
    address 192.168.0.128
    netmask 255.255.255.0

auto eth1
auto eth2

```

dnsmasq mentions supporting DHCP. Does that mean I can use it instead of DHCPD and if so should I uninstall dhcpd and just copy paste what I wrote above for dhcpd.conf into dnsmasq.conf or does it just extend dhcpd?

---

### Post by brettg on 2010-06-23
dnsmasq will do dhcp as well and it is a lot easier to set up, especially if you want your clients to be able to tell the dns server their hostname when they connect.

It is seperate to DHCPD so you should uninstall that.

/etc/dnsmasq.conf is very well documented in the comments. 

To setup dhcp you need a single line like this per subnet

dhcp-range=192.168.1.10,192.168.1.100,12h

If you have been moving or inserting LAN cards then you may need to clear out old entries in your udev rules.

Edit /etc/udev/rules.d/70-persistent-net.rules

Clear out all the entries there and reboot. See if your interfaces appear.

---

### Post by Shinhan on 2010-06-24
Ok, I tried to do what you wrote. 
For the  iproute, it said I cant use eht0 with PREROUTING, so after looking at some other masquerading guides, I did this:

```

sudo /sbin/tables --table nat -A POSTROUTING -o ETH0 -j MASQUERADE
sudo /sbin/iptables -A INPUT -m state --state ESTABLISHED -j ACCEPT

```

And I set the dnsmasq.conf as this:
```

# /etc/dnsmasq.conf

domain-needed
bogus-priv
address=/doubleclick.net/127.0.0.1
except-interface=eth0
dhcp-range=interface:eth1,192.168.1.10,192.168.1.127,12h
dhcp-range=interface:eth2,192.168.2.10,192.168.2.127,12h
log-queries

```

Btw, how do I reload network settings? If I change resolv.conf or dnsmasq.conf or iproutes...

Anyway, dnsmasq aint working. Says "failed to bind DHCP server socket: Address already in use"

How do I find out which address he says is in use and how do I fix this?

Ping works for 192.168.0.1 (which should be ADSL router, his IP address is fixed to that) but other addresses aint working (prolly becuase dnsmasq is not working).

I put my ISP's two DNS servers into resolv.conf as well as 8.8.8.8. Is that ok?

---

### Post by Shinhan on 2010-06-24
Still not working, but I tried couple things and maybe now someone will have an idea that can help me?

lsof -i 
shows only following commands: portmap, rpc.statd, smbd, sshd, mysqld, named, samba and apache2.

netstat -antuevp 
shows only programs: mysqld, smbd, rpc.statd, portmap, apache2, named, sshd and smbd.

Might dnsmasq have some problems with Samba (and if so do I need to change samba config or dnsmasq config and how)?

---

### Post by brettg on 2010-06-24
Looking back at your previous messages, you have 

```
iface eth2 inet dhcp
iface eth1 inet dhcp
```

If that is still the case then you will need to set them both as static addresses. Those addresses will be the default gateways for their respective subenets.

---

### Post by Shinhan on 2010-06-25
Like this?

```

# /etc/network/interfaces
auto lo
iface lo inet loopback

mapping hotplug
        script grep
        map eth1

auto eth0
iface eth0 inet static
    address 192.168.0.128
    netmask 255.255.255.0

auto eth1
iface eth1 inet static
    address 192.168.1.128
    netmask 255.255.255.0

auto eth2
iface eth2 inet static
    address 192.168.2.128
    netmask 255.255.255.0

```

---

### Post by Shinhan on 2010-06-25
After some help from dnsmasq mlist, turns out I need to remove "named" which I found out is from bind9 package so I removed that, and dnsmasq starts up normally now.

Internet connectivity solved thanks to [http://www.tldp.org/HOWTO/IP-Masquerade-HOWTO/firewall-examples.html](http://www.tldp.org/HOWTO/IP-Masquerade-HOWTO/firewall-examples.html) but since that guide is not for ubuntu I had to do some changes and I'm ignoring some kind of missing LSB information warnings. Oh well, at least its working now.

---

### Post by critter.be on 2010-06-25
For starters, IP Forwarding must be enabled:
```

root@d530001:~# cat /proc/sys/net/ipv4/ip_forward 
0

```
0 = no IP forwarding, 1 = IP forwarding.
To enable it:
```
sysctl -w net.ipv4.ip_forward=1
```

To make sure your routing is active when rebooting, edit /etc/sysctl.conf
look for and replace:
```
net.ipv4.ip_forward = 1
```

I believe you may have forgotten the following rules:
```
iptables --append FORWARD --in-interface eth0 -j ACCEPT
iptables --append FORWARD --in-interface eth1 -j ACCEPT
```


And you may want to read up on iptables...

INPUT is for any inbound traffic on the interface
OUTPUT is for any outbound traffic on the interface
FORWARD if for any traffic routed by the machine

So your INPUT statement is only for traffic on the machine itself.

Have a look at this page: [http://www.howtoforge.com/nat_iptables]("http://www.howtoforge.com/nat_iptables")
Will.

---

### Post by Shinhan on 2010-06-25
First I'm really thankful for that sysctl bit, the 

```

echo "1" > /proc/sys/net/ipv4/ip_forward 

```

that I was told by others works but looks like an ugly hack and I'm glad I know the proper way to enable ip forwarding.

Sorry I edited my previous message, should've refreshed but didnt so I didnt  notice your reply. 
The internet is working now, and like I mentioned in edit I used  [http://www.tldp.org/HOWTO/IP-Masquerade-HOWTO/firewall-examples.html](http://www.tldp.org/HOWTO/IP-Masquerade-HOWTO/firewall-examples.html). Since thats not for ubuntu I had to make some changes (I also removed the ip_forwarding thanks to you tip just now), and now after doing 

```

update-rc.d firewall-iptables defaults

```

looks like everything should work after restart. I just get missing LSB information warning.

---

