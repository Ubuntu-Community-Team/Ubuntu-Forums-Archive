---
title: "Security through obscurity"
date: 2007-05-31
forum: The Cafe
---

### Post by mips on 2007-05-31
[http://www.iol.co.za/index.php?set_id=1&click_id=13&art_id=nw20070531130320583C902906](http://www.iol.co.za/index.php?set_id=1&click_id=13&art_id=nw20070531130320583C902906)

> Advocate Pat Ellis, SC, for the department, said it was in the public interest not to have the security problems exposed in detail in the public domain.
 
 "Heaven forbid car theft syndicates use the information to break into the system to cover up their crimes," he said.

These idiots make me cringe. They implemented system that was flawed from the word go, ignoring a AG report. Now the general populous suffers due to outages & the possibility of sensitive private information being open to all. Fortunately our constitution is still somewhat sound, very hard to silence anyone in this country which is a good thing. I suspect those to blame will be promoted, thats the usual way things get done here.

In case anyone is wondering what eNaTIS is look here,   [http://www.enatis.com/](http://www.enatis.com/)

---

### Post by Tomosaur on 2007-05-31
Security through obscurity is so laughably poor and INsecure that only a moron would think it was a good idea. We need security through **secure products**, not by hiding any security holes found. All it takes is someone to discover a security hole and start telling everybody about it, and the whole system is defeated.

---

### Post by aysiu on 2007-05-31
I don't know much about security, but it makes logical sense to me that you would warn users about potential security threats but **not** publish the details about how a security hole can be exploited... at least until it has been patched.

---

### Post by az on 2007-05-31
> **aysiu said:**
> I don't know much about security, but it makes logical sense to me that you would warn users about potential security threats but **not** publish the details about how a security hole can be exploited... at least until it has been patched.

That depends on whom is fixing the hole.  In the "many eyes makes for shallow bugs" philosophy, you need to make the exploit available.

All software has bugs.  I think the concensus with FLOSS is that you know where you stand a lot better than with proprietary softeare.

In an *obscure* model, the exploit can remain unpatched for a long time before it is discovered.  In a *transparent* model there is more of a chance that the exploit is found, but it is more likely that it is found by someone who will report it.

Security is taken serously in a transparent model.  The security advisory mechanism is quite robust and mature.  People are paid to keep up-to-date with reported vulnerabilities.

---

### Post by aysiu on 2007-05-31
It's one thing to say, "Hey, we have this buffer overrun possibility here. Users, be aware of this security hole. Developers, if you have patches, please let us know."

It's another thing entirely to say, "Hey, we have this buffer overrun possibility here. If you want to exploit this vulnerability, run this code."

---

### Post by Brunellus on 2007-05-31
> **aysiu said:**
> It's one thing to say, "Hey, we have this buffer overrun possibility here. Users, be aware of this security hole. Developers, if you have patches, please let us know."

It's another thing entirely to say, "Hey, we have this buffer overrun possibility here. If you want to exploit this vulnerability, run this code."
Functionally, they amount to the same thing.

---

### Post by aysiu on 2007-05-31
> **Brunellus said:**
> Functionally, they amount to the same thing.
I guess you're right. If someone knows about a vulnerability and has malicious intent and know-how, she can easily craft the exploiting code.

---

### Post by Brunellus on 2007-05-31
> **aysiu said:**
> I guess you're right. If someone knows about a vulnerability and has malicious intent and know-how, she can easily craft the exploiting code.
It makes no difference how politely the exploit is published--it only matters that the exploit is published at all.  

In a proprietary environment, however, a published exploit is cause for panic:  you're begging God or the maintainers for a fix, since only they can save you.  In a FLOSS environment, it's almost as likely that someone with a perverse desire to squash bugs (and these people do exist) will get it done "just because."

---

