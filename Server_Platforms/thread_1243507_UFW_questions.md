---
title: "UFW questions"
date: 2009-08-18
forum: Server Platforms
---

### Post by jfmanamtr on 2009-08-18
Ok. I am trying to setup UFW to act as an ACL for a few of the services that I run off my server for my local network. I have been having troubles with people in other countries probing my system & trying to modify my site. I want to have UFW filter what IP (address & subnet) are allowed to access certain services (i.e: letting only local requests access the DHCP & DNS). I am just running into troubles. When I enable the UFW, all my home computers stop getting IPs & can't connect to the internet. I think it blocks all the services by default (at least that is what I have read). I use my server for DHCP, DNS, SSH, FTP, Apache, MySQL, PHP, SAMBA & Firefly (I think that is all my services). I am not sure how to make the firewall play nice with all these services. Any ideas on how I would go about accomplishing this?

~John

---

### Post by jfmanamtr on 2009-08-18
So, any ideas?

Bump!

~John

---

### Post by jfmanamtr on 2009-08-19
Bump!

~John

---

### Post by koenn on 2009-08-19
bumps within less than 24 hrs are considered impolite.

tcp/ip apps such as most of the ones you mention are client/server apps, with the server listening at a given tcp or udp port at a given address. 

you therefore need to configure your firewall so it allow traffic from the client(s) to the relevant address and port, + traffic from that address and port back to the clients.

eg for apache to work you need to allow traffic to and from port 80/tcp at the ip address of the machine where apache runs.

---

### Post by jfmanamtr on 2009-08-19
Sorry. I didn't know that.

I have tried to set it up, but for some reason it still seems to block the service. I have a DHCP server running on my server. I add the 2 TCP ports for DHCP (67 & 68 TCP) & tell it to allow the service for 192.168.1.0\24 (which is the local subnet that I use). But for some reason, the DHCP service doesn't seem to be available for my local subnet while the UFW is turned on. Same thing happens with the DNS, SAMBA, FTP & Firefly (these are the services I want restricted to my local subnet). If I enable the firewall & tell it to allow the required ports for these services for my local subnet, these services cease functioning. Any ideas on what I am doing wrong? I can post any files you may need.

~John

---

### Post by koenn on 2009-08-19
dhcp goes over udp, not tcp. 

I don't do UFW, so i can't tell you how to do this.


You can start by explaining a bit about your network, like ; are all these services on the same server ? Is the firewall also running on this server or on a separate machine ? How is your LAN connected to the internet ? ....

you can also run this command
```
iptables -L -n
```

that should show your firewall config, maybe there's something there worth seeing.

---

### Post by jfmanamtr on 2009-08-19
> You can start by explaining a bit about your network, like ; are all these services on the same server ? Is the firewall also running on this server or on a separate machine ? How is your LAN connected to the internet?

Ok. All the services are on the same server & so is the firewall. I have a cable modem going to a netgear router & then form the router to 2 wireless laptops & 3 wired PCs (the server & 2 desktops). I will run that command once I get home. I turned off the internet access to the server until I can set this up & prevent random people from trying to attach to my system.

~John

---

### Post by jfmanamtr on 2009-08-21
I am sorry that I took so long to reply. I had a few troubles that prevented me from getting online for a few days. I ran that command & got the following output. I am not quite sure what all this means, but any help on how to make it play nice is appreciated. I haven't added all the services yet. I got stuck with getting DHCP & DNS passing correctly first. Thanks again for all your help!

~John

*iptables -L -n*
               ```
Chain INPUT (policy DROP)
target     prot opt source               destination         
ufw-before-logging-input  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-before-input  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-after-input  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-after-logging-input  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-reject-input  all  --  0.0.0.0/0            0.0.0.0/0           

Chain FORWARD (policy DROP)
target     prot opt source               destination         
ufw-before-logging-forward  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-before-forward  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-after-forward  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-after-logging-forward  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-reject-forward  all  --  0.0.0.0/0            0.0.0.0/0           

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
ufw-before-logging-output  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-before-output  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-after-output  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-after-logging-output  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-reject-output  all  --  0.0.0.0/0            0.0.0.0/0           

Chain ufw-after-forward (1 references)
target     prot opt source               destination         

Chain ufw-after-input (1 references)
target     prot opt source               destination         
RETURN     udp  --  0.0.0.0/0            0.0.0.0/0           udp dpt:137 
RETURN     udp  --  0.0.0.0/0            0.0.0.0/0           udp dpt:138 
RETURN     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:139 
RETURN     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:445 
RETURN     udp  --  0.0.0.0/0            0.0.0.0/0           udp dpt:67 
RETURN     udp  --  0.0.0.0/0            0.0.0.0/0           udp dpt:68 
RETURN     all  --  0.0.0.0/0            0.0.0.0/0           ADDRTYPE match dst-type BROADCAST 

Chain ufw-after-logging-forward (1 references)
target     prot opt source               destination         
LOG        all  --  0.0.0.0/0            0.0.0.0/0           limit: avg 3/min burst 10 LOG flags 0 level 4 prefix `[UFW BLOCK] ' 

