---
title: "dpkg-buildpackage fakeroot vs sudo  different results"
date: 2007-01-23
forum: Repositories &amp; Backports
---

### Post by joneZ on 2007-01-23
Hi,

I wanne make a package from XML:RSS::Feed module from cpan. 

Now the Problem is that a test ( from original perl Makefile ) from that module goes 
to a RSS-Feed and wanne read this and do some checks and fails under fakeroot.

here is that test that fails:

[http://search.cpan.org/src/JBISBEE/XML-RSS-Feed-2.212/t/008_store_retrieve.t]("http://search.cpan.org/src/JBISBEE/XML-RSS-Feed-2.212/t/008_store_retrieve.t")


It fails on ....

```
ok( $feed_title->cache,           "Successfully Cached File" );

because it can't find http://www.jbisbee.com/rsstest


```


But when i do 
```
dpkg-buildpackage -rsudo
``` 
it works like a charm ...

The test connects to that feed above and do some hardcoded test with that file. 

But why pass the test with sudo and fail with fakeroot , is that normal ??  

And can I upload packages with sudo, assuming that this is not good ...

Greetings and thx for some hints ...
Erik

---

