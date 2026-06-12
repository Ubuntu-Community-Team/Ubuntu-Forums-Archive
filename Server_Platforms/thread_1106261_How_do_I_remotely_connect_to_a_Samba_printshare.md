---
title: "How do I remotely connect to a Samba printshare"
date: 2009-03-25
forum: Server Platforms
---

### Post by cfree220 on 2009-03-25
Hi, I tried posting a similar question in a different section, but was not able to get any help with it.

I have a print and file server running on a wired network in my dorm room. When I have the client machine also on the wired network, I am able to access and print through the printer.

What I really need to be able to do is print to this over my school's wireless network. I tried doing this by adding the Listen IP:Port directive to the cupsd.conf file. When I tried to find the queue, I got the following error:
> Not Possible
It is not possible to obtain a list of queues from muse.dyndns.ws:631.

Obtaining a list of queues is a CUPS extension to IPP, Network printers do not support it.

I then tried to connect to it by selecting "Connect to server..." from the printers dropdown menu. I entered the IP address and port, and received this error:
> CUPS server error
There was an error during the CUPS operation: 'client-error-forbidden'.

I'm wondering if the problem is that the connection is still local (same domain). Connections to the server from on campus are routed through the University's servers. Does this then constitute being on the same network?

If that is the problem, and CUPS is right out, is there a way for me to do this via Samba? The thing making it difficult is that, while the different networks (wired, wireless, and secure wireless) are all able to communicate locally, machines on different networks on not able to see each other (at least they do not appear on the network).

---

### Post by cfree220 on 2009-03-25
That smiley should be colon port

---

### Post by dfreer on 2009-03-25
My Guess? That you are connecting to two different subnets; one wired and one wireless, and that there is a firewall/router between you and your server when you are wireless.

I'd start with posting your ifconfig information for when you are connected to the wired network/wireless network, to see if you are on the same network. Then try some basic connectivity tests (try pinging your server, testing if the ports is visible, etc). I'd double check my logs on the server just to ensure that my packets from the wireless client are hitting the server itself and not some random computer.

---

### Post by cfree220 on 2009-03-25
EDIT: I've removed ifconfig info for security reasons. If you are able to help, please PM me.

---

### Post by cfree220 on 2009-03-25
Will a port scan @ server-ip reveal show whether or not those ports are being blocked by a server or network firewall?

EDIT: Actually did the port scan. The default 631 used by CUPS for IPP appeared, as did SSH port 22, netbios-port 139 and port 445 (I think used by Samba)

---

### Post by cfree220 on 2009-03-25
Update: I tried routing my outgoing traffic through a proxy (tor). My exit node is somewhere in Spain. I could not print using CUPS even using the proxy.

---

### Post by HermanAB on 2009-03-25
Maybe this will help:
[http://aeronetworks.ca/print-howto.html](http://aeronetworks.ca/print-howto.html)

Cheers,

Herman

---

### Post by cfree220 on 2009-03-26
Thanks for the link. What I'm trying to do is set that up as a default printer, so that I can send to it with ctr+p when using any word processing program.

---

