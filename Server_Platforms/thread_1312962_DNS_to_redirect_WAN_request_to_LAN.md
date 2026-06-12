---
title: "DNS to redirect WAN request to LAN"
date: 2009-11-03
forum: Server Platforms
---

### Post by raydowe on 2009-11-03
Having a problem with my new Ubuntu server. I can't seem to access my machine from inside my network with my WAN address. Works fine outside the network, and LAN address works fine within. I know port forwarding and firewall are not problems for that reason.

I'm guessing that my server/router doesn't like requests to my WAN address from my WAN address. Is there a way I setup a DNS server to get around this problem, by rewriting all requests to my WAN as the LAN IP of the server? I'm not even sure what this would be called, or if I'm way off.

Any help is appreciated :)

---

### Post by i.r.id10t on 2009-11-03
You'd need 2 dns set ups - one for WAN, one for LAN

---

### Post by raydowe on 2009-11-03
Well I don't have a domain name associated with the address, so I was thinking:

1 - Everything from outside will work fine
2 - Everything from inside that request 69.XXX.XXX.XXX will be rewritten to 192.168.0.2.

Am I wrong with this? Why do I need two? Can you point me toward more information?

---

### Post by cdenley on 2009-11-03
> **raydowe said:**
> Well I don't have a domain name associated with the address, so I was thinking:

1 - Everything from outside will work fine
2 - Everything from inside that request 69.XXX.XXX.XXX will be rewritten to 192.168.0.2.

Am I wrong with this? Why do I need two? Can you point me toward more information?

