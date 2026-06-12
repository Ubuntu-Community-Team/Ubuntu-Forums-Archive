---
title: "Portforwarding For Ktorrent and security Issue"
date: 2009-08-26
forum: Security
---

### Post by chandru155 on 2009-08-26
I am about to portforwad to increase my Ktorrent speed. If i do, Is there possiblity that anyone can hack my System? I am newbie. I was using Windows. In windows, i use antivirus and firewall . Some times they show some alert. But in ubuntu, configuring Firewall(firestarter is very hard). Simply i dont know  how  configure even after reading the documentation.

---

### Post by cdenley on 2009-08-26
Port forwarding allows people to connect to ktorrent. The only risk is if there is a security vulnerability in ktorrent which can be exploited remotely, which is unlikely.

Firestarter is no longer maintained, and I recommend that you don't start using it. If you need a GUI frontend for iptables, use GUFW.
[https://help.ubuntu.com/community/Gufw](https://help.ubuntu.com/community/Gufw)

Unless you installed server software and didn't configure it properly, a firewall will not really accomplish anything, especially since you're apparently already behind a hardware firewall (NAT router).

---

### Post by update_manager on 2009-08-26
> **chandru155 said:**
> I am about to portforwad to increase my Ktorrent speed. If i do, Is there possiblity that anyone can hack my System? I am newbie. I was using Windows. In windows, i use antivirus and firewall . Some times they show some alert. But in ubuntu, configuring Firewall(firestarter is very hard). Simply i dont know  how  configure even after reading the documentation.

Port forwarding a specific port to your machine usually means that any IP address from the Internet can send data to that port and the router will send that traffic to your computer instead of discarding it.

This does present a (usually small) risk. The typical problem is a misconfiguration - a server running without a username/password for an example. The service listening for connections on that port may also have vulnerabilities as said earlier.

You can mitigate the risk a little by only forwarding one port, setting up a local firewall (mostly as a sanity check for what your router is doing), and not allowing ktorrent to run when you aren't using it.

---

### Post by update_manager on 2009-08-26
> **cdenley said:**
> 
Unless you installed server software and didn't configure it properly, a firewall will not really accomplish anything, especially since you're apparently already behind a hardware firewall (NAT router).

This is only 99.897% accurate. :-D

Depending on the NAT router's functionality, it might allow traffic to pass through (invalid combinations of TCP flags, impossible source addresses/ports, etc) that the local firewall does not.

---

