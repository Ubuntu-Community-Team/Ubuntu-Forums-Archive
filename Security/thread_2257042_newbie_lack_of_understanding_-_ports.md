---
title: "newbie lack of understanding - ports"
date: 2014-12-16
forum: Security
---

### Post by Quarkrad on 2014-12-16
On my 14.04 machine Transmission works OK.  So ..... I looked at Preferences/Network and noted that I was using port (say) 50000 - I clicked on Test Port to be informed that the port was closed.  (My first lack of understanding is that Transmission works but the port is closed).  I have unticked the option to pick a random port everytime Transmission is started so  think ..... I now use port 50000 for Transmission.  I have configured gufw to allow 50000 as well as my router - restarted and still the port is closed.  I do not understand what the significance of the port is.

---

### Post by papibe on 2014-12-16
Hi Quarkrad.

**Ports in general:**
Ports exists so you can interact with several applications (or protocols) simultaneously. For instance, your web traffic can get over port 80, and a ssh session on the terminal through port 22.

**Port forwarding:**
ISP gives you one public IP address so you get into the Internet. That address is usually hold by the router. In order for all devices in your home to connect to the Internet, the router uses NAT. In other words, it assigns a private, or LAN, address to each machine in the home network, and routes the traffic both going in, and going out.

If a computer request a web page, and a phone sends a Whatsapp message, the router is smart enough to remember who asked what, so the content is delivered to the proper device.

When a connection is not generated from the home network, like a bittorrent peer requesting a file block, the router won't be able to route the request to the proper machine. Port forwarding solves this issue by creating explicit rules to map a request to a specific port to a singular machine (referred usually by its IP address).

Note that since the LAN addresses machines get are not always the same, it is recommendable that a machine that is going to receive external requests have a static (fixed) IP address. Just like port forwarding rules, this is done on the router too.

**Bittorrent protocol and transmission:**
Bittorrent is a complex protocol and it uses several ports at the same time.

For each request you make to a file block it would use a port between 49152 and 65535. Since the response of that request would come over the same port the router would manage the response without the need for port forwarding on the router.

However, if you receive a request from another peer it only receives connection over a predefined port. By default 51413, but it can be changed as you have done. If the router doesn't have a port forwarding rule to map that port to a machine, the request from that peer will be ignored. Note that this is the 'sharing' part of the protocol.

Does that helps? Let us know how it goes.
Regards.

P.S.: If you router supports NAT PMP or UPnP, you don't need to concern with port forwarding as Transmission will request the router to create the rule using these protocols. It may be necessary to enable this feature in the router because the default is off usually for security reasons.

---

### Post by Quarkrad on 2014-12-16
Thank you, that is very helpful.  My router does support UPnP and just checking - it is activated.  As this is the case, and from what you have said above (if I understand correctly), should I forget configuring specific ports for Transmission in gufw and on the router?  I rarely use a-mule but note that there is an option to *Enable UPnP for router port forwarding* in the preserences - so does the same apply for a-mule - do not assign anything specific in the router or gufw - just leave them (Transmission/a-mule) and the router/UPnP will sort?

---

### Post by papibe on 2014-12-16
Yes, pick one, or use the default (51413).

I believe you need to restart transmission (quit and reopen), if you change the port. At least that's the case in the server version (transmission-daemon).

You can also monitor the port traffic by checking your upload speed. If it is zero, something may be wrong.

Software firewalls are different story. I don't think gufw support UPnP. In this case, you should definitively open a port in your firewall.

Hope it helps. Let us know how it goes.
Regards.

---

### Post by Quarkrad on 2014-12-18
All sorted - thank you for your help.

---

