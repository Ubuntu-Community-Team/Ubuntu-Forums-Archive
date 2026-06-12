---
title: "LDAP Server Efficiency Question"
date: 2011-08-05
forum: Server Platforms
---

### Post by Affrikka on 2011-08-05
I am working on a school project setting up a virtual LDAP Server and I have a few questions concerning what would be more efficient.

The scenario is that there will be 10 different domains, each with 10 different users. Each domain has to be segregated to where it is completely secluded and won't cross or won't be hacked through another domain. For example, domain A shouldn't be visible on domain B and domain A has no way of accessing domain B.

Would it be more efficient to have one LDAP server running with all 10 domains and all 10 clients on each domain, or would it be more efficient/more secure to have one LDAP for each domain?

I do want to clarify that each LDAP server will be running as a virtual machine, not a physical box.

Thanks,


Mathieu

---

