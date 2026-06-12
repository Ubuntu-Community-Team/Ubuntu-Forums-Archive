---
title: "Transparent Squid + iptables"
date: 2007-12-27
forum: Server Platforms
---

### Post by numeritos on 2007-12-27
Hi, I had setup a regular proxy and it was working just fine, but when I tried to use Outlook Express on a client PC it didn't work. So I decided to make the proxy transparent and handle all the packets with iptables. 

Here are the rules:
```

#!/bin/bash

iptables -F
iptables -X
iptables -t nat -F
iptables -t nat -X
iptables -t mangle -F
iptables -t mangle -X

echo 1 > /proc/sys/net/ipv4/ip_forward
echo "nameserver 200.51.211.7" > /etc/resolv.conf
echo "nameserver 200.51.212.7" >> /etc/resolv.conf
echo "nameserver 192.168.1.1" >> /etc/resolv.conf

iptables -t nat -A PREROUTING -i eth0 -p TCP --dport 80 -j REDIRECT --to-port 3128
iptables -t nat -A POSTROUTING -o eth1 -p TCP --dport 22 -j MASQUERADE
iptables -t nat -A POSTROUTING -o eth1 -p TCP --dport 25 -j MASQUERADE
iptables -t nat -A POSTROUTING -o eth1 -p TCP --dport 53 -j MASQUERADE
iptables -t nat -A POSTROUTING -o eth1 -p UDP --dport 53 -j MASQUERADE
iptables -t nat -A POSTROUTING -p TCP --dport 110 -j MASQUERADE
iptables -t nat -A POSTROUTING -p TCP --dport 143 -j MASQUERADE


```

I also added the word "transparent" next to what I had put on the "http_port" line. It just doesn't work, but when I put the sites IP's instead of the URL, it works just fine. I suppose it is a DNS problem, but I have put my ISP's DNS in resolv.conf file! I don't understand why it's not working.
On the client PC's both  the default gateway and the DNS is the proxy server LAN IP.

Any clues what the problem is?

---

### Post by koenn on 2007-12-27
If I remember correctly, Outlook Express is a mail client, and talks to mail servers on port 25 and 110. Squid is a web proxy, so it's not quite clear what you're trying to achieve. Redirecting port 80 to 3128 is not going to help, it would seem.

---

