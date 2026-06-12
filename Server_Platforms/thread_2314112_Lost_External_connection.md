---
title: "Lost External connection"
date: 2016-02-18
forum: Server Platforms
---

### Post by Marc_Parsons on 2016-02-18
Hi all,

I have been running Ubuntu 15.10  for a week now (after a rebuild) as a home server for email, web, plex etc.. and ISPConfig 3... with no issues. 

Today however, something odd has happened. I cannot connect to any services on the server at all either from my LAN or external internet. I have made no changes to my router/firewall (but rebooted it anyway). I have moved the system and connected it up via HDMI to my TV so I could see what what happening. It booted up fine, no failures, apt-get update works. I can ping external sites and I can ping the server IP address from another computer. If I do netstat -tap I get a list of all the services I expect to be running but each only showing "LISTEN". No "ESTABLISHED/TIMEWAIT" connections though. I really can't work out why this is happening. The server is behaving like it is not allowing any inbound connections on any port. I can't post any actual logs as I can't SSH into it.

I am really hoping someone can offer some advice as I really don't want to have to rebuild from scratch again...

Thanks in advance

Marc

---

### Post by darkod on 2016-02-18
You didn't mention activating any firewalls so i assume you didn't??? Because a wrongly implemented firewall can cut you out, and all services too. Just in case, check iptables while having the server connected to the TV/monitor:
```
sudo iptables -L -n -v
```

Does it show the INPUT chain policy as ACCEPT or DROP?

Do you have a static IP on the server? If it's dynamic could it have changed? Just because you can ping an IP it doesn't mean it's the server IP. :)

What does this say for the IP:
```
ifconfig
```

---

### Post by Marc_Parsons on 2016-02-18
Thanks for your reply. Since posting this thread I put a different HDD in the system which contained an old Ubuntu 12.04 LTS installation. All the services worked fine and could connect internally and externally, so I definitely know it's not a router issue. In terms of a firewall, I have not specifically configured one in Ubuntu when I installed it or since then. I saved the outputs of a few commands to a usb stick:

sudo iptables -L -n -v >>>>

Chain INPUT (policy DROP 2167 packets, 142K bytes)
 pkts bytes target     prot opt in     out     source               destination         
  176 10560 f2b-dovecot-pop3imap  tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            multiport dports 110,995,143,993
    0     0 f2b-pureftpd  tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            multiport dports 21
  170  9672 f2b-postfix-sasl  tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            multiport dports 25
    3   180 f2b-sshd   tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            multiport dports 22
 6962 2230K ufw-before-logging-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
 6962 2230K ufw-before-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
 2834  190K ufw-after-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
 2191  143K ufw-after-logging-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
 2191  143K ufw-reject-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
 2191  143K ufw-track-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0           


