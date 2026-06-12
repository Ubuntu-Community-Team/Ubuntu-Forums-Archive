---
title: "squidguard blocking subdomains"
date: 2012-08-31
forum: Server Platforms
---

### Post by dcrst75 on 2012-08-31
hi
i have squidguard and i want to block all subdomains and all directorys of domain but not root domain.
example: i want access to [www.poker.com]("http://www.poker.com") but not access all subdomains like [www.xxx.poker.com]("http://www.xxx.poker.com") , [www.example.poker.com]("http://www.example.poker.com") etc, and subdirectory like [www.poker.com/game]("http://www.poker.com/game") , [www.poker.com/travel]("http://www.poker.com/travel") , etc
I want only access to root [www.poker.com]("http://www.poker.com") 
how write in urls file of blacklists of squidguard?
thks.

---

### Post by dcrst75 on 2012-08-31
nobody work with squidGuard ?
plese help.
for 2 days I searched this with no luck....

---

### Post by SeijiSensei on 2012-08-31
That's a very strange request.  It's not surprising that you cannot find much help for it.

Do you want to do this for any random URL, or just poker.com?  If the latter, you can add an ACL to squid itself (not squidguard) that will do what you want.  Something like (untested):

```

acl nopokersubs dstdom_regex -i www\..+\.poker\.com$
http_access deny nopokersubs

```

Writing a generic rule for all possible URL patterns that have subdomains would be quite tricky.

---

### Post by dcrst75 on 2012-08-31
thks for reply.
poker.com is an example. i have strange cilents, for that ..i have strange request. i chose squiguard for simply way than squid acl.
I think I understand with subdomains and whant to block all subdirectory because there are many and I dont whant to manualy put all on urls files
ex.
poker.com/x1
.....
poker.com/xN
poker.com/y1/z1
etc....

---

