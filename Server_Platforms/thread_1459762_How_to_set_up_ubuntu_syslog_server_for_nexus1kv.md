---
title: "How to set up ubuntu syslog server for nexus1kv?"
date: 2010-04-21
forum: Server Platforms
---

### Post by jiangcx on 2010-04-21
I can't get the log messages from nexus 1000v on my ubuntu server. I configured nexus 1000v with the following commands:
 
Nexus1000v# conf t
Nexus1000v(config)# show logging server
Logging server: disabled
Nexus1000v(config)# logging server 10.117.4.49 7
Nexus1000v(config)# show logging server
Logging server: enabled
{10.117.4.49}
server severity: debugging
server facility: local7
server VRF: management
 
Then I configured on my ubuntu9.10 server:
 
1. sudo apt-get install sysklogd
2. insert a line to /etc/syslog.conf:
local*.* /home/cx/cisco.log
3. change SYSLOGD="" to SYSLOGD="-r" in /etc/default/syslogd
4. sudo iptables -I INPUT -p udp -i eth0 -s 10.117.0.0/16 --dport 514 -j ACCEPT
5. touch /home/cx/cisco.log
6. chmod 666 /home/cx/cisco.log
7. sudo /etc/init.d/sysklogd restart
 
I found cisco.log was changed to the owner syslog:adm. But there is no content in cisco.log.
 
Is there any wrong setting? Any help?
 
Thanks,
cx

---

