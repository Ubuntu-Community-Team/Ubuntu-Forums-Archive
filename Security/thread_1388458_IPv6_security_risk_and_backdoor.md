---
title: "IPv6 security risk and backdoor"
date: 2010-01-23
forum: Security
---

### Post by cilbuper on 2010-01-23
I forget what I was reading or what I was listening to, it may have been Hakin9 magazine or some security podcast.  I am not a security expert so bare with me as I will try to explain what I heard.  


The jist of the report was that many people have missed a large security issue which is related to the IPv6 protcol.  Since most people are not using IPv6 yet, many people forget to secure it.  

I think this is especially an issue for anyone with a server that is connected to the internet.  

I don't remember much more than this, but I do remeber that the expert said that it is a high security risk and it needed to be addressed.  

I was wondering if there are steps that should be gone through to secure this protocol?

---

### Post by Lars Noodén on 2010-01-23
Is it delayed memory recall of the March / April 2007 discussions of IPv6 type 0 route headers which, before that was fixed, could be used to mount a DoS attack against hosts and networks?

Post back if you can find a link to whatever it was that you are trying to describe.  Otherwise...

---

### Post by rookcifer on 2010-01-23
I think you're probably talking about [this.]("http://www.networkworld.com/news/2009/071309-rogue-ipv6.html?page=1")  But this is not really a flaw in the protocol itself, but a result of many people not realizing that IPv6 is operating on their machine.

---

### Post by movieman on 2010-01-26
I believe the Ubuntu firewalls (at least firestarter and I think ufw) block IPV6 by default, because I remember having to hack some configuration files to get it to work.

---

### Post by bodhi.zazen on 2010-01-26
> **movieman said:**
> I believe the Ubuntu firewalls (at least firestarter and I think ufw) block IPV6 by default, because I remember having to hack some configuration files to get it to work.


No, they do not.

I can not imagine firestarte does this, firestarter is very old and has not been maintained since 2005.

UFW does not.

To see your ip6 rules you need to use ip6tables

```
sudo ip6tables -L -v
```

If you start UFW or firestarter, you can see your ipv4 rules

```
sudo iptables -L -v
```

but there are no rules for ipv6

```
sudo ip6tables -L -v
```

---

### Post by movieman on 2010-01-26
> **bodhi.zazen said:**
> No, they do not.

Ah, you're right: I just checked the config file and it was IPSEC I had to hack in there.

---

