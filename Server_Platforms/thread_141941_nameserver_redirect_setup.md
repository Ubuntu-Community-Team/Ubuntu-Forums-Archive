---
title: "nameserver redirect setup"
date: 2006-03-09
forum: Server Platforms
---

### Post by sleepkreep on 2006-03-09
OK, I'm very new to bind and named and actually am not sure if it will do what I want.  I currently have a subdomain registered with dyndns.org (carl.homelinux.com).  This points to my router's IP and I have my Ubuntu box setup as DMZ.  My roommate has a Windows XP Pro box and would like for me to setup a domain for him to access his machine with.  What I want is a subdomain for him such as jason.carl.homelinux.com where all traffic for telnet, ftp, http, etc will be directed to his machine.  I cannot have multiple IPs as I cannot afford it.  How do I do that?

---

### Post by robert_pectol on 2006-03-09
Don't bother running a nameserver until you have a dedicated, static IP for it, and also your own domain name.  If you set up a nameserver for your current subdomain, it will never be asked to resolve anything until it is designated as authoritative for the domain.  Since yours is only a subdomain of one of dyndns's domains, it's not going to happen!

Why not just have your buddy register another subdomain with dyndns and have it also point to your router's IP?  Seems like that would be the simplest solution.  :)

---

### Post by sleepkreep on 2006-03-23
That won't work because my router can't know which call is supposed to go to his computer and which is supposed to go to mine.  For some reason, Linksys didn't build that ability into this router.  But I have mine set up as DMZ so everything goes here automatically.  Is there a way to set up iptables to route packets to his computer based on the domain called?  For instance have carlcaum.com ( new domain by the way, no static ip ) go to my local device (stay on the computer it's on) but have all logic.carlcaum.com go to his?

---

### Post by nagilum on 2006-03-25
[QUOTE=sleepkreep]That won't work because my router can't know which call is supposed to go to his computer and which is supposed to go to mine.[/QUOTE]
And that will always be the case if you have just one IP address unless you apply filters on the application level, i.e. HTTP or something like that. You can also try to setup a proxy on your machine for a specific protocol and let it reroute everything to your mate's machine. 
"Normal" filtering on TCP/IP basis won't work since it doesn't know about hostnames, just IPs and ports. That's why you have to do a DNS lookup after all. What you can do is port-based filtering, for example route all HTTP requests on port 80 to your friends computer and let your machine handle other services.

---

### Post by sleepkreep on 2006-03-25
> "Normal" filtering on TCP/IP basis won't work since it doesn't know about hostnames, just IPs and ports.
I was afraid of that.  I thought maybe the url requested was sent with the packets.  But oh well, I'll just have to set him up a user account on my machine and he'll have to deal with it.  Thanks for the help!

---