### Post by numeritos on 2007-12-27
> **koenn said:**
> If I remember correctly, Outlook Express is a mail client, and talks to mail servers on port 25 and 110. Squid is a web proxy, so it's not quite clear what you're trying to achieve. Redirecting port 80 to 3128 is not going to help, it would seem.
Precisely... That's why I'm not trying to make Squid handle SMTP neither POP3 (as it just can't anyway). I'm making it transparent to its users and sending mails directly over the Internet

---

### Post by koenn on 2007-12-27
> **numeritos said:**
> Hi, I had setup a regular proxy and it was working just fine, but when I tried to use Outlook Express on a client PC it didn't work. So I decided to make the proxy transparent and handle all the packets with iptables. 

That reads as : I have a problem with a _mail (smtp/pop)_ client, and I'm trying to fix it by changing my_ web (http)_ proxy config.
What's wrong with leaving the web proxy as it was (i.e. working), and fix the mail problem ? Why do you think making your web proxy "transparent" is going to halp to make the email problem go away ?

forget the REDIRECT for a moment. 
Apparently you need MASQUERADING, and you want to limit outgoung traffic to dns, ssh, and email. 
try something this (needs work) :```

IF_WAN="eth0"
iptables -t nat -A POSTROUTING -o $IF_WAN -j MASQUERADE

iptables -A FORWARD -m state --state ESTABLISHED,RELATED -j ACCEPT

for tcp_ports in 22 143 25 110 53;  do
    iptables -A FORWARD -p tcp --dport $tcp_port  -o $IF_WAN -j ACCEPT
done

for udp_ports in 53 ; do
     iptables -A FORWARD -p tcp --dport $udp_port  -o $IF_WAN -j ACCEPT
done



```
## you'll also need INPUT and OUTPUT rules to allow access to the server itself (the packets that arent routed / forwarded, eg acces to your DNS server, proxy server, etc.

---

### Post by numeritos on 2007-12-27
I do not want to make it transparent, I NEED to make it transparent. Outlook Express uses its "designated" (Internet Explorer) to configure its connection. If I use a regular proxy, it just won't work as it will try to use a web proxy for smtp and pop3.

As you can see in my iptables rules, I already use masquerade for the ports I don't want Squid to handle

---

### Post by koenn on 2007-12-27
> **numeritos said:**
> I do not want to make it transparent, I NEED to make it transparent. Outlook Express uses its "designated" (Internet Explorer) to configure its connection. If I use a regular proxy, it just won't work as it will try to use a web proxy for smtp and pop3.

Read what you just said : that would mean that, from 1995 till now, EVERY Windows user has had to find a transparent proxy to make Outlook Express work. You really believe that ? 

True, you can manage internet connections settings (eg access the web trhough dial-in or LAN, etc) from a tab in IE Options, and those will apply to other MS programs as well, but even a Microsoft programmer wouldn't make a mail client use a web proxy - it would never work. 

> **numeritos said:**
> 
As you can see in my iptables rules, I already use masquerade for the ports I don't want Squid to handle
Have a look at my ip tables rules, and note how they're different. 

you try to set a MASQUERADE rule for each service port, and don't have any ACCEPT rules. Mine set MASQUARADE for everything that goes out to the internet, then set ACCEPT for traffic you want to allow out. 
Mine work.

---

### Post by numeritos on 2007-12-28
Nevermind, I've got everything working with a transparent proxy. Mails are going directly throught the Internet and it's working like a charm.

I think you didn't understand what I wanted to say, but thanks anyway for trying to help

---

### Post by greenday on 2008-02-18
> **numeritos said:**
> Nevermind, I've got everything working with a transparent proxy. Mails are going directly throught the Internet and it's working like a charm.

I think you didn't understand what I wanted to say, but thanks anyway for trying to help

I have a same problem like you, so please tell me the solution.
thanks

---

### Post by chizo on 2008-02-21
:guitar: First sorry for my english..is so bad!!

Numeritos: Obviously you problem is the DNS. I think that you Should Specifying the input and output for DNS port.

Something Something like this:

ppp0 INTERNET   eth1 LAN
---------------------------------------------------
#!/bin/sh

modprobe ip_conntrack
modprobe ip_conntrack_ftp

fw="/usr/sbin/iptables"

iptables -F


#------------------------Rechazo todo por Default

$fw -P INPUT DROP
$fw -P OUTPUT DROP
$fw -P FORWARD DROP

#------------------------Reglas generales

#----Forwardea todo el tcp, controla el protocolo de 3 vias y fija el tamano del paquete

$fw -A FORWARD -p tcp --tcp-flags SYN,RST SYN -m tcpmss --mss 1400:1536 -j TCPMSS --clamp-mss-to-pmtu

#-----Permisos para el localhost

$fw -A INPUT -i lo -j ACCEPT
$fw -A OUTPUT -o lo -j ACCEPT

#-----Permite Conexiones Establecidas y Relacionadas

$fw -A INPUT -i ppp+ -m state --state ESTABLISHED,RELATED -j ACCEPT
$fw -A OUTPUT -o ppp+ -m state --state ESTABLISHED,RELATED -j ACCEPT
$fw -A INPUT -i eth1 -m state --state ESTABLISHED,RELATED -j ACCEPT
$fw -A OUTPUT -o eth1 -m state --state ESTABLISHED,RELATED -j ACCEPT

#----Rechaza los paquetes invalidos

$fw -A INPUT -i ppp+ -m state --state INVALID -j DROP
$fw -A OUTPUT -o ppp+ -m state --state INVALID -j DROP
$fw -A INPUT -i eth1 -m state --state INVALID -j DROP
$fw -A OUTPUT -o eth1 -m state --state INVALID -j DROP
#---este modulo esta en prueba.....OJO!!
$fw -A INPUT -i ppp+ -m unclean -j DROP
$fw -A OUTPUT -o ppp+ -m unclean -j DROP
$fw -A INPUT -i eth1 -m unclean -j DROP
$fw -A OUTPUT -o eth1 -m unclean -j DROP



#-----------------------------InPUT PPP0

#----DHCP BootP
$fw -A INPUT -i ppp+ -p udp -s 0.0.0.0/0 --dport 67 -m state --state NEW -j ACCEPT
$fw -A INPUT -i ppp+ -p udp -s 0.0.0.0/0 --dport 68 -m state --state NEW -j ACCEPT



#-----------------------------OUTPUT ppp0

#----DHCP BootP
$fw -A OUTPUT -o ppp+ -p udp -s 0.0.0.0/0 --dport 67 -m state --state NEW -j ACCEPT
$fw -A OUTPUT -o ppp+ -p udp -s 0.0.0.0/0 --dport 68 -m state --state NEW -j ACCEPT
#----Ftp
$fw -A OUTPUT -o ppp+ -p tcp -d 0.0.0.0/0 --dport 21 -m state --state NEW -j ACCEPT
#----Http
$fw -A OUTPUT -o ppp+ -p tcp -d 0.0.0.0/0 --dport 80 -m state --state NEW -j ACCEPT
#----HTTPS/SSL
$fw -A OUTPUT -o ppp+ -p tcp -d 0.0.0.0/0 --dport 443 -m state --state NEW -j ACCEPT
#----Dns
$fw -A OUTPUT -o ppp+ -p udp -d 0.0.0.0/0 --dport 53 -m state --state NEW -j ACCEPT
$fw -A OUTPUT -o ppp+ -p tcp -d 0.0.0.0/0 --dport 53 -m state --state NEW -j ACCEPT

#---POP3 and SMTP "NAT!!"
$fw -A POSTROUTING -t nat -o ppp0 -p tcp --dport110 -j MASQUERADE
$fw -A POSTROUTING -t nat -o ppp0 -p tcp --dport25 -j MASQUERADE


.....etc..



I hope that this help you!!

---

