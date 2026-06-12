---
title: "Problems setting up a private svn repository"
date: 2010-09-10
forum: Server Platforms
---

### Post by Milambar on 2010-09-10
I need to set up a private SVN repository, and please don't suggest GIT, as the developers have specified explicitly that they want SVN.

Setting up the repository is no issue:
```

svnadmin create /home/svn/repositoryname

```
I then edit svnserve.conf, authz, and passwd:

```

svnserve.conf:
[general]
anon-access=none
password-db=passwd
authz-db=authz

passwd:
[users]
milambar=fakepass

authz:
[/]
milambar=rw

```

With this config, I found that only I could read or commit, which is what I want (I will add the other users later when I've got it working properly), however, the svn logs were unreadable. 

A bit of google searching suggested I add * = r into authz, which I did.

Now the svn logs work, but anyone can checkout. This is NOT what I need. I need the logs to work and only known users can check out.

Notice, I haven't enabled webDAV, because it will be used via svn:// not http://

Can anyone suggest a fix or what I'm doing wrong?

---

