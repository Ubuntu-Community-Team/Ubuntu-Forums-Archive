---
title: "command that lists all ip address?"
date: 2011-01-18
forum: Server Platforms
---

### Post by bone2006 on 2011-01-18
I have a bunch of windows machines connected to a server running samba. I would like to know if there's a way or hopefully a quick command I could type in the terminal that would tell me the machine name and the associated IP address?

---

### Post by matt-fender on 2011-01-18
On windows?

arp -a in a command prompt will show your routing table

ipconfig /all will give the IP of the machine you are sat on

------------

On Ubuntu 

System > Administration > Network Tools > Choose Device (top of box) Ip will be shown underneath

Theres also a routing table on the network tools manager in Ubuntu ^

---

### Post by matt_symes on 2011-01-18
Hi

This will give all the IP addresses on a network by pinging them to see if they are up.

```
nmap -sP <address>/<mask_size>
```

i.e. 

```
nmap -sP 192.168.1.0/24
```

Kind regards

---

### Post by SeijiSensei on 2011-01-18
The nmblookup command that comes with the Samba package is what you need.  Running the command "nmblookup -A 1.2.3.4" will return the Netbios name of the host at 1.2.3.4.  You can use this in a script in conjunction with "nmap -sP" to first scan the network for active IPs, then determine their Netbios names with nmblookup.

On my Maverick system, nmblookup is part of the samba-common-bin package.

---

