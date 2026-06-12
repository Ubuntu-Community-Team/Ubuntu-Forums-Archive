---
title: "Firewall fails Shieldsup (only one port)"
date: 2008-11-05
forum: Security
---

### Post by zedx555 on 2008-11-05
Well, I set up Firewall using Firestarter and shieldsup. All ports were stealthed except 1050, which is said to be 'Corba Management Agent' and is open. Is my computer safe? How can I stealth it too?

---

### Post by brian_p on 2008-11-05
> **zedx555 said:**
> Well, I set up Firewall using Firestarter and shieldsup. All ports were stealthed except 1050, which is said to be 'Corba Management Agent' and is open. Is my computer safe? How can I stealth it too?

In the same way you used firestarter to close and stealth all the other ports on the computer. Assuming you were seeing scan results for the machine rather than your router. Which I have some doubts about.

---

### Post by cdenley on 2008-11-05
[http://forums.whirlpool.net.au/forum-replies-archive.cfm/653295.html](http://forums.whirlpool.net.au/forum-replies-archive.cfm/653295.html)

I don't think your router/network is safe. I think that's an administration interface which shouldn't be accessible over the internet.

---

### Post by cariboo on 2008-11-05
I agree with the previous poster, shut down remote management on your router. You only need remote management if you want to manage your router from outside of your internal network, which you shouldn't be doing.

Jim

---

### Post by zedx555 on 2008-11-06
Well, I turned off the router's firewall then tried the test and got 0 stealth. Most were closed and 6 open (along with 1050).  I don't know the difference between checking for router or machine nor do I know anything about administration. This is just a desktop computer in which i'm using ADSL for accessing internet I hope it is not that big of a problem. Thank's for the support anyway.

---

### Post by brian_p on 2008-11-06
> **zedx555 said:**
> Well, I turned off the router's firewall then tried the test and got 0 stealth. Most were closed and 6 open (along with 1050).  I don't know the difference between checking for router or machine nor do I know anything about administration. This is just a desktop computer in which i'm using ADSL for accessing internet I hope it is not that big of a problem. Thank's for the support anyway.

Any probes from the internet (such as those from GRC) hit your router first. They never get beyond it unless they are forwarded. This means your machine never sees them and so it is not checked. It also means setting up a firewall on the machine in this situation is a waste of time and energy.

You probably don't want an extra five ports open on the router. If you are unable to close 1050 and it bothers you there is always the option of forwarding it to a non-existent address, 192.168.19.55 say.

---

### Post by hyper_ch on 2008-11-06
> **brian_p said:**
> any probes from the internet (such as those from grc) hit your router first. They never get beyond it unless they are forwarded. This means your machine never sees them and so it is not checked. It also means setting up a firewall on the machine in this situation is a waste of time and energy.
+1

---

### Post by cdenley on 2008-11-06
> **brian_p said:**
> If you are unable to close 1050 and it bothers you there is always the option of forwarding it to a non-existent address, 192.168.19.55 say.

That was the suggested solution in the thread I linked to, since it is apparently a bug in the firmware of some routers, and the server on port 1050 can't be disabled.

---

### Post by brian_p on 2008-11-06
> **cdenley said:**
> That was the suggested solution in the thread I linked to, since it is apparently a bug in the firmware of some routers, and the server on port 1050 can't be disabled.

It appears TR-069 is involved here. It takes me ages to get to grips with jargon but as far as I can see it is to do with automatic provision of services by remote centralised management. As such, port 1050 would have to open for it to work but I have no definite idea what the security implications for the router are.

[http://www.ixbt.com/comm/adsl/acorp-lan-422/3.7.1_nspwebcfg.pdf](http://www.ixbt.com/comm/adsl/acorp-lan-422/3.7.1_nspwebcfg.pdf)

shows provision for a username/password combination and read-only access. Knowing zedx555's model of router might be helpful.

---

