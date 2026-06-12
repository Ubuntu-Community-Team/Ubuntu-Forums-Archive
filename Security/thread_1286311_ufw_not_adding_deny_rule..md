---
title: "ufw not adding deny rule."
date: 2009-10-08
forum: Security
---

### Post by rusty0101 on 2009-10-08
I'm running into a bit of a problem. I have a php page that is nicely collecting IP addresses from boxes that apparently are compromised. A cron job is then using ufw to filter the addresses. 

For some reason now, addresses being added via this method are not actually being added or filtered out. 

So for example if I use the commands:

[-$] sudo ufw status | grep 10.20.30.40
[-$] sudo ufw deny from 10.20.30.40
[-$] sudo ufw status | grep 10.20.30.40

Both of the 'status' runs generate no matches. If the address was not in the deny access list the first time status was pulled, it should be in the second time. For whatever reason, that is not what I am seeing at this time.

Running on the most recent LTS edition, 8.04.3 I believe.

My suspicion is that either I've exceeded the number of entries that ufw can manage, or there is something preventing the address that I'm trying to add to the list from being added because of the IP address itself. 

Ufw is otherwise working. I'm getting messages that it's dropping packets as other deny rules have specified, showing up in /var/log/syslog. It just doesn't seem to be allowing me to add more rules.

---

### Post by rusty0101 on 2009-10-21
Still an issue.

---

### Post by rusty0101 on 2009-10-21
> **rusty0101 said:**
> Still an issue.


As a workaround I ended up doing an ipchains-save to dump the current rules, edit the output and add the addresses that I've accumulated and ufw was unable to insert into the rules, and then do an ipchains-restore from that file. 

The thing is that ufw should be able to handle the rules insertion itself, I shouldn't have to add them this way.

---

### Post by bodhi.zazen on 2009-10-22
As a work around, I suggest you go to iptables directly, and not use ufw.

[http://bodhizazen.net/Tutorials/iptables/](http://bodhizazen.net/Tutorials/iptables/)

The syntax for iptables is very similar to ufw so it should be an easy transition.

Simply use a user defined chain, like blacklist

---

