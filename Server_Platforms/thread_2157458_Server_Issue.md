---
title: "Server Issue"
date: 2013-06-25
forum: Server Platforms
---

### Post by andrew0401 on 2013-06-25
We are running a mixed environment of windows & ubuntu (12.04 server) primarily for a postgresql based application.

On the LAN everything works fine. The problems come with trying to access remotely over an IPSEC VPN.

We can access all of the windows based servers with no problem at all - the ubuntu based machines are completely invisible and it is impossible to connect to them. Ping comes back as destination unreachable (both to and from the ubuntu machines) but works fine to and from all windows machines. (All machines are correctly registered in DNS & WINS)

Have done sudo ufw disable to try and ensure no firewall issue, both the windows servers and the ubuntu servers receive address via DHCP so network config should be consistent. I assume that as the windows communication works that it is not a VPN issue but am unable to work out what is making the ubuntu box invisible (even nmap is unable to get a response) I am sure it must be somthing obvious - just not sure what!

Not sure if relevant but all the windows & ubuntu servers are running under ESXi 5.0

Any help appreciated.

Andrew

---

### Post by dino99 on 2013-06-25
similar request: [http://dba.stackexchange.com/questions/18717/how-to-connect-to-an-remote-postgresql-database-on-ubuntu-using-pgadmin3](http://dba.stackexchange.com/questions/18717/how-to-connect-to-an-remote-postgresql-database-on-ubuntu-using-pgadmin3)

---

### Post by andrew0401 on 2013-06-25
Not really same as can access all functions/ports on local LAN - just no response on any port over the VPN link

---

### Post by wildmanne39 on 2013-06-25
*Thread moved to **Server Platforms**.*  Change title to be descriptive of the issue.

---

### Post by koenn on 2013-06-25
> Ping comes back as destination unreachable (both to and from the ubuntu machines) but works fine to and from all windows machines. (All machines are correctly registered in DNS & WINS)

is that ping by hostname ot ping by address ?

try address if you haven't already

tun traceroute  and compare to see where it stops.

---

### Post by SeijiSensei on 2013-06-25
It sounds to me like the Ubuntu boxes are missing a route to send reply traffic back to you over the VPN tunnel.  I don't use IPsec (I much prefer the simplicity of OpenVPN), so I cannot say whether that matters.  However if, as an example, your machine has a tunnel address of 10.10.10.10/255.255.255.0, then the Ubuntu machine needs to know that traffic for 10.10.10.0/24 has to be sent to the proxy server rather than to the default gateway.

Take a look at the routing table on one of the Ubuntu servers with "route -n".  Do you see a route for the VPN subnet with the proxy server as its gateway?

---

### Post by trundlenut on 2013-06-25
What is the vpn running on?  I have just had fun and shenanigans setting up a connection to my work VPN which uses a Sonicwall device, I got the connection working but couldn't actually access anything, turned out to be a routing problem..

---

### Post by andrew0401 on 2013-06-27
Various answers to the question.

PING - have tried via ip and via address - no response
TRACEROUTE - appears to follow correct route, all intermediate machines answer OK but the target machine respons ok to the first packet and then no more

ROUTE - had assumed that as the windows machine did not need a specific return route then the UBUNTU machines would not so a route -n only shows all routes back to the network gateway/firewall/proxy
     - update - have put a return route onto the ubuntu box - same result with travceroute, first packet from target machine works but then all fail.

IPSEC is being supported by the network gateway/firewall which is pfsense 2.0. - actually proved very easy to set up 

Andrew

---

