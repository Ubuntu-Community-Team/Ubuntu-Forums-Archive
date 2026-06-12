---
title: "Firewall Issue"
date: 2008-04-28
forum: Server Platforms
---

### Post by paulpc on 2008-04-28
I've installed ubuntu 7.10 server edition as a guest OS on a WIN XP Pro machine using VMware. I now need to ftp, telnet and SWAT to the ubuntu server, but the firewall prevents me from doing this. The only protocol it allows is SSH. 

How do I change the firewall on the ubuntu server to accept these protocols? I've already tried using 'iptables' but to not avail. 

Thanks,

paulpc.

---

### Post by cdtech on 2008-04-28
> **paulpc said:**
> I've installed ubuntu 7.10 server edition as a guest OS on a WIN XP Pro machine using VMware. I now need to ftp, telnet and SWAT to the ubuntu server, but the firewall prevents me from doing this. The only protocol it allows is SSH. 

How do I change the firewall on the ubuntu server to accept these protocols? I've already tried using 'iptables' but to not avail. 

Thanks,

paulpc.

Did you try:
```
iptables -I INPUT -p tcp --dport 25 -j ACCEPT
```
Which ever port to accept. Using the -A in place of the -I flag will add the rule to the end of the iptables, which the last rule is to deny all anything after that it will not read.

I use shorewall myself.

---

### Post by paulpc on 2008-04-28
I've since discovered that my firewall doesn't have any rules. So, it can't be a firewall issue after all. 

Each time I try to access the service, it returns, "Connection Failed". This indicates that the service handling the request probably isn't running. Although, telnet and SWAT use the super server xinetd, which is certainly running, so they should respond. 

Any ideas?

---

