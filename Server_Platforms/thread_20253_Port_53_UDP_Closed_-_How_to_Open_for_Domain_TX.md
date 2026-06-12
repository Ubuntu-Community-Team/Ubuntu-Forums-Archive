---
title: "Port 53 UDP Closed - How to Open for Domain TX"
date: 2005-03-15
forum: Server Platforms
---

### Post by stardotstar on 2005-03-15
Hi all, I am setting up a new web server (a first time experience for me with a dedicated clean install) and I have my bind configs sorted - name resolution working internally and for external lookups. But domain transfer has not worked. 

I suspected port 53 blocked but with nmap found it open - but that was only TCP as I eventually found after some hunting and noticing this in my secondary and external DNS server (a trusted friendly server) 

Code: 

[myip]#53: failed while receiving responses: permission denied 



It seems that bidirectional UDP port 53 and unidirectional TCP port 53 
from secondary to primary is needed to effect domain transfer and get things really running... 

So how do I enable UDP port 53 on my ubuntu server? 

I am guessing it is default closed on the firewall and being new to these security measures and configurations I don't know where to start.. 

I hope someone has some time to guide me through the process. 

Cheers and TIA, 
*.str

---

### Post by BoBoB on 2005-03-16
Basically, TCP on port 53 is only used when the packets is quite large, like the ones used in zone transfers. (I think packets < 1K are using UDP, not sure though..)

Anyway, nmap is only reporting the ports that the host is listening on, not the outgoing ports, so if you have problems making an outbond connection to port 53/tcp then it may be a firewall issue on the client PC, You should look in your logs to see what is blocking it.

I'm not a iptables/ipchains expert, maybe someone else has some hints on that...

---

### Post by tonym on 2005-03-18
Are you sure this is the problem?  Have you set permissions in BIND to allow zone transfer?

---

