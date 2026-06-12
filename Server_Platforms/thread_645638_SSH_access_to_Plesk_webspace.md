---
title: "SSH access to Plesk webspace"
date: 2007-12-20
forum: Server Platforms
---

### Post by The_Fallen on 2007-12-20
Hi,

I have a vserver with Ubuntu and Plesk. After creating a new domain with Plesk, there is a directory structure like this:

```

# ls -al
total 14
drwxr-xr-x 14 root      root    1024 Dec 19 13:24 .
drwxr-xr-x  8 root      root    1024 Dec 19 13:24 ..
drwxr-x---  5 fallen    psaserv 1024 Dec 19 13:24 anon_ftp
drwxr-xr-x  2 root      psaserv 1024 Dec 19 13:24 bin
drwxr-x---  3 fallen    psaserv 1024 Dec 19 13:24 cgi-bin
drwxr-x---  2 root      psaserv 1024 Dec 19 15:21 conf
drwxr-xr-x  2 root      psaserv 1024 Dec 19 13:24 error_docs
drwxr-x--- 11 fallen    psaserv 1024 Dec 19 14:36 httpdocs
drwxr-x---  7 fallen    psaserv 1024 Dec 19 13:24 httpsdocs
drwxr-x---  2 root      psaserv 1024 Dec 19 15:03 pd
drwx------  2 fallen    root    1024 Dec 19 13:24 private
dr-xr-x---  7 root      psaserv 1024 Dec 19 13:24 statistics
drwxr-xr-x  4 root      psaserv 1024 Dec 19 13:25 subdomains
drwxr-xr-x  2 root      psaserv 1024 Dec 19 13:24 web_users

```

Unfortunately with Plesk I need to create a new user for every domain ('fallen' for this domain). Since I already have a shell login for that server, I would like to use that one to manage my homepages, too.

The problem is just: how to do that? I don't really want to change anything in the directory structure created by Plesk. That would mean work for me every time I create a new (sub)domain.

Adding myself to the "psaserv" group also doesn't solve the problem, since the "httpdocs" doesn't have write permissions for the group.

Any ideas, what I could do about this?

thx,
fallen

---

