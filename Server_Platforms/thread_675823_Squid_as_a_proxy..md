---
title: "Squid as a proxy."
date: 2008-01-23
forum: Server Platforms
---

### Post by wanabewired on 2008-01-23
Hi,

I want to create a proxy which allows me to masquerade as the IP of the  dedicated box on which the proxy will be running. I don't want the proxy to cache anything at all and I only want to be able to access it from a certain IP address.

Is it squid which I need for this task and also is there a name for this type of config which I can google?

Thanks.

---

### Post by CheShA on 2008-01-23
It sounds to me like you just want to configure a box to act as a NAT router/gateway, you don't need squid for that, just the right netowrk config.  2 NICs would make it easier but are  not strictly neccessary.

---

### Post by wanabewired on 2008-01-28
Hi,

Thanks for the response. I see what you're saying and yes a gateway would fix it but I would only want it to act as a proxy for http. Also, I need the box to function properly as a web server with this proxy functionality tagged on.

Would I not be able to use squid and simply set the level of memory it can use to zero?

Thanks.

---

### Post by MJN on 2008-01-28
Yes - Squid can be configured to not cache anything.
 
Add the following:

acl all src 0.0.0.0/0.0.0.0
no_cache deny all

This sets up an ACL called 'all' covering every possible client, and then denies caching for those clients.

Mathew

---

