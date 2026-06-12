---
title: "Strange Network Connection Usage"
date: 2011-03-10
forum: Security
---

### Post by shariq on 2011-03-10
I am getting problem in consumption of my bandwidth either my ubuntu server hacked or any other problem. All of my bandwidth is consuming in RX packets to an IP 65.111.166.219, I have already blocked this IP in iptables as well, but consumption is still showing on MRTG. It means iptables was not be able to block the traffic properly. I want to know what is the command from which i know which process is creating such traffic so that i can kill that process. netstat -p command is not showing any established connection.

Here is the statistics of iftop command

124.29.235.202:5060  => 65.111.166.219:5073   0b      0b      0b
                     <=                1.12Mb  1.08Mb  1.04Mb

TX:  cumm:  3.32KB   peak:   8.61Kb rates:  0b      0b    609b
RX:         11.3MB           1.03Mb        787Kb   912Kb   984Kb
TOTAL:      11.3MB           1.03Mb        787Kb   912Kb   985Kb

I have 2 interfaces eth0 and eth1, eth0 is for Local network and eth1 is using as a gateway for internet access.

I am using ubuntu server with Asterisk Sip server. My iptables rules are

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
REJECT     all  --  0.0.0.0/0            65.111.166.219      reject-with icmp-port-unreachable 
DROP       all  --  65.111.166.219       0.0.0.0/0           
DROP       all  --  65.111.166.219       0.0.0.0/0           
DROP       all  --  65.0.0.0/8           0.0.0.0/0           

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
REJECT     all  --  0.0.0.0/0            65.111.166.219      reject-with icmp-port-unreachable 
DROP       all  --  65.111.166.219       0.0.0.0/0           
DROP       all  --  65.111.166.219       0.0.0.0/0           

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
REJECT     all  --  0.0.0.0/0            65.111.166.219      reject-with icmp-port-unreachable 
DROP       all  --  65.111.166.219       0.0.0.0/0           
DROP       all  --  65.111.166.219       0.0.0.0/0      


Please let me know how can i find the process that is creating problem :confused:

---

### Post by wacky_sung on 2011-03-10
See [here]("http://whois.domaintools.com/65.111.166.219") for the mention ip address and [MRTG]("http://oss.oetiker.ch/mrtg/doc/mrtg.en.html").:popcorn:

---

### Post by shariq on 2011-03-10
I would like to know the command which show the processes which will display the establish connection of that process, so that i can kill that process easily.

---