Chain FORWARD (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ufw-before-logging-forward  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 ufw-before-forward  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 ufw-after-forward  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 ufw-after-logging-forward  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 ufw-reject-forward  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 ufw-track-forward  all  --  *      *       0.0.0.0/0            0.0.0.0/0           


Chain OUTPUT (policy ACCEPT 2 packets, 80 bytes)
 pkts bytes target     prot opt in     out     source               destination         
 2234  184K ufw-before-logging-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
 2234  184K ufw-before-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
 1018 80857 ufw-after-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
 1018 80857 ufw-after-logging-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
 1018 80857 ufw-reject-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
 1018 80857 ufw-track-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0           


Chain f2b-dovecot-pop3imap (1 references)
 pkts bytes target     prot opt in     out     source               destination         
  176 10560 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0           


Chain f2b-postfix-sasl (1 references)
 pkts bytes target     prot opt in     out     source               destination         
  170  9672 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0           


Chain f2b-pureftpd (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0           


Chain f2b-sshd (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    3   180 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0           


Chain ufw-after-forward (1 references)
 pkts bytes target     prot opt in     out     source               destination         


Chain ufw-after-input (1 references)
 pkts bytes target     prot opt in     out     source               destination         
  220 18132 ufw-skip-to-policy-input  udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:137
   41  9762 ufw-skip-to-policy-input  udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:138
    0     0 ufw-skip-to-policy-input  tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:139
    0     0 ufw-skip-to-policy-input  tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:445
    2   691 ufw-skip-to-policy-input  udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:67
    0     0 ufw-skip-to-policy-input  udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:68
  380 18248 ufw-skip-to-policy-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0            ADDRTYPE match dst-type BROADCAST


Chain ufw-after-logging-forward (1 references)
 pkts bytes target     prot opt in     out     source               destination         


Chain ufw-after-logging-input (1 references)
 pkts bytes target     prot opt in     out     source               destination         


Chain ufw-after-logging-output (1 references)
 pkts bytes target     prot opt in     out     source               destination         


Chain ufw-after-output (1 references)
 pkts bytes target     prot opt in     out     source               destination         


Chain ufw-before-forward (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0            ctstate RELATED,ESTABLISHED
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0            icmptype 3
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0            icmptype 4
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0            icmptype 11
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0            icmptype 12
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0            icmptype 8
    0     0 ufw-user-forward  all  --  *      *       0.0.0.0/0            0.0.0.0/0           


Chain ufw-before-input (1 references)
 pkts bytes target     prot opt in     out     source               destination         
  406 19556 ACCEPT     all  --  lo     *       0.0.0.0/0            0.0.0.0/0           
 1324  962K ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0            ctstate RELATED,ESTABLISHED
    5   200 ufw-logging-deny  all  --  *      *       0.0.0.0/0            0.0.0.0/0            ctstate INVALID
    5   200 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0            ctstate INVALID
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0            icmptype 3
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0            icmptype 4
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0            icmptype 11
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0            icmptype 12
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0            icmptype 8
    1   328 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp spt:67 dpt:68
 5226 1248K ufw-not-local  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
  107 23204 ACCEPT     udp  --  *      *       0.0.0.0/0            224.0.0.251          udp dpt:5353
 2285 1034K ACCEPT     udp  --  *      *       0.0.0.0/0            239.255.255.250      udp dpt:1900
 2834  190K ufw-user-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0           


Chain ufw-before-logging-forward (1 references)
 pkts bytes target     prot opt in     out     source               destination         


Chain ufw-before-logging-input (1 references)
 pkts bytes target     prot opt in     out     source               destination         


Chain ufw-before-logging-output (1 references)
 pkts bytes target     prot opt in     out     source               destination         


Chain ufw-before-output (1 references)
 pkts bytes target     prot opt in     out     source               destination         
  406 19556 ACCEPT     all  --  *      lo      0.0.0.0/0            0.0.0.0/0           
  810 83235 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0            ctstate RELATED,ESTABLISHED
 1018 80857 ufw-user-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0           


Chain ufw-logging-allow (0 references)
 pkts bytes target     prot opt in     out     source               destination         


Chain ufw-logging-deny (2 references)
 pkts bytes target     prot opt in     out     source               destination         


Chain ufw-not-local (1 references)
 pkts bytes target     prot opt in     out     source               destination         
 2177  130K RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0            ADDRTYPE match dst-type LOCAL
 2406 1071K RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0            ADDRTYPE match dst-type MULTICAST
  643 46833 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0            ADDRTYPE match dst-type BROADCAST
    0     0 ufw-logging-deny  all  --  *      *       0.0.0.0/0            0.0.0.0/0            limit: avg 3/min burst 10
    0     0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           


Chain ufw-reject-forward (1 references)
 pkts bytes target     prot opt in     out     source               destination         


Chain ufw-reject-input (1 references)
 pkts bytes target     prot opt in     out     source               destination         


Chain ufw-reject-output (1 references)
 pkts bytes target     prot opt in     out     source               destination         


Chain ufw-skip-to-policy-forward (0 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           


Chain ufw-skip-to-policy-input (7 references)
 pkts bytes target     prot opt in     out     source               destination         
  643 46833 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           


Chain ufw-skip-to-policy-output (0 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           


Chain ufw-track-forward (1 references)
 pkts bytes target     prot opt in     out     source               destination         


Chain ufw-track-input (1 references)
 pkts bytes target     prot opt in     out     source               destination         


Chain ufw-track-output (1 references)
 pkts bytes target     prot opt in     out     source               destination         
   17  1020 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            ctstate NEW
  997 79677 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0            ctstate NEW


Chain ufw-user-forward (1 references)
 pkts bytes target     prot opt in     out     source               destination         


Chain ufw-user-input (1 references)
 pkts bytes target     prot opt in     out     source               destination         


Chain ufw-user-limit (0 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0            limit: avg 3/min burst 5 LOG flags 0 level 4 prefix "[UFW LIMIT BLOCK] "
    0     0 REJECT     all  --  *      *       0.0.0.0/0            0.0.0.0/0            reject-with icmp-port-unreachable


Chain ufw-user-limit-accept (0 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           


Chain ufw-user-logging-forward (0 references)
 pkts bytes target     prot opt in     out     source               destination         


Chain ufw-user-logging-input (0 references)
 pkts bytes target     prot opt in     out     source               destination         


Chain ufw-user-logging-output (0 references)
 pkts bytes target     prot opt in     out     source               destination         


Chain ufw-user-output (1 references)
 pkts bytes target     prot opt in     out     source               destination  

ifconfig >>>>>

enp4s0    Link encap:Ethernet  HWaddr 48:5b:39:92:d4:e7  
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::4a5b:39ff:fe92:d4e7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10211 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2288 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2774903 (2.7 MB)  TX bytes:228426 (228.4 KB)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1140 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1140 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:230481 (230.4 KB)  TX bytes:230481 (230.4 KB)

netstat -tap >>>>

Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 *:imaps                 *:*                     LISTEN      1/init          
tcp        0      0 *:pop3s                 *:*                     LISTEN      961/dovecot     
tcp        0      0 *:9091                  *:*                     LISTEN      978/transmission-da
tcp        0      0 localhost:10024         *:*                     LISTEN      1867/amavisd-new (m
tcp        0      0 localhost:10025         *:*                     LISTEN      1721/master     
tcp        0      0 localhost:10026         *:*                     LISTEN      1867/amavisd-new (m
tcp        0      0 localhost:10027         *:*                     LISTEN      1721/master     
tcp        0      0 *:submission            *:*                     LISTEN      1721/master     
tcp        0      0 localhost:11211         *:*                     LISTEN      970/memcached   
tcp        0      0 *:netbios-ssn           *:*                     LISTEN      730/smbd        
tcp        0      0 *:pop3                  *:*                     LISTEN      961/dovecot     
tcp        0      0 *:imap2                 *:*                     LISTEN      1/init          
tcp        0      0 *:urd                   *:*                     LISTEN      1721/master     
tcp        0      0 *:ftp                   *:*                     LISTEN      1637/pure-ftpd (SER
tcp        0      0 192.168.0.2:domain      *:*                     LISTEN      946/named       
tcp        0      0 localhost:domain        *:*                     LISTEN      946/named       
tcp        0      0 *:51413                 *:*                     LISTEN      978/transmission-da
tcp        0      0 *:ssh                   *:*                     LISTEN      938/sshd        
tcp        0      0 *:smtp                  *:*                     LISTEN      1721/master     
tcp        0      0 localhost:953           *:*                     LISTEN      946/named       
tcp        0      0 *:9981                  *:*                     LISTEN      1392/tvheadend  
tcp        0      0 *:microsoft-ds          *:*                     LISTEN      730/smbd        
tcp        0      0 *:9982                  *:*                     LISTEN      1392/tvheadend  
tcp6       0      0 [::]:imaps              [::]:*                  LISTEN      1/init          
tcp6       0      0 [::]:pop3s              [::]:*                  LISTEN      961/dovecot     
tcp6       0      0 [::]:mysql              [::]:*                  LISTEN      1293/mysqld     
tcp6       0      0 [::]:submission         [::]:*                  LISTEN      1721/master     
tcp6       0      0 [::]:netbios-ssn        [::]:*                  LISTEN      730/smbd        
tcp6       0      0 [::]:pop3               [::]:*                  LISTEN      961/dovecot     
tcp6       0      0 [::]:imap2              [::]:*                  LISTEN      1/init          
tcp6       0      0 [::]:http-alt           [::]:*                  LISTEN      1488/apache2    
tcp6       0      0 [::]:http               [::]:*                  LISTEN      1488/apache2    
tcp6       0      0 [::]:urd                [::]:*                  LISTEN      1721/master     
tcp6       0      0 [::]:tproxy             [::]:*                  LISTEN      1488/apache2    
tcp6       0      0 [::]:ftp                [::]:*                  LISTEN      1637/pure-ftpd (SER
tcp6       0      0 [::]:domain             [::]:*                  LISTEN      946/named       
tcp6       0      0 [::]:51413              [::]:*                  LISTEN      978/transmission-da
tcp6       0      0 [::]:ssh                [::]:*                  LISTEN      938/sshd        
tcp6       0      0 [::]:smtp               [::]:*                  LISTEN      1721/master     
tcp6       0      0 localhost:953           [::]:*                  LISTEN      946/named       
tcp6       0      0 [::]:https              [::]:*                  LISTEN      1488/apache2    
tcp6       0      0 [::]:microsoft-ds       [::]:*                  LISTEN      730/smbd      




 Thank you!

Marc

---

### Post by Marc_Parsons on 2016-02-18
I ha[FONT=arial][/FONT]ve fixed it (SSH anyway for now) I did [COLOR=#333333][FONT=UbuntuMono]sudo iptables -A INPUT -p tcp --dport ssh -j ACCEPT

[/FONT][/COLOR]

---

### Post by Marc_Parsons on 2016-02-18
I'm just concerned that iptables decided to just block everything. I have a pfsense router so don't really need a firewall on the server. Would there be any implications for uninstalling iptables altogether?

Thank you for your assistance - it pointed me in the right direction.

---

### Post by Marc_Parsons on 2016-02-18
I just did:

sudo ufw disable :)

Thanks again

---

### Post by darkod on 2016-02-18
So, you did have the ufw firewall active. Is the server working as expected now?

No, you don't need a firewall when the server is sitting behind your router which is protected by a firewall. The server has a private IP and is unreachable directly from the internet (only ports that you forward to it).

iptables itself is not removed, but programs that use it as backend (like ufw). Default iptables policies are ACCEPT to all, unless you modify that.

If ufw was active, disabling it solves it.

---

