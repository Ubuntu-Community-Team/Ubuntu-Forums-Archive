---
title: "Browsing alternative to SOCKS Proxy (SSH)"
date: 2009-09-22
forum: Security
---

### Post by WinstonChurchill on 2009-09-22
Hello all.

I'm looking for a secure way for (practically) anonymous users to "tunnel" their web traffic through a remote server running Ubuntu (For purposes of security, bypassing draconian firewalls, watching NetFlix from Mexico, etc.)

I currently accomplish this for myself using a SOCKS proxy (ssh ... -D port) - however, the machines on my network generally assume that they can trust themselves, so any user I allow to do this has access to whatever open SMB shares, Web-based configuration, printers, etc that exist on my local network, not to mention possible sniffing of my traffic, which is obviously undesirable. 

Rather than having to secure my network against itself, my solution is: set up a Squid proxy and allow these limited users to forward only port 3128 (via PermitOpen in sshd_config). They would then point their web browsers to an HTTP Proxy at their localhost:3128. Thus, they would still be able to browse the web over an SSH tunnel, and they would not have access to any of my local resources besides Squid.

So, I have 2 questions:
1) Is this a good solution, security-wise?
2) Will the users DNS lookups be performed locally by default, or over the proxy?

Thanks!

---

### Post by openfly on 2009-09-23
I do this.  It works.  DNS lookups should be performed by the proxy server.

Onion Routing and VPN are also more robust solutions to your problem I'd guess.

---

