---
title: "Can't access my website over the internet."
date: 2010-10-08
forum: Server Platforms
---

### Post by tad1073 on 2010-10-08
I have ubuntu 10.04 running LAMP and proftpd, I can access over LAN but not when I type my domain name in. I have forwarded all necessary port to to the local ip of that box, added rules to ufw to allow traffic on those specific ports. I use dyndns for a second level domain and have used all their tools to check whether the ports are open and have the results I am looking for.

```
:~$ sudo iptables -L
[sudo] password for thomas: 
Chain INPUT (policy DROP)
target     prot opt source               destination         
ufw-before-logging-input  all  --  anywhere             anywhere            
ufw-before-input  all  --  anywhere             anywhere            
ufw-after-input  all  --  anywhere             anywhere            
ufw-after-logging-input  all  --  anywhere             anywhere            
ufw-reject-input  all  --  anywhere             anywhere            
ufw-track-input  all  --  anywhere             anywhere            

Chain FORWARD (policy DROP)
target     prot opt source               destination         
ufw-before-logging-forward  all  --  anywhere             anywhere            
ufw-before-forward  all  --  anywhere             anywhere            
ufw-after-forward  all  --  anywhere             anywhere            
ufw-after-logging-forward  all  --  anywhere             anywhere            
ufw-reject-forward  all  --  anywhere             anywhere            

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
ufw-before-logging-output  all  --  anywhere             anywhere            
ufw-before-output  all  --  anywhere             anywhere            
ufw-after-output  all  --  anywhere             anywhere            
ufw-after-logging-output  all  --  anywhere             anywhere            
ufw-reject-output  all  --  anywhere             anywhere            
ufw-track-output  all  --  anywhere             anywhere            

Chain ufw-after-forward (1 references)
target     prot opt source               destination         

Chain ufw-after-input (1 references)
target     prot opt source               destination         
ufw-skip-to-policy-input  udp  --  anywhere             anywhere            udp dpt:netbios-ns 
ufw-skip-to-policy-input  udp  --  anywhere             anywhere            udp dpt:netbios-dgm 
ufw-skip-to-policy-input  tcp  --  anywhere             anywhere            tcp dpt:netbios-ssn 
ufw-skip-to-policy-input  tcp  --  anywhere             anywhere            tcp dpt:microsoft-ds 
ufw-skip-to-policy-input  udp  --  anywhere             anywhere            udp dpt:bootps 
ufw-skip-to-policy-input  udp  --  anywhere             anywhere            udp dpt:bootpc 
ufw-skip-to-policy-input  all  --  anywhere             anywhere            ADDRTYPE match dst-type BROADCAST 

Chain ufw-after-logging-forward (1 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            limit: avg 3/min burst 10 LOG level warning prefix `[UFW BLOCK] ' 

