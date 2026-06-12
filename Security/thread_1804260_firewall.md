---
title: "firewall"
date: 2011-07-14
forum: Security
---

### Post by kirthi on 2011-07-14
Windows have many firewalls to prevent the system. But Ubuntu have few. Why is it so? Is it not needed to prevent Ubuntu or if it is prevented?

---

### Post by dFlyer on 2011-07-14
Ubuntu is more secure than windows. Linux was built as a multi-tasking, multi-user networking OS. Windows was built as a single user not networking OS that had networking added as an after thought.

---

### Post by conradin on 2011-07-14
You are mistaken. Both have many but all you need is one. 
ubuntu has a nice one. Enable it with:```
sudo ufw enable
sudo ufw logging on

```

---

### Post by kirthi on 2011-07-14
ufw is a standard firewall configuration for Ubuntu. But in what ways does it help to protect my system?

---

### Post by bodhi.zazen on 2011-07-14
> **kirthi said:**
> ufw is a standard firewall configuration for Ubuntu. But in what ways does it help to protect my system?

Sounds as if you are new to both Ubuntu and Firewalls.

By default, there are no sigificant open ports, so a firewall adds very little, if anything, to a default installation.

Firewalls add to security by restricting access to open ports / servers.

I suggest you read the security sticky.

For additional information see :

[https://wiki.ubuntu.com/SecurityTeam/Policies](https://wiki.ubuntu.com/SecurityTeam/Policies)

[https://wiki.ubuntu.com/Security/Features](https://wiki.ubuntu.com/Security/Features)

[http://bodhizazen.net/Tutorials/iptables](http://bodhizazen.net/Tutorials/iptables)

---

### Post by Lars Noodén on 2011-07-14
> **kirthi said:**
> ufw is a standard firewall configuration for Ubuntu. But in what ways does it help to protect my system?

It uses the packet filter (firewall) IPTables to filter certain ports, either inbound or outbound.  UFW is just a front-end UI for IPTables.

It's not a big deal because the default on Ubuntu is to not have services listening.  But it's there if you want to play with it.

---

