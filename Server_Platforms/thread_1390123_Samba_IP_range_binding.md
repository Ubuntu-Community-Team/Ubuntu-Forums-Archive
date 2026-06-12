---
title: "Samba IP range binding"
date: 2010-01-25
forum: Server Platforms
---

### Post by BarryDocks on 2010-01-25
Probably a simple question, but I can't seem to find the answer.

Basically I have a series of PCs allocated fixed IP addresses by dhcp server on the subnet 135.120.135.1 to 135.120.135.10
I also have a series of pooled addresses allocated to unknown hosts 135.120.135.11 to 135.120.135.15
I would like to limit samba access to the PCs with fixed IP addresses only.  If I add the following lines to the smb.conf with this will it work?:

```
	interfaces = 135.120.135.1/255.255.255.0 135.120.135.10/255.255.255.0
        bind interfaces only = yes
```
or will I only have access from the IP addresses specified rather than the range of IPs?
Thanks

---

### Post by Roger_Smith on 2010-01-25
```

interfaces = <ip of your samba server>/255.255.255.0
bind interfaces only = yes
hosts allow = 135.120.135. localhost
hosts deny = 135.120.135.11 135.120.135.12 135.120.135.13 135.120.135.14 135.120.135.15

```
          
Leave your interface line to the interfaces you want samba to listen to.

This will allow the entire subnet except for the ones you put in the hosts deny line. 

To make it easier you may want to separate out the hosts that should have access to one subnet, and the ones that shouldn't to another, that way could just use a subnet of 135.120.135.0/24 for the allow statement and then all other subnets would not be able to connect.

---

