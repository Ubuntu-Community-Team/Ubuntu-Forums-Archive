---
title: "Should the default firewall settings in Ubuntu do OK"
date: 2009-10-04
forum: Security
---

### Post by gamefreak2009 on 2009-10-04
For the average user of course.

---

### Post by scragar on 2009-10-04
You shouldn't have any problems at all.

---

### Post by fela on 2009-10-04
A good firewall app is Firestarter, and another one is UFW (ubuntu firewall). They're both in add/remove.

Not that you'd really need one. The defaults are pretty much fine for every day use.

---

### Post by kevdog on 2009-10-04
There are really no default firewall settings since by default there are no listening processes or servers installed by default.  I would suggest that unless you are behind a router, that if you set up a server (like ftp, ssh, etc), you then may want to modify the firewall rules to restrict access.  Of course there are multiple layers of security you can use besides or in addition to iptables (which is the linux firewall), so one size might not fit all in your situation.

---

### Post by scragar on 2009-10-04
> **kevdog said:**
> There are really no default firewall settings since by default there are no listening processes or servers installed by default.  I would suggest that unless you are behind a router, that if you set up a server (like ftp, ssh, etc), you then may want to modify the firewall rules to restrict access.  Of course there are multiple layers of security you can use besides or in addition to iptables (which is the linux firewall), so one size might not fit all in your situation.

For the average user though? I don't know many average users that use a computer for FTP servers or whatever.

---

### Post by undecim on 2009-10-04
The average Ubuntu user does not need to worry about firewalls. There are no open ports unless you install server programs, so a firewall will do nothing.

---

### Post by __p1n__ on 2009-10-04
If you're not running an external service (e.g. ssh, ftp, etc.) then the only actual difference between using netfilter configured with ufw default drop and not using netfilter at all is where the inbound packet gets dropped.  There is a limit* to the maximum number of unprocessed packets on the network stack so in a DOS situation dropping them slightly sooner might keep your networking functional versus not however this is an extremely esoteric example.

Externally the difference between actually using netfilter (configured via iptables and ufw/etc.) and not is that the network ports on your computer will appear filtered versus closed respectively.  In both cases penetration attempts against those ports will fail and you'll be OK.

note: the guidance on these forums is to actually use the internal firewall and inasmuch as there is an incremental improvement in security when doing so then you should do it too.  It's not however absolutely necessary in any practical sense unless you do set up those aforementioned external services.


* defaults to 128 on modern linux distros unless explicitly modified

---

### Post by kevdog on 2009-10-04
I'm curious -- but I get the sense that more Ubuntu users than not run at least one server on their installs.  I'd bet an ftp or ssh server would be the most used but I could be wrong!!!

---

### Post by update_manager on 2009-10-09
> **undecim said:**
> The average Ubuntu user does not need to worry about firewalls. There are no open ports unless you install server programs, so a firewall will do nothing.

mdns seems to be on by default.

Also, a firewall can do more than block servers. iptables can block connections from known bad hosts/ports/IPs, invalid combinations of tcp flags, etc.

---

### Post by SoylentSteak on 2009-10-10
By default, all ports are either closed or stealthed in Ubuntu, which is quite secure. However, if you use Firestarter, they'll *all* be stealthed, and you can do one or two more things to make your computer more invisible. I doubt you'll ever need that extra security, but it's there, just in case.

Here is a good place to see the status of such things:

[https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)

Click on "Proceed", then "All Service Ports".

---

### Post by __p1n__ on 2009-10-10
> **SoylentSteak said:**
> By default, all ports are either closed or stealthed in Ubuntu, which is quite secure. However, if you use Firestarter, they'll *all* be stealthed, and you can do one or two more things to make your computer more invisible. I doubt you'll ever need that extra security, but it's there, just in case.

Here is a good place to see the status of such things:

[https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)

Click on "Proceed", then "All Service Ports".

What do you mean when you say stealthed, do you mean filtered?

I appreciate that if something is not visible to steve gibson then he calls it "stealthed" (which actually covers a lot of ground lol) but don't think that your computer is "invisible to the internet" just because that PR site of his says so.  It will actually show up quite nicely to a passive ARP scanner on the same network or an active ARP or UDP external scan even if the local f/w is configured to drop unsolicited TCP packets.

---

### Post by SoylentSteak on 2009-10-10
Now we're getting into semantics. :wink:

AFAIK, there's no perfect invisibility on the net, but some setups are more invisible than others.

---

### Post by __p1n__ on 2009-10-13
> **SoylentSteak said:**
> Now we're getting into semantics. :wink:

AFAIK, there's no perfect invisibility on the net, but some setups are more invisible than others.

No, it's not just semantics.  Gibson uses phrases like "from the point of view of attacking probes your system doesn't exist" and you yourself mention "invisibility."

If someone bothers to scan your system and it is actually running they will find out that:

1. it's up and running
2. it's either running a firewall or not depending on whether it's actually running a firewall or not

This information does not align with the "doesn't exist" and "invisibility" comments.

---

### Post by rookcifer on 2009-10-13
> **update_manager said:**
> mdns seems to be on by default.

Not on my box.  On a fresh install, there is nothing listening.

> Also, a firewall can do more than block servers. iptables can block connections from known bad hosts/ports/IPs, invalid combinations of tcp flags, etc.


Block them from doing what?  If there are no open services, there is no one to block.

---

### Post by jerome1232 on 2009-10-13
There are cases where the firewall itself is the point of attack. Firestarter (a gui frontend to iptables) used to  (still is?) be vulnerable to attack when left running as root to monitor network traffic.

For an average desktop I think time is much better spent securing your browser, it's, in my opinion, the most wide open window to your computer.

---

