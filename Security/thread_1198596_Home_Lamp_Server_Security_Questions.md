---
title: "Home Lamp Server Security Questions"
date: 2009-06-27
forum: Security
---

### Post by waloshin on 2009-06-27
I am running a Home lamp server with Ubuntu 8.10. I was wondering if I use my ip address as the server address and someone hacks my address, what damage could they do?

Would it affect the Server or just the Windows machines?

I was also wondering firestarter vs selinux?

Thanks

---

### Post by cariboo on 2009-06-27
If you are behind a router and using standard non-routable class C ip addresses, and you don't have any ports forwarded in the router, you should be failry safe.

---

### Post by Agent ME on 2009-06-27
> **waloshin said:**
> I was also wondering firestarter vs selinux?
Firestarter is a firewall front-end.
SELinux is an optional Linux subsystem which can enforce access control lists, an advanced system for setting what users can and can't access, which are more flexible than the regular Unix permissions scheme.

---

### Post by SlugSlug on 2009-06-28
> **waloshin said:**
> I am running a Home lamp server with Ubuntu 8.10. I was wondering if I use my ip address as the server address and someone hacks my address, what damage could they do?

Would it affect the Server or just the Windows machines?

I was also wondering firestarter vs selinux?

Thanks

using your IP address is the same as using a host name; 
ping [www.ubuntuforums.org](www.ubuntuforums.org) - you get the IP 

Would it affect the Server or just the Windows machines?

you need to elaborate here.. wheres the service getting pointed to ? why would it touch windows machine? 
am no sql or php expert but I know enough if there set up by novices there more that likely to be a security flaw but your router should take care of that unless you forward the ports on to the server

---

### Post by TurboRush on 2009-06-30
Are you questioning what risk do you have if your LAMP server is not a seperate physical server from the one you use to surf the web, write emails, store personal information, etc?

---

### Post by hackertarget on 2009-07-02
Taking a guess at what the OP is attempting to ask, I will make some assumptions.

Lets say you are wanting to run a web server out of your home LAN.

Your home LAN is on a private range 192.168.x.x behind a home router that is using NAT. 

For external access to your web server you need to forward port 80 from external sources to your internal IP of server.

To see if your http port forwarding is working - you can use an online port scanner to scan your public IP for open ports. Check my sig or google it. :)

[COLOR="Red"]Now for the second part of the question, security[/COLOR].

If you are wanting to play around with apache and some php scripts as an example, you need to be aware of the risks and understand that it is possible for your server to get taken over unless it is secured and well managed.

Now if that happens the attacker has full access to your web server and from there he can bounce to internal hosts and play with your internal windows workstations depending on your Windows security.


Hope this helps...

---

