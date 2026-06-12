---
title: "Subversion server help"
date: 2009-08-11
forum: Server Platforms
---

### Post by Barry Carroll on 2009-08-11
Hi All,

I have set up subversion and access to it is via WebDAV. The OS is Ubuntu 8.04 server.

I created the repo with svnadmin create at /usr/local/svn/repo and then places my project in there. I created branches, tags and trunk and then did an svn import to bring them in. This all works fine.

I can do everything that is expected via the web interface but one thing is puzzling me. When I go to the actual repo location at /usr/local/svn/repo/project/trunk I see no files even though I can see them when browsing the repository via the web interface.

There are files corresponding to the revisions in the repo:

```
barry@<server>:/usr/local/svn/repo/db/revs$ ls -l
total 92
-rw-r--r-- 1 www-data www-data   115 Aug  4 17:13 0
-rw-r--r-- 1 www-data www-data 51506 Aug  4 22:53 1
-rw-r--r-- 1 www-data www-data   198 Aug  4 22:57 2
-rw-r--r-- 1 www-data www-data   862 Aug  4 23:00 3
-rw-r--r-- 1 www-data www-data  4260 Aug  5 13:08 4
-rw-r--r-- 1 www-data www-data  1545 Aug  5 13:22 5
-rw-r--r-- 1 www-data www-data  1889 Aug  5 13:31 6
-rw-r--r-- 1 www-data www-data  1330 Aug  5 13:35 7
-rw-r--r-- 1 www-data www-data   890 Aug 10 21:55 8
```

The config in apache is:

```
<Location /svn>
  DAV svn
  SVNPath /usr/local/svn/repo
  AuthType Basic
  AuthName "SVN"
  AuthUserFile /etc/subversion/passwd
  Require valid-user
</Location>
```

There are no conflicting configuration files in apache too.  I initially thought that this was my problem but unfortunately not.

The authentication is working fine when I browse or commit and the repo itself has the same owner / group as the user the webserver is running with.

Am I missing some face palmingly obvious or something else? Many thanks for any help.

---

### Post by karlw on 2009-08-12
Maybe this will at least bump your post.

Seems like there is something funny going on with your permissions.  You could try opening up your permissions (chmod 777) for the SVN repo to see if that fixes your issue.  I'm not sure what the proper perms are for svn hosted with web dav.

Good luck.

---

### Post by Barry Carroll on 2009-08-13
Thanks, it is actually working as designed.  I found out that you cannot use ls in the repo and expect to see your files, you must use svn ls <path>.  It was confusing to me until I learned that ;)

---

