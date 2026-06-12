---
title: "help me with nmap output"
date: 2012-02-23
forum: Security
---

### Post by HodboH on 2012-02-23
hi
i need help to understand the meaning of a nmap output. I made many tests on different webserver (with linux or win 2008 standard ed.)

when i tried with servers with win 2008 server RELEASE 2, my nmap, on the MS RPC ports, told me:

RST from ****, port ****. Is this port really open?

can you help me with this? i can't understand what it means.. i saw it only with that servers.

---

### Post by Doug S on 2012-02-24
It sounds as though when nmap sends a packet with the SYN bit set to that server that port it gets a packet back with the RST bit set. The original SYN packet is trying initiate handshake to create a TCP connection. A RST packet is to terminate any connection, ungracefully (Microsoft tends to use RST, whereas MAC's tend to use FIN-ACK).
 
To test my theory for this reply, I made an iptable rule for a few ports to reject with RST. Then I tried nmap on those ports from a different computer. However, I did not get the same message as you reported. I do not know if that is because I might be using a different version of nmap, or, more likely, because I am wrong in what I thought was the cause. What I would do next is capture the namp session packets with tcpdump or wireshark and examine the actual packets.
 
Edit: It seems this repsonse can be caused by a port that appears to be open but it doesn't respoond as might be expected (perhaps with a RST packet) during OS detection. Were you trying to do OS detection during your nmap scan?

---

### Post by HodboH on 2012-02-27
yeah, i set -O option in nmap command...

that message was given only when the remote server's OS was Win Srv 2008 RELEASE 2... do u think it's possibile that in that release new security features were implemented in Remote Procedure Call service?

---

