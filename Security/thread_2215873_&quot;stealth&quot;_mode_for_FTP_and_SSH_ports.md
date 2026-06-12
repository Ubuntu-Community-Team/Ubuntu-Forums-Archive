---
title: "&quot;stealth&quot; mode for FTP and SSH ports?"
date: 2014-04-08
forum: Security
---

### Post by ieee488 on 2014-04-08
I ran the Common Ports test at [https://www.grc.com/x/ne.dll?rh1dkyd2](https://www.grc.com/x/ne.dll?rh1dkyd2)
and FTP and SSH ports shows as Closed but not Stealth.

Anything I can do in Ubuntu to fix this?

---

### Post by HermanAB on 2014-04-09
It isn't really useful to do that.  The Linux ethernet stack is very rugged.

If you don't want a service to be available, just stop it.

---

### Post by Lars Noodén on 2014-04-09
Also the idea that ports can be 'stealthed' is a myth.   I wish GRC would fix their program.  

[list]
[*] [http://www.chiark.greenend.org.uk/~peterb/network/drop-vs-reject](http://www.chiark.greenend.org.uk/~peterb/network/drop-vs-reject)
[*] [http://www.chrisbrenton.org/2009/07/why-firewall-reject-rules-are-better-than-firewall-drop-rules/](http://www.chrisbrenton.org/2009/07/why-firewall-reject-rules-are-better-than-firewall-drop-rules/)
[/list]

Now tarpit, on the other hand, has humor value:[list]
[*] [http://www.netfilter.org/projects/patch-o-matic/pom-external.html#pom-external-TARPIT](http://www.netfilter.org/projects/patch-o-matic/pom-external.html#pom-external-TARPIT)
[/list]

---

### Post by coldraven on 2014-04-09
Would that not be ports on your router rather than your PC?
I found that my Edimax router had Telnet and FTP ports open by default!! I had to enable SPI (whatever that is!) to close them.
SPI is an option in the firewall section of the router.

---

### Post by Xentime on 2014-04-11
> **Lars Noodén said:**
> Also the idea that ports can be 'stealthed' is a myth.

Seconded with "stealth" ports being a myth.

@OP
Stealth ports just make your IP appear as if no one "lives" there, but  even then there are ways for a persistant attacker to know if that is  true or not. I remember reading an article that went more in depth on  how it's done (I'll post it if I can find it again.). It's better to  just harden said services because if you can detect any services being  run, an attacker will be able to just as easily.

I personally wouldn't be too worried about having closed ports being  shown, a skilled attacker will find out if anyone is attached to the IP  unfortunately.

---

### Post by Xentime on 2014-04-11
Sorry about the double post! Could a moderator please delete this. Sorry!

---

