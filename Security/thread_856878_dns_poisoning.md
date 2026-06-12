---
title: "dns poisoning"
date: 2008-07-11
forum: Security
---

### Post by kevmitch on 2008-07-11
Was reading this article today that I found on Linux Today:
[http://practical-tech.com/operating-system/preventing-dns-poisoning-in-linux/](http://practical-tech.com/operating-system/preventing-dns-poisoning-in-linux/)

I actually heard about this a couple days ago. It seems especially relevant in the context of the recent research into package management security which is being discussed in this thread: [http://ubuntuforums.org/showthread.php?t=855829](http://ubuntuforums.org/showthread.php?t=855829).

Can someone please explain what this means to the average user in plain English. In particular does it matter to you if you aren't running a DNS server yourself, but merely accessing one as most users are?

Of course, it shouldn't do any harm just to make sure your system is up to date regardless, but it's probably better to be conscious of what the vulnerabilities being fixed are. And more importantly to what degree they ARE fixed.

Also, part of me is wondering why this is news. I mean anyone with half a security conscious brain knows that you need to be wary of both DNS AND ip spoofing. Does this vulnerability just mean that DNS spoofing is easier than previously thought?

---

### Post by The Tronyx on 2008-07-12
> **kevmitch said:**
> Does this vulnerability just mean that DNS spoofing is easier than previously thought?

Not sure if I grasp your post in its entirety but security researcher Dan Kaminsky will drop some bombshells regarding just how flawed DNS has been since it's inception in August at BlackHat.  That may be neither here nor there but as far as previously thought, that depends largely upon what DNS software is being used and how it is configured and what other security measures are put in place.  IIRC DNS poisoning was never thought to be terribly hard but some recent research has apparently simplified it to point-and-click doability.  This research is what I was referring to previously.

> 
Can someone please explain what this means to the average user in plain English. In particular does it matter to you if you aren't running a DNS server yourself, but merely accessing one as most users are?

> 
Normally, an Internet-connected computer uses a DNS server provided by the computer owner's Internet Service Provider, or ISP. This DNS server generally serves the ISP's own customers only and contains a small amount of DNS information cached by previous users of the server. A poisoning attack on a single ISP DNS server can affect the users serviced directly by the compromised server or indirectly by its downstream server(s) if applicable.

To perform a cache poisoning attack, the attacker exploits a flaw in the DNS (Domain Name Server) software that can make it accept incorrect information. If the server does not correctly validate DNS responses to ensure that they have come from an authoritative source, the server will end up caching the incorrect entries locally and serve them to users that make the same request.

This technique can be used to replace arbitrary content for a set of victims with content of an attacker's choosing. For example, an attacker poisons the IP address DNS entries for a target website on a given DNS server, replacing them with the IP address of a server he controls. He then creates fake entries for files on the server they control with names matching those on the target server. These files could contain malicious content, such as a worm or a virus. A user whose computer has referenced the poisoned DNS server would be tricked into thinking that the content comes from the target server and unknowingly download malicious content.


Source: [http://en.wikipedia.org/wiki/DNS_cache_poisoning](http://en.wikipedia.org/wiki/DNS_cache_poisoning)

---

### Post by kevmitch on 2008-07-14
Aha, this is exactly what I was looking for:
[http://www.debian-administration.org/articles/602](http://www.debian-administration.org/articles/602)

Thanks again Debian!

---

