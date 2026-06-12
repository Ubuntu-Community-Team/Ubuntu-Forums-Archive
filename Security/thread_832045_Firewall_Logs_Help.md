---
title: "Firewall Logs Help?"
date: 2008-06-17
forum: Security
---

### Post by dlehman on 2008-06-17
I have googled and read a lot about firewall logging recently and I am trying to get a handle on Iptables.  I think I have finally found the log reader I want to use but have a few questions.  

I use fwbuilder to create my firewall and I have 6 rules rule 0 anything imbound on eth0 from the firewall is blocked I read something about anti spoofing rule 1 is to allow anything on looopback 

rule 2 is to src firewall to any several know services incluinding http, the win2000 service group and useful icmp and this is in an outbound direction 

rule 3 from home network to the firewall and allowed services in booth directions this includes win2000 service group for such things as samba 

rule 4 from anywhere to the firewall  allow certing services such as http and this is inbound 

rule 5 deny anything else

I setup logging for rule 0 and rule 5

now when I first started I set my syslog warn to got /var/log/iptables.log and have many hits 

> Jun 17 10:27:47 dlehman kernel: [982846.584713] RULE 0 -- DENY IN=eth0 OUT= MAC= SRC=192.168.1.2 DST=192.168.1.255 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=46590 DPT=137 LEN=58 

Jun 17 10:29:03 dlehman kernel: [982922.789191] RULE 0 -- DENY IN=eth0 OUT= MAC= SRC=192.168.1.2 DST=192.168.1.255 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=137 DPT=137 LEN=58 

Jun 17 10:31:58 dlehman kernel: [983097.345032] RULE 5 -- DENY IN= OUT=eth0 SRC=192.168.1.2 DST=224.0.0.251 LEN=72 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=52 

I looks to me as if this is blocking broadcast trafic but I am not sure why because it is from the firewall it should be allowed unless it is blocking the response and I am not sure about that mulicast address I have not looked into it yet.  Also port 137 should be open with the windows 2000 services group being allowed 

the odd thing now is when I switch logging to ulog this is what I get

> Jun 16 00:43:56 dlehman RULE 0 -- DENY  IN=eth0 OUT= MAC= SRC=0.0.0.0 DST=0.0.0.0 LEN=0 TOS=00 PREC=0x00 TTL=0 ID=0 PROTO=0 

Jun 16 00:44:12 dlehman RULE 5 -- DENY  IN= OUT=eth0 MAC= SRC=0.0.0.0 DST=0.0.0.0 LEN=0 TOS=00 PREC=0x00 TTL=0 ID=0 PROTO=0 

Jun 16 00:44:35 dlehman RULE 0 -- DENY  IN=eth0 OUT= MAC= SRC=0.0.0.0 DST=0.0.0.0 LEN=0 TOS=00 PREC=0x00 TTL=0 ID=0 PROTO=0 

Iptable log viewer show the protocal as HOPOPT and from what I find that is a bad checksum 

I have now switched back to logging to iptables.log and I am working with using fwlogwatch

So what I don't understand is how the logging format will affect what gets logged and could someone help me make sense of what each means 

Thank you

dlehman

---

### Post by gaten on 2008-06-17
One thing I noticed is that all the blocked traffic you posted is UDP. Did you allow for both UPD and TCP when you created the rules? Post your iptables -L output

---

### Post by dlehman on 2008-06-17
I noticed that too but looking at the fwbuilder it says that port 137 UDP is open 

any way here is the iptables -L

> Chain INPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
In_RULE_0  all  --  dlehman.###.net  anywhere            state NEW 
In_RULE_0  all  --  dlehman.###.net  anywhere            state NEW 
ACCEPT     all  --  anywhere             anywhere            state NEW 
Cid4841ACDD4885.0  all  --  192.168.1.0/24       anywhere            state NEW 
ACCEPT     tcp  --  anywhere             anywhere            tcp multiport dports www,https,nntp,ssh,domain state NEW 
ACCEPT     udp  --  anywhere             anywhere            udp multiport dports ntp,domain state NEW 
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
RULE_5     all  --  anywhere             anywhere            

Chain FORWARD (policy DROP)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
In_RULE_0  all  --  dlehman.###.net  anywhere            state NEW 
In_RULE_0  all  --  dlehman.###.net  anywhere            state NEW 
ACCEPT     all  --  anywhere             anywhere            state NEW 
ACCEPT     all  --  anywhere             anywhere            state NEW 
RULE_5     all  --  anywhere             anywhere            

Chain OUTPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     all  --  anywhere             anywhere            state NEW 
ACCEPT     icmp --  anywhere             anywhere            icmp ttl-zero-during-transit state NEW 
ACCEPT     icmp --  anywhere             anywhere            icmp ttl-zero-during-reassembly state NEW 
ACCEPT     icmp --  anywhere             anywhere            icmp type 0 code 0 state NEW 
ACCEPT     icmp --  anywhere             anywhere            icmp destination-unreachable state NEW 
ACCEPT     tcp  --  anywhere             anywhere            tcp multiport dports www,https,nntp,ssh,domain,netbios-ssn,loc-srv,nameserver,microsoft-ds,kerberos,ldap,ldaps,3268,3269,webmin state NEW 
ACCEPT     tcp  --  anywhere             anywhere            tcp multiport dports 5900,3389 state NEW 
ACCEPT     udp  --  anywhere             anywhere            udp multiport dports ntp,domain,bootpc,bootps,netbios-dgm,netbios-ns,kerberos state NEW 
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
RULE_5     all  --  anywhere             anywhere            

Chain Cid4841ACDD4885.0 (1 references)
target     prot opt source               destination         
ACCEPT     icmp --  anywhere             anywhere            icmp ttl-zero-during-transit 
ACCEPT     icmp --  anywhere             anywhere            icmp ttl-zero-during-reassembly 
ACCEPT     icmp --  anywhere             anywhere            icmp type 0 code 0 
ACCEPT     icmp --  anywhere             anywhere            icmp destination-unreachable 
ACCEPT     tcp  --  anywhere             anywhere            tcp multiport dports domain,netbios-ssn,loc-srv,nameserver,microsoft-ds,kerberos,ldap,ldaps,3268,3269,webmin,5900,3389 
ACCEPT     udp  --  anywhere             anywhere            udp multiport dports bootpc,bootps,domain,netbios-dgm,netbios-ns,kerberos 

Chain In_RULE_0 (4 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            LOG level warning prefix `RULE 0 -- DENY ' 
DROP       all  --  anywhere             anywhere            

Chain RULE_5 (3 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            LOG level warning prefix `RULE 5 -- DENY ' 
DROP       all  --  anywhere             anywhere            


I hashed out my full hostname

also here is a screen shot of my fwbuilder file 

Thanks

---

### Post by gaten on 2008-06-18
> ACCEPT     udp  --  anywhere             anywhere            udp multiport dports ntp,domain state NEW 

I don't see port 137 (netbios) included in that, could that be the problem? I'm not familiar with fwbuilder, so I can't help you in that respect.

---

### Post by dlehman on 2008-06-19
You are right I didn't notice that before, however I have just deleted the first rule all together I think it was more trouble then it was worth.  I found a few articles on the anti spoofing and I get the impression it is only for firewalls with more then one NIC, 

I still don't understand why the syslog showed the IP Address and ports but the ULOG showed 0.0.0.0 and proto 0 so I will stick with the syslog

Using Firewall Builder, [Part I]("http://www.linuxjournal.com/article/6625")  [Part II]("http://www.linuxjournal.com/article/6715")

Thanks

---

