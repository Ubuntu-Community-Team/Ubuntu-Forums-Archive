---
title: "Firewall UI"
date: 2006-11-19
forum: Server Platforms
---

### Post by mlw4428@gmail.com on 2006-11-19
Ok I know that linux comes with a built=in firewall (IP Tables). I'd love to use it and am looking for a UI that'll help me do it...what's a good one?


I've heard of Firestarter and have used it, it's nice...but I'd like to have something a little bit more advanced (same ease of use, just more features). Anyone got anything?

---

### Post by Jussi Kukkonen on 2006-11-19
think it's pretty much assumed that once firestarter is too simple, one should do it via command line and config files (iptables or shorewall)... You could try  knetfilter, but I've never used it so I can't comment on it.

---

### Post by Klaidas on 2006-11-19
You don't like firestarter because you can do a lot with a simple UI? o_O

---

### Post by mlw4428@gmail.com on 2006-11-19
> **Klaidas said:**
> You don't like firestarter because you can do a lot with a simple UI? o_O

I'm slightly confused as to where you got that idea from...but okay I'll try to help clarify...

I'd like to have some extra customization of my firewall without having to manually do something like scripting out an entire batch of access-control like lists. I'd like something that does something like...

IP Address:+++++++ (Or something to include the range of it)
Port/Packet Type: +++++++
Allow Deny Ask <- If possible

The idea is to have a blacklist at hand that I can update/modify and from what I remember using (maybe I've thought of the wrong program and if so kindly ask for this post to be deleted) Firestarter doesn't have this kind of functionality. If I'm wrong my sincerest apologies this is a recovery after downgrading from Edgy and I just wanted to try out a slightly different setup.

---

### Post by gschoper on 2006-11-19
> **mlw4428@gmail.com said:**
> I'm slightly confused as to where you got that idea from...but okay I'll try to help clarify...

I'd like to have some extra customization of my firewall without having to manually do something like scripting out an entire batch of access-control like lists. I'd like something that does something like...

IP Address:+++++++ (Or something to include the range of it)
Port/Packet Type: +++++++
Allow Deny Ask <- If possible

The idea is to have a blacklist at hand that I can update/modify and from what I remember using (maybe I've thought of the wrong program and if so kindly ask for this post to be deleted) Firestarter doesn't have this kind of functionality. If I'm wrong my sincerest apologies this is a recovery after downgrading from Edgy and I just wanted to try out a slightly different setup.

afaik, what your looking to do can only be done via commandline.

---

### Post by CatalinuX- on 2006-11-20
[http://www.netfilter.org/documentation/index.html](http://www.netfilter.org/documentation/index.html)

I myself would strongly advise you to do things on your own, than rather rely on fancy GUIs that may or may not do what you want. Anyway, there will surely be a moment in time when you will need to use iptables manually, so it's better to learn it. C'mon, it's not that hard. And you will feel a lot more powerful after finishing learning it. :D

---

