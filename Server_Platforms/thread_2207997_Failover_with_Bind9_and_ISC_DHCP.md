---
title: "Failover with Bind9 and ISC DHCP"
date: 2014-02-26
forum: Server Platforms
---

### Post by joebell on 2014-02-26
I am new in the Ubuntu World, but full of enthusiasm to learn as much as possible. After few new system installations and configurations were managed, I decided to set up a fail-over with Bind9 DNS server dynamically updated by ISC DHCP server on two physical boxes. Here are the two tutorials I used when deploying my scenario ---> [http://blog.bigdinosaur.org/running-bind9-and-isc-dhcp/](http://blog.bigdinosaur.org/running-bind9-and-isc-dhcp/) and [http://www.madboa.com/geek/dhcp-failover/](http://www.madboa.com/geek/dhcp-failover/). The DHCP fail-over seems to work smoothly, however I have a feeling there is something bad with the DNS fail-over, as documented later on in this post. It is because of some tests I made, and due to my poor knowledge of Ubuntu Linux being a newbie as explained above. This uncertainty bothers my head, and I need to be sure everything is working perfectly. Investigating the syslog files of both physical server brought the following results:


[LIST=1]
[*]   restarting **Primary DNS** server
[LIST]
[*]primary - lines indicating the server has been restarted, plus
[LIST]
[*]zone my_domain/IN: sending notifies (serial number) 
[*]client 192.168.0.20#32951: transfer of '0.168.192.in-addr.arpa/IN': IXFR started: TSIG dns-server.key 
[*]client 192.168.0.20#32951: transfer of '0.168.192.in-addr.arpa/IN': IXFR ended 
[/LIST]
  
[*]secondary:
[LIST]
[*]client 192.168.0.10#63196: received notify for zone 'my_domain': TSIG 'dns-server.key' 
[*]zone my_domain/IN: notify from 192.168.0.10#63196: zone is up to date 
[*]zone 0.168.192.in-addr.arpa/IN: Transfer started. 
[/LIST]
     
[/LIST]
  
[*]    restarting **Secondary DNS** Server
[LIST]
[*]secondary - lines indicating the server has been restarted, plus
[LIST]
[*]zone 0.168.192.in-addr.arpa/IN: sending notifies (serial number) 
[/LIST]
  
[*][COLOR=#ff0000]**primary - no record in syslog**[/COLOR] 
[/LIST]
  
[*]restarting **Primary DHCP** server
[LIST]
[*]primary - lines indicating the server has been restarted, plus
[LIST=|INDENT=1]
[*]failover peer dhcp: I move from normal to startup 
[*]failover peer dhcp: peer moves from normal to communications-interrupted 
[*]failover peer dhcp: I move from startup to normal 
[*]balancing pool 7fdd7f9c9e50 192.168.0.0/24  total 80  free 40  backup 39  lts 0  max-own (+/-)8 
[*]balanced pool 7fdd7f9c9e50 192.168.0.0/24  total 80  free 40  backup 39  lts 0  max-misbal 12 
[*]Sending updates to dhcp. 
[*]failover peer dhcp: peer moves from communications-interrupted to normal 
[/LIST]
  
[*]secondary:
[LIST]
[*]peer dhcp: disconnected 
[*]failover peer dhcp: I move from normal to communications-interrupted 
[*]failover peer dhcp: peer moves from normal to normal 
[*]failover peer dhcp: I move from communications-interrupted to normal 
[*]balancing pool 7f10ab427e40 192.168.0.0/24  total 80  free 40  backup 39  lts 0  max-own (+/-)8 
[*]balanced pool 7f10ab427e40 192.168.0.0/24  total 80  free 40  backup 39  lts 0  max-misbal 12 
[/LIST]
     
[/LIST]
  
[*]restarting **Secondary DHCP** server
[LIST]
[*]secondary - lines indicating the server has been restarted, plus
[LIST]
[*]failover peer dhcp: I move from normal to startup 
[*]failover peer dhcp: peer moves from normal to communications-interrupted 
[*]failover peer dhcp: I move from startup to normal 
[*]balancing pool 7fdbc3ea9e40 192.168.83.0/24  total 80  free 40  backup 39  lts 0  max-own (+/-)8 
[*]balanced pool 7fdbc3ea9e40 192.168.83.0/24  total 80  free 40  backup 39  lts 0  max-misbal 12 
[*]failover peer dhcp: peer moves from communications-interrupted to normal 
[/LIST]
  
[*]primary:
[LIST]
[*]peer dhcp: disconnected 
[*]failover peer dhcp: I move from normal to communications-interrupted 
[*]failover peer dhcp: peer moves from normal to normal 
[*]failover peer dhcp: I move from communications-interrupted to normal 
[*]balancing pool 7f348f1d8e50 192.168.83.0/24  total 80  free 40  backup 39  lts 0  max-own (+/-)8 
[*]balanced pool 7f348f1d8e50 192.168.83.0/24  total 80  free 40  backup 39  lts 0  max-misbal 12 
[/LIST]
     
[/LIST]
     
[/LIST]

From what I have documented above the following two questions are to be answered:



[LIST=1]
[*]Is the behavior of the two DHCP servers OK? Just one remark - the DHCP servers are assigning IP addresses with no troubles, and that is done either if both are online, or just one of them. 
[*]When doing analysis of the two DNS servers, and trying to be sure if fail-over is working OK, that line in red color (see point 2 - primary) is confusing. I would expect some records in the log file stating the notification sent by the secondary DNS server was received by the primary server. 
[/LIST]

Finally, besides what I need to be clarified as asked above, I can see another strange indicator in the syslog file of the secondary server. This is the line I do not like to be there:


[LIST]
[*]client 127.0.0.1#45937: update forwarding 'my_domain/IN' denied 
[/LIST]

Can somebody be nice enough and submit short answers to my questions and also let me know how to fix the update forwarding denied issue?

Many thanks in advance for any help/support.

---

### Post by joebell on 2014-03-03
Hm, nobody is willing to support poor-knowledge Ubuntu user? Anyhow, thanks for reading my post and good luck to all of you.

---