Well, if you want a DNS solution, then you will need to associate it with a domain. Then you can configure your DNS server to resolve your domain to the LAN IP, then forward other requests to another DNS server. Then you would need to configure all your LAN clients to use this DNS server (if they aren't already), and make sure this DNS server isn't the authoritative DNS server for your publicly available domain.

A much simpler solution would be to add entries to your clients' hosts files (/etc/hosts or c:\windows\system32\drivers\etc\hosts). An even simpler solution would be to enable "NAT relection" or "local loopback" on your router, if such an option is available.

---

### Post by raydowe on 2009-11-03
Thanks for the reply.

I have been bouncing between these possible solutions but I can't find the best answer yet. I'm hoping there is some setting I can change on the server (possibly with DNS) as I had a Windows server running previously and never had this problem

1 - I don't want to use a hosts file because some of my computers are laptops, so leaving/entering the network would require a change in these files. Not a great solution.

2 - Loopback on the router does not exist (as far as I can find, I'm using dlink 1310). Although I never had this problem with my previous windows server setup, with or without internal DNS. That makes me wonder if the router is even a problem.

Is there a way that I can test to see if my WAN address requests are getting stuck in the router or getting through to the server?

---

### Post by cdenley on 2009-11-03
> **raydowe said:**
> 
Is there a way that I can test to see if my WAN address requests are getting stuck in the router or getting through to the server?

Well, the server doesn't usually care where the requests come from. If apache is listening on that interface, it should give some response to anything it receives, regardless of originating IP. It would also log the request. You can capture all packets received on the server with tcpdump, but that would be a little redundant.

---

### Post by raydowe on 2009-11-03
Ok, that makes sense and helps a lot.

So I guess right now I'm still on my original route: setting up my Ubuntu server to filter most requests out to my ISP's DNS, but keeping those addressed to my own WAN IP for itself.

Is there a way to do this? Am I right thinking it involves setting up my server up as a DNS Server for the network?

---

### Post by cdenley on 2009-11-03
[https://help.ubuntu.com/community/BIND9ServerHowto](https://help.ubuntu.com/community/BIND9ServerHowto)

Configure a caching DNS server, then add a zone for your domain which will be used to access to access your LAN servers. Then configure your router's DHCP server so it assigns your new DNS server to the client machines.

---

### Post by raydowe on 2009-11-03
I will do that. Thanks very much for the reference.

One last question: Can I still do this without a domain name? I only have a static WAN IP.

---

### Post by cdenley on 2009-11-03
> **raydowe said:**
> I will do that. Thanks very much for the reference.

One last question: Can I still do this without a domain name? I only have a static WAN IP.

You can make up a domain, and that domain will have to be used internally if you don't want to enter the LAN IP. I don't think you can configure DNS to resolve your WAN IP to your LAN IP, though. If you're accessing by IP anyway, why not simply use your LAN IP internally?

---

### Post by raydowe on 2009-11-03
Because that is where I run into the problem of:

1 - LAN Server address works (only) inside of network
2 - WAN Address works (only) outside of network

So i'm looking for a solution where I can use my WAN address whether I'm inside or outside of my home network. Otherwise my netbook will have to switch addresses depending on where I'm using it.

DNS would work, but seems I would need an internal domain name that matches a public domain name.

There must be a way to somehow do this. Like I said earlier, it was working fine last week with my windows server, so I'm convinced I can get it working somehow with my router the way it is.

---

### Post by raydowe on 2009-11-03
Is there a way to make a DNS Server "catch" IP's and use them as it's own?

For example, if I request 69.XX.XX.XX, it goes to the network DNS server (on 192.168.0.2) and instead of sending it out to be resolved, it says, "That's mine", and tries to serve the request itself?

---

### Post by cdenley on 2009-11-03
> **raydowe said:**
> 
There must be a way to somehow do this. Like I said earlier, it was working fine last week with my windows server, so I'm convinced I can get it working somehow with my router the way it is.

Was your Windows server acting as a router? Was it replaces with the D-link router you're using now? Was it a DNS server? When a client attempts to send a request to your WAN IP, it will be routed to the default gateway (your router). Some router's will see it is for its own WAN interface, check for any port forwarding rules, then route it back to the LAN server. Some will not do this for connections from the LAN. If your router does not route LAN packets according to your port forwarding rules, then there is nothing you can do except replace it with a router that does, or add a second router which does.

Client computers will not send DNS queries for IP addresses, only hostnames.

---

### Post by raydowe on 2009-11-03
Not as a router, but as a DNS server. All my computers would request lookups from the server first (192.168.0.2), and then the router (192.168.0.1) as a backup. The server would also forward requests to the router as needed, which forwarded them to my ISP. Gateways for all the computers were/are set to be the router.

Really, the only change I made was to replace windows server 2003 with ubuntu server. I have one router behind which are a few computers and this one server. No changes to the router, same ip's for everything.

Is there a difference between going to a local dns server and forwarding and going to the router directly?

I really appreciate your input on all of this :)

---

### Post by cdenley on 2009-11-03
> **raydowe said:**
> Is there a difference between going to a local dns server and forwarding and going to the router directly?

Not unless you configure the "local dns server" to resolve certain domains itself instead of simply forwarding and caching all the queries. Packets being sent to your WAN IP would go directly to the router (default gateway), and have nothing to do with a local DNS server. The only way that windows server could have affected requests to your web server is if you used it to resolve the domain name of your server.

---

### Post by redmk2 on 2009-11-03
> **Originally Posted by raydowe]
Is there a difference between going to a local dns server and forwarding and going to the router directly?[/QUOTE]

Yes.  using local DNS allows you to name your local hosts and resolve them to the local (NAT'd) private non route-able  IP addresses.  If all of your LAN are public IP addresses, then there is no difference between LAN and WAN except who is administrating the DNS server.

See: [Internet Assigned Numbers Authority (IANA)]("http://www.iana.org/")

[QUOTE=cdenley said:**
> ... I don't think you can configure DNS to resolve your WAN IP to your LAN IP, though. If you're accessing by IP anyway, why not simply use your LAN IP internally?

@cdenley,

That's correct, DNS is only to map host names or FQDN to IP addresses.  As a mater of fact, if the OP is using IP addresses only, there is NOTHING TO CACHE.  Caching only caches the name to IP mapping so the host does not need to ask for the same information over and over from a remote DNS server.   

And this is the core thought, The OP may not be able to view his web page from an internal host via the external IP address on his router (his "WAN IP address"), but it is not a DNS problem per se.  

Ultimately if the router is capable of allowing traffic originating from an inside IP address back inside (a security risk in my opinion), then DNS would make it irrelevant as to whether it was an internal or external address that was resolved.

In the end the IP packet will arrive at the private address anyway.

---

### Post by confusedstingray on 2009-11-05
from what i have read you want to type in [www.mydomain.com](www.mydomain.com) from internal (lan) and from external (wan) and get to the same site.

if this is right you have to set you dns lookup on you internal lan to point to your local dns server. and on your netbook have it point to local and your isp as secondary

so on your lan clients have the dns point to local dns server. If your lan clients are ubuntu do this in the /etc/resolv.conf and add the ip of your dns server
if the clients are windows do it under network settings 

On your dns server you set the dns to point your isp and set the gateway as your router

---

