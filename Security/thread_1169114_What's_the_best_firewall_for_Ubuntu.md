---
title: "What's the best firewall for Ubuntu?"
date: 2009-05-24
forum: Security
---

### Post by Ubersci on 2009-05-24
Just wondering do you need a firewall for Ubuntu 9.04. I installed Firestarter but i found out its just a graphical interface for the built in firewall. Does anyone know the best one to use, especially for previous windows users?

I'm trying to make Ubunut and Vista secure as possible because i duel boot.

---

### Post by Dave_Connor on 2009-05-24
There is the built in firewall "iptables" and it works well, Firestarter is a graphical front end for Iptables.

---

### Post by Ubersci on 2009-05-24
Thank you for the help, 'i'm new to ubuntu' Dave_Connor, so is this best one to use or should i install a separate one?

---

### Post by logos34 on 2009-05-24
> **Ubersci said:**
> Thank you for the help, 'new to ubuntu' Dave_Connor, so is this best one to use or should i install a separate one?

dave is right--iptables is the default and is more than adequate...it all comes down to how restrictive you want to make it/what to blacklist/whitelist, etc.

If you have a router, that combined with the firewall is plenty protection.

here [try this]("https://www.grc.com/x/ne.dll?bh0bkyd2") to test your machine

---

### Post by Ubersci on 2009-05-24
Thank you for the help "logos34",I use a BT router. I also liked using the firewall (firestarter) because it tells me how much I've downloaded, i use Broadband choices download monitor on vista but it does'nt work on Ubuntu but if you know one that works please direct me, I have download limit and i have looked for one but now luck.

---

### Post by lovinglinux on 2009-05-24
Firestarter is not recommended anymore. You should use UFW, which is also a firewall-manager for iptables and comes installed by default. If you want a gui for ufw, then install gufw, which is listed in the "Add/Remove" manager as "Firewall Configuration".

---

### Post by kevdog on 2009-05-25
Just to be a pain in the ***, I think iptables is technically a frontend for netfilter -> which I think is the actual built in firewall.  If I am wrong about this someone please correct me.

To answer the original question directly, there is no best firewall interface to iptables/netfilter.  It sounds like you need a gui for easy configuration.  These would be Firestarter or UFW/GUFW.  UFW is command line based but there is a GUI frontend known as GUFW.

Good luck.

---

### Post by lovinglinux on 2009-05-25
> **kevdog said:**
> Just to be a pain in the ***, I think iptables is technically a frontend for netfilter -> which I think is the actual built in firewall.  If I am wrong about this someone please correct me.

I think you are correct, but I still prefer to call it firewall rather than explaining that the netfilter is the backend for all that stuff. It would be too confusing, specially for newcomers. 

For instance, you can control netfilter without Firestarer or UFW/GUFW, but as far as I know, you can't control it without iptables.

---

### Post by The Cog on 2009-05-25
All this discussion about which firewall front-end is best is fine, but in response to the first question... No, you probably don't need a firewall. 

A standard Ubuntu install isn't listening for incoming connections, so there is nothing for a firewall to prevent from happening. Unless you install a server of some sort (web server, SSH server etc) then you have no need of a firewall. And even if you do install such a service, unless you have a restricted list of addresses that you want to allow to connect to that service, then you still have no use for a firewall.

If you do install a service and want to limit which IP addresses can connect to it, then gufw will probably do the trick for you. For more complicated requirements, perhaps guarddog. Most versatile of all of course would be to use the iptables command line directly, but it is a little complicated.

---

### Post by lovinglinux on 2009-05-25
> **The Cog said:**
> If you do install a service and want to limit which IP addresses can connect to it, then gufw will probably do the trick for you. For more complicated requirements, perhaps guarddog. Most versatile of all of course would be to use the iptables command line directly, but it is a little complicated.

Gufw can handle IPs inserted manually, but if you need to load IP blocklists, then it is terrible. It's better to use [moblock](http://moblock-deb.sourceforge.net/) or [iplist](http://iplist.sourceforge.net/) for that.

---

### Post by sarfarazkazi on 2009-05-25
> **Ubersci said:**
> Thank you for the help "logos34",I use a BT router. I also liked using the firewall (firestarter) because it tells me how much I've downloaded, i use Broadband choices download monitor on vista but it does'nt work on Ubuntu but if you know one that works please direct me, I have download limit and i have looked for one but now luck.

For tracking usage, you can use this package called vnstat. It's an easy to use command line utility and can be easily installed from the package manager. I use it for monitoring the data transfer on my broadband connection that has a monthly limit.

---

