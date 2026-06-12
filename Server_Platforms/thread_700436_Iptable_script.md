---
title: "Iptable script"
date: 2008-02-18
forum: Server Platforms
---

### Post by Zemich on 2008-02-18
Hello

I have a bit of a problem, I have made a script for iptable. But when I try to restore it via the terminal it writes "line 8 failed, 22, 28 and so on.
Even the command "iptables -F" it won't take. I did try to comment some of the script but it just moved on to the next command and wrote "line xx failed"

I am no Linux wiz by a long shot. so I need a bit of help.

Here is my script:

#!/bin/bash
#
#
set -x # tjekker script for fejl
#
# Variabler
#WAN_IF="eth0"
#DMZ_IF="eth1"
#LAN_IF="eth2"
WAN_IP="172.16.4.12"
DMZ_IP="10.10.10.2"
LAN_IP="192.168.0.1"
LAN_IP_VPN="192.168.0.2"
WAN_NET="172.16.0.0/16"
LAN_NET="192.168.0.0/24"
DMZ_NET="10.10.10.0/30"
#
#
# Modul Installation
/sbin/modprobe ip_conntrack
/sbin/modprobe ip_conntrack_ftp
/sbin/modprobe ip_nat_ftp
#
#
# Flush iptables og nat tables
iptables -F
iptables -t nat -F
#
# Luk for alt
iptables -P INPUT DROP
iptables -P OUTPUT DROP
iptables -P FORWARD DROP
#
#
iptables -A OUTPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A FORWARD -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
#
#
# Tillader Ping ud fra
# LAN
iptables -A FORWARD -i $LAN_IF -o $WAN_IF -p icmp -j ACCEPT
# DMZ
iptables -A FORWARD -i $DMZ_IF -o $WAN_IF -p icmp -j ACCEPT
iptables -A FORWARD -o $DMZ_IF -i $WAN_IF -p icmp -j ACCEPT
#
#
# Source NAT ved udgående pakker fra LAN siden
iptables -t NAT -A POSTROUTING -s $LAN_NET -o $WAN_IF -j SNAT --to-source $WAN_IP
# Source NAT udgående pakker fra DMZ siden
iptables -t nat -A POSTROUTING -s $DMZ_NET -o $WAN_IF -j SNAT --to-source $WAN_IP
#
#
# Tillad DNS opslag til firewall
iptables -A INPUT -i $LAN_IF -p udp --sport 53 -j ACCEPT
iptables -A OUTPUT -o $LAN_IF -p udp --dport 53 -j ACCEPT
#
# Tillader DNS opslag på DMZ
iptables -A FORWARD -i $DMZ_IF -o $WAN_IF -p udp --dport 53 -j ACCEPT
#
#
# Tillad Samba fra LAN til DMZ
iptables -A FORWARD -i $LAN_IF -o $DMZ_IF -p tcp --dport 139 -j ACCEPT
#
#
#Router alt fra DMZ
iptables -t nat -A PREROUTING -p tcp -s $WAN_NET --dport 1:1722 -j DNAT --to-destination $DMZ_IP
iptables -t nat -A PREROUTING -p tcp -s $WAN_NET --dport 1725:65535 -j DNAT --to-destination $DMZ_IP
iptables -A FORWARD -p tcp -s $WAN_NET -d $DMZ_NET --dport 1:1722 -j ACCEPT
iptables -A FORWARD -p tcp -s $WAN_NET -d $DMZ_NET --dport 1725:65535 -j ACCEPT
#
#
# Tillader routing fra LAN til DMZ på port 700 over 80
# iptables -t nat -A PREROUTING -p tcp -i $LAN_IF --dport 700 -j DNAT --to-destination 10.10.10.2:80
# iptables -A FORWARD -p tcp -s $LAN_NET -d $DMZ_NET -m multiport --dport 700,21 -j ACCEPT
#
#
# Adgang fra LAN til DMZ siden
iptables -A FORWARD -p tcp -s $LAN_NET -d $DMZ_NET --dport 1:65535 -j ACCEPT
#
#
# LAN Siden
# Tillader http, smtp, pop3, ssh fra LAN til firewall
iptables -A INPUT -i $LAN_IF -p tcp -m multiport --dport 80,25,110 -j ACCEPT
iptables -A FORWARD -i $LAN_IF -o $WAN_IF -p all -j ACCEPT
iptables -A INPUT -i $LAN_IF -p tcp --dport 22 -j ACCEPT
#
# VPN
# VPN Tilladelser
iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 1723 -j DNAT --to 192.168.0.2
iptables -t nat -A PREROUTING -i eth0 -p gre -j DNAT --to 192.168.0.2
iptables -A FORWARD -p gre -d $LAN_IP_VPN -j ACCEPT
iptables -A FORWARD -p tcp --dport 1723 -d $LAN_IP_VPN -j ACCEPT
#
#
# Tillad Loopback
iptables -A OUTPUT -o lo -p all -j ACCEPT
iptables -A INPUT -i lo -p all -j ACCEPT
#
#
# Tillader Squid
iptables -A INPUT -i $LAN_IF -p tcp --dport 3128 -j ACCEPT
#
#
# Tillader Internet til webserver
# iptables -A OUTPUT -o $DMZ_IF -p tcp --dport 80 -j ACCEPT
# iptables -A OUTPUT -o $WAN_IF -p tcp --dport 80 -j ACCEPT
#
#
# iptables -t nat -A PREROUTING -i $LAN_IF -p tcp --dport 80 -j DNAT --to 192.168.0.1:3128
# iptables -t nat -A PREROUTING -i $WAN_IF -p tcp --dport 80 -j REDIRECT --to-port 3128
#
#
# Kopier firewall til iptables og kører så hver gang ved opstart af maskinen
iptables-save > /etc/iptables
#

