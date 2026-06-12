---
title: "LAMP Server help"
date: 2008-06-15
forum: Server Platforms
---

### Post by geekytechguy on 2008-06-15
I have recently setup a LAMP server with Ubuntu 8.04, and I have bought a domain name from 1&1, how do I get my server running so that it hosts the domain name I have bought?

---

### Post by japhyr on 2008-06-15
Do you want to host the site on your computer, or just develop it on your computer and then find a hosting company?

---

### Post by windependence on 2008-06-15
> **geekytechguy said:**
> I have recently setup a LAMP server with Ubuntu 8.04, and I have bought a domain name from 1&1, how do I get my server running so that it hosts the domain name I have bought?

You need to point your site at your IP address. Do you have a static IP? There should be a control panel for your domain on their site. You need to set your 'A' record and C name to point to the IP address of your server.

-Tim

---

### Post by PacketCollision on 2008-06-15
A word on terminology: An A record is a record for a server, it points to an IP address.  A CNAME record is a nickname, it points to another CNAME or an A record.

If you have a static IP for the server, add the IP address of the server as an A record for "*yourdomainname.tld*.".  Then, either create a CNAME record for "www" pointing to "*yourdomainname.tld*." or create an A record for "www" to the IP as well.

Two notes:
1) The dots "." at the end of the domain name are important.  They mean the domain name is absolute, not a subdomain.  The lack of a . at the end of the "www" part means it is a subdomain of "*yourdomainname.tld*.".

2) While many people choose to create an A record for "www" and CNAME the root ("*yourdomainname.tld*.") to "www", that is in violation of the RFC.  It works, but it's bad practice.


If you have a dynamic IP, get a free dynamic IP service like [http://www.dyndns.org](http://www.dyndns.org) or [https://www.sitelutions.com](https://www.sitelutions.com) (whom I highly recommend for all of your DNS needs ), set up their client on your server, and then CNAME your domain to the dynamic domain name you get through the service.

---

### Post by geekytechguy on 2008-06-15
I have a static IP set up for the server, is there a IP address that is only for my server, that is for the whole internet? The server is on my personal network, and behind a firewall, so the static IP address is only for the internal network, correct?
@japhyr
I have developed the site for a while (see my signature for the php version of it, but I need (well, want) to host it my self so I can config the server to my needs, and so I can upload my linux distro with out having a space issue, or having to pay for hosting fees.

!!Also, if my server is on my private LAN network, will setting up this server to host my site for the whole internet to find, will it expose my network also??:confused:

---

### Post by windependence on 2008-06-16
Actually you will have an external and an internal IP address. Your internal IP cannot be seen from the outside and is non-routable so what you need to do is point your domain at your external IP which really should be a static one, and then forward port 80 and 443 to your private internal IP using your router.

Although you can use a redirection service such as PacketCollision mentioned, however, your site may not be reachable by everyone because some places block redirected URLs. I found out the hard way when I started hosting my own site as many of my forum users e-mailed me to tell me they could not access the site from their companies, and whether they admit it or not, most people do the majority of their surfing at work.

You usually can purchase a static IP from your ISP. If they don't offer one or block your ports, you could try switching to an ISP like SpeakEasy which does not do this.

As to your question about exposing your network to the web, the short answer is no, but should your server become compromised, then yes they certainly could breal into your network also. It sounds like you are fairly new to this, so you should be extra paranoid about security. Don't use real words for passwords, and mix case and letters, numbers, and symbols into your passwords. Only open ports you need to and use a good hardware firewall. Do all the reading you can onlocking down your server because running a web server on your network does present a very real risk. When sites are hosted commercially, they are usually placed on a separate subnet or vlan, and in a DMZ where they are isolated from the rest of the network.

-Tim

---

### Post by PacketCollision on 2008-06-16
> **geekytechguy said:**
> I have a static IP set up for the server, is there a IP address that is only for my server, that is for the whole internet? The server is on my personal network, and behind a firewall, so the static IP address is only for the internal network, correct?
@japhyr
Yes, the static IP is only for your LAN.  Your router should have options for forwarding port 80 (http) and port 443 (https) as windependence said.


> **windependence said:**
> 
Although you can use a redirection service such as PacketCollision mentioned, however, your site may not be reachable by everyone because some places block redirected URLs. I found out the hard way when I started hosting my own site as many of my forum users e-mailed me to tell me they could not access the site from their companies, and whether they admit it or not, most people do the majority of their surfing at work.

You usually can purchase a static IP from your ISP. If they don't offer one or block your ports, you could try switching to an ISP like SpeakEasy which does not do this.
-Tim
If you can't get a static IP and are worried about a redirection service being blocked, use Sitelutions as your DNS provider (they should have instructions on how to use their nameservers instead of 1&1's).  They provide a service where you run a client on your computer and it automatically updates your A record with them, so even though your IP is dynamic, it will look exactly like a static IP to the world (it will just look like you move your server around a lot).  I use them for my DNS even though I have my own servers colocated, because their free DNS service is more reliable than paid services I've used, and more trouble-free than running DNS myself.

And no, I'm not an employee or otherwise paid to promote them, I've just been a happy customer for 5 years.

---

### Post by geekytechguy on 2008-06-16
> **windependence said:**
> You usually can purchase a static IP from your ISP. If they don't offer one or block your ports, you could try switching to an ISP like SpeakEasy which does not do this.
I have Comcast for my ISP, and my friends who has set up a web server for his site also has Comcast, with no static IP, and he has had no problems with them as far as I know.

About the security, we have a hardware firewall, but can I also put a software firewall on the server? My dad is parinoid that I'll expose the whole network to the world by setting up this web server on our network, so is there any recommendations on improving security?

Thanks
Josh

---

