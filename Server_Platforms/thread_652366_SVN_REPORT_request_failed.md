---
title: "SVN: REPORT request failed"
date: 2007-12-28
forum: Server Platforms
---

### Post by The_Fallen on 2007-12-28
Hi,

I'm trying to get a SVN server (using apache/dav) running on Ubuntu 7.10.

Everything works fine, if I access the repository locally on the server ('svn co file:://svn/project/'). LIST requests also work fine, if I try to access from a remote machine ('svn list http://domain.com/project/]). But if I try to checkout the project, I get an error message:

```

$ svn co http://domain.com/project/
svn: REPORT request failed on /svn/!svn/vcc/default«
svn: Unusable URI: it does not refer to this repository

```

Google gave me some hints that a transparent proxy could cause this problem. But I'm not using one and as far as I know there isn't one at my provider.

So any idea, what this is all about?

thx,
fallen

---