---

### Post by Subliminal Aura on 2008-02-18
Can you post your error messages as I belive that you are not loading the kernel drivers or setting up forwarding correctly.

Since you're using NAT you'll need this in your script :

echo 1 > /proc/sys/net/ipv4/ip_forward

---

### Post by Zemich on 2008-02-18
[http://img225.imageshack.us/img225/8675/69786494gz7.png](http://img225.imageshack.us/img225/8675/69786494gz7.png)

---

### Post by Subliminal Aura on 2008-02-18
Just comment that line out using # at the beginning of the line

Also add forwarding 

echo 1 > /proc/sys/net/ipv4/ip_forward

---

### Post by Zemich on 2008-02-18
line 7 failed...

Line 7 is "echo 1 > /proc/sys/net/ipv4/ip_forward "

Could it be a service that is not running?

---

### Post by Subliminal Aura on 2008-02-18
Sorry can you move that line to after all the modprobes....

(lets also add iptables just in case)

Run the script directly so that we can see the errors ie run

/etc/firewall.sh


#
# Modul Installation
/sbin/modprobe ip_conntrack
/sbin/modprobe ip_conntrack_ftp
/sbin/modprobe ip_nat_ftp
#

Should now be

#
# Modul Installation
/sbin/modprobe ip_tables
/sbin/modprobe ip_conntrack
/sbin/modprobe ip_conntrack_ftp
/sbin/modprobe ip_nat_ftp
echo 1 > /proc/sys/net/ipv4/ip_forward
#


EDIT
PS What is the output from this command

file /etc/firewall.sh

---

### Post by Zemich on 2008-02-18
ok then...

When I run the file directly and I select "Run in Terminal" it opens the terminal and closes it right after. If I select "Run" nada happens.

---

### Post by Subliminal Aura on 2008-02-18
> **Zemich said:**
> ok then...

When I run the file directly and I select "Run in Terminal" it opens the terminal and closes it right after. If I select "Run" nada happens.


open up a terminal and then type this into it.

/etc/firewall.sh

---

### Post by Zemich on 2008-02-18
root@ubuntu:~# /etc/firewall.sh
bash: /etc/firewall.sh /bin/sh^M: Bad interpreter: No such file or directory

---

### Post by Subliminal Aura on 2008-02-18
> **Zemich said:**
> root@ubuntu:~# /etc/firewall.sh
bash: /etc/firewall.sh /bin/sh^M: Bad interpreter: No such file or directory

OK you hava a dos file here can you do a save as unix with that file editor or something ?

If not close down the editor and these commands from the terminal

apt-get install sysutils

cat /etc/firewall.sh | dos2unix > /root/firewall.sh

/etc/firewall.sh

---

### Post by Zemich on 2008-02-18
[http://img138.imageshack.us/img138/6158/55070257bs3.png](http://img138.imageshack.us/img138/6158/55070257bs3.png)

---

### Post by Subliminal Aura on 2008-02-18
Oops sorry the last command should have been...

/root/firewall.sh

---

### Post by Zemich on 2008-02-18
[http://img258.imageshack.us/img258/2796/44776612ma7.png](http://img258.imageshack.us/img258/2796/44776612ma7.png)

---

### Post by Subliminal Aura on 2008-02-18
> **Zemich said:**
> [http://img258.imageshack.us/img258/2796/44776612ma7.png](http://img258.imageshack.us/img258/2796/44776612ma7.png)

You're still running the old script...

Please run

/root/firewall.sh

---

### Post by Zemich on 2008-02-18
I get "Permission denied"

EDIT My fault!

---

### Post by Subliminal Aura on 2008-02-18
> **Zemich said:**
> I get "Permission denied"

chmod 755 /root/firewall.sh

/root/firewall.sh

---

### Post by Zemich on 2008-02-18
[http://img233.imageshack.us/img233/2302/59242486cm8.png](http://img233.imageshack.us/img233/2302/59242486cm8.png)

[http://img409.imageshack.us/img409/1294/44814316qc8.png](http://img409.imageshack.us/img409/1294/44814316qc8.png)
[http://img111.imageshack.us/img111/1458/72433224he2.png](http://img111.imageshack.us/img111/1458/72433224he2.png)

---

### Post by Subliminal Aura on 2008-02-18
Hmmmm inadvertantly somewhere along the lines it has worked.

The following command will show your rules

iptables -L

---

### Post by Zemich on 2008-02-18
[http://img519.imageshack.us/img519/4585/37111573kq8.png](http://img519.imageshack.us/img519/4585/37111573kq8.png)

---

### Post by Subliminal Aura on 2008-02-18
so you're set up now all youve got to work  out is where to place your iptables-save file so that it runs automatically at boot.

Soz I'm mobile now so cant post links

---

### Post by Zemich on 2008-02-18
Thank you very much :)

---

### Post by Zemich on 2008-02-18
Now when I try "/etc/firewall.sh" it show an error.

[http://img134.imageshack.us/img134/1644/43116803dz4.png](http://img134.imageshack.us/img134/1644/43116803dz4.png)

---

