---
title: "Gutsy server: Strange nslookup behaviour"
date: 2007-11-21
forum: Server Platforms
---

### Post by ToniVC1963 on 2007-11-21
Hi,

I have two Ubuntu 7.10 servers. Both work ok, but there's something in their nslookup behaviour that I don't understand:

When trying to resolve any non-existen domain (say aaa.bbb.ccc) using nslookup, I get a message like:

"** server can't find aaa.bbb.ccc**.<mydomain>**: NXDOMAIN"

where <mydomain> is my domain name as appears in resolv.conf "domain" directive.

i think this is weird. On all my other systems (many different OS) the answer is always something like:

"** server can't find aaa.bbb.ccc: NXDOMAIN"

that is, without appending my domain to the address I'm trying to resolve. I think this is the correct behaviour. So, why does Ubuntu append my domain to it?? Do your nslookup act like that or it's just mine?

I would understand if nslookup appended my domain when asked for domain names without any dot, like "aaa", but not when at least one dot is present...

Maybe it's not an important issue because name resolution seems to be working flawlessly, but still it puzzles me a lot!

Thanks,

Toni

---

### Post by MJN on 2007-11-21
Do not use nslookup - it is now deprecated due to numerous quirks with its operation. Use **dig** instead.
 
In this instance nslookup appears to be appending your domain the query because the initial query failed and hence it was attempting to 'help' by assuming you missed off the correct domain portion of the name, even if you tried to terminate it with a trailing dot.
 
Either way it's not worth your time wondering about it as you'll find dig is far more robust and predictable.
 
Mathew

---

### Post by ToniVC1963 on 2007-11-21
> **MJN said:**
> Do not use nslookup - it is now deprecated due to numerous quirks with its operation. Use **dig** instead.

OK, I will. I didn't know nslookup was deprecated...
 
> 
In this instance nslookup appears to be appending your domain the query because the initial query failed and hence it was attempting to 'help' by assuming you missed off the correct domain portion of the name, even if you tried to terminate it with a trailing dot.
 
If I terminate it with a trailing dot it seems to work ok. I think you must be right: nslookup tries to help, but does exactly the opposite! What was puzzling me is why Ubuntu nslookup acts differently that the same nslookup on other systems. I was wondering if I had some mistake on my network configuration. But surely you are right and it's not worth the time. I'll use dig instead ;)

Thanks!

Toni

---

