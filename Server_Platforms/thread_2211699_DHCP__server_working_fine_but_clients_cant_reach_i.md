---
title: "DHCP  server working fine but clients cant reach internet"
date: 2014-03-17
forum: Server Platforms
---

### Post by Erdem on 2014-03-17
Hello,

I have an ubuntu server 12.04.04 i installed dhcp server on it and its working fine... but clients cant reach internet

my interfaces file configured

```
auto lo
iface lo inet loopback

auto eth1
iface eth1 inet static
address 192.168.1.100
netmask 255.255.255.0
gateway 192.168.1.1


auto eth0
iface eth0 inet static
address 192.168.2.1
netmask 255.255.255.0
gateway 192.168.1.100
```

and my dhcpd.conf file configuration

```
default-lease-time 600;
max-lease-time 7200;

subnet 192.168.2.0 netmask 255.255.255.0 {
 range 192.168.2.1 192.168.2.200;
 option routers 192.168.2.254;
 option domain-name-servers 192.168.2.1;
 option domain-name "server.local";
} 

host ubuntu-server {
	hardware ethernet 00:13:d4:3e:2c:d1;
	fixed-address 192.168.2.1;
}
```

i run that commands to let eth1 accept request from eth0

```
echo 1 > /proc/sys/net/ipv4/ip_forward

iptables -t nat -A POSTROUTING -o eth1 -j MASQUERADE
iptables -A FORWARD -i eth1 -o eth0 -m state --state RELATED,ESTABLISHED -j ACCEPT
iptables -A FORWARD -i eth0 -o eth1 -j ACCEPT
```

i dont know where is problem...

thanks everyone for spending your time to answer

---

### Post by RL600 on 2014-03-17
First I would change in the dhcp config 192.168.2.1 t0 192.168.2.2.
Why?  because this is already been used. Normally this shouldn't be a problem but when troubleshooting make sure every thing is good.
I think the problem is on the eth0. Your gateway isn't in the same subnet as the NIC itself. 
When a client has a ip address try to do the following:
1. ping 192.168.2.1
2. ping 192.168.1.100
3. ping 192.168.1.1
4. ping [www.google.com](www.google.com)
Tell us which one doesn't succeeded.
Hope this helps!

---

### Post by SeijiSensei on 2014-03-17
> ```
subnet 192.168.2.0 netmask 255.255.255.0 {
 range 192.168.2.1 192.168.2.200;

```

Your range of client addresses includes 192.168.2.1, which is the address of your DHCP server.  The range must include only addresses not being used by other machines.  Start at 2.10 or 2.100, to leave some unallocated addresses to use if you add additional servers for which you want static addresses.

---

### Post by Erdem on 2014-03-17
1. ping 192.168.2.1 -> [COLOR="#00FF00"]OK[/COLOR]
2. ping 192.168.1.100 -> [COLOR="#FF0000"]cant reach[/COLOR]
3. ping 192.168.1.1 -> [COLOR="#FF0000"]cant reach[/COLOR]
4. ping [www.google.com](www.google.com) -> [COLOR="#FF0000"]cant reach[/COLOR]

and its pinging other devices on same network like i can ping my two laptops which connected dhcp...

---

### Post by Erdem on 2014-03-17
btw eth1 is internet interface eth0 is for dhcp network...

---

### Post by RL600 on 2014-03-17
Thanks for doing the pings.
This is the answer to the thought I already had.
You have a subnet 192.168.2.0 and a subnet 192.168.1.0. To go from one subnet to the other u have to configure something called a  "static route".
You can found how to make one here: [http://askubuntu.com/questions/168033/how-to-set-routes](http://askubuntu.com/questions/168033/how-to-set-routes) .
I hope this helps.


If you ever run into a problems with networks. One of the best ways to found the problem is to draw the way a packet goes from point A to point B.
You saw that the packet didn't get by the 192.168.1.100. You now know where the problem is in the route from A to B. I think a good thing to remember!

---

