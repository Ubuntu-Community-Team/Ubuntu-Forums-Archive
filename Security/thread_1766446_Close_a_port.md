---
title: "Close a port?"
date: 2011-05-24
forum: Security
---

### Post by LifeForce4 on 2011-05-24
I ran nmap on my system and all ports were closed. Then I installed httpd(apache2) and port 80 was open. I have been trying to get the port closed again this is just a dev install of apache and only localhost needs access to it. I've been trying many different ways all have been unsuccessful. Currently I'm trying ufw before going back to iptables again.

Is there a simple way to accomplish this?

```
The lines I entered when trying.
UFW: deny proto tcp to any port 80
IPTABLES: -I INPUT 1 -i eth0 -p tcp -m tcp --dport 80 -j DROP
```

Thank you,
LF4

---

### Post by tgm4883 on 2011-05-24
> **LifeForce4 said:**
> I ran nmap on my system and all ports were closed. Then I installed httpd(apache2) and port 80 was open. I have been trying to get the port closed again this is just a dev install of apache and only localhost needs access to it. I've been trying many different ways all have been unsuccessful. Currently I'm trying ufw before going back to iptables again.

Is there a simple way to accomplish this?

```
The lines I entered when trying.
UFW: deny proto tcp to any port 80
IPTABLES: -I INPUT 1 -i eth0 -p tcp -m tcp --dport 80 -j DROP
```

Thank you,
LF4

There is a difference in the two terms you are using there, and it's an important one to at least know about.

None of the ports were initially 'closed' since the firewall wasn't active. There was just nothing listening for connections on any ports.

After installing Apache, it started listening on port 80. You can use a firewall to block that port, which will not allow other clients to connect to it (but it will still be listening for connections). 

While having a firewall is good, I say configure apache to only listen on localhost. If that cannot be done then go ahead and block it with the firewall.

Also, IIRC UFW is just a frontend for iptables. You can also try GUFW

---

### Post by LifeForce4 on 2011-05-24
That makes sense thank you for pointing it out. I'll configure apache for that.

---

### Post by Lars Noodén on 2011-05-24
Consider using REJECT instead of DROP, there's no advantage in security or other factors for using DROP. 

If you use the target [REJECT](http://www.chrisbrenton.org/2009/07/why-firewall-reject-rules-are-better-than-firewall-drop-rules/) instead of [DROP](http://www.chiark.greenend.org.uk/~peterb/network/drop-vs-reject), then you make it easier for yourself when diagnosing your filter.

---

