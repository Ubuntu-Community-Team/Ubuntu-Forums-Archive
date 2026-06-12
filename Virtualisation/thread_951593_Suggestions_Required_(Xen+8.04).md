---
title: "Suggestions Required (Xen+8.04)"
date: 2008-10-18
forum: Virtualisation
---

### Post by shoaibi on 2008-10-18
okay, people, i am gonna tell you mysetup and you will let me know what is better.

Home Server Setup:
Hardware Specs:
Intel P4 3.0HT
3GB RAM
500GB SATA2 + 120GB ATA
2 NICs:
eth0: External IP(single)
eth1: Local Network(172.30.10.xxx)

What i want to run on this server:
1.DHCP, DNS, Firewall, Web Server*, Database Server, FTP Server, Mail Server, OpenVPN, Jabber Server.
2.File Share Server (NFS, Samba/CIFS)
3.Backup Server (of Server 1)
4. apt-proxy server
5. Failover of server 1
 
* Will be hosting 2 sites, both simple joomla based:
1. simple site, atmost will take 5GB in the nest 5 years..
2. Pure download based site, containing manuals, audios, videos, etc. will start from 200GB, and with more content take more space.

What i have plans:
Using Xen:

dom0:
Ubuntu Server 8.04 LTS
6GB+1GB SWAP
Firewall

Rest of hard disk all in an VG



domU:

Server 1:
Needs NAT to boths eths to get the external IP and run DHCP.
5GB [OS] + 10GB(Site1)+ 300G [Site2] + 1GB SWAP

Server 2:
Bridged to get IP from DHCP in dom1
File Server = 3GB [Ubuntu minimal] + 100GB [share]

Server 3:
Bridged to get IP from DHCP in dom1
Backup= 50GB [Ubuntu minimal + resync, won't backup site2] + 1GB SWAP 

Server 4:
Bridged to get IP from DHCP in dom1
Apt-proxy= 8GB [OS (using ubuntu 8.04LTS minimal) + apt-proxy-cache ] + 1GB SWAP

Server 5:
Same as Server1


Can i run DHCP in a domU? 
what do you suggest? something which i missed? or i should change?

---

