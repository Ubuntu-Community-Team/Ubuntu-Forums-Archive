---
title: "UEC and ElasticFox doesn't work"
date: 2009-12-29
forum: Server Platforms
---

### Post by cctalma on 2009-12-29
I've installed Enterprice cloud just to test. But I can't get Elestic Fox to find or even add my region :(

I'm following this guide:

[https://help.ubuntu.com/community/UEC/ElasticFox#Configuration](https://help.ubuntu.com/community/UEC/ElasticFox#Configuration)

And this doens't work
*Your UEC instance is seen by [ElasticFox]("https://help.ubuntu.com/community/ElasticFox") as a new region for EC2.  To add a region: *

[LIST=1]
[*]*click on the "Regions" button  *
[*]*Fill "Region Name" with any string describing your UEC setup *
[*]*Fill "Endpoint URL" with http://<cloud-ip-address>:8773/services/Eucalyptus* 
[*]***Click on the "Add" button ***
[*]*Click on "Close"  *
[/LIST]
When I click the add button nothing happens no error. Nothing. The endpoint URL was copied form the credential .zip...

Anyone any idea??

I'm really getting frustrated over here ....

---

### Post by sonoffett on 2010-01-05
I'm having this same problem.

---

### Post by cctalma on 2010-01-05
@sonoffett: I have the sollution:

Since elasticfox 1.7+ the internal cloud is not working proppely. Instead you should download Hybridfox. But there is a but in Hybridfox (which patially covers this issues). The guys who make Hybridfox are fixing it at the moment, but here's the work around:

[http://code.google.com/p/hybridfox/issues/detail?id=6](http://code.google.com/p/hybridfox/issues/detail?id=6)

Good luck!

Chris

---

### Post by bluntknife on 2010-01-21
I'm having the same problem and after following the link from post 3 I still cannot get elasticfox working.

---

### Post by darrenm on 2010-02-24
This is now working fine using HybridFox for me.

---

### Post by chronos00 on 2010-05-02
> **cctalma said:**
> @sonoffett: I have the sollution:

Since elasticfox 1.7+ the internal cloud is not working proppely. Instead you should download Hybridfox. But there is a but in Hybridfox (which patially covers this issues). The guys who make Hybridfox are fixing it at the moment, but here's the work around:

[http://code.google.com/p/hybridfox/issues/detail?id=6](http://code.google.com/p/hybridfox/issues/detail?id=6)

Good luck!

Chris

Thanks!
This worked for me. I still had to use the workaround, though.

@bluntknife:
Be sure you use the workaround, because otherwise I'll be stuck in the same problem you had using ElasticFox.

By the way, I tried using the workaround with ElasticFox, but had no luck. You NEED to use HybridFox

Regards

---

### Post by skimnetster on 2010-05-14
The problem has been resolved in Hybridfox.

Cheers
Prashant Vivek

---

