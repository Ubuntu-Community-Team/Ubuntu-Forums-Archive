---
title: "Squid3 and sytem wide proxy settings"
date: 2013-05-08
forum: Server Platforms
---

### Post by tad1073 on 2013-05-08
I have squid3 running as a caching proxy and works fine when I point firefox to my proxy but when I try to apply it system wide I get an error saying that my proxy is refusing connections, any help would be appriciated.

---

### Post by bullet333 on 2013-05-08
I'm not sure if this is the same for Firefox as it is for IE but try only setting proxy for HTTP and leave the rest blank.  I had an issue whenever I had a proxy for Gopher selected.

If I'm not mistaken, Squid only filters HTTP anyways unless you specify in the config.

Also nice 1337 beans :P

---

### Post by tad1073 on 2013-05-08
> **bullet333 said:**
> I'm not sure if this is the same for Firefox as it is for IE but try only setting proxy for HTTP and leave the rest blank.  I had an issue whenever I had a proxy for Gopher selected.

If I'm not mistaken, Squid only filters HTTP anyways unless you specify in the config.

Also nice 1337 beans :P

That's what it was, thanks!:P

I jumped he gun, it's still not working when I apply it in system wide settings.

---

### Post by tad1073 on 2013-05-09
bump

---

