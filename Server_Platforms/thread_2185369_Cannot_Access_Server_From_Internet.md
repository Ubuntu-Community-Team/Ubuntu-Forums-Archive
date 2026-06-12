---
title: "Cannot Access Server From Internet"
date: 2013-11-02
forum: Server Platforms
---

### Post by benf101 on 2013-11-02
I admit it, I'm not a networking genius.  I need help here.  I know this question has been asked a thousand times but every answer just seems to say to set up port forwarding and everything will magically work.  I've done that with no success.  There must be something more.

I set up Ubuntu Server 12.04.3 on an old "box" and it runs fine on my local network.  The server can get out to the internet without issue.  I cannot access the server from the outside internet, however.  I called RoadRunner and they confirmed that they do not block any ports.  I can ping my IP successfully but cannot get to the server via browser.

I have set up port forwarding.
Here's a screenshot of my forwarding: [https://docs.zoho.com/file/gu1wa1c104d6ec01c4707a2ec3e5b69c4f813](https://docs.zoho.com/file/gu1wa1c104d6ec01c4707a2ec3e5b69c4f813)

These are my router settings that were auto generated:
Connection Type:	Automatic Configuration - DHCP
Internet IP Address:	192.168.0.2
Subnet Mask:	255.255.255.0
Default Gateway:	192.168.0.1

My router is a linksys WRT160Nv3.

How do I troubleshoot this?  No matter how much I read about default gateways, subnet masks, and NATs, it's not clicking.

Thanks.

---

### Post by volkswagner on 2013-11-03
You have an ip address mismatch.  Do you have more than one router?  I see two different networks (192.168.0.1 and 192.168.1.1).
Please explain your network setup and why we see two different networks (router screen shot and router settings from text in your post).

From your sever please post output of:

```
ifconfig
```

```
cat /etc/network/interfaces
```

---

### Post by nerdtron on 2013-11-04
> **benf101 said:**
> 
I have set up port forwarding.
Here's a screenshot of my forwarding: [https://docs.zoho.com/file/gu1wa1c104d6ec01c4707a2ec3e5b69c4f813](https://docs.zoho.com/file/gu1wa1c104d6ec01c4707a2ec3e5b69c4f813)

These are my router settings that were auto generated:
Connection Type:    Automatic Configuration - DHCP
Internet IP Address:    192.168.0.2
Subnet Mask:    255.255.255.0
Default Gateway:    192.168.0.1

My router is a linksys WRT160Nv3.

Thanks.

I don't think is possible. Your router has a private address? And it is even configured as DHCP. If you can't access (or even ping) your router from the outside world (the internet) how can it even perform port forwarding to your desired server?

---

