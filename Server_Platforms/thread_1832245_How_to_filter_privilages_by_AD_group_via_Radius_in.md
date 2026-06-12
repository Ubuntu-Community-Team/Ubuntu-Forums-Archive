---
title: "How to filter privilages by AD group via Radius in Apache?"
date: 2011-08-24
forum: Server Platforms
---

### Post by alienimplant on 2011-08-24
I have successfully configured Radius authentication in Apache2 using the auth_radius.load module. The Radius server app is on a Microsoft 2008 R2 server and already has the User Group associated with its network policy. Everything is peachy. Apache authenticates through the Radius server, and the Radius server does all the security group management.

The problem is, I want different accounts to have varied permissions in Apache's www subdirectories. In other words, people in one AD group should be able to access /var/www/site but not /var/www/site/upload. I want another AD admin group to have access to both.

It is very easy to set up multiple User Group network policies and associate them with a single host on the Radius server itself. My question is: how do I select a specific policy per directory in Apache2? It is a fairly straight forward process to configure multiple policies (filter-ids) on our firewall and logging appliances. But in Ubuntu, I cannot find the equivalent with respect to web directories. I've been googling my butt off to no avail.

Has anyone out there gotten past this point with an identical configuration? I am not looking for LDAP-related solutions, only Radius-specific accountability in Apache2. Thanks in advance for any insight.

---

