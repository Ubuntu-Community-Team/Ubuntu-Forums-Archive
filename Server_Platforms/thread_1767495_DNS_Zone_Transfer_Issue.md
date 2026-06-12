---
title: "DNS Zone Transfer Issue"
date: 2011-05-25
forum: Server Platforms
---

### Post by shanth2600 on 2011-05-25
Hey Guys,
I'm having an issue with my DNS server. I want to set up a secondary zone on my ubuntu server who's master server is a Windows Server 2003. I don't know whether the problem lies in the Ubuntu box or the Windows Server.
 
heres the secondary zone inside of /etc/bind/named.conf.local
(192.168.0.66 is the windows server)
 
zone "xyz.com" {
type slave;
file "/etc/bind/slaves/slave.xyz.com.db";
masters{ 192.168.0.66; };
allow-transfer { 192.168.0.66; };
allow-notify {192.168.0.66;}; 
}; 
 
I have not added any transfer or notification lines into named.conf.options
 
I have set up the xyz.com zone in the windows server and have configured it to allow zone transfers and notification to the Ubuntu server.
 
When I saw that it wasn't working I decided to look in the syslog and saw something interesting:
May 25 05:52:40 ns1 named[12104]: transfer of 'xyz.com/IN' from 192.168.0.66#53: failed to connect: timed out
May 25 05:52:40 ns1 named[12104]: transfer of 'xyz.com/IN' from 192.168.0.66#53: Transfer completed: 0 messages, 0 records, 0 bytes, 21.039 secs (0 bytes/sec)
 
 
Thanks In advance for any responses.

---

### Post by hawkmage on 2011-05-26
Are you allowing TCP port 53 connections.  Normal DNS look-ups are done via UDP but zone transfers are done via TCP.

---

