---
title: "iptables - troubles with port forwarding"
date: 2014-07-14
forum: Server Platforms
---

### Post by jagrok on 2014-07-14
Dear ALL

I was builded router on my miniPC with 2 NICs.
I decided to leave Debian for Ubuntu server after many noticed troubles with this system ( spent many days for troubleshooting )
Internet getting on interface p4p1 called as WAN , dhcp server working on interface p1p1 called as LAN.
At this moment 
My machine is visible for SSH and WEB from INTERNET, answering for ping

Because i do not have a lot experience with Linux, i get from my friends firewall script based on iptables, which was edited and applicated for my own use.
I was trying 2 scripts from other people. Whenever which script i was used, unfortunately i noticed a lot of troubles with port forwarding.
Any restart rules, or rebooting the machine not giving effect.
Always problem is the same.
This is the last thing which i need to finish my home project.


Every time when i was trying to forward port for any machine in my local network i cannot connect.

Look at my script and please tell me why it doesnt working for me ? 
Where i`m make a fault ?

```
#!/bin/bash




### BEGIN INIT INFO
# Provides:          firewall.sh
# Required-Start:    $local_fs $remote_fs
# Required-Stop:     $local_fs $remote_fs
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: Start daemon at boot time
# Description:       Enable service provided by daemon.
### END INIT INFO


echo "0" > /proc/sys/net/ipv4/icmp_echo_ignore_all
echo "1" > /proc/sys/net/ipv4/ip_forward




global=$(ip addr show p4p1 | grep -o 'inet [0-9]\+\.[0-9]\+\.[0-9]\+\.[0-9]\+' | grep -o [0-9].*)
echo $global
export WAN=p4p1
export LAN=p1p1


###
### CLEANING
###
iptables -F
iptables -F -t nat
iptables -F -t mangle


###
### DEFAULT POLITICS
###
iptables -P OUTPUT ACCEPT
iptables -P FORWARD ACCEPT
###
### INCOMING CONNECTION DROP
###
iptables -P INPUT DROP


###
### LEAVE ESTABLISHED CONNECTION
###
iptables -A INPUT ! -i ${WAN} -j ACCEPT
iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT


###
###DOCSIS compliant cable modems Drop without logging.
###
iptables -A INPUT -p ALL -d 224.0.0.1 -j DROP


###
### ICMP REQUEST
###
iptables -A INPUT -p icmp -m state --state NEW -j ACCEPT


###
### OPENING TCP PORTS
###
iptables -A INPUT -p TCP --dport 2788 -i ${WAN} -j ACCEPT
iptables -A INPUT -p TCP --dport 80 -i ${WAN} -j ACCEPT
iptables -A INPUT -p TCP --dport 3074 -i ${WAN} -j ACCEPT
iptables -A INPUT -p TCP --dport 8080 -i ${WAN} -j ACCEPT
iptables -A INPUT -p TCP --dport 8888 -i ${WAN} -j ACCEPT
iptables -A INPUT -p TCP --dport 8988 -i ${WAN} -j ACCEPT
iptables -A INPUT -p TCP --dport 8999 -i ${WAN} -j ACCEPT
iptables -A INPUT -p TCP --dport 9200 -i ${WAN} -j ACCEPT
iptables -A INPUT -p TCP --dport 8002 -i ${WAN} -j ACCEPT
iptables -A INPUT -p TCP --dport 8111 -i ${WAN} -j ACCEPT
iptables -A INPUT -p TCP --dport 5455 -i ${WAN} -j ACCEPT
iptables -A INPUT -p TCP --dport 1723 -i ${WAN} -j ACCEPT
iptables -A INPUT -p TCP --dport 53 -i ${WAN} -j ACCEPT


