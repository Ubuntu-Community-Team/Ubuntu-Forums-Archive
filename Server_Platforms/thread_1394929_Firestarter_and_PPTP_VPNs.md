---
title: "Firestarter and PPTP VPNs"
date: 2010-01-31
forum: Server Platforms
---

### Post by BlackBird28 on 2010-01-31
Hi guys,
I've searched almost all the net lookin for a fix for my problem but found nothing good. I'm runnin a pptp vpn server on ubuntu 9.10 with firestarter firewall, if I disable it all works but activating firestarter it keeps blocking connections on GRE protocol.

This is my user-pre file:
> #$IPT -A INPUT -i eth0 -p all -s 0.0.0.0/0 -j ACCEPT
$IPT -A OUTPUT -p all -d 192.168.1.1/0 -j ACCEPT
$IPT -A FORWARD -i eth0 -p all -s 0.0.0.0/0 -d 0.0.0.0/0 -j ACCEPT



$IPT -A INPUT -s 224.0.0.0/8 -d 0/0 -j ACCEPT
$IPT -A INPUT -s 0/0 -d 224.0.0.0/8 -j ACCEPT
$IPT -A OUTPUT -s 224.0.0.0/8 -d 0/0 -j ACCEPT
$IPT -A OUTPUT -s 0/0  -d 224.0.0.0/8 -j ACCEPT

$IPT -A INPUT -i tap+ -j ACCEPT
$IPT -A OUTPUT -o tap+ -j ACCEPT
$IPT -A FORWARD -i tap+ -j ACCEPT

#Abilitare le connessioni VPN PPTP
SERVER=192.168.1.1 #SERVER VPN INTERNO

$IPT -A FORWARD -i $IF -o $INIF -p tcp --dport 1723 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
$IPT -t nat -A PREROUTING -i $IF -p tcp --dport 1723 -j DNAT --to $SERVER
$IPT -A FORWARD -i $IF -o $INIF -p 47 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
$IPT -t nat -A PREROUTING -i $IF -p 47 -j DNAT --to $SERVER


This is the result of editing the file as described in various solutions I found on the net with no fix.

Any ideas?

---

### Post by sanjiro on 2010-02-01
[SIZE=3]I have the same problem and this is my user-pre file[/SIZE]:

[SIZE=1]# Forward PPTP VPN client traffic
$IPT -A FORWARD -i $IF -o $INIF -p tcp --dport 1723 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
$IPT -A FORWARD -i $IF -o $INIF -p 47 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
$IPT -A FORWARD -i $INIF -o $IF -p 47 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT

# Forward PPTP VPN connections to internal server
SERVER=192.168.2.50 # Internal VPN server

$IPT -A FORWARD -i $IF -o $INIF -p tcp --dport 1723 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
$IPT -t nat -A PREROUTING -i $IF -p tcp --dport 1723 -j DNAT --to $SERVER
$IPT -A FORWARD -i $IF -o $INIF -p 47 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
$IPT -t nat -A PREROUTING -i $IF -p 47 -j DNAT --to $SERVER


[SIZE=3]Any ideas?[/SIZE] 


 [/SIZE]

---

### Post by R.Bucky on 2010-02-03
*2 on the firewall issue. Just disable it!!! Make sure you have a solid firewall like pfSense...

---

### Post by koenn on 2010-02-04
it would be helpful if you explain tour network layout : iptables rules will jave to be different depending on whether they run on the same host as the vpn server or not.

also, posting a rule set is quite useless if you don't mention what the default policies are

---

### Post by ub-newbie on 2010-12-26
I'm trying to set up PPTP between Ubuntu 10.04 x64 Desktop & IPOD.
Desktop is behind Linksys router, but is still running Firestarter 1.0.3.  

PPTP VPN is running on Ubuntu box (so I can access UPNP transcoding server)

Firestarter page says :*Firestarter 1.0 does not support VPN configurations without some tweaking. VPN capability in Firestarter is currently planned for version 1.1. * but they only give examples for MS, Open, Cisco, and Nortel.  

I REALLY want to keep Firestarter (so suggestions of other firewalls will not solve this issue).

Right now I have Port 1723, and 500, open to all.  VPN works with Firestarter disabled, so I can assume Router setup is good.    

Has anyone got this working?

---

### Post by bodhi.zazen on 2010-12-26
> **ub-newbie said:**
> I'm trying to set up PPTP between Ubuntu 10.04 x64 Desktop & IPOD.
Desktop is behind Linksys router, but is still running Firestarter 1.0.3.  

PPTP VPN is running on Ubuntu box (so I can access UPNP transcoding server)

Firestarter page says :*Firestarter 1.0 does not support VPN configurations without some tweaking. VPN capability in Firestarter is currently planned for version 1.1. * but they only give examples for MS, Open, Cisco, and Nortel.  

I REALLY want to keep Firestarter (so suggestions of other firewalls will not solve this issue).

Right now I have Port 1723, and 500, open to all.  VPN works with Firestarter disabled, so I can assume Router setup is good.    

Has anyone got this working?

First, IMHO, you really should not be running X on a server.

Second, you answered your own question, it is not supported in Firestarter.

There are several alternates, really you should use a web interface (webmin or similar) and either learn iptables (it is not *that* hard) or use an alternate tool (ssh for example).

---

### Post by ub-newbie on 2010-12-27
First, let me address Bodhi.Zazen....
If it helps you, think of it not as X on a server, but a server on X..

As my quote says "without some tweaking"... I was looking for advice from someone with the skills to do that tweaking.. 

But, I took your advice and removed Firestarter and am just using Iptables now...

For anyone else looking at this thread, here is what I learned in this process.  
Install (or make sure you already have)
[LIST=1]
[*]Openssh-server
[*]PPP
[*]PPTP-linux
[*]bcrelay
[/LIST]

Then I edited ```
/etc/pptpd.conf
```
by uncommenting ```
enable bcrelay eth1
``` (or eth0, which ever you use).
and set your local & remote IP's
```
# Local network ip
localip 10.0.4.1
# the IP the VPN will give
remoteip 10.0.4.2-4
```
(the man page is very usefull)

Then I edited ```
/etc/ppp/pptpd-options
```to set MTU/R and assign DNS (not sure if this is necessary).
```
ms-dns 8.8.8.8
ms-dns 8.8.4.4
mtu 1490
mru 1490 
```

After that I went into /etc/sysctl.conf and uncommented ```

net.ipv4.ip_forward=1
```

Then off to ```
/etc/ppp/chap-secrets
``` to set the username & password.  

Then restarted the PPTP with ```
/etc/init.pptpd restart
```

Enabled port forwarding in my router for port 1723, enabled PPTP VPN passthrough.

At this point I could connect to the VPN, but that was about all (ping yes, all others no).  After looking at the logs I could tell it was a firewall issue (hence my original post).  So, I removed Firestarter (I doesn't look like it is being maintained anymore) & went with Iptables.

The rule in iptables that got things going for me was ```
sudo iptables -t nat -A POSTROUTING -j MASQUERADE
```  
This enabled the traffic coming in on the VPN to go back out to my router, and the Internet...  I won't post all my rules here, I can't take the criticism...

So now I can connect via VPN on my IPOD to my Ubuntu GUI server running an Alpha version of the AirVideo server that transcodes my media into IPOD format... or the UPNP server in XBMC, or to Mediatomb..etc, ad nauseam

---

### Post by bodhi.zazen on 2010-12-27
congrats, looks as if you learned a ton =)

---