Chain ufw-after-logging-input (1 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            limit: avg 3/min burst 10 LOG level warning prefix `[UFW BLOCK] ' 

Chain ufw-after-logging-output (1 references)
target     prot opt source               destination         

Chain ufw-after-output (1 references)
target     prot opt source               destination         

Chain ufw-before-forward (1 references)
target     prot opt source               destination         
ufw-user-forward  all  --  anywhere             anywhere            

Chain ufw-before-input (1 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ufw-logging-deny  all  --  anywhere             anywhere            state INVALID 
DROP       all  --  anywhere             anywhere            state INVALID 
ACCEPT     icmp --  anywhere             anywhere            icmp destination-unreachable 
ACCEPT     icmp --  anywhere             anywhere            icmp source-quench 
ACCEPT     icmp --  anywhere             anywhere            icmp time-exceeded 
ACCEPT     icmp --  anywhere             anywhere            icmp parameter-problem 
ACCEPT     icmp --  anywhere             anywhere            icmp echo-request 
ACCEPT     udp  --  anywhere             anywhere            udp spt:bootps dpt:bootpc 
ufw-not-local  all  --  anywhere             anywhere            
ACCEPT     all  --  BASE-ADDRESS.MCAST.NET/4  anywhere            
ACCEPT     all  --  anywhere             base-address.mcast.net/4 
ufw-user-input  all  --  anywhere             anywhere            

Chain ufw-before-logging-forward (1 references)
target     prot opt source               destination         

Chain ufw-before-logging-input (1 references)
target     prot opt source               destination         

Chain ufw-before-logging-output (1 references)
target     prot opt source               destination         

Chain ufw-before-output (1 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ufw-user-output  all  --  anywhere             anywhere            

Chain ufw-logging-allow (0 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            limit: avg 3/min burst 10 LOG level warning prefix `[UFW ALLOW] ' 

Chain ufw-logging-deny (2 references)
target     prot opt source               destination         
RETURN     all  --  anywhere             anywhere            state INVALID limit: avg 3/min burst 10 
LOG        all  --  anywhere             anywhere            limit: avg 3/min burst 10 LOG level warning prefix `[UFW BLOCK] ' 

Chain ufw-not-local (1 references)
target     prot opt source               destination         
RETURN     all  --  anywhere             anywhere            ADDRTYPE match dst-type LOCAL 
RETURN     all  --  anywhere             anywhere            ADDRTYPE match dst-type MULTICAST 
RETURN     all  --  anywhere             anywhere            ADDRTYPE match dst-type BROADCAST 
ufw-logging-deny  all  --  anywhere             anywhere            limit: avg 3/min burst 10 
DROP       all  --  anywhere             anywhere            

Chain ufw-reject-forward (1 references)
target     prot opt source               destination         

Chain ufw-reject-input (1 references)
target     prot opt source               destination         

Chain ufw-reject-output (1 references)
target     prot opt source               destination         

Chain ufw-skip-to-policy-forward (0 references)
target     prot opt source               destination         
DROP       all  --  anywhere             anywhere            

Chain ufw-skip-to-policy-input (7 references)
target     prot opt source               destination         
DROP       all  --  anywhere             anywhere            

Chain ufw-skip-to-policy-output (0 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            

Chain ufw-track-input (1 references)
target     prot opt source               destination         

Chain ufw-track-output (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            state NEW 
ACCEPT     udp  --  anywhere             anywhere            state NEW 

Chain ufw-user-forward (1 references)
target     prot opt source               destination         

Chain ufw-user-input (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:ftp 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:ftp-data 
ACCEPT     udp  --  192.168.1.0/29       anywhere            udp dpt:netbios-ns 
ACCEPT     udp  --  192.168.1.0/29       anywhere            udp dpt:netbios-dgm 
ACCEPT     tcp  --  192.168.1.0/29       anywhere            tcp dpt:netbios-ssn 
ACCEPT     tcp  --  192.168.1.0/29       anywhere            tcp dpt:microsoft-ds 
ACCEPT     tcp  --  192.168.1.0/29       anywhere            tcp dpt:ssh 


```

---

### Post by CharlesA on 2010-10-08
Try running shieldsup or something similar to see if the ports are in fact open to the internet.

If it's accessible locally but not externally and the ports are open, it could be that yer ISP is blocking those ports.

Double check port forwarding and whatnot as well.

---

### Post by tad1073 on 2010-10-08
SheildsUp reports that 80 and 21 are open, a few months back I had the same configuration but was using CentOs 5.4 and was successful accessing http and ftp from the outside so that may rule out isp blocking.

Should I use ufw or just create iptables rules?

```
[SIZE=-1][COLOR=#000066][SIZE=3][COLOR=black]GRC Port Authority Report created on UTC: 2010-10-08 at 12:06:47

Results from scan of ports: 0-1055

    2 Ports Open
    1 Ports Closed
 1053 Ports Stealth
---------------------
 1056 Ports Tested

Ports found to be OPEN were: 21, 80

The port found to be CLOSED was: 20

Other than what is listed above, all ports are STEALTH.

TruStealth: FAILED - NOT all tested ports were STEALTH,
                   - NO unsolicited packets were received,
                   - NO Ping reply (ICMP Echo) was received.
 [/COLOR][/SIZE][/COLOR][/SIZE]
```

---

### Post by metcarob on 2010-10-08
Are you using apache virtual hosts? This can sometimes mean the site isn't found. (I have my server setup to direct to a diffrent site depending on the host name. 

I looked at your firewall config to see if established and related connections were allowed. I am not sure but I think you need to allow established and related connections in both your OUTPUT and INPUT chains.

---

### Post by CharlesA on 2010-10-08
I'd use iptables, but then I like using iptables, since I know what each rule I have in place does. :)

Use whatever is easier for you.

Like the above poster mentioned: Are you use virtualhosts by chance?

---

### Post by tad1073 on 2010-10-08
I am trying to set up virtual host but only have one site for the time being. I need to get the configuration files back to their default states and start from scratch but I did not make copies of them.

---

### Post by CharlesA on 2010-10-08
You can purge apache and clean out any leftovers and then reinstall.

That should get you a good place to start.

---

### Post by tad1073 on 2010-10-09
Well, I installed centOs 5.5 because I am more familiar with httpd on that system. Big mistake, so I will be reinstalling ubuntu 10.04 when I get home from school. Thanks for all the help.

---

