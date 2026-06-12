---
title: "Please can correct this iptables config?"
date: 2011-02-08
forum: Security
---

### Post by acastrolorenzo on 2011-02-08
Hi everyone!

I am creating an iptables config to my server, but im not sure if am doing right.

This is it, iptables.cf : 

[PHP]

iptables -F
iptables -X
iptables -t nat -F
iptables -P INPUT ACCEPT
iptables -P OUTPUT ACCEPT
iptables -P FORWARD ACCEPT
iptables -t nat -P PREROUTING ACCEPT
iptables -t nat -P POSTROUTING ACCEPT

# Accept all from localhot
/sbin/iptables -A INPUT -i lo -j ACCEPT

# Port 80 (www) open, and need add other like ssh or mail
iptables -A INPUT -p tcp --dport 80 -j ACCEPT

# Close from 1 to 1024
iptables -A INPUT -p tcp --dport 1:1024 -j DROP
iptables -A INPUT -p udp --dport 1:1024 -j DROP

# Close the rest
iptables -A INPUT -p tcp --syn --dport 1025:65535 -j DROP
iptables -A INPUT -p udp --syn --dport 1025:65535 -j DROP

[/PHP]Any suggestion? tutorial link? etc.

Thanks in advance! :p

---

### Post by cipherboy_loc on 2011-02-08
Just looking at that, first you open up port 80 for HTTP, but then you close ports 1-1024. I don't know much about IP Tables (other than how to block IP addresses), but I think that might be one of your issues.


Cipherboy

---

### Post by acastrolorenzo on 2011-02-08
Thanks cipherboy, but I think rules are defined by priority, and when close ports, the ones wich where opened before keeps opened. Not sure.

---

### Post by elico on 2011-02-08
what is your problem?
if in any part of the script you are using the full path you should use it in all over your script and you can use a macro.
and then you script will loo like this:
( a nice thing of security is in the sysctl.conf to enable synflood defence in kernel by adding the file
net.ipv4.tcp_syncookies=1
)
also in iptables the rules are from top to buttom and first match rule wins..
[PHP]
IPT=/sbin/iptables
$IPT -F
$IPT -X
$IPT -t nat -F
$IPT -P INPUT ACCEPT
$IPT -P OUTPUT ACCEPT
$IPT -P FORWARD ACCEPT
$IPT -t nat -P PREROUTING ACCEPT
$IPT -t nat -P POSTROUTING ACCEPT


# Accept all from localhot
$IPT -A INPUT -i lo -j ACCEPT

#add this line here to match first the established connections
$IPT -A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT

#you can add these rules to more secure and safe by limiting "3 hits" per second for an ip
#defend from simple DOS
$IPT -A INPUT -i ppp0 -p udp -m udp -m limit --limit 3/sec -m state --state NEW
$IPT -A INPUT -i ppp0 -p tcp -m tcp -m limit --limit 3/sec -m state --state NEW

# Port 80 (www) open, and need add other like ssh or mail (added ports 25,110,143 for mail and 22,21 for ssh+ftp)
$IPT -A INPUT -p tcp -p tcp -m tcp --dport 25,110,143,21,22,80 -j ACCEPT

# ports 22,21 udp for tftp and other stuff of ftp and ssh
$IPT -A INPUT -p udp -m udp --dport 21,22 -j ACCEPT


# Close from 1 to 1024
$IPT -A INPUT -p tcp -m tcp --dport 1:1024 -j DROP
$IPT -A INPUT -p udp -m udp --dport 1:1024 -j DROP

# Close the rest
$IPT -A INPUT -p tcp -m tcp --syn --dport 1025:65535 -j DROP
$IPT -A INPUT -p udp -m udp --syn --dport 1025:65535 -j DROP[/PHP]

---

### Post by acastrolorenzo on 2011-02-08
Thanks Elico,

So, its your ruletable complete to make it run in my server?

Thanks again :p

---

### Post by CharlesA on 2011-02-08
Just use iptables-save and iptables-restore to apply iptables rules. So much easier then using a shell script.

See here: [http://bodhizazen.net/Tutorials/iptables](http://bodhizazen.net/Tutorials/iptables)

---

### Post by elico on 2011-02-09
yes these rules are kind of everything you might need.
and also you can use examples.

this script is only for the basic setup.
i really like iptables-save and restore.
and this link you got is very nice.
there is another one but it's a bit long (in case any one will see it)
[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch14_:_Linux_Firewalls_Using_iptables](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch14_:_Linux_Firewalls_Using_iptables)

---