###
### OPENING UDP PORTS
###
iptables -A INPUT -p UDP --dport 1194 -i ${WAN} -j ACCEPT
iptables -A INPUT -p UDP --dport 53 -i ${WAN} -j ACCEPT
iptables -A INPUT -p UDP --dport 3074 -i ${WAN} -j ACCEPT
iptables -A INPUT -p UDP --dport 5060 -i ${WAN} -j ACCEPT


###
### FORWARDING PORTS
###
# Xbox Live
iptables -t nat -A PREROUTING -p tcp --dport 3074 -i ${WAN} -j DNAT --to 192.168.1.16
iptables -t nat -A PREROUTING -p udp --dport 3074 -i ${WAN} -j DNAT --to 192.168.1.16
iptables -t nat -A PREROUTING -p udp --dport 88 -i ${WAN} -j DNAT --to 192.168.1.16
iptables -t nat -A PREROUTING -p tcp --dport 53 -i ${WAN} -j DNAT --to 192.168.1.16
iptables -t nat -A PREROUTING -p udp --dport 53 -i ${WAN} -j DNAT --to 192.168.1.16
# SYNOLOGY
iptables -t nat -A PREROUTING -p udp --dport 1194 -i ${WAN} -j DNAT --to 192.168.1.10
iptables -t nat -A PREROUTING -p tcp --dport 1723 -i ${WAN} -j DNAT --to 192.168.1.10
iptables -t nat -A PREROUTING -p tcp --dport 5000 -i ${WAN} -j DNAT --to 192.168.1.10
# WEBCAM
iptables -t nat -A PREROUTING -p tcp --dport 8080 -i ${WAN} -j DNAT --to 192.168.1.20
# VUDUO
iptables -t nat -A PREROUTING -p tcp --dport 5455 -i ${WAN} -j DNAT --to 192.168.1.4
iptables -t nat -A PREROUTING -p tcp --dport 8988 -i ${WAN} -j DNAT --to 192.168.1.4:80
iptables -t nat -A PREROUTING -p tcp --dport 8002 -i ${WAN} -j DNAT --to 192.168.1.4
iptables -t nat -A PREROUTING -p tcp --dport 8111 -i ${WAN} -j DNAT --to 192.168.1.4:8001
# PHONE
iptables -t nat -A PREROUTING -p tcp --dport 5060 -i ${WAN} -j DNAT --to 192.168.1.254
# JNIOR
iptables -t nat -A PREROUTING -p tcp --dport 8999 -i ${WAN} -j DNAT --to 192.168.1.9:80
iptables -t nat -A PREROUTING -p tcp --dport 9200 -i ${WAN} -j DNAT --to 192.168.1.9
###
### MASQUARADA
###
iptables -t nat -A POSTROUTING -o ${WAN} -j MASQUERADE

```

---

### Post by Doug S on 2014-07-14
Hi and welcome to Ubuntu forums.

I think you will have to give us more specifics and hints about your port forwarding troubles, as your script looks O.K. to me (which doesn't mean I didn't miss something obvious).

You probably do NOT want to port forward your dns (port 53) stuff to your xbox, so remove that.

---

### Post by jagrok on 2014-07-15
> **Doug S said:**
> Hi and welcome to Ubuntu forums.

I think you will have to give us more specifics and hints about your port forwarding troubles, as your script looks O.K. to me (which doesn't mean I didn't miss something obvious).

You probably do NOT want to port forward your dns (port 53) stuff to your xbox, so remove that.


Hello, thank you for your replay.
About my problem, yes the script is ok, and rules looking ok, becouse today when i was checking from the other site ( other internet connection ) i was suprised becouse my forwarding is working.
Only what i notice, that i cannot check from my local network behind server.
How to enable this to check if forwarding working ok from the internal network ? 

Thanks for your helping.
About xbox, i found list of ports on the microsoft, so i enable it.

---

### Post by Doug S on 2014-07-15
> **jagrok said:**
> How to enable this to check if forwarding working ok from the internal network ?You cann't.

Thanks for reporting back.

---

