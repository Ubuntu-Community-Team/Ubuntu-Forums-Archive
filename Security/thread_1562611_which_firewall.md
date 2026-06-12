---
title: "which firewall?"
date: 2010-08-27
forum: Security
---

### Post by 007casper on 2010-08-27
guarddog or firestarter?

I would've created a poll, either I dont see it, or it doesnt exist anymore.

---

### Post by uRock on 2010-08-27
Neither, use GUFW. Firestarter hasn't received any updates in years.

BTW, they aren't firewalls, just a front-end to the firewall that is already there.

---

### Post by jtarin on 2010-08-27
Before you instal any GUI for firewall [go here]("https://www.grc.com/x/ne.dll?bh0bkyd2") and check what you have.

---

### Post by oldsoundguy on 2010-08-27
Neither.. I use the firewall that is in my router.

---

### Post by Iowan on 2010-08-27
> **007casper said:**
> I would've created a poll, either I dont see it, or it doesnt exist anymore. Polls were removed from the support forums as they (generally) don't apply. As I recall, the Community Cafe still offers them.

---

### Post by 007casper on 2010-08-27
jtarin - the link you suggested goes to grc - ???

---

### Post by jtarin on 2010-08-27
> **007casper said:**
> jtarin - the link you suggested goes to grc - ???

Run the shieldsup application and it will tell you your present firewall state. You could be surprised.

---

### Post by wacky_sung on 2010-08-27
Iptables is the best firewall but it take effort to learn.

---

### Post by uRock on 2010-08-27
GUFW and the others alter iptables for us to take the work out of it. On my netbook, I have to be able to change settings on the fly and prefer not to sift through a string of commands to get the right settings for the right place.

---

### Post by 007casper on 2010-08-28
shieldsup is interesting - thank you.

---

### Post by jtarin on 2010-08-28
Ubuntu comes out of the box pretty well protected.....

---

### Post by The Cog on 2010-08-28
grc shields up will scan your router, telling you nothing about your OS firewall status. If you really feel the need to scan your PC for open ports, do it from another PC on the same network using nmap.

In my opinion, setting firewall rules is generally not needed. It is only needed if **both** you have installed a server program **and** you want to restrict which IP addresses can gain access to it.

---

### Post by Lars Noodén on 2010-08-30
> **007casper said:**
> guarddog or firestarter?

Neither are firewalls (or packet filters).  They are GUI front ends for IP Tables, as are all other linux based firewall tools.

[UFW](https://help.ubuntu.com/community/UFW) seems to be the official Ubuntu UI being recommended.  It is also a front end for IP Tables.  So is GUFW.

Firewalls don't really help and when misconfigured cause lots of headache.  If the application is not secure to begin with, then a filter won't help it anyway.  Packet filtering is usually only useful if you are building a router.  Note that even it's not useful it can still be fun and also informative.  

If you want more than just opening or closing a port or thinking about building a router or wireless access point, then it's easier in the long run to work with iptables directly.  See [iptables-save and iptables-restore](https://help.ubuntu.com/community/IptablesHowTo) if that is interesting for you.

---

