---
title: "Subversion"
date: 2010-11-17
forum: Server Platforms
---

### Post by The_Fallen on 2010-11-17
Hi,

I'm running Subversion via Apache on a machine with Ubuntu 8.04. I created a new repo using svnadmin in /path/to/repos/myrepo and imported some files locally (to file:///...). When I switched to using Apache, my first try was:
```

<Location />
        DAV svn
        SVNParentPath /path/to/repos
        SVNListParentPath On
</Location>

```
Everything seemed to work fine I could check out the files. But when I tried to commit again after some changes, I got:
```

svn: Commit failed (details follow):
svn: Could not open the requested SVN filesystem
svn: Could not open the requested SVN filesystem

```
Then I changed my Apache config to using SVNPath instead of SVNParentPath, like this:
```

<Location /myrepo>
        DAV svn
        SVNPath /path/to/repos/myrepo
</Location>

```
And now commiting my changes back to the repo works fine.
But like this I'd need to change my config for every new repo, so using SVNParentPath would really be nice.
Any ideas? Thanks.

Cheers,
fallen

---

