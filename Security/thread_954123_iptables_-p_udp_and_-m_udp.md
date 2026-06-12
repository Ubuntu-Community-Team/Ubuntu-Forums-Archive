---
title: "iptables -p udp and -m udp"
date: 2008-10-20
forum: Security
---

### Post by Shwick2 on 2008-10-20
Running ubuntu 8.04.

Recently I was making some iptables rules to allow samba services.  As a proof of concept:

```

iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A INPUT -i eth1 -p udp -m udp --dport 137 -m state --state NEW -j ACCEPT
iptables -A INPUT -i eth1 -p udp -m udp --dport 138 -m state --state NEW -j ACCEPT
iptables -A INPUT -i eth1 -p tcp --dport 139 -m state --state NEW -j ACCEPT
iptables -A INPUT -i eth1 -p tcp --dport 445 -m state --state NEW -j ACCEPT
iptables -P INPUT DROP

```

The rules worked properly.  I then removed the "-m udp" part, restarted my windows machine and couldn't look at samba files.

I thought that "-p tcp" implied "-m tcp", so why doesn't "-p udp" imply "-m udp".  That's why I don't have "-m tcp" on all of my rules.

I understand that "various extra command line options become available, depending on the specific module", [http://iptables-tutorial.frozentux.net/other/iptables.html](http://iptables-tutorial.frozentux.net/other/iptables.html), but I thought all you needed to match a protocol was "-p".

---

### Post by kevdog on 2008-10-21
Where is -m udp even documented?  I can't find any documentation for this explicit match

---

### Post by The Cog on 2008-10-22
In **man iptables**, look for the heading **MATCH EXTENSIONS**. The udp module is listed there. The documentation clearly says that the udp module is loaded implicitly by the -p specification, so **-m udp** should not be needed.
 I just tried without the -m here, and I do seem to be picking out IPP adverts from CUPS on another box correctly. This line:
```
iptables -A INPUT -p udp --dport 631 -j ACCEPT
```
produces this output after a couple of minutes:
```
root@Titch:~# iptables -nvL
Chain INPUT (policy ACCEPT 3838 packets, 1952K bytes)
 pkts bytes target     prot opt in     out     source               destination         
    2   378 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:631 

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 3557 packets, 332K bytes)
 pkts bytes target     prot opt in     out     source               destination         

```

This makes me wonder if you are just having some kind of "finger trouble" because it is behaving as documented for me.

---

### Post by Shwick2 on 2008-10-22
hmmmm... maybe I shouldn't have used samba as a the program to test this out...

---

