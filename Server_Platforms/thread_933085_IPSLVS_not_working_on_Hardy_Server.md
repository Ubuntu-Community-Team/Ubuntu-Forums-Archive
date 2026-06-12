---
title: "IPS/LVS not working on Hardy Server"
date: 2008-09-29
forum: Server Platforms
---

### Post by batosai on 2008-09-29
Hi,

I'm trying to setup a load-balancing service on two "real" apache servers. In the rest of this post, I will replace my IPs as follows :
$VIP  : "virtual IP", address of the load balancer
$RIP1 : address of apache server number 1
$RIP2 : address of apache server number 2


On the load balancer, I did :
ipvsadm -A -t $VIP:80 -s rr
ipvsadm -a -t $VIP:80 -r $RIP1:80 -g
ipvsadm -a -t $VIP:80 -r $RIP2:80 -g

On each apache server, I did :
ifconfig lo:0 $VIP netmask 255.255.255.255 up
echo 1 > /proc/sys/net/ipv4/conf/lo/arp_ignore
echo 2 > /proc/sys/net/ipv4/conf/lo/arp_announce
echo 1 > /proc/sys/net/ipv4/conf/all/arp_ignore
echo 2 > /proc/sys/net/ipv4/conf/all/arp_announce

As explained on [http://www.linuxvirtualserver.org/VS-DRouting.html](http://www.linuxvirtualserver.org/VS-DRouting.html)

When I point a browser to http://$VIP I just get a timeout.
Firewall rules are disabled on all three servers.

In all doncumentations I found, people just had problems with real servers announcing the virtual IP address, trashing ARP tables. I've tried a few variation from the above, blocking ARP announces on eth0 or lo0, with no more luck.

Can comeone help ?

---

### Post by batosai on 2008-09-29
Add on : I tried the Hidden interface approach suggested here [http://www.linuxvirtualserver.org/docs/arp.html](http://www.linuxvirtualserver.org/docs/arp.html) and it worked for about 5 seconds. After that, I'm back to the timeout problem. 

Note that all 3 servers have been idle for about an hour before I did it. I guess this is the time my switches need to flush their ARP tables.

This made me suspect that commands given for 2.2 kernels don't work with 2.6, or not exactly as expected.

Any help would be much appreciated.

---

### Post by batosai on 2008-10-06
Still nobody has an idea ?

Here are the news : LVS folks confirm that it is an ARP problem. Ubuntu announces secondary address despite the sysctl.conf configuration. This doesn't happen with Debian Etch, but I can't use it in our production environment...

If no solution arises, I will have to switch to pound for load-balancing :(

---

