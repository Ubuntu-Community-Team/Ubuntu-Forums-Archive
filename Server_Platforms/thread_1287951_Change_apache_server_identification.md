---
title: "Change apache server identification"
date: 2009-10-10
forum: Server Platforms
---

### Post by Tux.Ice on 2009-10-10
See this screenshot:

[http://imgur.com/05MAm.png](http://imgur.com/05MAm.png)

How do I change this, to for example 'MyWebServer' (just wondering).

Thanks. :popcorn::popcorn:

---

### Post by lkagan on 2009-10-11
In your apache config file, change or add the config item ServerTokens so the value is 'Prod' (no quotes). That will only display 'Apache' with no version. It's the safest. You can't change what it says without modifying source code and compiling your own binary.

---

