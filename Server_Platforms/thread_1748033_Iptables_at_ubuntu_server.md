---
title: "Iptables at ubuntu server"
date: 2011-05-03
forum: Server Platforms
---

### Post by alfamuzjak on 2011-05-03
Hello,
Im running Ubuntu server 10.10 on my virtual mashine, and i have 2 questions. I followed some guide about configuring firewall and now im trying to test my firewall...But i dont know how to connect to hackerwatch.org site when i dont have GUI, to perform some udp and tcp scans...Second thing is that i dont even know was my script good configured. I tryed to run my script at ubuntu desktop but something goes wrong so i lost my connection to internet even i had some rules about allowing responces such as internet connection.

So my question are: 
1. Can someone help me with my script and tell me where i made mistakes?
2. How can i connect to that site using command line (im not sure it would have same results if i connect with desktop version where i didnt configured nothing (apache,ftp...)) ?





This is my script:

```
#!/bin/bash

# loading some modules
modprobe ip_tables
modprobe ip_nat_ftp
modprobe iptable_filter
modprobe iptable_nat
modprobe ip_conntrack
modprobe ip_conntrack_ftp

IPT=/sbin/iptables
$IPT -F
$IPT -X

# Policy
$IPT -P OUTPUT DROP
$IPT -P INPUT DROP
$IPT -P FORWARD DROP

$IPT -N SERVICES

# anti-spoofing --> btw this rule always output some error so i commented it
#$IPT -A INPUT --in-interface ! lo --source 127.0.0.0/8 -j DROP

# or ...
#if [ -e /proc/sys/net/ipv4/conf/all/rp_filter ]
#then
#for filtre in /proc/sys/net/ipv4/conf/*/rp_filter
#do
#echo 1 > $filtre
#done
#fi

# No icmp
#echo 1 > /proc/sys/net/ipv4/icmp_echo_ignore_all
#echo 1 > /proc/sys/net/ipv4/icmp_echo_ignore_broadcasts

# smurf attack
$IPT -A INPUT -p icmp -m icmp -m limit --limit 1/second -j ACCEPT

# drop bogus packets
$IPT -A INPUT -m state --state INVALID -j DROP
$IPT -A FORWARD -m state --state INVALID -j DROP
$IPT -A OUTPUT -m state --state INVALID -j DROP

$IPT -t filter -A INPUT -p tcp --tcp-flags FIN,ACK FIN -j DROP
$IPT -t filter -A INPUT -p tcp --tcp-flags ACK,PSH PSH -j DROP
$IPT -t filter -A INPUT -p tcp --tcp-flags ACK,URG URG -j DROP
$IPT -t filter -A INPUT -p tcp --tcp-flags SYN,FIN SYN,FIN -j DROP
$IPT -t filter -A INPUT -p tcp --tcp-flags SYN,RST SYN,RST -j DROP
$IPT -t filter -A INPUT -p tcp --tcp-flags FIN,RST FIN,RST -j DROP
$IPT -t filter -A INPUT -p tcp --tcp-flags ALL FIN,PSH,URG -j DROP

#allowed inputs
$IPT -A INPUT --in-interface lo -j ACCEPT
$IPT -A INPUT -j SERVICES

#allow responses     --> Internet konekcija
$IPT -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT

#allow services

# allow http
$IPT -A SERVICES -p tcp --dport 80 -j ACCEPT
# allow ftp
$IPT -A SERVICES -p tcp -m tcp --dport 21 -j ACCEPT

$IPT -A SERVICES -p tcp -s 0/0 --sport 1024:65535 -d 192.168.1.3 --dport 21 -m state --state NEW,ESTABLISHED -j ACCEPT
$IPT -A SERVICES -p tcp -s 0/0 --sport 1024:65535 -d 192.168.1.3 --dport 1024:65535 -m state --state ESTABLISHED,RELATED -j ACCEPT
$IPT -A SERVICES -p tcp -s 0/0 --sport 1024:65535 -d 192.168.1.3 --dport 20 -m state --state ESTABLISHED -j ACCEPT

$IPT -A OUTPUT -p tcp -s server.ip.address --sport 21 -d 0/0 --dport 1024:65535 -m state --state ESTABLISHED -j ACCEPT
$IPT -A OUTPUT -p tcp -s server.ip.address--sport 1024:65535 -d 0/0 --dport 1024:65535 -m state --state ESTABLISHED -j ACCEPT
$IPT -A OUTPUT -p tcp -s server.ip.address --sport 20 -d 0/0 --dport 1024:65535 -m state --state ESTABLISHED,RELATED -j ACCEPT
# allow ssh
$IPT -A INPUT -p tcp -s 0/0 --sport "sport" -d server.ip.address --dport "dport" -j ACCEPT

# End message
echo " [End iptables rules setting]"

```


P.S. Sorry for my english

---

### Post by lee.bumblebee on 2011-05-03
Hi!

To connect to a website from a server machine (no x server) just install Lynx, a text web browser which you can find in the standard Ubuntu repository.

