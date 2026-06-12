---
title: "dhcp3 not forwarding dns server to clients"
date: 2007-08-22
forum: Server Platforms
---

### Post by cleanroom on 2007-08-22
Hi 
   I'm running Feisty server as a DHCP server and gateway for about 12 computers to the internet.  I'm also running a transparent squid proxy on the server.  While I can access websites with domain name on my server,  all the computers (windows systems) on my network can access websites by ip address only.  So I could get around this problem  by manually specifying dns servers on each of the 12 computers, but I'm sure that there is an easier way.  My /etc/resolv.conf file is not updating the way that I would expect.  In my dhcp.conf file have changed the dns address that I want dhcp3 to use.  Then I restart dhcp3 and look that the resolv file and it still has the old dns addresses in it.  I have also tried configuring the /etc/dhcp3/dhclient.conf such that the line 
     prepend domain-name-servers 127.0.0.1;

is uncommented and changed to the dns ipaddress of choice.  After restarting dhcp3 I look at the resolv file and the prepend dns server is at the top, but the other server addresses are still unchanged.  

So two questions.  
1.  Is there an obvious reason why the dhcp server is not allowing dns access to the computers on my network?  
2.  Is there another place that dns servers are specified besides the config files located in /etc/dhcp3/ and is that why my /etc/resolv.conf file is not updating as I expect it to?

---

### Post by Wicca on 2007-08-22
Hi cleanroom,

I'm not sure if I understand your fully, but here is what I think about it.

DHCP doesn't effect your resolv.conf on the server. It just pushes the settings to your clients who are configured to get a dhcp-lease. Your server should have a static IP and not to be configured to get a dhcp-lease from its own server.
What's in your resolv.conf is only the DNS-server your server itself is using, not the clients. This can be the DNS of your provider, or the server itself (127.0.0.1) ONLY if you have DNS-server implemented on the same server. I don't think you have, don't you?


>  
My /etc/resolv.conf file is not updating the way that I would expect
.
As I said, this file is not updated (and shouldn't) by your own DHCP-server.
>   
In my dhcp.conf file have changed the dns address that I want dhcp3 to use.  
.
You mean the DNS that you want your DHCP-server to send to your clients? That should be put in dhcpd.conf, not dhcp.conf.
.> 
I have also tried configuring the /etc/dhcp3/dhclient.conf......
.
That file has nothing to do with your DHCP-server either. In this file are settings In case your server is a DHCP-client itself (gets its settings from another DHCP-server).

So:
The DNS-server you want your window-clients to use: put it in the subnetsettings of the dhcpd.conf of your server.
The DNS-server you want your server to use: put it manually in resolv.conf.

---

