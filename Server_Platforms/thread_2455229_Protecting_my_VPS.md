---
title: "Protecting my VPS"
date: 2020-12-15
forum: Server Platforms
---

### Post by atux on 2020-12-15
i bought a VPS to create an OpenVPN server. I got my Openvpn service up and running and i would like to ask for some help with the rest of the iptables please. Seems that i got a ton of port scanners and i do not know how to block them. I go the code from [https://bash.cyberciti.biz/firewall/linux-iptables-firewall-shell-script-for-standalone-server/](https://bash.cyberciti.biz/firewall/linux-iptables-firewall-shell-script-for-standalone-server/) 
The thing is that the /Scripts/blockedips.txt does not contain anything. I would appreciate all the help available please.

here is my code:
```
#!/bin/bashIPT="/sbin/iptables"
SPAMLIST="blockedip"
SPAMDROPMSG="BLOCKED IP DROP"
 
echo "Starting IPv4 Wall..."
$IPT -F
$IPT -X
$IPT -t nat -F
$IPT -t nat -X
$IPT -t mangle -F
$IPT -t mangle -X
modprobe ip_conntrack
 
[ -f /atux/Scripts/blocked.ips.txt ] && BADIPS=$(egrep -v -E "^#|^$" /atux/Scripts/blocked.ips.txt)
 
PUB_IF="eth0"
 
#unlimited
$IPT -A INPUT -i lo -j ACCEPT
$IPT -A OUTPUT -o lo -j ACCEPT
 
# DROP all incomming traffic
$IPT -P INPUT DROP
$IPT -P OUTPUT DROP
$IPT -P FORWARD DROP
 
if [ -f /atux/Scripts/blocked.ips.txt ];
then
# create a new iptables list
$IPT -N $SPAMLIST
 
for ipblock in $BADIPS
do
   $IPT -A $SPAMLIST -s $ipblock -j LOG --log-prefix "$SPAMDROPMSG"
   $IPT -A $SPAMLIST -s $ipblock -j DROP
done
 
$IPT -I INPUT -j $SPAMLIST
$IPT -I OUTPUT -j $SPAMLIST
$IPT -I FORWARD -j $SPAMLIST
fi
 
# Block sync
$IPT -A INPUT -i ${PUB_IF} -p tcp ! --syn -m state --state NEW  -m limit --limit 5/m --limit-burst 7 -j LOG --log-level 4 --log-prefix "Drop Sync"
$IPT -A INPUT -i ${PUB_IF} -p tcp ! --syn -m state --state NEW -j DROP
 
# Block Fragments
$IPT -A INPUT -i ${PUB_IF} -f  -m limit --limit 5/m --limit-burst 7 -j LOG --log-level 4 --log-prefix "Fragments Packets"
$IPT -A INPUT -i ${PUB_IF} -f -j DROP
 
# Block bad stuff
$IPT  -A INPUT -i ${PUB_IF} -p tcp --tcp-flags ALL FIN,URG,PSH -j DROP
$IPT  -A INPUT -i ${PUB_IF} -p tcp --tcp-flags ALL ALL -j DROP
 
$IPT  -A INPUT -i ${PUB_IF} -p tcp --tcp-flags ALL NONE -m limit --limit 5/m --limit-burst 7 -j LOG --log-level 4 --log-prefix "NULL Packets"
$IPT  -A INPUT -i ${PUB_IF} -p tcp --tcp-flags ALL NONE -j DROP # NULL packets
 
$IPT  -A INPUT -i ${PUB_IF} -p tcp --tcp-flags SYN,RST SYN,RST -j DROP
 
$IPT  -A INPUT -i ${PUB_IF} -p tcp --tcp-flags SYN,FIN SYN,FIN -m limit --limit 5/m --limit-burst 7 -j LOG --log-level 4 --log-prefix "XMAS Packets"
$IPT  -A INPUT -i ${PUB_IF} -p tcp --tcp-flags SYN,FIN SYN,FIN -j DROP #XMAS
 
$IPT  -A INPUT -i ${PUB_IF} -p tcp --tcp-flags FIN,ACK FIN -m limit --limit 5/m --limit-burst 7 -j LOG --log-level 4 --log-prefix "Fin Packets Scan"
$IPT  -A INPUT -i ${PUB_IF} -p tcp --tcp-flags FIN,ACK FIN -j DROP # FIN packet scans
 
$IPT  -A INPUT -i ${PUB_IF} -p tcp --tcp-flags ALL SYN,RST,ACK,FIN,URG -j DROP
 
# Allow full outgoing connection but no incomming stuff
$IPT -A INPUT -i eth0 -m state --state ESTABLISHED,RELATED -j ACCEPT
$IPT -A OUTPUT -o eth0 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
 
# Allow ssh
$IPT -A INPUT -p tcp --destination-port 55522 -j ACCEPT
 
# allow incomming ICMP ping pong stuff
$IPT -A INPUT -p icmp --icmp-type 8 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
$IPT -A OUTPUT -p icmp --icmp-type 0 -m state --state ESTABLISHED,RELATED -j ACCEPT
 
# Allow port 53 tcp/udp (DNS Server)
$IPT -A INPUT -p udp --dport 53 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
$IPT -A OUTPUT -p udp --sport 53 -m state --state ESTABLISHED,RELATED -j ACCEPT
 
$IPT -A INPUT -p tcp --destination-port 53 -m state --state NEW,ESTABLISHED,RELATED  -j ACCEPT
$IPT -A OUTPUT -p tcp --sport 53 -m state --state ESTABLISHED,RELATED -j ACCEPT
 
# Open port 80
#$IPT -A INPUT -p tcp --destination-port 80 -j ACCEPT
##### Add your rules below ######


# 1194 OpenVPN
$IPT -A INPUT -m state --state NEW -m udp -p udp --dport 1194 -j ACCEPT


#################################################
# enable NAT
#################################################
sysctl -w net.ipv4.ip_forward=1 
$IPT -t nat -A POSTROUTING -o eth0 -j MASQUERADE


#################################################
#OpenVpn_NAT. Allows connected devices to access Internet
#showing the VPSs IP
#################################################
$IPT -A POSTROUTING -s 172.16.1.0/24 -j tun0 -j MASQUERADE
echo 1 > /proc/sys/net/ipv4/ip_forward
#iptables -A FORWARD -i tun0 -o eth0 -j ACCEPT
$IPT -I INPUT -i tun0 -j ACCEPT
$IPT -I FORWARD -i tun0 -j ACCEPT
$IPT -I FORWARD -o tun0 -j ACCEPT
$IPT -I OUTPUT -o tun0 -j ACCEPT
$IPT -I INPUT -t filter -p udp --dport 1723 -j ACCEPT
$IPT -A POSTROUTING -t nat -s 172.16.1.0/24 -j SNAT --to eth0
echo -e "allow openvpn connections\n"




#################################################
# ssh protection
#################################################


$IPT -N ATTACKED 
$IPT -N ATTK_CHECK 
$IPT -A INPUT -p tcp -m tcp --dport 55522 -m recent --update --seconds 86400 --name BANNED --rsource -j DROP
$IPT -A ATTACKED -m recent --update --seconds 600 --hitcount 3 -j LOG --log-prefix "IPTABLES (Rule ATTACKED): " --log-level 7
$IPT -A ATTACKED -m recent --set --name BANNED --rsource -j DROP
$IPT -A ATTK_CHECK -m recent --set --name ATTK --rsource
$IPT -A ATTK_CHECK -m recent --update --seconds 600 --hitcount 3 --name ATTK --rsource -j ATTACKED
$IPT -A ATTK_CHECK -j ACCEPT
##### END your rules ############
 
# Do not log smb/windows sharing packets - too much logging
$IPT -A INPUT -p tcp -i eth0 --dport 137:139 -j REJECT
$IPT -A INPUT -p udp -i eth0 --dport 137:139 -j REJECT
 
# log everything else and drop
$IPT -A INPUT -j LOG
$IPT -A FORWARD -j LOG
$IPT -A INPUT -j DROP
 
exit 0



```

---

### Post by darkod on 2020-12-15
I suggest to learn little about iptables and how to use the basics instead of getting scripts like that. You probably don't understand most of it and making modifications will be more difficult for you.

For examle this script seems to allow port 80. Do you have a webserver running or port 80 at all? Do you want to open it?

In fact if you are only running OpenVPN then basic iptables with fail2ban look enough to give you solid protection.

---

### Post by atux on 2020-12-16
Hi @darkod. the script has commented out the port 80. It is for future reference, only. The script is an enhancement from me, but i am not sure if it covers me or not. The reason i am looking to have it in a script is due to the fact that i have multiple VPS in different providers and i have to find an all in one solution. 
According to the /var/log/messages, the attacked IPs are blocked, but i see an overall rise in system performance during these attack times. At the moment i am blocking them on each attack, but i would like to take it a step further:
-register these IPs in a file
-block the registered IPs for 2 days 
-in second block, then make it a month, without even processing it

---

### Post by atux on 2021-05-25
I have done some work with the iptables and it seems to work, even it is very strict for non used ports. i am trying to add the Spamhaus, but i am not sure that i added it correctly in the iptables that i have. 
In a folder ```
/home/atux/Scripts
``` i have 3 scripts, which are attached
start.sh starts the firewall
stop.fw  stops the firewall
spamhaus.sh updates the spamhaus list in the system
[ATTACH]288547[/ATTACH]
[ATTACH]288548[/ATTACH]
[ATTACH]288549[/ATTACH]

```
0 3 * * * /home/atux/Scripts/spamhaus.sh

```


first the /home/atux/Scripts/blocked.ips.txt does not written anything at all.
Also, is the Spamhaus list correctly added in my iptables firewall? any suggestions on that?

Could someone help me on that please?

---

### Post by TheFu on 2021-05-25
If you are adding single IPs to iptables, one at a time, you'll quickly find that system performance suffers. There is no way to allow access, yet block selected IPs/subnets, without having system utilization rise.  However, you could use **ipset** to make all the blocked subnets part of a fast, single, iptables rule.

I'm concerned about this question: 
> Also, is the Spamhaus list correctly added in my iptables firewall? any suggestions on that?
To output the rules and review each (iptables -L), then it will be easier to solve this.  Look at fail2ban for the easy way to ban single IPs with different periods.

On my vpn server(s), I don't bother blocking attempted connections. It isn't like they will be getting the 4096 key correct. But if you want better limitation, perhaps blocking all inbound connections, then setting up a port knock code that only opens the VPN port to the specific IP would be a better technique for a few VPN users? I've not used port knocking myself.

---

### Post by rsteinmetz70112 on 2021-05-25
I second fail2 ban it will catch the port scanners and block them. It is easy to set up and will provide a degree of security while you work on the iptables.

---

