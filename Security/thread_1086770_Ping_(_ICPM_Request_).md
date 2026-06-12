---
title: "Ping ( ICPM Request )"
date: 2009-03-04
forum: Security
---

### Post by Tews on 2009-03-04
I recently ran across Gibson Research Corps' website (grc.com) to check how secure my ports were.  It showed that all were in "stealth" mode ( very good! ) but said that my computer was responding to their PING requests ..

>  Ping Reply: RECEIVED (FAILED) — Your system REPLIED to our Ping (ICMP Echo) requests, making it visible on the Internet. Most personal firewalls can be configured to block, drop, and ignore such ping requests in order to better hide systems from hackers. This is highly recommended since "Ping" is among the oldest and most common methods used to locate systems prior to further exploitation.

I always have ufw enabled just to be on the safe side, however I cant figure out how to ignore/block ping requests... Does anyone know how this is done, or am I unnecessarily paranoid??

Thanks!!

---

### Post by Nepherte on 2009-03-04
According to [https://help.ubuntu.com/community/Uncomplicated_Firewall_ufw#Enable%20PING](https://help.ubuntu.com/community/Uncomplicated_Firewall_ufw#Enable%20PING), ufw blocks ping requests by default. Are you behind a router? If so, that website will scan your router instead. You're better off scanning your computer with nmap from another computer in your network.

---

### Post by markharding557 on 2009-03-04
ping blocking can be done in the router if using one or if not in iptables,firestarter gui has a setting for this

---

### Post by Vantrax on 2009-03-04
Unfortunately Steve Gibson is a well known Quack in the security community, but many other regular users still recommend and propagate his particular brand of FUD. 

Dont worry about it too much, use UFW, or a GUI interface for iptables such as Firestarter.

Also ping is used by alot of other valid services as well. Your system (with firewall enabled) should be hardened enough that you never have to worry. If you are worried read the sticky in this subforum on AppArmor and sleep easy.

---

