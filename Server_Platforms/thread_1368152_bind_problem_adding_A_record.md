---
title: "bind problem adding A record"
date: 2009-12-30
forum: Server Platforms
---

### Post by xkaliburx on 2009-12-30
Not sure if I need more coffee or what, but here is my problem.  I have 10+ zones all working fine, but one is not responding on the domain.com (note the [www.domain.com](www.domain.com) works fine).

The odd thing is using nslookup, I don't get an error, but no address, note there is NO ww.domain.com which I use to test and do get an error.  See below;
################################################
> server ns1.domain.com
Default Server:  ns1.domain.com
Address:  1.1.1.1

> [www.domain.com](www.domain.com)
Server:  ns1.domain.com
Address:  1.1.1.1

Name:    [www.domain.com](www.domain.com)
Address:  2.2.2.2

> ww.domain.com
Server:  ns1.domain.com
Address:  1.1.1.1

*** ns1.domain.com can't find ww.domain.com: Non-existent domain

> domain.com
Server:  ns1.domain.com
Address:  1.1.1.1

Name:    domain.com
#############################################

So, when I put an A record like ww.domain.com which does NOT exist in the zone file, it does give an error.  When I put the domain.com I don't get the resolution, nor do I get an error.

Any .02 or direction to look?



** Not sure why as the others work fine, but as a workaround, I just stuck an;
domain.com.  IN  A IP  as a record as opposed to the default one I use;
             IN  A IP

and it worked for this domain.  Odd, but sorry to bother.

---

