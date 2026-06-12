---
title: "[SOLVED] Port Forward on Name Based Hosts (similary to virtual hosts in apache)?"
date: 2008-08-04
forum: Server Platforms
---

### Post by ulnagar on 2008-08-04
Hi,

I'm fairly new to Ubuntu and have been playing around with 8.04 Server for a couple of months now. I've set up apache with a number of virtual hosts and I'd like to take the next step of separating some of the hosts onto another physical machine.

I was wondering if anyone knew of a way to create port forwarding rules based on the server name requested? At the moment I have my ADSL "modem/router" port forwarding all requests on port 80 to my server. As I understand it though, if I move some of my websites to another box, it wont get any requests from the internet.

If there is an application that can do this, I am quite happy to have an Ubuntu box running as NAT/Firewall in the DMZ of my ADSL connection, which would then separate the website requests for my LAN. I know this is probably not an easy undertaking, but I built my Ubuntu server to play around, and I figure it's time to move forward. :D

Thanks

---

### Post by netztier on 2008-08-05
> **ulnagar said:**
> 
I was wondering if anyone knew of a way to create port forwarding rules based on the server name requested? At the moment I have my ADSL "modem/router" port forwarding all requests on port 80 to my server. As I understand it though, if I move some of my websites to another box, it wont get any requests from the internet.


Unless your DSL router can inspect and understand HTTP headers, there's no way to do this with the router. Normally, routers only understand IP adresses and TCP ports. Your DSL service probably only has a single external IP address, assigned to your router by PPPoE, PPPoA or DHCP.

If you were to run multiple Web services with that, you'd have to have multiple DNS records resolve to that single IP address of yours. Probably some dynamic DNS service also comes into play, let's have an example:

[LIST]
[*] Your ISP assigns you: 84.196.22.33, which might reverse-resolve to something like dyn-84-196-22-33.yourisp.com
[*] You'll use some DynDNS-style service to register "mydsl.dyndns.org" as your "first" DNS record that points to the above IP address.
[*] You'll then have a DNS domain of your own, say "mylittlewebservice.com", and in this domain, you want to have "server1.mylittlewebservice.com" and "server2.mylittlewebservice.com". These are CNAME records that point to "mydsl.dyndns.org"
[/LIST]

Now - someone will want to access [http://server2.mylittlewebservice.com/](http://server2.mylittlewebservice.com/). This will trigger a DNS lookup that will eventually return 84.196.22.33 as an answer, and since it's a HTTP request, there will be a TCP SYN being sent to port 80 on that IP address. 

This TCP SYN cannot be discerned from TCP SYN that has been sent by someone looking for [http://server1.mylittlewebservice.com/](http://server1.mylittlewebservice.com/) , since it looks exactly the same: same destination IP address, same destination TCP port.

A TCP SYN has no payload, no "URL inside" that could be interpreted and reacted to. So your router has a problem: Where to forward these SYNs to? Before the client system on the Internet can send it's HTTP request, it needs an "ACK" back from the server it wants to talk to - but again: from which one? The router cannot know it, since the client hasn't yet said which server it wants to talk to...


Solution: **Reverse Proxy.**

On one of your hosts, run a reverse proxy service (for example **squid** can be configured to  do this). That would be the system "in a DMZ" you were referring to. If you google around for it, you should be able to find guides how to configure squid as a reverse proxy.

Have the forwarding of port 80 point to the proxy host's IP address. This proxy host will accept and interprete the incoming connection request (including the URL) and then issue a web request to the right internal server.

This has the surplus advantage that only your Proxy host is exposed towards the internet, not the individual hosts that run the Web servers. However, it is important to run the reverse proxy with a configuration that only allows requests for your own web servers - if configured badly, you expose it to the risk of being an "open Proxy" that will soon be abused in various ways...

regards

Marc


PS: Some broadband routers allow you to run Linux-based firmware that can be modified and extended to your needs, maybe even to run squid right on that small box. So you might not need to run another host just for a reverse proxy.

PS2: only do the "DMZ" thing if your router actually has a dedicated DMZ port. What is often called "DMZ host" on many broadband routers is an "exposed host": *all* incoming traffic from the Internet will be forwarded to that host. Calling this a "DMZ host" is one of the most horrible misnomers (or a plain, blunt, marketing blunder) of the networking industry. If you don't have an actual DMZ port, just use a "pinhole" port forwarding to your proxy host, with only the actually needed TCP port(s).

---

### Post by ulnagar on 2008-08-05
Excellent, thanks! That's exactly what I wanted to know.

My DSL router is a fairly cheap one, so it doesn't support a Linux Firmware, and it doesn't have a dedicated DMZ port, so I will definately go for the port forwarding option to the Reverse Proxy.

I do actually have a registered domain name, and my ISP gives me a static IP, so I don't need the DYNDNS account.

Thanks again for pointing me in the right direction!

---

