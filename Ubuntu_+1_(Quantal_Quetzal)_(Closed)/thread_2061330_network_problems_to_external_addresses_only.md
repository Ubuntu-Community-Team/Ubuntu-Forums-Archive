---
title: "network problems to external addresses only"
date: 2012-09-22
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by emk2203 on 2012-09-22
During the update from Precise to the latest beta of Quantal, an age-old tryout of TOR obviously interfered with my upgrade.
I de-installed TOR after the upgrade, but now I cannot connect to external computers or ip addresses.

The internal stuff works fine; I can use the laptop to configure the router, see it's web page etc. All external addresses give a DNS error that there is no ip attached to this address.

What can I do to restore the default settings or deactivate every firewall in the laptop?

---

### Post by Iowan on 2012-09-22
Still running Quantal?

---

### Post by emk2203 on 2012-09-22
> **Iowan said:**
> Still running Quantal?

Yes, I have it on a couple of other computers, without any problems. Quantal has nothing to do with it. I had the same problem earlier when I played with TOR during my tryouts.

At that time, I switched it on and back off which cured the problem. Now it's uninstalled and I cannot reinstall it without the network.

I had hoped for a more constructive answer... :icon_frown:

---

### Post by dodo3773 on 2012-09-22
Running tor should not interfere with your firewall setup. What are you using for your network connections? Network manager or something? Check the settings there. Make sure it is not setup to go through the tor proxy. Also, I am thinking you should be able to reinstall a package from your cache if Ubuntu keeps one in the system. Maybe somewhere like -> /var/cache/apt/

---

### Post by steeldriver on 2012-09-22
I don't know how tor works - does it stomp on the default dnsmasq conf? if so maybe that would be the place to start

[https://help.ubuntu.com/community/Dnsmasq](https://help.ubuntu.com/community/Dnsmasq)

---

### Post by TheFu on 2012-09-22
What troubleshooting have you performed? netstat, routes, ifconfig, any interesting iptables lines?  What about the /etc/resolve.conf?


BTW, I really appreciate you running the beta and locating issues for the rest of the community. Thank you very much.

---

### Post by emk2203 on 2012-09-27
> **TheFu said:**
> What troubleshooting have you performed? netstat, routes, ifconfig, any interesting iptables lines?  What about the /etc/resolve.conf?


BTW, I really appreciate you running the beta and locating issues for the rest of the community. Thank you very much.

All the troubleshooting I did over the last days didn't show anything out of the ordinary.

I tried to compare with another laptop in the house also running Ubuntu Quantal, but for the life of me, I couldn't spot any noticeable differences.

All programs you mentioned gave an innocent, non-suspicious output. I finally accepted that the root cause analysis is not worth the trouble, backed up the home directory and installed the beta 2 from scratch.

Sorry to disappoint anyone with a similar problem. I'd still would like to know what the cause was.

---

