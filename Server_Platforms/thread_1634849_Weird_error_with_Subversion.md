---
title: "Weird error with Subversion"
date: 2010-12-01
forum: Server Platforms
---

### Post by James78 on 2010-12-01
I'm getting a really weird error in my Apache log about Subversion.
```
[Wed Dec 01 00:08:41 2010] [error] [client xxx.xxx.xxx.xxx] Could not fetch resource information.  [301, #0]
[Wed Dec 01 00:08:41 2010] [error] [client xxx.xxx.xxx.xxx] Requests for a collection must have a trailing slash on the URI.  [301, #0]

```
After some testing, I determined that if I access the repository from

svn.domain.com/repo1

It gives me the error, and it redirects to

svn.domain.com/repo1/

Of course it works without an error if you request it with the / after. But what gives? Anyone know why this could be happening and if there is anything I can do about it?

As another note, the error appears to only come when you browse to the repository with your browser, as if I do the same thing with the SVN CLI client, I don't see any problems. From the looks of the error message, it may be just one of those things you can do nothing about.

---

