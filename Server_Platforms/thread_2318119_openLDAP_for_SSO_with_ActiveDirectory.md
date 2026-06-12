---
title: "openLDAP for SSO with ActiveDirectory"
date: 2016-03-23
forum: Server Platforms
---

### Post by Marcwa19197 on 2016-03-23
Hi,

in our company we use mostly linux servers and services. (Postfix, Dovecot, FileServers etc.).
At the moment we are using NIS and Kerberos Tickets for the user authentification with those services.

We also have an running ActiveDirectory domain (Based on WinServer2012R2), which holds seperated users/groups. (so most users which use Windows and Linux services, have two accounts/passwords.)

in the future we are looking for an centralized user system, so we would like to use openLDAP for this. (because we mostly use linux services)

**Now my question is, how to tell ActiveDirectory that it should get the userinformation from the openLDAP server?**
or are there any other single-sign-on solutions / concepts?

Thanks in advice!

---

