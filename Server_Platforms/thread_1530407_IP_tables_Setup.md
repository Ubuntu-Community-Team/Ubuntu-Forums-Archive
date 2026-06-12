---
title: "IP tables Setup"
date: 2010-07-13
forum: Server Platforms
---

### Post by Carleas on 2010-07-13
In the [iptables how-to]("https://help.ubuntu.com/community/IptablesHowTo"), it suggests the following lines in /etc/network/interfaces to save and restore the rules:
```
auto eth0
iface eth0 inet dhcp
  pre-up iptables-restore < /etc/iptables.rules
```
However, the file in my server doesn't have a line "iface eth0 inet dhcp".  Instead, it has "iface eth0 inet static" and "iface eth0 inet6 static"
Will putting the lines in those sections work?  I take it inet6 is for IPv6, and I have separate rules for ip6tables, so can I put a separate couple lines of code in each section, e.g.:
```
auto eth0
iface eth0 inet static
  pre-up iptables-restore -c < /etc/network/iptables.rules
  pre-down iptables-save -c  > /etc/network/iptables.rules
iface eth0 inet6 static
  pre-up ip6tables-restore -c < /etc/network/ip6tables.rules
  pre-down ip6tables-save -c  > /etc/network/ip6tables.rules
```

---

### Post by arrrghhh on 2010-07-13
I believe the 'official' way to manage your firewall is UFW.  Or maybe it's just for special people like me, but it makes managing the firewall a heckuva lot easier than using iptables directly!

---

### Post by spynappels on 2010-07-13
UFW is no more official than using iptables directly.

UFW is fine for simple rules, but when it comes to firewalling separate interfaces differently, it's hard to beat iptables.

To the OP, the first section is fine, I'm not sure if the IPv6 bit will work but the other bit should be fine.

---

### Post by Carleas on 2010-07-13
I think ufw is just another way to do firewall, not necessarily the "official" way.  I used iptables only because I've seen it recommended so often.

---

### Post by arrrghhh on 2010-07-13
Well of course iptables is going to be more powerful, but you also must agree for simple firewall rules UFW is much easier to configure/manage.

I also put 'official' in quotes for a reason...  I didn't mean to insinuate that you can't use iptables at all - clearly that's not the case.  It's just much more difficult to configure/maintain.

---

### Post by YesWeCan on 2010-07-14
[http://www.cyberciti.biz/faq/setting-up-an-network-interfaces-file/](http://www.cyberciti.biz/faq/setting-up-an-network-interfaces-file/)

I think this will work:

auto eth0
iface eth0 inet static
iface eth0 inet6 static
  
pre-up iptables-restore -c < /etc/network/iptables.rules
post-down iptables-save -c  > /etc/network/iptables.rules

---

