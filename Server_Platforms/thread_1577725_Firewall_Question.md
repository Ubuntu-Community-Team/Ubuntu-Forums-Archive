---
title: "Firewall Question"
date: 2010-09-19
forum: Server Platforms
---

### Post by mistypotato on 2010-09-19
What is the absolute quickest or easiest way to block an incoming connection by their IP address ?  I'm running an apache2 LAMP server on Ubuntu 8.10

For example, let's say I'm watching my server error logs and I see someone using a script to check for phpmyadmin and other such folders.  Right away I know this is a hack attempt.

Firestarter does not allow ANY way to block an incoming connection by IP (to my disappointment) and adding the IP to an apache configuration file requires an apache restart (way too much trouble and time).

Any suggestions?

thx

---

### Post by jbrown96 on 2010-09-19
```
sudo iptables -A INPUT -p tcp -s <Address> -j DROP
```

---

### Post by mistypotato on 2010-09-19
Thank you !!  :ks

---

### Post by LightningCrash on 2010-09-19
Look into Fail2Ban, OP. It can automatically (and temporarily) block people based upon certain log entries.
With some tinkering, it can even permanently ban people

---

### Post by mistypotato on 2010-09-19
> **LightningCrash said:**
> Look into Fail2Ban, OP. It can automatically (and temporarily) block people based upon certain log entries.
With some tinkering, it can even permanently ban people

That would seem to be an excellent solution for those who run scripts against a server looking for certain directories such a phpmyadmin.

While I try my best to avoid putting anything like that within a script's reach, accidents happen.

I just wouldn't want someone to get lucky running one of these scripts and find a way in.

Having Fail2ban check for multiple simultaneous log entries where /phpmyadmin is the target for example and instantly banning by that IP address seems as though it would offer some protection.

I wonder how difficult that would be to set up?

Have you ever done that with Fail2ban?

---

### Post by LightningCrash on 2010-09-19
Wouldn't be difficult at all

[http://foosel.org/blog/2008/04/banning_phpmyadmin_bots_using_fail2ban](http://foosel.org/blog/2008/04/banning_phpmyadmin_bots_using_fail2ban)

---

