---
title: "Ubuntu 8.10 with Squid proxy with LDAP authentication - refresh time?"
date: 2008-11-12
forum: Server Platforms
---

### Post by kungfoomasta on 2008-11-12
I'm setting up a squid proxy, using ldap_auth to provide authentication aginst my Windows domain and ACLs based on AD group membership. Everything seems to work fine, except one thing - when I make a group membership change in AD, squid doesn't seem to pick up on it until after I restart it.

For example, I have a group "fullaccess" in AD. I have an ACL that allows that group unrestricted access to the internet. Everyone else gets denied.
1. I put a user in "fullaccess", restart squid, and that user can access the internet.
2. I take that user out of "fullaccess", and that user can still access the internet.
3. I restart squid, and that user can no longer access the internet.

Is there some sort of ttl that I have to set somewhere, or is this a limitation of Squid, or am I missing something else?

---

