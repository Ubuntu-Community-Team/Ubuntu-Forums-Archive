---
title: "sudo ufw allow from 192.168.0.0/24 to Samba"
date: 2009-03-01
forum: Security
---

### Post by loopyzort on 2009-03-01
I know this is kinda stupid, but doing:

sudo ufw allow Samba

basically says anyone can access the samba ports on my server. maybe it's pointless (as if someone's hacked my network they'd have an internal IP anyway), but I'd like to allow the ports defined in certain preconfigured applications to only be accessible from my internal network IPs (192.168.0.0/24). Is there any way to do this besides:

sudo ufw allow proto tcp from 192.168.0.0/24 to 445

Or a I stuck with the prepackaged application profile allowing access from Anywhere vs. manually entering the information (not that it's a huge problem, just seems stupid to limit the "allow <<application>>" syntax like that).

Sorry if this is clearly written somewhere that I missed...

---

### Post by bodhi.zazen on 2009-03-01
For samba you need to allow :

tcp : ports 135 , 139, and 445
udp : ports 137 and 138

So you can allow all traffic from your LAN :

sudo ufw allow 192.168.1.0/24

Or add each port :

```
sudo ufw allow proto tcp from 192.168.0.0/24 to 192.168.0.50 port 135 
sudo ufw allow proto tcp from 192.168.1.0/24 to 192.168.0.50 port 139
sudo ufw allow proto tcp from 192.168.0.0/24 to 192.168.0.50 port 445
sudo ufw allow proto udp from 192.168.0.0/24 to 192.168.0.50 port 137
sudo ufw allow proto udp from 192.168.0.0/24 to 192.168.0.50 port 138
```The above command assume your network is 192.168.0.0/16 and your server IP address is 192.168.0.50 , adjust accordingly :twisted:

---

### Post by sefs on 2009-03-21
for me i've also realised that this does not work unless I change in 

/etc/default/ufw

```

IPT_MODULES="nf_conntrack_ftp nf_nat_ftp nf_conntrack_irc nf_nat_irc

```

to

```

# The nf_contrack_netbios_ns has been added
IPT_MODULES="nf_conntrack_ftp nf_nat_ftp nf_conntrack_irc nf_nat_irc nf_conntrack_netbios_ns"

```

---

