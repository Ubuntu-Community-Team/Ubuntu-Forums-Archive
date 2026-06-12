---
title: "Bind and windows clients"
date: 2011-06-14
forum: Server Platforms
---

### Post by mist_01 on 2011-06-14
I am trying to set up a DNS server on my local network.  When I set linux clients to use it, it works as expected.  However, when I set windows clients to it, the root name doesn't resolve.  For example, I have a zone called daniel.  On linux "anything.daniel" resolves to the correct ip as does "daniel"  which is the behavior I want.  However, on windows 7, "anything.daniel" resolves correctly, but "daniel" doesn't.  Any ideas why this might be?

I am new to BIND9 so my config is mostly copy and pasted.
Here is my zone file for daniel (where #.#.#.# is the ip I want daniel to resolve to):

@       IN      SOA     ns1.daniel.     admin.daniel. (
                2007031001
                28800
                3600
                604800
                38400 )
        IN      NS              ns1.daniel.
        IN      A               #.#.#.#
*       IN      A               #.#.#.#

---

### Post by mist_01 on 2011-06-15
Turns out the problem was default dns suffixes.  Windows machines will, by default, append a default suffix to any name that is not qualified by a period.  To keep the functionality I wanted, I ended up having my dhcp server hand out a domain-name of "internal" (not actual name) and then set up my dns to have an entry for internal with references for names like "somename".  That way, when windows looks up "somename" it will try "somename.internal" which will resolve correctly.  I also left my original dns entry for "somename" so that "anything.somename" will still resolve correctly.  This combination seems to have given me the configuration I was looking for.

---

