---
title: "blocking attempts to port scan"
date: 2010-11-19
forum: Server Platforms
---

### Post by tapas_mishra on 2010-11-19
I  and see following attempts in /var/log/auth.log which I was told by some one could be port scanning attempts.(Not sure though)
```
Nov 18 23:50:19 server sshd[21716]: Did not receive identification string from 186.0.80.197
Nov 19 00:05:57  server sshd[24056]: Did not receive identification string from 85.108.110.66

```
How can I block above such attempts?

---

### Post by SeijiSensei on 2010-11-19
Use iptables to block connections to your ssh port from machines other than ones you control or trust.

```

MYSERVER=192.168.100.100
TRUST=192.168.1.1

iptables -A INPUT -p tcp -s $TRUST -d $MYSERVER --dport 22 -j ACCEPT
iptables -A INPUT -p tcp -d $MYSERVER --dport 22 -j REJECT


```

Use something like this instead of a blanket ACCEPT for port 22 in your iptables firewalling script.

---

### Post by tapas_mishra on 2010-11-19
> **SeijiSensei said:**
> Use iptables to block connections to your ssh port from machines other than ones you control or trust.

I regularly do that but I want to automate suspicious login attempts.
Lot of people login and they come from various countries and various IP's which are daynamic  given to them by their ISPs

---

### Post by SlugSlug on 2010-11-19
install denyhosts

---

### Post by SeijiSensei on 2010-11-19
> **tapas_mishra said:**
> I regularly do that but I want to automate suspicious login attempts.
Lot of people login and they come from various countries and various IP's which are daynamic  given to them by their ISPs

And when you know it's coming from some host in Malaysia, what are you going to do with that information?  Reporting them to ISPs is a fruitless task.  Any script kiddie with half a mind can automate attempts to log into ssh.  I long ago stopped paying attention to the sources of attempted intrusions and just made sure they couldn't get access to the ssh port by using iptables.  Then I stopped worrying about it.

Nowadays I rarely even leave ssh open to the outside.  I run OpenVPN tunnels and limit connectivity to those.

---

### Post by tapas_mishra on 2010-11-19
> **SeijiSensei said:**
> And when you know it's coming from some host in 
 

> **SlugSlug said:**
> install denyhosts
I do use denyhosts and that does block after a threshold attempts I have also rate limited IPTABLES.
My question is not how to stop SSH brute force my question is I want people not to be able to scan ports.
Ok I got some thing useful for my question I am sharing here might help some one.
[http://www.ossramblings.com/using_iptables_rate_limiting_to_prevent_portscans](http://www.ossramblings.com/using_iptables_rate_limiting_to_prevent_portscans)

---

### Post by alienprdkt on 2010-11-19
> **tapas_mishra said:**
> 
Ok I got some thing useful for my question I am sharing here might help some one.
[http://www.ossramblings.com/using_iptables_rate_limiting_to_prevent_portscans](http://www.ossramblings.com/using_iptables_rate_limiting_to_prevent_portscans)

Thanks! Will help me out.

---

