---
title: "Help on Apache Request"
date: 2010-01-06
forum: Server Platforms
---

### Post by comingme on 2010-01-06
Done. Thanks for help.

---

### Post by firefly2442 on 2010-01-07
Sounds like a programming syntax error and not an issue with Apache.  I don't know Perl though...

I would suggest searching google for:

```
Can't locate object method "new" via package
```

I came across these: (may or may not be helpful)

[http://www.perlmonks.org/?node_id=642962](http://www.perlmonks.org/?node_id=642962)

[http://www.webmasterworld.com/forum13/4130.htm](http://www.webmasterworld.com/forum13/4130.htm)

It looks like you're trying to instantiate an object.  Oh, maybe the $r that you're passing into the new (constructor probably?) hasn't been instantiated yet or maybe the constructor doesn't take any arguments?  Just some ramblings...

Hope you get it working.  Cheers.  :)

---

