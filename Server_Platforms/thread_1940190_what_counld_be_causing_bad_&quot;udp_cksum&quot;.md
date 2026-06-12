---
title: "what counld be causing bad &quot;udp cksum&quot;"
date: 2012-03-13
forum: Server Platforms
---

### Post by clubbing80s on 2012-03-13
Hi.

I have an Ubuntu LTS 10.04 dns server running as a guest on VMware ESXi 4.0 when I run nslookup against it I don't always get a response. After not seeing anything in the bind or system logs I ran tcpdump. I'm seeing alot of transactions with "[bad udp cksum d095!]" errors 

typical :

tcpdump: listening on eth0, link-type EN10MB (Ethernet), capture siz                                                                                      e 65535 bytes
23:20:48.716521 IP (tos 0x0, ttl 64, id 58538, offset 0, flags [none], proto UDP (17), length 59)
    10.0.32.21.54147 > 10.0.32.7.53: [udp sum ok] 19253+ A? domain.com. (31)
23:20:48.716787 IP (tos 0x0, ttl 64, id 58206, offset 0, flags [none], proto UDP (17), length 143)
    10.0.32.7.53 > 10.0.32.21.54147: **[bad udp cksum d095!] 19253* q: A**? domain.com. 1/2/2 domain.com. [1d] A 10.0.32.7 ns: domain.com. [1d] NS ns3.domain.com., domain.com. [1d] NS ns4.domain.com. ar: ns3.domain.com. [19h] A 10.0.32.7, ns4.domain.com. [19h] A 10.0.32.9 (115)

the nslookup client is 10.0.32.21 and the Bind sever is 10.0.32.7

I have just noted that his is effecting other protocols 

23:35:20.213944 IP (tos 0x0, ttl 64, id 3305, offset 0, flags [DF], proto TCP (6), length 52)
    10.0.32.21.36398 > 10.0.32.7.10050: Flags [.], cksum 0x381e (correct), seq 23, ack 6, win 46, options [nop,nop,TS val 3390602771 ecr 124121009], length 0
23:35:20.213961 IP (tos 0x0, ttl 64, id 3306, offset 0, flags [DF], proto TCP (6), length 52)
    10.0.32.21.36398 > 10.0.32.7.10050: Flags [F.], cksum 0x380b (correct), seq 23, ack 24, win 46, options [nop,nop,TS val 3390602771 ecr 124121009], length 0
23:35:20.213972 IP (tos 0x0, ttl 64, id 35687, offset 0, flags [DF], proto TCP (6), length 52)
    10.0.32.7.10050 > 10.0.32.21.36398: Flags [.],** cksum 0xc193 (incorrect -> 0x3822)**, seq 24, ack 24, win 23, options [nop,nop,TS val 124121009 ecr 3390602771], length 0


This is traffic from the monitoring 10.0.32.21 server and the same bind server 10.0.32.7 .

These machines are on the same Virtual switch inside the ESXi host.

What would cause this ? How can I fix it ?

Thanks

G

---

### Post by clubbing80s on 2012-03-13
Hi.
Problem is related to hardware offload engine used in vmware virtual nicks 

Solution: 
[http://www.linuxquestions.org/questions/linux-networking-3/help-needed-disabling-tcp-udp-checksum-offloading-in-debian-880233/](http://www.linuxquestions.org/questions/linux-networking-3/help-needed-disabling-tcp-udp-checksum-offloading-in-debian-880233/)

"
$ ethtool --offload  eth0  rx off  tx off $ ethtool -K eth0 gso off"

---

