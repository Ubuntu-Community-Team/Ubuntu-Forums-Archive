---
title: "Squid - cache_peer and http_port or arp"
date: 2012-04-26
forum: Server Platforms
---

### Post by Pimpn8ezy on 2012-04-26
Good Day,

I am running squid 2.7 on our local school internal proxy (Ubuntu) that is behind a larger network proxy (which I don't have control over).

We have started allowing students to access our wireless network as the proliferation of smart phones, tablets and laptops has been steadily increasing.

The problem is Andorid does not play nice with proxies that require authentication.  I had an idea of a way around this that would still tie things to the individual logins.  The solution I have been looking at is to either bind the http_port or MAC address (through arp) to a specific cache peer.  Here is what I was thinking:

Either:
http_port 123 name=student1_port
cache_peer 10.x.x.x parent 3128 no-query login=user:my_pass name=student1_peer
cache_peer_access student1_peer allow student1_port

Or:
cache_peer 10.x.x.x parent 3128 no-query login=user:my_pass name=student1_peer
acl student1_mac arp 01:01:01:01:01:01
cache_peer_access student1_peer allow student1_mac

I was hoping that one of these solutions would allow me to point at the local proxy and avoid having to provide details for the upstream proxy which requires authentication (basic auth - which I continue to rail against).  However, no such luck just yet.  

I am still relatively new to squid, and searches along with trial and error have also been unsuccessful.

Any suggestions would be greatly appreciated.

Cheers.

---

### Post by elico on 2012-04-27
will try to help later but as for now try to also post on the squid users mailing list.
it's the best spot with all squid experts.

---

### Post by Pimpn8ezy on 2012-04-30
I appreciate any assistance.  I have posted to the squid mailing list.  If I do manage to find a workable solution I will be sure to post it here.

Cheers

---

