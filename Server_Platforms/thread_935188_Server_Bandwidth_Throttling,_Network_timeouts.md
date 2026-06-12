---
title: "Server Bandwidth Throttling, Network timeouts"
date: 2008-10-01
forum: Server Platforms
---

### Post by fowie on 2008-10-01
My server is connect via optical fiber to the internet, and I've never had this problem before.  I just did a fresh install to Hardy LTS and now I've noticed what seems like throttling.  I don't have any problem serving up web pages or small files, but anything over a few megabytes times out when trying to download (using HTTP, FTP, SVN, unison, rsync, scp, etc..., they all stall)  I get a few seconds of 800kpbs transfer rate, sometimes up to 2Mbps, and then it'll just drop off to 0.  Any idea what could be causing this?  I've tried from multiple computers and multiple ISPs using multiple protocols (listed above) and the connection always stalls.  Where should I start troubleshooting this?

---

### Post by alastair on 2008-10-01
A fresh install of Hardy from something else?

Maybe something has changed with the ethernet device driver? Checkout which driver it is and do some research about changes between good and bad. Maybe some driver module "options" have changed, or can be tweaked. Is there any enabled firewall or traffic control? Either on your system or a system between you and the net?

Alastair

---

### Post by fowie on 2008-10-02
Fresh install of Hardy from Dapper, but not an upgrade, I wiped the drives and started fresh.  Where does it tell me what driver is being used for the ethernet cards?  Yes, there is a firewall enabled on my system, since it's being used as a router for my home.

Here's the output of iptables --list:
```

Chain INPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  dns1.*myisp*.net   anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN 
ACCEPT     udp  --  dns1.*myisp*.net   anywhere            
ACCEPT     tcp  --  dns2.*myisp*.net   anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN 
ACCEPT     udp  --  dns2.*myisp*.net   anywhere            
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5 
DROP       all  --  anywhere             255.255.255.255     
DROP       all  --  anywhere             avaliable.*myisp*.net 
DROP       all  --  BASE-ADDRESS.MCAST.NET/8  anywhere            
DROP       all  --  anywhere             BASE-ADDRESS.MCAST.NET/8 
DROP       all  --  255.255.255.255      anywhere            
DROP       all  --  anywhere             0.0.0.0             
DROP       all  --  anywhere             anywhere            state INVALID 
LSI        all  -f  anywhere             anywhere            limit: avg 10/min burst 5 
INBOUND    all  --  anywhere             anywhere            
INBOUND    all  --  anywhere             192.168.0.1         
INBOUND    all  --  anywhere             avaliable.*myisp*.net 
INBOUND    all  --  anywhere             192.168.0.255       
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Input' 

Chain FORWARD (policy DROP)
target     prot opt source               destination         
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5 
TCPMSS     tcp  --  anywhere             anywhere            tcp flags:SYN,RST/SYN TCPMSS clamp to PMTU 
OUTBOUND   all  --  anywhere             anywhere            
ACCEPT     tcp  --  anywhere             192.168.0.0/24      state RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             192.168.0.0/24      state RELATED,ESTABLISHED 
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Forward' 

Chain OUTPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  avaliable.*myisp*.net  dns1.*myisp*.net  tcp dpt:domain 
ACCEPT     udp  --  avaliable.*myisp*.net  dns1.*myisp*.net  udp dpt:domain 
ACCEPT     tcp  --  avaliable.*myisp*.net  dns2.*myisp*.net  tcp dpt:domain 
ACCEPT     udp  --  avaliable.*myisp*.net  dns2.*myisp*.net  udp dpt:domain 
ACCEPT     all  --  anywhere             anywhere            
DROP       all  --  BASE-ADDRESS.MCAST.NET/8  anywhere            
DROP       all  --  anywhere             BASE-ADDRESS.MCAST.NET/8 
DROP       all  --  255.255.255.255      anywhere            
DROP       all  --  anywhere             0.0.0.0             
DROP       all  --  anywhere             anywhere            state INVALID 
OUTBOUND   all  --  anywhere             anywhere            
OUTBOUND   all  --  anywhere             anywhere            
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Output' 

Chain INBOUND (4 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:www 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:www 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpts:ftp-data:ftp 
ACCEPT     udp  --  anywhere             anywhere            udp dpts:20:fsp 
ACCEPT     tcp  --  192.168.0.0/24       anywhere            tcp dpts:bootps:bootpc 
ACCEPT     udp  --  192.168.0.0/24       anywhere            udp dpts:bootps:bootpc 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:webmin 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:10000 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:ssh 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:ssh 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:imap2 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:imap2 
ACCEPT     tcp  --  192.168.0.0/24       anywhere            tcp dpts:netbios-ns:netbios-ssn 
ACCEPT     udp  --  192.168.0.0/24       anywhere            udp dpts:netbios-ns:netbios-ssn 
ACCEPT     tcp  --  192.168.0.0/24       anywhere            tcp dpt:microsoft-ds 
ACCEPT     udp  --  192.168.0.0/24       anywhere            udp dpt:microsoft-ds 
LSI        all  --  anywhere             anywhere            

Chain LOG_FILTER (5 references)
target     prot opt source               destination         

Chain LSI (2 references)
target     prot opt source               destination         
LOG_FILTER  all  --  anywhere             anywhere            
LOG        tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN 
LOG        tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST 
LOG        icmp --  anywhere             anywhere            icmp echo-request limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
DROP       icmp --  anywhere             anywhere            icmp echo-request 
LOG        all  --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Inbound ' 
DROP       all  --  anywhere             anywhere            

Chain LSO (0 references)
target     prot opt source               destination         
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Outbound ' 
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable 

Chain OUTBOUND (3 references)
target     prot opt source               destination         
ACCEPT     icmp --  anywhere             anywhere            
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     all  --  anywhere             anywhere            


```

---

