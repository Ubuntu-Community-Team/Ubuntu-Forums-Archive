---
title: "need help setting up gateway...."
date: 2008-09-28
forum: Server Platforms
---

### Post by meomike2000 on 2008-09-28
i have my server up and running and have installed second ethernet card (eth1) and have it set up with static ip.
my first ethernet card (eth0) is connected to modem and that connection is working fine. i want to add couple windows xp computers to the second ethernet card (eth1) and let them share the internet connection of the server. is this possible and if so what more do i need to do to get it to work. my windows xp machine can ping and see the ubuntu server with this setup, buth they can not get out to the internet.

server version is 8.04.0

thanks in advance

---

### Post by cariboo on 2008-09-29
Have a look at his howto:

[http://ubuntuforums.org/showthread.php?t=713874](http://ubuntuforums.org/showthread.php?t=713874)

It should get you started towards what you would like to achieve.

Jim

---

### Post by ady on 2008-09-29
or you can try this script


[FONT="Lucida Console"]#!/bin/sh
IPEXT="eth0 ip" 
IPTABLES="/sbin/iptables"

EXTIF=eth0
INTIF=eth1
LOCALNET="192.168.0.0/255.255.255.0"

echo 1 > /proc/sys/net/ipv4/tcp_syncookies
echo 1 > /proc/sys/net/ipv4/icmp_echo_ignore_broadcasts
echo 1 > /proc/sys/net/ipv4/ip_forward

echo 'Flushing previous rules'
$IPTABLES -F
$IPTABLES -X
CHAINS=`cat /proc/net/ip_tables_names 2>/dev/null`
for i in $CHAINS
do
$IPTABLES -t $i -F
done ;
for i in $CHAINS
do
$IPTABLES -t $i -X
done;


echo 'Internet access'
$IPTABLES -t nat -A PREROUTING -i $INTIF -s 192.168.0.2 -j ACCEPT
$IPTABLES -t nat -A PREROUTING -i $INTIF -s 192.168.0.3 -j ACCEPT
$IPTABLES -t nat -A PREROUTING -i $INTIF -s 192.168.0.4 -j ACCEPT
$IPTABLES -t nat -A PREROUTING -i $INTIF -s 192.168.0.5 -j ACCEPT

$IPTABLES -t nat -A PREROUTING -i $INTIF -j DROP

$IPTABLES -t nat -A POSTROUTING -o $EXTIF -s $LOCALNET -j SNAT --to-source $IPEXT[/FONT]
 

let's suppose your script was saved in /etc/script

[FONT="Lucida Console"]#chmod +x /etc/script
#/etc/script[/FONT]

---

