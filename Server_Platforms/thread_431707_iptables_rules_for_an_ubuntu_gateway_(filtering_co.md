---
title: "iptables rules for an ubuntu gateway (filtering connections to and from Internet)"
date: 2007-05-03
forum: Server Platforms
---

### Post by Zingaro2002 on 2007-05-03
I followed this article:
Setting up a simple Debian gateway
[http://www.debian-administration.org/articles/23](http://www.debian-administration.org/articles/23)
on an ubuntu server 6.10 linux box and it worked perfectly!

(many thanks to the author!!!)

Now I only need to put some limitations (but I don't know iptables rules...) in 00-firewall script.
This script is loaded at startup and it is:
```

#!/bin/sh

PATH=/usr/sbin:/sbin:/bin:/usr/bin

#
# delete all existing rules.
#
iptables -F
iptables -t nat -F
iptables -t mangle -F
iptables -X

# Always accept loopback traffic
iptables -A INPUT -i lo -j ACCEPT


# Allow established connections, and those not coming from the outside
iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A INPUT -m state --state NEW -i ! eth1 -j ACCEPT
iptables -A FORWARD -i eth1 -o eth0 -m state --state ESTABLISHED,RELATED -j ACCEPT

# Allow outgoing connections from the LAN side.
iptables -A FORWARD -i eth0 -o eth1 -j ACCEPT

# Masquerade.
iptables -t nat -A POSTROUTING -o eth1 -j MASQUERADE

# Don't forward from the outside to the inside.
iptables -A FORWARD -i eth1 -o eth1 -j REJECT

# Enable routing.
echo 1 > /proc/sys/net/ipv4/ip_forward

```

Now I want that :
- ONLY some MAC ADDRESSES (I decide which ones) must be able to use this gateway to surf the net
AND
- machines behind the gateway can access only some ports (say ONLY 80) and estabilish connections only to/from some google subdomains (say ####.google.com and maps.google.it)

Well, my users should use Google earth (that makes connections to various ####.google.com domains) and [http://maps.google.it](http://maps.google.it)

These must be THE ONLY CONNECTIONS ENABLED to and from Internet.

No other internet connection should be available through the gateway (no ssh, no smtp, no pop, no emule, no ftp, and so on...).

Can you help me to implement the right iptables rules (without using any proxy)?

How should I modify that script?

Thanks in advance for any suggestion.

---

### Post by Bill007 on 2007-05-03
Kia Ora Zingaro2002

here is a great way to set up packet forwarding on a server edgy 6.10 
with 2 network cards eth0 facing the WAN 192.168.1.4 and eth1 is facing the LAN 192.168.2.100 these are my ip addresses as an example

eth1 is  MASQUERADED out 

Take what you need our use it

Make a file called /etc/init.d/iptables and make it look something like this

sudo nano /etc/init.d/iptables  # makes file

If eth1 faces the WAN THEN CHANGE IT BELOW

```
#---------------------------------------------------------------
#!/bin/bash

# flush old rules
iptables -F

# Masquerade out eth1
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE

# Disallow NEW and INVALID incoming or forwarded packets from ppp0.
iptables -A INPUT   -i eth0 -m state --state NEW,INVALID -j DROP
iptables -A FORWARD -i eth0 -m state --state NEW,INVALID -j DROP

# allow ssh ftp http https from everywhere
iptables -I INPUT -p tcp --destination-port 2200 -j ACCEPT
iptables -I INPUT -p tcp --destination-port 22  -j ACCEPT
iptables -I INPUT -p tcp --destination-port 21  -j ACCEPT

# proftpd : passive transfers : firewall add here for others
# file /etc/proftpd.conf
iptables -I INPUT -p tcp --destination-port 60000:65000 -j ACCEPT
iptables -I INPUT -p tcp --destination-port 8081 -j ACCEPT
iptables -I INPUT -p tcp --destination-port 8082 -j ACCEPT
iptables -I INPUT -p tcp --destination-port 80  -j ACCEPT
iptables -I INPUT -p tcp --destination-port 443 -j ACCEPT
iptables -I INPUT -p tcp --destination-port 873 -j ACCEPT

# Teamspeak server
iptables -I INPUT -p udp --destination-port 8767 -j ACCEPT

# Teamspeak web interface
iptables -I INPUT -p tcp --destination-port 14534 -j ACCEPT
iptables -I INPUT -p tcp --destination-port 51234 -j ACCEPT

# Enemy territory
iptables -I INPUT -p udp --destination-port 27950 -j ACCEPT
iptables -I INPUT -p udp --destination-port 27951 -j ACCEPT
iptables -I INPUT -p udp --destination-port 27952 -j ACCEPT
iptables -I INPUT -p udp --destination-port 27960 -j ACCEPT
iptables -I INPUT -p udp --destination-port 27965 -j ACCEPT

# GhostRecon Interface
iptables -I INPUT -p tcp --destination-port 2346 -j ACCEPT
iptables -I INPUT -p udp --destination-port 2347 -j ACCEPT
iptables -I INPUT -p udp --destination-port 2348 -j ACCEPT

# Turn on IP forwarding
echo 1 > /proc/sys/net/ipv4/ip_forward

#-------------------------------------------------------------------


```


#Run manually thru the command line

# Make file  executable
sudo chmod +x /etc/init.d/iptables

# restart the itables script
sudo /etc/init.d/iptables


#-------------------------------------------------------------------


Hope it helps 

Regards Bill007

---

### Post by Zingaro2002 on 2007-05-04
well... thank you very much!

the following rule:
iptables -A FORWARD -i eth0 -o eth1 -d google.com -p tcp --dport 80 --sport 1024:65355 -j ACCEPT

gives me ane error because -d parameter only wants host or host/mask expressed as numeric ip address

google.com has got several different ip addresses... so I cannot write an iptable rule for every one of them!

Is there a way to express destination parameter as "google.com" (without quotes, and including all subdomains)?

Is there a way (a rule, an option, etc...) to enable only certain mac addresses (instead of ip addresses) to go to Internet?

Thanks for your help,
Zingaro2002

---

### Post by Bill007 on 2007-05-06
Why do you want to accept just packets from google.com

Yeah i think there is a way of using ip address  or machine numbers will have to look into it

But again is it necessary

If you want to block i can see some benefit

Regards Bill

---

### Post by Zingaro2002 on 2007-05-07
> 
Why do you want to accept just packets from google.com


Because my users MUST connect ONLY to maps.google.com and maps.google.it (they use google maps) and to NOTHING else (with netstat I can see that there are several *.google.com and *.google.it subdomains to which connections are redirected).
This is necessary for my users.

---

### Post by Bill007 on 2007-05-07
Aaaaah I see well

 I haven't had much time to look at your problem yet in the middle of grooming a server

keep googling 

Bill007

---

### Post by garba on 2007-05-08
> **Zingaro2002 said:**
> Because my users MUST connect ONLY to maps.google.com and maps.google.it (they use google maps) and to NOTHING else (with netstat I can see that there are several *.google.com and *.google.it subdomains to which connections are redirected).
This is necessary for my users.

what about using squid and content blocking? this is one interesting topic should you come up with a solution please let us know thanks

---