As for the script, I'll try to have a look at it as soon as I have some spare time :)

[EDIT: I took a look to the script, but it is not very clear to me.. What do you want to accomplish with it?]

See You,
LL

---

### Post by alfamuzjak on 2011-05-03
Thank you, i will try with Lynx...

Im running web and ftp server (school work). Basically i tried to create some "inside" firewall besides of schools primary... 

For example, i need to protect my ftp server on standard ports 20 and 21, apache on 80, and leave only one port (<1024) for ssh access for example 1 computer with specific mac address and maybe 1 range of ip addresses in schools network/workgroup or something (script is not finnished as u can see, it misses part with ssh mac and ip addresses, but in global is allowed ssh access in that random port) - all other ports blocked.

+my scipt include prevention for some basic attacks(anti spoofing,smurf...)        ?!? that sentance looks like im very confident and i know what i am doing, true is that i approximately understand that rules which i took from this forum ;)

And thats all i try to accomplish...I hope u can help me with this when u have time and i hope i didnt confused u cause i am also weak with time - i must finnish soon this project.

Thank you again for your time.

---

### Post by lee.bumblebee on 2011-05-03
Well, a couple of ideas just to get you started:

- The allow_ftp and allow_http rules are ok, keep them..
- Drop the attack protection, it only causes troubles if not implemented VERY well.
- Keep the "DROP when STATE is INVALID" rules, remove the others under "Drop Bogus Packets"
- Allow INPUT traffic TO the SSH port FROM the IP of your client(s) and DROP all the rest.
- DROP ALL input traffic not caught by previous rule (a.k.a.: that's gonna be the last iptables command of the script)
- DON'T DROP ALL INPUT traffic. You'll cut yourself out of the network (think you already got this ;) )

This should be a good starting point.. Good luck, and feel free to ask if you need something else (no full script, tho.. it's a School project ;) )

---

### Post by elico on 2011-05-03
if you want to make sure you dont lock yourself use crontab and a script to load iptables basic rules every 5 minutes or another times that are good for you.

if you want to test you can use NMAP for it..
dont need some strage "hack" site.
nmap will give you many levels and depth of checks on each port UDP\TCP...

---

### Post by alfamuzjak on 2011-05-07
I test recently my firewall and i noticed something, when i turn on my firewall (and lose connection) ...and then try to flash iptables and delete all rules and chains with following:
```
sudo iptables -F          and
sudo iptables -X
```

(all rules are flashed...)
I still dont have connection until i restart server...(only shuntdown and restart works- I alternatively try to restart networking without success, so it must be system restart)

So my conclusion is that something is wrong with loaded modules!...Because it is only rule that are not related with iptables. (only they affect system... )

So my question is **what (necessary) modules i need to load** in my case?

---

### Post by alfamuzjak on 2011-05-08
People please help me, i need some answer as soon as possible.
Thanks

---

### Post by elico on 2011-05-08
it will not clear your tables!
there are couple of options but for starter use
> iptables-saveto see if there are rules that are applied on the firewall.
also try to see the output of
> route -n(if the next thing wont help it's not iptables fault)
and one last thing is to use:

> iptables-restore </tmp/iptables.acceptallcontent of /tmp/iptables.acceptall

```
# Generated by iptables-save v1.4.4 on Sun May  8 22:44:08 2011
*security
:INPUT ACCEPT [882792:598646115]
:FORWARD ACCEPT [337024:154622791]
:OUTPUT ACCEPT [953847:596525288]
COMMIT
# Completed on Sun May  8 22:44:08 2011
# Generated by iptables-save v1.4.4 on Sun May  8 22:44:08 2011
*raw
:PREROUTING ACCEPT [1220304:753524982]
:OUTPUT ACCEPT [953847:596525288]
COMMIT
# Completed on Sun May  8 22:44:08 2011
# Generated by iptables-save v1.4.4 on Sun May  8 22:44:08 2011
*nat
:PREROUTING ACCEPT [5918:738011]
:POSTROUTING ACCEPT [16084:1145752]
:OUTPUT ACCEPT [24268:1738499]
COMMIT
# Completed on Sun May  8 22:44:08 2011
# Generated by iptables-save v1.4.4 on Sun May  8 22:44:08 2011
*mangle
:PREROUTING ACCEPT [1220304:753524982]
:INPUT ACCEPT [883148:598865985]
:FORWARD ACCEPT [337024:154622791]
:OUTPUT ACCEPT [953847:596525288]
:POSTROUTING ACCEPT [1291124:751193621]
COMMIT
# Completed on Sun May  8 22:44:08 2011
# Generated by iptables-save v1.4.4 on Sun May  8 22:44:08 2011
*filter
:INPUT ACCEPT [877:90993]
:FORWARD ACCEPT [0:0]
:OUTPUT ACCEPT [953847:596525288]
COMMIT
# Completed on Sun May  8 22:44:08 2011

```

and if you do use ubuntu most of the basic modules for iptables are loaded with basic installation so..
you dont need to load.

---

