---
title: "LDAP drop outs"
date: 2009-01-15
forum: Server Platforms
---

### Post by stonneway on 2009-01-15
Hi chaps,

We've got a problem with a new ubuntu server which we've setup to be our SVN and TRAC box. For months we've been doing testing on how to move the sites over, configure them for LDAP at the same time, and we haven't had a problem. However, as often happens due to sods law, when the box went live with all our svn sites (around 100 or so with around 80 users) we started getting sudden Internal Server Errors appear in the browsers when viewing Trac sites (or when viewing SVNs in a browser) and the SVN clients reported that they couldn't connect. 

Checking the /var/log/apache2/error.log shows the following for each attempt to view a site.

[Thu Jan 15 08:56:15 2009] [warn] [client <IP>] [29467] auth_ldap authenticate: user administrator authentication failed; URI /svn/project1 [ldap_search_ext_s() for user failed][Can't contact LDAP server]

This is only solved by restarting apache. It all suddenly comes back again for a period of time (maybe 4 hours, may be more or less really). However restarting apache obviously isnt ideal with so many users uploading/downloading info.

The LDAP server in this case is an Active Directory server also handling authentication for other boxes and users, and they continue to authenticate during this period without any problem.

Any ideas what may be causing this sudden drop out or how I can go about finding out more about the problem ?

Olly

---

