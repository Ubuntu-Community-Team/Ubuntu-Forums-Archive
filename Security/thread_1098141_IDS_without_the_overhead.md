---
title: "IDS without the overhead?"
date: 2009-03-16
forum: Security
---

### Post by FiberOptix on 2009-03-16
Hey all,

I've been working on my snort configuration for a little while now and would like to start using it soon, same goes for ossec-hids. However, despite the fact that these appear to be wonderful tools I'm not crazy about setting up mysql and apache services on a stand-alone laptop just to be able to use BASE and OSSEC-HIDS.

Is there any way to use this great tools without the overhead? Maybe I'm crazy but even if I firewall these services and move them to some non-standard high level ports I still find the cost almost equal to the potential gain.

---

### Post by bodhi.zazen on 2009-03-16
Well, to be honest, snort + ossec is not really that much over head.

What are you wanting exactly ?

You can look at Barnyard ;

[http://searchenterpriselinux.techtarget.com/tip/0,289483,sid39_gci1255683,00.html](http://searchenterpriselinux.techtarget.com/tip/0,289483,sid39_gci1255683,00.html)

But really, to be honest, on your lap top, are you running a server ?

If not, just enable ufw and confine any network apps you use with Apparmor.

---

### Post by FiberOptix on 2009-03-16
My point was that since I'm running a *stand alone* laptop, then the *overhead* (as in additional services) from the BASE and ossec tools (like apache, mysql) may just outweigh the benefit of these tools. A good firewall policy & apparmour may be a better solution, as you suggest.

So I wanted to ask if anybody knew of any companion-tools (like BASE) that did the equivalent but without having to enable services like mysql, etc. Barnyard is a good suggestion and I was planning on using it but of course it doesn't have a nice graphical layout like BASE does. Just curious to see if there is much else to be done about this.

---

### Post by The Tronyx on 2009-03-18
There is no less overhead than with Snort/Apache/PHP/MySQL or OSSEC and Apache or whatever.

If you want minimal overhead, look into libsafe and go with Apparmor and a very restrictive IPTables ruleset.

---

