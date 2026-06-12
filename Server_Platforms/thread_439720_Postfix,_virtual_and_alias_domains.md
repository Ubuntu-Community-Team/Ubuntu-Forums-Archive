---
title: "Postfix, virtual and alias domains"
date: 2007-05-10
forum: Server Platforms
---

### Post by dalto on 2007-05-10
Hi,

I am in the process of migrating my mail server from Red Hat to Ubuntu.  In the process of this I am migrating from qmail to postfix.  But I am struggling to figure out how to implement some functionality using postfix.  I have postfix up and running with virtual users and domains via sql and everything is working.

I host about 20 domains but I only have 3 that are really different.  I have the three different domains setup but I am not sure how to create the aliased domains.

I have found lots of documentation on how to alias to individual mailboxes but not entire domains.

For example:

I want to alias everything that comes to domain1.com and domain2.com to domain5.com.

So [email]bob@domain1.com[/email] is aliased to [email]bob@domain5.com[/email] and [email]jane@domain2.com[/email] is aliased to [email]jane@domain5.com[/email].  Except there are dozens of accounts like this and I don't want to have to do it individually.

I appreciate any advice anyone can provide.

---

### Post by dalto on 2007-05-11
OK, I figured it out. 

@domain1.com @domain5.com

Is a valid alias map.

---

