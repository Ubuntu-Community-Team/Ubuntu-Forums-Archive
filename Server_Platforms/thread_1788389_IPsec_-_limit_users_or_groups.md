---
title: "IPsec - limit users or groups"
date: 2011-06-22
forum: Server Platforms
---

### Post by Corlis on 2011-06-22
Hello all,

I successfully configured a VPN using IPSec(Openswan) and xl2ptd. While roughly following this guide (among countless others): [http://riobard.com/blog/2010-04-30-l2tp-over-ipsec-ubuntu/](http://riobard.com/blog/2010-04-30-l2tp-over-ipsec-ubuntu/)

The VPN-Connection works fine, connecting to it is also a swirl, I can reach all that I want in the network, and also the gateway to the Internet works - everything being routed through that VPN.

Now my problem is actually the next steps, and I didn't succeed finding the right result on any possible search:

a) I want to limit, that the VPN-Connection is only used for distinct connections to hosts, that aren't in a "company subnet", but the IP's are publicly available. (Example: The Target-IP 8.8.8.8 allows per iptables, that only my VPN-Host 1.2.3.4 accesses it via SSH, and thus I only can access that Target-IP via SSH when I'm on the VPN). When actually browsing to the ubuntu-website, I want, that NOT the VPN-Connection is used but rather my normal connection (as a reference: i'm on a Windows-Client - not my choice, btw.)

b) I want to have several such "limitations" grouped, and give users 'access-rights' to certain hosts (Examples: 
[LIST]
[/LIST][LIST]
[*]Admin gets access to all on all ports
[*]Testers get access to some machines on distinct ports
[*]CEO gets access only to the mailserver via POP3 or IMAP
[/LIST])

So, the question here is:
Is that actually possible, and if yes, can someone point me towards the solution?

---

### Post by Corlis on 2011-06-22
After a small break, it actually hit me, as I was constantly looking at the wrong end: the Ipsec-Connections, the xl2tpd, etc. Where I SHOULD have looked would have been the assigning of local IP's to the users, which is done by PPP, and not IPsec itself.

This excellent thread: [http://ubuntuforums.org/showthread.php?t=1645473](http://ubuntuforums.org/showthread.php?t=1645473) brought me to my solution:

In /etc/ppp/chap-secrets I have to assign distinct users its IP

```
test l2tpd testpass 192.168.1.233
l2tpd test testpass 192.168.1.233
```

This IP then can be restricted with IPtables in every way necessary.

---

