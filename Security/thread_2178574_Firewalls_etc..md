---
title: "Firewalls etc."
date: 2013-10-04
forum: Security
---

### Post by MikeCyber on 2013-10-04
HI
I hear all the time from Wirows user's that they have better Firewalls etc.

Now all I know is that Firewalls close ports. Hence they're wrong or am I missing 
something about Firewalls? Do expensive FW more than that? Maybe some 
are available for Linux?
Thanks

---

### Post by sq8jmd on 2013-10-04
Hi,
firewalls no only do job with open/close ports. Firewall in Linux (for example iptables) can look into packet and drop or pass packet if it got some phrase. Also with iptables in Linux you can decide which host can make connection with You or cannot. With iptables you can set a mark for packet if it has something special (for example it is from google dns with src port 53).

---

### Post by ajgreeny on 2013-10-04
Lots of info on this and related security topics at:-

[https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)
[https://wiki.ubuntu.com/Security/Features](https://wiki.ubuntu.com/Security/Features)
[https://help.ubuntu.com/community/Security](https://help.ubuntu.com/community/Security)

---

### Post by Hungry Man on 2013-10-04
Windows Firewalls focus on Outbound connections as well as inbound. Linux firewalls can do this as well, but outbound restrictions are *trivially* bypassed. That's why so much work goes into outbound Firewalls like comodo to prevent programs from doing things that might allow an outbound connection. On Linux there's no all-in-one tool for this, but if you're familiar enough with Linux you can get similar (if not better) results than any Windows Firewall.

---

### Post by Lars Noodén on 2013-10-05
All Linux based firewalls are based on IPtables.  So tools like UFW and GUFW are just front-ends for IPTables and if you learn to work with IPTables directly you can do anyting.  You could even build your own router or netbased firewall.  In fact many companies sell such appliances.  Many so-called "hardware" firewalls at the consumer level are running Linux.  If you have an ADSL modem, chances are it is already running linux and if you wanted to you could replace what is on there with [DD-WRT](http://www.dd-wrt.com/)

Unfortunately, the documentation for IPTables lags behind some other tools like BSD's [PF](http://www.openbsd.org/faq/pf/) in documentation.  The best overview that I know of is [Oskar Andreasson's Iptables Tutorial 1.2.2](http://www.frozentux.net/documents/iptables-tutorial/).  But that is from 2006 and still some things have been added and others removed, even if the changes are not many.

In short, you could build the equivalent of any network device on the market using Linux.

---

### Post by Lars Noodén on 2013-10-05
Just an after thought, if you are looking for the authoritative documentation (not tutorials or guides) for IPTables, you have them on your machine alread.  Look in [iptables](http://manpages.ubuntu.com/manpages/raring/en/man8/iptables.8.html) and especially **iptables-extensions**.  The latter is not online, just on your machine. 

```

man iptables-extensions

```

---

