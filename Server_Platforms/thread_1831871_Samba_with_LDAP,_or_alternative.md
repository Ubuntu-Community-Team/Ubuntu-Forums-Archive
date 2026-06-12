---
title: "Samba with LDAP, or alternative"
date: 2011-08-24
forum: Server Platforms
---

### Post by ragnarok189 on 2011-08-24
To start off with, this is not my first solution to a problem, to post on this forum. I've been beating my head against a brick wall with this problem for months. But it's getting down to crunch time, so here goes.

I am a sysadmin on a university campus, and this university campus has a very limited LDAP server (username, password, full name. That's it), but it is heavily used. We have most of our servers and labs configured to authenticate against it, so it is easy for all the students to use the same password as the online web apps.

EDIT: To be clear, I do not have any control, whatsoever, over the central LDAP server. I am not central IT, I am just a college sysadmin.

Now my problem lies in trying to get SAMBA set up to map drives using the same credentials as the login credentials. I don't want a DC, I just want a mapped network drive (with obvious security), but no GP's, no printer server, just network drives. We can configure our SAMBA to hit our own office LDAP server with all the right POSIX information, but we can't get it to just look at the LDAP server for password to username matching.

My ultimate goal is to have a SAMBA server hit LDAP ONLY for password, and use a different file, maybe /etc/passwd & /etc/group for all the other information like path and group memberships. If this is not possible, is there an SMB or CIFS compliant file server that runs on Ubuntu that plays nice with Win XP - 7? That satisfies my strict LDAP requirements?

Thank you in advance for reading this long post.

Ragnarok189

---

