---
title: "Server 8.04 - hostname resolveing (with no hosts file edit or DNS)"
date: 2008-07-15
forum: Server Platforms
---

### Post by hexbin on 2008-07-15
Ok, here's the deal...
On older Ubuntu Servers, when I installed it, and gave it a name **server-machine**, each time I entered **server-machine** in my web browser on the other computers in my network, I was directed to this server.

Now, this same **server-machine**, doesn't introduce it self at all to the network. Even when using Webmin and Virtualmin to create new virtual host, with virtualhost names... Let's say I created **vserv** virutal host, I get a entry **vserv.** in my DNS, instead of **vserv.server-machine**

I need a solution without using host file, since the network uses a lot of random computers... Also, I would need this computer to respond to **server-machine**, or virtual host to **vserv.server-machine** when using Telnet, SSH, FTP and other programs that require connection to the server.

Thanks in advance for all your helpful and constructive comments ;)

---

### Post by p_quarles on 2008-07-16
No hosts or DNS, huh? I don't think there's anything we can do apart from wishing you luck. 

Without delegating the responsibility for names to a particular process, the computers will never be able to agree on what is what. /etc/hosts and DNS are the tools that allow you to do this.

---

### Post by windependence on 2008-07-16
> **hexbin said:**
> Ok, here's the deal...

Now, this same **server-machine**, doesn't introduce it self at all to the network. Even when using Webmin and Virtualmin to create new virtual host, with virtualhost names... Let's say I created **vserv** virutal host, I get a entry **vserv.** in my DNS, instead of **vserv.server-machine**


It would only be vserv.server-machine if server-machine was your domain. This is NOT the case, server-machine in this case is the name of the host computer (hostname). 

What you are trying to do is next to impossible as was suggested. DNS is something everyone has a hard time with. If you are going to keep swapping out random computers, even a DNS server won't work without making a DNS entry for each new computer. I am curious as to what you are trying to accomplish here, is this a gaming LAN type situation?

-Tim

---

