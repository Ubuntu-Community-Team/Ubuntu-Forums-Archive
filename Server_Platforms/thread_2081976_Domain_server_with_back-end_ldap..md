---
title: "Domain server with back-end ldap."
date: 2012-11-08
forum: Server Platforms
---

### Post by eldaria on 2012-11-08
Hello.

I'm looking for a solution and wondering if this is even possible.

We have a group of windows servers and workstations.
In the company we have a company wide Intranet login that is backed by ldap. So you can make queries against the ldap server to get authenticated.
However, I have no possiblity to modify or add to this ldap system. I only want to piggyback on the authentication, to prevent having an additional username/password for the windows environment.

What I want to do is to set up an Ubuntu server that should act as an Active Directory server for the Windows hosts.
But it should not handle the authentication on it's own, instead I only want to define Usergroups and Hosts here, but the users should be authenticated against the ldap server.

Is this possible, and if so what would be a good read or guide on how to set up such a system?

---