Chain ufw-after-logging-input (1 references)
target     prot opt source               destination         
LOG        all  --  0.0.0.0/0            0.0.0.0/0           limit: avg 3/min burst 10 LOG flags 0 level 4 prefix `[UFW BLOCK] ' 

Chain ufw-after-logging-output (1 references)
target     prot opt source               destination         

Chain ufw-after-output (1 references)
target     prot opt source               destination         

Chain ufw-before-forward (1 references)
target     prot opt source               destination         
ufw-user-forward  all  --  0.0.0.0/0            0.0.0.0/0           

Chain ufw-before-input (1 references)
target     prot opt source               destination         
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0           
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
ufw-logging-deny  all  --  0.0.0.0/0            0.0.0.0/0           state INVALID 
DROP       all  --  0.0.0.0/0            0.0.0.0/0           state INVALID 
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0           icmp type 3 
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0           icmp type 4 
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0           icmp type 11 
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0           icmp type 12 
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0           icmp type 8 
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           udp spt:67 dpt:68 
ufw-not-local  all  --  0.0.0.0/0            0.0.0.0/0           
ACCEPT     all  --  224.0.0.0/4          0.0.0.0/0           
ACCEPT     all  --  0.0.0.0/0            224.0.0.0/4         
ufw-user-input  all  --  0.0.0.0/0            0.0.0.0/0           

Chain ufw-before-logging-forward (1 references)
target     prot opt source               destination         

Chain ufw-before-logging-input (1 references)
target     prot opt source               destination         

Chain ufw-before-logging-output (1 references)
target     prot opt source               destination         

Chain ufw-before-output (1 references)
target     prot opt source               destination         
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0           
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           state NEW,RELATED,ESTABLISHED 
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           state NEW,RELATED,ESTABLISHED 
ufw-user-output  all  --  0.0.0.0/0            0.0.0.0/0           

Chain ufw-logging-allow (0 references)
target     prot opt source               destination         
LOG        all  --  0.0.0.0/0            0.0.0.0/0           limit: avg 3/min burst 10 LOG flags 0 level 4 prefix `[UFW ALLOW] ' 

Chain ufw-logging-deny (2 references)
target     prot opt source               destination         
LOG        all  --  0.0.0.0/0            0.0.0.0/0           limit: avg 3/min burst 10 LOG flags 0 level 4 prefix `[UFW BLOCK] ' 

Chain ufw-not-local (1 references)
target     prot opt source               destination         
RETURN     all  --  0.0.0.0/0            0.0.0.0/0           ADDRTYPE match dst-type LOCAL 
RETURN     all  --  0.0.0.0/0            0.0.0.0/0           ADDRTYPE match dst-type MULTICAST 
RETURN     all  --  0.0.0.0/0            0.0.0.0/0           ADDRTYPE match dst-type BROADCAST 
ufw-logging-deny  all  --  0.0.0.0/0            0.0.0.0/0           limit: avg 3/min burst 10 
DROP       all  --  0.0.0.0/0            0.0.0.0/0           

Chain ufw-reject-forward (1 references)
target     prot opt source               destination         

Chain ufw-reject-input (1 references)
target     prot opt source               destination         

Chain ufw-reject-output (1 references)
target     prot opt source               destination         

Chain ufw-user-forward (1 references)
target     prot opt source               destination         

Chain ufw-user-input (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  192.168.1.0/24       0.0.0.0/0           tcp dpt:2222 
ACCEPT     tcp  --  192.168.1.0/24       0.0.0.0/0           tcp dpt:53 
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:53 /* 'dapp_Bind9' */ 
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           udp dpt:53 /* 'dapp_Bind9' */ 

Chain ufw-user-limit (0 references)
target     prot opt source               destination         
LOG        all  --  0.0.0.0/0            0.0.0.0/0           limit: avg 3/min burst 5 LOG flags 0 level 4 prefix `[UFW LIMIT BLOCK] ' 
REJECT     all  --  0.0.0.0/0            0.0.0.0/0           reject-with icmp-port-unreachable 

Chain ufw-user-limit-accept (0 references)
target     prot opt source               destination         
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0           

Chain ufw-user-logging-forward (0 references)
target     prot opt source               destination         

Chain ufw-user-logging-input (0 references)
target     prot opt source               destination         

Chain ufw-user-logging-output (0 references)
target     prot opt source               destination         

Chain ufw-user-output (1 references)
target     prot opt source               destination
```

---

